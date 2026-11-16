# Análise de jogadores da NBA com Machine Learning

**Pergunta norteadora:** quais são os jogadores mais superfaturados da NBA?

Neste projeto, um **jogador superfaturado** é aquele cujo **salário é maior do que o seu desempenho em quadra justificaria**. A premissa é simples: o salário deveria acompanhar o desempenho. A ideia é treinar um modelo que prevê o salário a partir das estatísticas e, depois, procurar as temporadas em que o salário real ficou muito acima do previsto.

Toda a análise está em [`main.ipynb`](main.ipynb).

---

## Estrutura do repositório

```
├── main.ipynb                 # notebook com toda a análise
├── requirements.txt           # dependências
├── nba/                       # dados
│   ├── career_stats_by_season_with_salary.csv     # fonte: estatísticas por temporada + salário
│   ├── players_bio.csv                            # fonte: dados biográficos (posição, nome)
│   ├── players_stats_by_season_with_salary.csv    # dataset montado no notebook
│   └── dicionario_*.md                            # dicionários de dados de cada CSV
└── modelos/                   # Grid Searches já treinados (.joblib), um por pipeline
```

## Como executar

```bash
pip install -r requirements.txt
jupyter lab main.ipynb
```

O Grid Search é demorado. Se os arquivos em `modelos/` existirem, o notebook **carrega** os resultados em vez de treinar de novo.

---

## O que foi feito

### 1. Montagem do dataset

A fonte tem uma linha por jogador + temporada + tipo de temporada (Regular Season / Playoffs) + time. O salário, por outro lado, é por jogador + temporada. Para chegar a **uma linha por jogador e temporada**:

- **Remoção de inconsistências da fonte** (25 linhas): registros com acertos maiores que tentativas (ex.: `FGM > FGA`), comuns em playoffs dos anos 1940-50. Elas são removidas *antes* de calcular os acumulados para não contaminá-los.
- **Trocas de time**: só existem na Regular Season. Nesses casos fica só a linha `TOT` (soma de todos os times).
- **Quatro blocos de estatísticas** para cada temporada:
  - `Regular_Season_*` e `PLAYOFFS_*`: números **só daquela temporada**;
  - `TOT_Regular_Season_*` e `TOT_PLAYOFFS_*`: acumulado da carreira **antes** daquela temporada (só o passado, para não vazar informação da própria temporada).
- **Experiência** (`*_SEASON_EXP`) e percentuais recalculados a partir de acertos/tentativas.
- `POSITION` vem de `players_bio.csv`.

Resultado: 15.783 temporadas × 90 colunas, salvas em `nba/players_stats_by_season_with_salary.csv` (veja o dicionário de dados correspondente).

### 2. Exploração

- Correlação de cada coluna com o salário: as mais fortes são os **acumulados de carreira** (`TOT_Regular_Season_PTS`, `FG3A`, `FGM`…, ≈ 0,52).
- Histogramas de todas as colunas e dispersões salário × jogos e salário × ano.
- Salário bastante assimétrico: média de US$ 4,8 M, mediana de US$ 2,2 M e moda de US$ 1 M.

### 3. Definição da população

Foram retiradas temporadas que não servem para comparar salário com desempenho:

- **Sem jogos na Regular Season** (9 temporadas): não há desempenho a avaliar.
- **Salário abaixo de US$ 40 mil** (58 temporadas): contratos parciais (10 dias, dispensas), que medem tempo de contrato e não o valor do jogador.

Esses filtros são aplicados **depois** da montagem: as temporadas saem do dataset, mas continuam contando na experiência e nos acumulados das temporadas seguintes. População final: 15.719 temporadas.

### 4. Divisão treino/teste

- Alvo: `SALARY` em dólares.
- Divisão 80/20 com `StratifiedGroupKFold`:
  - **estratificada** por faixa de salário (quintis), mantendo a mesma distribuição de salários nos dois conjuntos;
  - **agrupada por jogador**: todas as temporadas de um jogador ficam no mesmo conjunto, para o modelo não "decorar" o jogador. Nenhum jogador aparece em treino e teste ao mesmo tempo.
- Tudo o que aprende com os dados (imputação, escala, seleção de atributos) é ajustado **só no treino**, dentro de pipelines do scikit-learn.

### 5. Engenharia de atributos e pipelines

Dois transformadores próprios:

- **`AtributosCombinados`**: converte totais em **médias por jogo** (o total depende de quantos jogos o jogador fez; a média mede qualidade), cria a taxa de titular (`GS/GP`) e indicadores `NOVATO`, `FEZ_PLAYOFFS` e `JA_JOGOU_PLAYOFFS` (para o modelo saber que um 0 significa "não jogou", e não "jogou mal"). Percentuais com menos de 10 tentativas viram `NaN` (1 de 1 = 100% não é confiável).
- **`AtributosMinimos`**: mantém só `SEASON_ID`, `POSITION` e as estatísticas mais correlacionadas com o salário em cada bloco (3 + 3 + 2), com a correlação calculada só no treino.

Quatro pipelines foram comparados — o modelo é o mesmo, muda só o que entra nele:

| Pipeline | Atributos |
|---|---|
| `pipeline_main` | colunas originais |
| `pipeline_atbcmb1` | médias por jogo + indicadores (sem os totais) |
| `pipeline_atbcmb2` | médias por jogo + indicadores + totais |
| `pipeline_min_features` | poucas colunas, para permitir polinômio de grau 3 |

Todos terminam no mesmo preparo: numéricos → mediana + padronização; `POSITION` → one-hot.

### 6. Modelos e Grid Search

- **Modelos:** Regressão Linear, Ridge, Elastic Net, Árvore de Decisão e Floresta Aleatória.
- **Regressão polinomial** (graus 1 e 2; grau 3 só no `pipeline_min_features`) nos modelos lineares.
- **Métrica:** RMSE em dólares.
- **Validação cruzada** de 5 folds, também estratificada e agrupada por jogador, com os mesmos folds para todos os pipelines.
- Curvas de aprendizado dos 11 melhores modelos para avaliar sub e sobreajuste.

### 7. Escolha do modelo

| | RMSE treino | RMSE validação |
|---|---|---|
| Floresta Aleatória (`pipeline_atbcmb1`) — menor erro de validação | 0,94 M | 2,97 M |
| **Elastic Net grau 2 (`pipeline_atbcmb1`) — escolhido** | 2,67 M | 3,36 M |

- A **Floresta Aleatória** teve o menor erro de validação, mas está **sobreajustada** (erro de treino muito abaixo do de validação).
- Os modelos lineares de grau 1 quase não sobreajustam, mas erram mais de US$ 4 M: estão **subajustados**.
- O **Elastic Net de grau 2** (`alpha=1`, `l1_ratio=0.8`) tem o melhor equilíbrio entre treino e validação, e suas curvas de aprendizado ainda estão convergindo.

**Teste final** (conjunto separado desde o início): RMSE de **US$ 3,58 M**, apenas ≈ US$ 0,22 M acima da validação — o modelo generaliza de forma consistente.

### 8. Identificação dos superfaturados

1. O modelo escolhido prevê o salário de todas as temporadas.
2. Resíduo = salário real − salário previsto (positivo = ganha mais que o previsto).
3. Como o erro cresce com o tamanho do salário, o resíduo é padronizado **por faixa de salário previsto** (decis), gerando um **z-score**.
4. Uma temporada é considerada **superfaturada** quando `z > 2`.

Temporadas mais superfaturadas encontradas:

| # | Jogador | Temporada | Salário real | Salário previsto | z |
|---|---|---|---|---|---|
| 1 | Jalen Rose | 2006-07 | US$ 16,1 M | US$ 2,6 M | 9,28 |
| 2 | Allen Crabbe | 2016-17 | US$ 18,5 M | US$ 3,4 M | 8,21 |
| 3 | John Stockton | 2002-03 | US$ 7,9 M | US$ 1,0 M | 7,65 |
| 4 | Reed Sheppard | 2024-25 | US$ 10,1 M | US$ 1,8 M | 7,19 |
| 5 | Tim Thomas | 2000-01 | US$ 8,5 M | US$ 1,0 M | 6,98 |

O ranking completo (top 20) está no final do notebook.

---

## Limitações

- O modelo só enxerga estatísticas de quadra; fatores como contratos assinados anos antes, lesões, mercado e escolhas altas de draft (contratos de novato com valor fixo) não estão nos dados — o que explica parte dos casos no topo do ranking (ex.: veteranos em fim de carreira e novatos recém-draftados).
- O erro do modelo (RMSE ≈ US$ 3,5 M) ainda é alto em relação à mediana salarial, por isso o critério usa o z-score por faixa em vez do resíduo absoluto.

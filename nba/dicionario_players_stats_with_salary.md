# Dicionário de dados — `players_stats_by_season_with_salary.csv`


## Identificação e experiência

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `PLAYER_ID` | Player ID | Identificador único do jogador na NBA. Chave para relacionar com `players_bio.csv` (coluna `PERSON_ID`). |
| `SEASON_ID` | Season ID | Ano de **início** da temporada, como inteiro (ex.: `2015` = temporada 2015-16). |
| `POSITION` | Position | Posição em quadra vinda de `players_bio.csv` (ex.: `Guard`, `Forward`, `Center`, `Guard-Forward`). É a posição cadastrada do jogador, igual em todas as temporadas. Pode ser nula (124 linhas). |
| `Regular_Season_SEASON_EXP` | Seasons of Experience (Regular Season) | Nº de temporadas de Regular Season disputadas **até aquela temporada, incluindo ela**. |
| `PLAYOFFS_SEASON_EXP` | Seasons of Experience (Playoffs) | Nº de temporadas com Playoffs disputados **até aquela temporada, incluindo ela** (`0` se nunca foi aos playoffs). |

> Atenção: `*_SEASON_EXP` **inclui** a temporada atual, enquanto os blocos `TOT_*` **não incluem**.

## Regular Season — temporada atual (`Regular_Season_*`)

Números **somente daquela temporada** de Regular Season. Se o jogador trocou de time na temporada, os valores são a soma de todos os times (linha `TOT` da origem). Se não jogou Regular Season no ano, as contagens são `0`.

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `Regular_Season_GP` | Games Played | Total de jogos disputados na Regular Season da temporada. |
| `Regular_Season_GS` | Games Started | Total de jogos como titular na Regular Season da temporada. |
| `Regular_Season_MIN` | Minutes | Total de minutos jogados na Regular Season da temporada. |
| `Regular_Season_FGM` | Field Goals Made | Total de arremessos de quadra (2 e 3 pontos) convertidos na Regular Season da temporada. |
| `Regular_Season_FGA` | Field Goals Attempted | Total de arremessos de quadra tentados na Regular Season da temporada. |
| `Regular_Season_FG_PCT` | Field Goal Percentage | Percentual de acerto de arremessos de quadra na Regular Season da temporada (`Regular_Season_FGM / Regular_Season_FGA`). |
| `Regular_Season_FG3M` | 3-Point Field Goals Made | Total de arremessos de 3 pontos convertidos na Regular Season da temporada. |
| `Regular_Season_FG3A` | 3-Point Field Goals Attempted | Total de arremessos de 3 pontos tentados na Regular Season da temporada. |
| `Regular_Season_FG3_PCT` | 3-Point Field Goal Percentage | Percentual de acerto de arremessos de 3 pontos na Regular Season da temporada (`Regular_Season_FG3M / Regular_Season_FG3A`). |
| `Regular_Season_FTM` | Free Throws Made | Total de lances livres convertidos na Regular Season da temporada. |
| `Regular_Season_FTA` | Free Throws Attempted | Total de lances livres tentados na Regular Season da temporada. |
| `Regular_Season_FT_PCT` | Free Throw Percentage | Percentual de acerto de lances livres na Regular Season da temporada (`Regular_Season_FTM / Regular_Season_FTA`). |
| `Regular_Season_OREB` | Offensive Rebounds | Total de rebotes ofensivos na Regular Season da temporada. |
| `Regular_Season_DREB` | Defensive Rebounds | Total de rebotes defensivos na Regular Season da temporada. |
| `Regular_Season_REB` | Rebounds | Total de rebotes (`OREB + DREB`) na Regular Season da temporada. |
| `Regular_Season_AST` | Assists | Total de assistências na Regular Season da temporada. |
| `Regular_Season_STL` | Steals | Total de roubos de bola na Regular Season da temporada. |
| `Regular_Season_BLK` | Blocks | Total de tocos/bloqueios na Regular Season da temporada. |
| `Regular_Season_TOV` | Turnovers | Total de perdas de bola na Regular Season da temporada. |
| `Regular_Season_PF` | Personal Fouls | Total de faltas pessoais cometidas na Regular Season da temporada. |
| `Regular_Season_PTS` | Points | Total de pontos (`2·FGM + FG3M + FTM`) na Regular Season da temporada. |

## Playoffs — temporada atual (`PLAYOFFS_*`)

Números **somente daquela temporada** de Playoffs. Se o jogador não disputou os playoffs no ano, as contagens são `0`.

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `PLAYOFFS_GP` | Games Played | Total de jogos disputados nos Playoffs da temporada. |
| `PLAYOFFS_GS` | Games Started | Total de jogos como titular nos Playoffs da temporada. |
| `PLAYOFFS_MIN` | Minutes | Total de minutos jogados nos Playoffs da temporada. |
| `PLAYOFFS_FGM` | Field Goals Made | Total de arremessos de quadra (2 e 3 pontos) convertidos nos Playoffs da temporada. |
| `PLAYOFFS_FGA` | Field Goals Attempted | Total de arremessos de quadra tentados nos Playoffs da temporada. |
| `PLAYOFFS_FG_PCT` | Field Goal Percentage | Percentual de acerto de arremessos de quadra nos Playoffs da temporada (`PLAYOFFS_FGM / PLAYOFFS_FGA`). |
| `PLAYOFFS_FG3M` | 3-Point Field Goals Made | Total de arremessos de 3 pontos convertidos nos Playoffs da temporada. |
| `PLAYOFFS_FG3A` | 3-Point Field Goals Attempted | Total de arremessos de 3 pontos tentados nos Playoffs da temporada. |
| `PLAYOFFS_FG3_PCT` | 3-Point Field Goal Percentage | Percentual de acerto de arremessos de 3 pontos nos Playoffs da temporada (`PLAYOFFS_FG3M / PLAYOFFS_FG3A`). |
| `PLAYOFFS_FTM` | Free Throws Made | Total de lances livres convertidos nos Playoffs da temporada. |
| `PLAYOFFS_FTA` | Free Throws Attempted | Total de lances livres tentados nos Playoffs da temporada. |
| `PLAYOFFS_FT_PCT` | Free Throw Percentage | Percentual de acerto de lances livres nos Playoffs da temporada (`PLAYOFFS_FTM / PLAYOFFS_FTA`). |
| `PLAYOFFS_OREB` | Offensive Rebounds | Total de rebotes ofensivos nos Playoffs da temporada. |
| `PLAYOFFS_DREB` | Defensive Rebounds | Total de rebotes defensivos nos Playoffs da temporada. |
| `PLAYOFFS_REB` | Rebounds | Total de rebotes (`OREB + DREB`) nos Playoffs da temporada. |
| `PLAYOFFS_AST` | Assists | Total de assistências nos Playoffs da temporada. |
| `PLAYOFFS_STL` | Steals | Total de roubos de bola nos Playoffs da temporada. |
| `PLAYOFFS_BLK` | Blocks | Total de tocos/bloqueios nos Playoffs da temporada. |
| `PLAYOFFS_TOV` | Turnovers | Total de perdas de bola nos Playoffs da temporada. |
| `PLAYOFFS_PF` | Personal Fouls | Total de faltas pessoais cometidas nos Playoffs da temporada. |
| `PLAYOFFS_PTS` | Points | Total de pontos (`2·FGM + FG3M + FTM`) nos Playoffs da temporada. |

## Regular Season — acumulado da carreira até a temporada anterior (`TOT_Regular_Season_*`)

Soma de todas as temporadas de Regular Season **anteriores** à da linha (a temporada atual **não** entra). Na 1ª temporada da carreira, todas as contagens são `0`. Inclui temporadas sem salário registrado (o filtro de salário é aplicado só depois do cálculo).

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `TOT_Regular_Season_GP` | Games Played | Total de jogos disputados na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_GS` | Games Started | Total de jogos como titular na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_MIN` | Minutes | Total de minutos jogados na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FGM` | Field Goals Made | Total de arremessos de quadra (2 e 3 pontos) convertidos na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FGA` | Field Goals Attempted | Total de arremessos de quadra tentados na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FG_PCT` | Field Goal Percentage | Percentual de acerto de arremessos de quadra na Regular Season, acumulado da carreira antes da temporada (`TOT_Regular_Season_FGM / TOT_Regular_Season_FGA`). |
| `TOT_Regular_Season_FG3M` | 3-Point Field Goals Made | Total de arremessos de 3 pontos convertidos na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FG3A` | 3-Point Field Goals Attempted | Total de arremessos de 3 pontos tentados na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FG3_PCT` | 3-Point Field Goal Percentage | Percentual de acerto de arremessos de 3 pontos na Regular Season, acumulado da carreira antes da temporada (`TOT_Regular_Season_FG3M / TOT_Regular_Season_FG3A`). |
| `TOT_Regular_Season_FTM` | Free Throws Made | Total de lances livres convertidos na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FTA` | Free Throws Attempted | Total de lances livres tentados na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_FT_PCT` | Free Throw Percentage | Percentual de acerto de lances livres na Regular Season, acumulado da carreira antes da temporada (`TOT_Regular_Season_FTM / TOT_Regular_Season_FTA`). |
| `TOT_Regular_Season_OREB` | Offensive Rebounds | Total de rebotes ofensivos na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_DREB` | Defensive Rebounds | Total de rebotes defensivos na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_REB` | Rebounds | Total de rebotes (`OREB + DREB`) na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_AST` | Assists | Total de assistências na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_STL` | Steals | Total de roubos de bola na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_BLK` | Blocks | Total de tocos/bloqueios na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_TOV` | Turnovers | Total de perdas de bola na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_PF` | Personal Fouls | Total de faltas pessoais cometidas na Regular Season, acumulado da carreira antes da temporada. |
| `TOT_Regular_Season_PTS` | Points | Total de pontos (`2·FGM + FG3M + FTM`) na Regular Season, acumulado da carreira antes da temporada. |

## Playoffs — acumulado da carreira até a temporada anterior (`TOT_PLAYOFFS_*`)

Soma de todas as temporadas de Playoffs **anteriores** à da linha (a temporada atual **não** entra). Antes do 1º playoff do jogador, todas as contagens são `0`. Inclui temporadas sem salário registrado.

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `TOT_PLAYOFFS_GP` | Games Played | Total de jogos disputados nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_GS` | Games Started | Total de jogos como titular nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_MIN` | Minutes | Total de minutos jogados nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FGM` | Field Goals Made | Total de arremessos de quadra (2 e 3 pontos) convertidos nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FGA` | Field Goals Attempted | Total de arremessos de quadra tentados nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FG_PCT` | Field Goal Percentage | Percentual de acerto de arremessos de quadra nos Playoffs, acumulado da carreira antes da temporada (`TOT_PLAYOFFS_FGM / TOT_PLAYOFFS_FGA`). |
| `TOT_PLAYOFFS_FG3M` | 3-Point Field Goals Made | Total de arremessos de 3 pontos convertidos nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FG3A` | 3-Point Field Goals Attempted | Total de arremessos de 3 pontos tentados nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FG3_PCT` | 3-Point Field Goal Percentage | Percentual de acerto de arremessos de 3 pontos nos Playoffs, acumulado da carreira antes da temporada (`TOT_PLAYOFFS_FG3M / TOT_PLAYOFFS_FG3A`). |
| `TOT_PLAYOFFS_FTM` | Free Throws Made | Total de lances livres convertidos nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FTA` | Free Throws Attempted | Total de lances livres tentados nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_FT_PCT` | Free Throw Percentage | Percentual de acerto de lances livres nos Playoffs, acumulado da carreira antes da temporada (`TOT_PLAYOFFS_FTM / TOT_PLAYOFFS_FTA`). |
| `TOT_PLAYOFFS_OREB` | Offensive Rebounds | Total de rebotes ofensivos nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_DREB` | Defensive Rebounds | Total de rebotes defensivos nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_REB` | Rebounds | Total de rebotes (`OREB + DREB`) nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_AST` | Assists | Total de assistências nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_STL` | Steals | Total de roubos de bola nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_BLK` | Blocks | Total de tocos/bloqueios nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_TOV` | Turnovers | Total de perdas de bola nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_PF` | Personal Fouls | Total de faltas pessoais cometidas nos Playoffs, acumulado da carreira antes da temporada. |
| `TOT_PLAYOFFS_PTS` | Points | Total de pontos (`2·FGM + FG3M + FTM`) nos Playoffs, acumulado da carreira antes da temporada. |

## Alvo

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `SALARY` | Salary | Salário do jogador naquela temporada, em dólares (fonte: HoopsHype). Nunca é nulo. |

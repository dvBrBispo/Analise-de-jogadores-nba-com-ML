# Dicionário de dados — `players_bio.csv`

Uma linha por jogador (5.103 no total), com informações biográficas e de carreira. Chave: `PERSON_ID`.

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `PERSON_ID` | Person ID | Identificador único do jogador na NBA. Chave para relacionar com `career_stats_by_season.csv` (coluna `PLAYER_ID`) e `career_totals.csv`. |
| `FIRST_NAME` | First Name | Primeiro nome. |
| `LAST_NAME` | Last Name | Sobrenome. |
| `DISPLAY_FIRST_LAST` | Display "First Last" | Nome completo no formato "Primeiro Último" (ex.: `LeBron James`). |
| `DISPLAY_LAST_COMMA_FIRST` | Display "Last, First" | Nome completo no formato "Último, Primeiro" (ex.: `James, LeBron`). |
| `DISPLAY_FI_LAST` | Display "F. Last" | Nome abreviado (ex.: `L. James`). |
| `PLAYER_SLUG` | Player Slug | Identificador em texto usado em URLs do site da NBA (ex.: `lebron-james`). |
| `BIRTHDATE` | Birth Date | Data de nascimento. |
| `SCHOOL` | School | Faculdade, colégio ou clube de origem antes da NBA. |
| `COUNTRY` | Country | País de nascimento/origem do jogador. |
| `LAST_AFFILIATION` | Last Affiliation | Última afiliação antes da NBA, no formato "Escola/País". |
| `HEIGHT` | Height | Altura, no formato pés-polegadas (ex.: `6-9`). |
| `WEIGHT` | Weight | Peso em libras (lbs). |
| `SEASON_EXP` | Seasons of Experience | Número de temporadas de experiência na NBA. |
| `JERSEY` | Jersey Number | Número da camisa (do time mais recente, se aplicável). |
| `POSITION` | Position | Posição em quadra (ex.: `Guard`, `Forward`, `Center`). |
| `ROSTERSTATUS` | Roster Status | Situação atual: `Active` (ativo) ou `Inactive` (inativo/aposentado). |
| `GAMES_PLAYED_CURRENT_SEASON_FLAG` | Games Played – Current Season Flag | `Y`/`N`: indica se o jogador tem jogos disputados na temporada vigente. |
| `TEAM_ID` | Team ID | Identificador do último time em que o jogador atuou. |
| `TEAM_NAME` | Team Name | Nome do último time (ex.: `Lakers`). |
| `TEAM_ABBREVIATION` | Team Abbreviation | Sigla do último time (ex.: `LAL`). |
| `TEAM_CODE` | Team Code | Código interno do time (ex.: `lakers`). |
| `TEAM_CITY` | Team City | Cidade do último time. |
| `PLAYERCODE` | Player Code | Código interno do jogador usado pela NBA (para jogadores históricos, costuma ter o prefixo `HISTADD_`). |
| `FROM_YEAR` | From Year | Primeiro ano/temporada em que o jogador atuou na NBA. |
| `TO_YEAR` | To Year | Último ano/temporada em que o jogador atuou na NBA. |
| `DLEAGUE_FLAG` | D-League Flag | `Y`/`N`: se o jogador também passou pela G League (antiga D-League). |
| `NBA_FLAG` | NBA Flag | `Y`/`N`: confirma que o jogador tem passagem pela NBA. |
| `GAMES_PLAYED_FLAG` | Games Played Flag | `Y`/`N`: se o jogador chegou a entrar em quadra em algum jogo oficial da NBA. |
| `DRAFT_YEAR` | Draft Year | Ano em que foi selecionado no draft (ou `Undrafted` se não foi draftado). |
| `DRAFT_ROUND` | Draft Round | Rodada do draft em que foi selecionado. |
| `DRAFT_NUMBER` | Draft Number (Pick) | Posição/número da escolha dentro do draft. |
| `GREATEST_75_FLAG` | NBA 75th Anniversary Team Flag | `Y`/`N`: se o jogador foi eleito um dos 75 maiores da história da NBA (lista de 2021, aniversário de 75 anos da liga). |
| `SUPPLEMENTAL_STATUS` | Supplemental Status | Campo adicional que a NBA só retorna para jogadores atualmente ativos; sem significado documentado oficialmente, geralmente vazio ou `0`. Fica vazio para jogadores inativos. |
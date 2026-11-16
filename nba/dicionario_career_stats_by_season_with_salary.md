# Dicionário de dados — `career_stats_by_season.csv`

Uma linha por combinação de **jogador + temporada + tipo de temporada** (regular ou playoffs). Estatísticas em **totais da temporada** (não médias por jogo) — para obter médias, divida pelo `GP`.

| Coluna | Significado da sigla | Descrição |
|---|---|---|
| `PLAYER_ID` | Player ID | Identificador único do jogador na NBA. Chave para relacionar com `players_bio.csv` (coluna `PERSON_ID`). |
| `SEASON_TYPE` | Season Type | Tipo de temporada: `Regular Season` (temporada regular) ou `Playoffs`. |
| `SEASON_ID` | Season ID | Temporada no formato `AAAA-AA` (ex.: `2015-16`). |
| `LEAGUE_ID` | League ID | Código da liga (`00` = NBA). |
| `TEAM_ID` | Team ID | Identificador único do time em que o jogador atuou naquela temporada. |
| `TEAM_ABBREVIATION` | Team Abbreviation | Sigla do time (ex.: `LAL`, `BOS`, `GSW`). Se o jogador passou por mais de um time na temporada, pode haver mais de uma linha (uma por time, mais uma linha `TOT` de total combinado). |
| `PLAYER_AGE` | Player Age | Idade do jogador durante aquela temporada. |
| `GP` | Games Played | Número de jogos disputados. |
| `GS` | Games Started | Número de jogos em que foi titular. |
| `MIN` | Minutes | Total de minutos jogados na temporada. |
| `FGM` | Field Goals Made | Total de arremessos de quadra (2 e 3 pontos) convertidos. |
| `FGA` | Field Goals Attempted | Total de arremessos de quadra tentados. |
| `FG_PCT` | Field Goal Percentage | Percentual de acerto nos arremessos de quadra (`FGM / FGA`). |
| `FG3M` | 3-Point Field Goals Made | Total de arremessos de 3 pontos convertidos. |
| `FG3A` | 3-Point Field Goals Attempted | Total de arremessos de 3 pontos tentados. |
| `FG3_PCT` | 3-Point Field Goal Percentage | Percentual de acerto de 3 pontos (`FG3M / FG3A`). |
| `FTM` | Free Throws Made | Total de lances livres convertidos. |
| `FTA` | Free Throws Attempted | Total de lances livres tentados. |
| `FT_PCT` | Free Throw Percentage | Percentual de acerto de lances livres (`FTM / FTA`). |
| `OREB` | Offensive Rebounds | Total de rebotes ofensivos. |
| `DREB` | Defensive Rebounds | Total de rebotes defensivos. |
| `REB` | Rebounds | Total de rebotes (`OREB + DREB`). |
| `AST` | Assists | Total de assistências. |
| `STL` | Steals | Total de roubos de bola. |
| `BLK` | Blocks | Total de tocos/bloqueios. |
| `TOV` | Turnovers | Total de perdas de bola. |
| `PF` | Personal Fouls | Total de faltas pessoais cometidas. |
| `PTS` | Points | Total de pontos marcados. |
| `SALARY` | Salary	| Salário do jogador naquela temporada (em dólares), vindo do HoopsHype. |
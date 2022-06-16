# Self-Isolation Game Analysis

This is the repository for the analysis of the Self-Isolation Game.

The analysis is done through first running the 'cleaning_self-isolation-game.Rmd' file in the scripts subdirectory, and then the 'analysis_self-isolation-game.Rmd' file.

Then, in the tables-and-figures folder, there is a 'tables-and-figures_self-isolation-game.Rmd' file, which can be run to reproduce the figures in the manuscript. Those figures are also contained in the folder.

The raw-data folder contains the raw data for the project, and the cleaned-data folder contains a file with the data that comes out after running the 'cleaning_self-isolation-game.Rmd', which can be used if skipping the cleaning phase is desired.

The 'modelling_self-isolation-game.Rmd' contains the simulations used in the manuscript. The 'secondary-analysis...Rmd' script contains the analysis without the participants that failed the attention check.

The R environment has been preserved in a lock file, such that it can be run in the future when the packages have been updated. It is also possible to load the .RData file directly, in order to have all objects in the environment pre-loaded.

## Data structure

The game consists of 11 players and 40 rounds per session. The participant.code is linked to the player ID, but can also be used to link survey responses to the game.

All the measurements are classified according to their level. Most importantly, the player-level, group-level, and session-level.

player.infected indicates whether the player was infected with the virus in that round.

player.contribution is the self-isolation level of that player [0,4]. For example, 0 is no self-isolation, 4 is complete self-isolation. player.actual_payment is proportional to this, and indicates how much income was sacrificed (contribution = 1 corresponds to actual_payment = 10).

player.payoff indicates the points earned by that player in that round.

player.cumulative_earnings tracks the cumulative points of the player up until that point in the game.

player.transmission_chance indicates the player's chance of getting infected in that round given their self-isolation level and that of others.

player.others_contribution indicates the average self-isolation level of others in the group (this was displayed to the participant).

player.timeout indicates whether a player's webpage timed out.

player.second_player_contribution indicates the self-isolation response to hypothetical scenarios. The column ending with 0 corresponds to the scenario where the average self-isolation of others was 'no self-isolation', and this goes up to 'complete self-isolation'.

player.others_prediction indicates what the player predicted others would do in that round. 

The important group variables are group.total_infections, showing how many infected players there are at the beginning of that round; group.lockdown, showing whether the group was in lockdown during that round; and group.lockdown_income where the players' lockdown income is indicated.
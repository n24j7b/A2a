java c
A2a - FIT1054 - Fantasy Football League
0  | Welcome to the FFL  | ⚽
Fantasy Football League
In this assignment, you will embark on an exciting journey of creating a Fantasy Football League system using various data structures and algorithms. You'll design and implement classes to represent players, teams, and the entire football season, ensuring eﬃcient data retrieval and manipulation. This project will challenge your understanding of linked data structures, hash tables, recursion, and iterators, as you simulate a full season of games, manage player and team statistics, and handle dynamic scheduling. By the end of this assignment, you'll have a deeper understanding of how to apply these fundamental concepts in a practical and engaging context.
⚽ Assignment Overview
Create a Fantasy Football League system using linked data structures, hash tables, recursion, and iterators to simulate a season and manage teams and player statistics.
0 Restrictions and Assumptions
.  You cannot modify the data structures folder. Similar to A1a you should import these data
structures as part of your solution orthe assignment. Additionally, you should not modify any ﬁles in the algorithms folder.
.  Please Note: With the advent of A2a, the ban on Python inbuilts is mostly lifted with the
exception of the  sorted  function and  dict  inbuilt type! Feel free to use  list  and it's
functionality. However, you should not be importing other external Python libraries for storing your collections. Using of any banned instructions (unless speciﬁed in the scaﬀold) will    result in the maximum marks penalty of the 'approach' category of the rubric. Note:
the entire assignment can be done without any external libraries.
·  You cannot use any built-in sorting algorithms. You must use one of the sorting algorithms in the scaﬀold OR use a data structure that facilitates sorting algorithms.
·  You cannot use generative AI, machine learning, or any other form. of AI software.
·  You cannot use any hard-coded constants, except the ones provided to you in the constants class. If you need to use a constant, please add it to the constants class.
.  You cannot access the internals of ANY data structures or any classes except the custom classes that you edit in the tasks. You can only access the methods of the data structures that are
provided to you in the scaﬀold. Each use of the internals of a data structure will count as a major mistake and will lose at least half of the marks for the task.
0 Link to the GitHub Scaﬀold
⚠ Important Notes
As you go through the content of the unit, you may realise that the ADT choices you made for some of your previous tasks in this assignment may not be optimal. Hence, it is important to go back and change them if you feel this makes the solution optimal and/or more elegant. Remember that you are being marked on the quality of your code, including scalability and choice of ADTs.
Complexity Notes [Important]
You must adhere to the complexity bounds given in this assignment. Failure to do so will attract hefty penalties, even if your code works.
0  | Structure of the Assignment  | 0This assignment is structured around building a comprehensive Fantasy Football League system by implementing several interconnected classes and data structures. The primary goal is to simulate a football season, managing teams and players while ensuring eﬃcient data retrieval and
manipulation. The assignment focuses on utilizing linked data structures, hash tables, recursion, and iterators.
Classes and Their Roles
.  Player Class:
The  Player  class represents individual football players. Each player has attributes such     as name, age, and position (e.g., goalkeeper, defender, midﬁelder, striker) which is unique (i.e., a player can only have one position).
o   Players also have associated statistics that reﬂ ect their performance, such as games played, goals scored, and assists made.
The  Player  class includes methods to update and retrieve these statistics eﬃciently.    Team Class:
The  Team  class encapsulates a collection of players and the team's overall statistics.
o   Players are stored based on their position, ensuring quick access and management. If    multiple players occupy the same position, they are linked together, creating a chain of players for each position.
o   The team statistics include metrics such as games played, wins, draws, losses, goals for, goals against, goal diﬀerence, points, and results of the last ﬁve games.
Methods in the  Team  class manage adding and retrieving players and updating team statistics.
Season Class:
The  Season  class manages the entire football season, including the teams participating and the schedule of games.
o   It holds a collection of teams and provides methods to add or remove teams from the season.
o   The game schedule is dynamic and can change at any given game week.
The  Season  class includes functionality to simulate the entire season, individual games, and update team statistics based on game outcomes.
o   Additionally, it maintains a leaderboard to track team rankings based on their
performance throughout the season.    Award Class:
o   The Award class is used to manage the player awards for the season. o   It holds a:
reference to the season
the player stat used to allocate awards
the number of players from each team that are receiving the award.
o   Additionally, it maintains a leaderboard to track player awards based on their
performance throughout the season. ·    Interconnections:
Player and Team: Each  Team  object holds a collection of  Player  objects, connecting     individual players to their respective teams. This relationship is crucial for managing and updating player and team statistics as the season progresses.
Team and Season: The  Season  class contains multiple  Team  objects, linking the teams to the overall season framework. The schedule of games involves these teams, and the   season simulation updates team statistics based on game results.
o   Award and Season: The Award class will use the season object to get the players from each team to generate their stats and calculate the ﬁnal player leaderboard.You will learn more about these classes and methods in the tasks that follow. Remember! You are on a continuous learning journey and if at any stage you feel that a particular data type would be better suited for a task, visit your previous tasks and change as necessary!
Player And Team Stats
Over the next few tasks you will learn about team and player statistics. These can be found in the constants .py  ﬁle and are divided into two enum classes. Here is an explanation of each of the    statistics.
Player Stats
1.   GAMES_PLAYED  - Games played by the player this season
2.   GOALS  - Goals scored by the player this season
3.   ASSISTS  - Assists provided by the player this season
4.   TACKLES  - Tackles made by the player this season
5.   INTERCEPTIONS  - Interceptions made by the player this season
6.   STAR_SKILL  - A star rating of the skills of the player (out of 5 stars) this season
7.   WEAK_FOOT_ABILITY  - A star rating of the weak foot ability of the player (out of 5 stars) this
season
8.   WEIGHT  - The weight of the player (in kg) this season
9.   HEIGHT  - The height of the player (in cm not freedom units) this season
NOTE - The  STAR_SKILL  , WEAK_ FOOT_ABILITY  , WEIGHT  ,  HEIGHT  should all be initialised as 0 at the start. These will be randomly generated by the tests.
Team Stats
1.   GAMES_PLAYED  - Games played by the team this season
2.   POINTS  - Points accrued by the team this season.
3.   WINS  - Number of wins by the team this season
4.   DRAWS  - Number of draws by the team this season
5.   LOSSES  - Number of losses by the team this season
6.   GOALS_FOR  - Goals scored for the team this season
7.   GOALS_AGAINST  - Goals scored against the team this season
8.   GOALS_DIFFERENCE  - Goal diﬀerence between scored vs conceded (calculated as  GOALS_FOR  - GOALS_AGAINST )
9.   LAST_FIVE_RESULTS  - The last 5 results of the team this season with the oldest one at the front. This CAN NOT be stored in an ArrayR. For example, if (the most recent) results of the team are   W W L D W then this should hold the appropriate enum values: GameResult.WIN,
GameResult.DRAW, GameResult.LOSS, GameResult.WIN, GameResult.WIN. If the team has  played less than 5 games, then this should contain the results of however many games the team has played.If the team has played NO games this season, then getting this statistic should just return  None  .
NOTE -  GAMES_PLAYED  ,  POINTS  ,  GOAL_DIFFERENCE  and  LAST_ FIVE_RESULTS  are stats that WILL NOT be
manually entered. These need to be calculated as a result of one of the other stats updating. For example - a    WIN  should update the wins by +1, games played by +1 and should add a result to the  LAST_ FIVE_RESULTS . It should also update the points by +3.
Constants and Enums
This assignment includes several enums and constants that are used throughout the assignment. These can be found in the ﬁle  constants .py  .
This ﬁle is dynamic and you can deﬁne your own enums and constants in this ﬁle if required. Here is a description of the constants and enums provided:
1.   GameResult  - This enum contains the possible outcomes of a game. The value of the outcome is the number of points the team gets for achieving that result:
- WIN : 3 points
- DRAW : 1 point
- LOSS - 0 points
2.   Constants  - This enum contains constants that you may ﬁnd convenient for your
implementation. These may or may not be useful for you. As in A1a, the constants should be treated as variable while programming as well as while performing complexity analysis.
1.   SEASON_LENGTH  : number of weeks the season runs for.
2.   TEAM_MIN_PLAYERS  :  minimum number of players in the team
3.   TEAM_MAX_PLAYERS  :  maximum number of players in the team
4.   MAX_NUM_TEAMS  :  maximum number of teams to play in a season
3.   PlayerStats  - This enum contains the various statistics associated with a player (explained in the previous slide)
4.   TeamStats  - This enum contains the various statistics associated with a team (explained in the previous slide)
5.   PlayerPosition  - This enum contains the position of the player (names specify what position they play but if you are keen to learn, you can follow this link).
6.   ResultStats  : This enum contains the statistics returned by a game's result:
1.   HOME_GOALS  : goals scored by the home team
2.   AWAY_GOALS  : goals scored by the away team
3.   GOAL_SCORERS  : an ArrayR of player objects that scored a goal (each mention is worth 1 goal)
4.   GOAL_ASSISTS  : an ArrayR of player objects that assis代 写A2a - FIT1054 - Fantasy Football LeaguePython
代做程序编程语言ted a goal (each mention is worth 1 assist)
5.   TACKLES  : an ArrayR of player objects that made a tackle in the game (each mention is worth 1 tackle)
6.   INTERCEPTIONS  : an ArrayR of player objects that made an interception in the game (each mention is worth 1 interception)
0  | Task 1 The Player Class
The Player Class
You must now modify the  player .py  ﬁle to implement the  Player  class with the following attributes:
·   name  - a string representing the name of the player. The name is given in the  init  method. You can assume the name is unique.
·   position  - a position is given by the  PlayerPosition  in  constants .py  . The position is given in the  init  method.
.   age  - an integer representing the age of the player (must be 18 or higher). The age is given in the   init  method.
.   statistics  - a data structure that holds the values of statistics relevant to the player. A list of    statistics is given in the  constants  ﬁle as  PlayerStats  and on  __init__  these stats should all be set to 0.
and  the following methods:
·    reset_stats  - resets all   PlayerStats  stats to 0.  ·   get_name(self)  - returns the name of the player.
.   get_position(self)  - returns the position of the player.
.   get_statistics(self)  - returns the statistics of the player.
.  __setitem__ (self,  statistic:  PlayerStats,  value:  int)  - updates the value of the statistic passed as   statistic  .
.   __getitem__ (self,  statistic:  PlayerStats)  - returns the value of the statistic passed as
key .
Methods  __str__  and  __ repr__  are included (though not implemented); these are optional to complete but are highly recommended.
·   Complexity analysis is not required for  __str__  and  __ repr__  .
0  | Task 2 - The Team Class
The Team Class
You must now modify the  team .py  ﬁle to implement the  Team  class with the following attributes:
.   number  - A unique number for this team. The ﬁ rst team number should be 1 (then 2, and so on).
·   name  - a string that refers to the team's name. The name is given in the  init  method. You can assume the name is unique.
·   statistics  - a data structure that contains statistics related to the  Team  class. These are
similar (but no the same as the player stats).  A list of statistics is given in the  constants  ﬁle as TeamStats  and on  __init__  these stats should all be set to 0 (with the exception of the
LAST_FIVE_RESULTS  statistic, which should be initialised to an empty container of the ADT of your choice).
·   players  - a collection of  Player  objects grouped by  PlayerPosition , initially provided to
__init__  as an ArrayR of players and then stored with an appropriate ADT to ensure they appear by the player's position (see image below). For example, all goalkeepers are saved together and  all midﬁelders are saved together. To see the possible positions, you can refer to the
PlayerPosition  enum. You can assume that the enum is exhaustive and we will never have another position that doesn't exist in the enum.
HINT - To get the number of values that exist in an enum class  EnumClass  , you can call len(EnumClass) 
NOTE - The order of the players is important. For example - if you get two goalkeepers, where gk1 arrives before gk2 to the team, then gk1 needs to be before gk2 .
See an example of the structure below:
Given an collection of players and their positions in brackets for visual purposes. 
The team class must also implement the following functions:
·   reset_stats  - resets all   TeamStats  stats to the state they were in during initialisation.
.   add_player(self,  player:  Player)  - This method adds a player to the team. The player must be added after the already existing players at that position in the team.
.   remove_player(self,  player:  Player)  - This method removes a player from the team.
·   get_players(position:  PlayerPosition  =  None)  ->  Collection[Player]  |   None  - Returns only the players in a team held that match the PlayerPosition provided return these players
objects in any of the data structures provided to you. The order in which a player was added to the team is important also within this method and is checked by the tests. If the value of position  is None, then it should return ALL players in the team. Do not aﬀect the  team 
instance variable after calling this method, i.e. do not lose data/change ordering after this
method is called. It should return  None  if no players match the provided criteria / the team is empty.
For example - if we called  get_players()  on the team in the example above, it should return a collection of Players in the following order:
[p1, p4, p7, p6, p9, p3, p8, p10, p2, p5]
So; goalkeepers followed by defenders followed by midﬁelders followed by attackers. And the order of the players is as they were added (if the position is the same).
.   get_number(self)  - Returns the team's number. .   get_name(self)  - Returns the team's name.
.   get_statistics(self)  - returns the statistics of the team.
·   get_last_five_ results(self)  ->  Collection[GameResult]  - this method returns the last 5   results in the order speciﬁed on the Player and Team Stats page these results are returned in a    data structure of your choice similar to  get_players  . The order of the match results is checked by the tests to ensure it matches the given requirement please.
.   __setitem__ (self,  statistic:  TeamStats,  value:  int)  - this method updates the value of the statistic that is passed as the  statistic  . Consider the cascading eﬀect of updating a
statistic as well. For example - if we are updating the number of wins, then you need to update the points as well as the last 5 games statistic as well.
For example - if statistic is WINS and the value being passed is n + 1 and the current value of WINS for the team is n, then we do the following:
o   Update the number of WINS by 1
o   Update the number of GAMES_PLAYED by 1 (this should be applied to the team and every player in the team).
o   Update the number of POINTS by adding the value of GameResult.WIN.value (which is set to 3 in the scaﬀold)
o   Add the result to the LAST_FIVE_RESULTS as the latest result.
NOTE - You can assume that  setitem  will always be additive, i.e. we will never call this method to 'reduce' the statistics in any way, it will always add to the existing value.
You should also consider updating  GOAL_DIFFERENCE  , when updating  GOALS_FOR  or
GOALS_AGAINST .
You can assume that  setitem  will never be called on  GOAL_DIFFERENCE  ,
LAST_FIVE_RESULTS  ,  GAMES_PLAYED  ,  POINTS  directly as these get set as a cascading eﬀect of other statistics.
·   __getitem__ (self,  statistic:  TeamStats)  - this method returns the value of the statistic that is passed as the  statistic  .
·   __len__ (self)  - this method returns the number of players in the team
Where possible you should aim to minimise time complexity of the above methods in order to receive full approach marks.
__str__  and  __ repr__  methods for the team class have been provided for you these are optional to complete but are highly recommended.
·   Complexity analysis is not required for  __str__  and  __ repr__  .
#D  | Task 3 - A couple of curious hash tables  | ┳┳
More Hash Tables - Introduction
The idea here is to provide two improvements to our Hash Table implementation. You can complete
the whole assignment without using these implementations, but you may ﬁnd it better to change your previous tasks to use these Hash Tables instead of just using the  LinearProbeTable 
implementation.
In this task we ask that you explore two key factors of the Hashtable ADT;
.  Collision resolution.
.  Hash functions and their performance.To do this you will make two implementations of the Hash Table. Each will be held in a diﬀerent class  within the ﬁles  hashy_perfection_table .py  and  hashy_step_table .py  you already have as part of the assignment's scaﬀold.
The HashyPerfectionTableIn this Hash Table, we will consider a niche example of when we already know the keys and deﬁne a Hash Table with a perfect Hash Function. For simplicity's sake, we will consider only the values that  exist in the  PlayerStats  enum, and no validation is required
The hash function for  HashyPerfectionTable  should return a unique position in the table for each of the stats, which means the following is true and should be true for all keys compared via their hash
values:
sample  =  HashyPerfectionTable()
sample.hash( 'Games  Played')  !=  sample.hash( 'Goals  For')  #  True
In addition to the hash value's output being diﬀerent for the given keys they should also not map to
the same position in the  HashyPerfectionTable  internal array.You must modify the hash method in ﬁle  HashyPerfectionTable .py  to achieve this. You may   increase the table size from 13, but by doing so, you probably will not receive full marks for the approach.
For example, the following would receive 0 marks for this section
def  hash(key:  K)  ->  int:
if  key  ==  "Games  Played":
return  1
elif  key  ==  "Goals  For": return  2
elif  key  ==  "Assists": return  3
#  ...
The HashyStepTable
Our second strategy is to modify the LinearProbeTable in a ﬁle called  hashy_step_table .py  . Our     current implementation uses a ﬁxed step size of 1 when probing through our table. Your task is to     implement a new hash function that will dynamically determine the step size based on the key. Your probe function should use this step size rather than using 1 as the step size.
You will need to implement the following methods to make Hash Table functional.
·    hash2(self,  key:  K)  ->  int  - Used to determine the step size for our Hash Table.
·   _hashy_probe(self,  key:  K,  is_insert:  bool)  - Find the correct position for this key in the Hash Table using linear probing. This method should use the  hash2  method to determine the    step size when probing.
·   delitem(self,  key:  K)  ->  None  - Deletes the item from the Hash Table using a key. You should use lazy deletion / sentinel deletion to implement this.
o   More information can be found in the pre-reading in Week 7 on slide 61.
Make sure you revisit the  _hash_probe  method to ensure your implementation works with the new deletion approach and makes appropriate optimisations.
·   _ rehash(self)  ->  None  - Used to resize the table when it becomes too full (see   setitem      ).
To get full approach marks your  HashyStepTable  should be relatively performant and  hashstep  should
return a variety of diﬀerent step sizes for an input of unique keys, as well as the table being fully functional for all inputs just as the LinearProbeTable is.

         
加QQ：99515681  WX：codinghelp

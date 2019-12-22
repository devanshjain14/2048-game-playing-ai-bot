# 2048 Game Playing AI

We created an AI which could play a game similar to 2048 tile game. We have tried implementing our AI through a game search tree and adversarial search approach.

In order to learn the do's and dont's for the game play, we spent good amount of time playing the game before we actually went on to decide upon which algorithm to choose or what heurisitic is to be deployed. There were several choices for the deterministic or non-deterministic version of the games. But, we went on to implement the algorithm and the heuristics keeping in mind the deterministic version of the game, as non-deterministic yields random choices every time and it's hard to predict the next move of the opponent. Therefore, we decided to keep things simple, and implemented the MinMax Algorithm upto depth 3.

Another important aspect of this problem was to do decide on the heuristics very optimally and openly, rather than going into details for any given situation in a game and deploying heuristics for the same. So we took a combination of three heuristics and gave all those heuristics different weights. The first part of the heuristic tries to maximize the number of empty tiles, which in other words means that we are trying to increase the duration of the game by every move, which also means that we want our AI to delay end of  the game. In the second part of the heuristic we considered the resulting highest tile of each player in the game, i.e. the biggest character and compare it to the respective smallest character for that which is( 'a' or 'A' ) and take its power of 2. 2 to the power of ( 'K' - 'a' ) for example.

The third part of the heuristic tries to make the move to minimize the spread of large valued characters in the mat, and keep them towards the edges, also keeping in mind that we are merging the two highest possible tiles on the board. To implement this we took average of difference of the four neighbours of all the tiles and took the absolute sum of this for all the tiles. Since the higher the difference between neighbours the higher the chance that we aren't merging 2 high possible values and instead just filling up the board. We should rather minimize the difference and collectively increase the value of all the characters so that on merging we can achieve the goal faster. So we subtract this instead of adding this to the resultant heuristic.

We add the first 2 heuristics and subtract the half of the third heuristic to get the resultant heuristic. The reason we scaled down the third heuristic was to diminish the influence of the third heuristic because the first 2 heuristics are of primary importance.

As can be seen from the hierarchy until high characters are achieved above 'e' or so, the influence of the first heuristic is considerable and usually the most. Only when the highest character reaches a certain threshold, its influence becomes maximum and it drives the heuristic significantly. So, the influence of the heuristic progresses with time which is a good thing that the heuristic doesn't remain stagnant throughout.

### How to run the code?
This To run the program from the command line, type in,

Format: ./ijk.py [uppercase-player] [lowercase-player] [mode]

./ijk.py human ai det

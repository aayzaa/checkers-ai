# Checkers AI

_Python-based AI for Checkers, using a minimax algorithm with alpha-beta pruning._

## How to try it 💻

### Requirements

```
python3
```

### Use

Download the files and execute main.py. The program will display the current board state after each move. The bot moves will take place automatically after a small number of seconds.

For the user moves, the program will show a list of possible moves. To select one, introduce the number shown next to it. The moves show the origin coordinates and the ending ones. Example:

```
     ------------------------
 8 |  .  b  .  b  .  b  .  b  | 
 7 |  b  .  b  .  b  .  b  .  | 
 6 |  .  b  .  b  .  .  .  b  | 
 5 |  .  .  .  .  b  .  .  .  | 
 4 |  .  w  .  .  .  .  .  .  | 
 3 |  w  .  w  .  w  .  w  .  | 
 2 |  .  .  .  w  .  w  .  w  | 
 1 |  w  .  w  .  w  .  w  .  | 
     ------------------------
      a  b  c  d  e  f  g  h 

0 : e7 to f6
1 : g7 to f6
2 : b6 to a5
3 : b6 to c5
4 : d6 to c5
5 : h6 to g5
6 : e5 to d4
7 : e5 to f4
Pick move: 3

     ------------------------
 8 |  .  b  .  b  .  b  .  b  | 
 7 |  b  .  b  .  b  .  b  .  | 
 6 |  .  .  .  b  .  .  .  b  | 
 5 |  .  .  b  .  b  .  .  .  | 
 4 |  .  w  .  .  .  .  .  .  | 
 3 |  w  .  w  .  w  .  w  .  | 
 2 |  .  .  .  w  .  w  .  w  | 
 1 |  w  .  w  .  w  .  w  .  | 
     ------------------------
      a  b  c  d  e  f  g  h 
```

To stop the program just type `exit` at any point.

```
Pick move: exit
```

## Process 👩🏽‍💻

My focus when creating this project was to put in practice the theory from an AI course on my university. In that exact course there was not a practical project where to develop a game AI, so I decided to create one by myself using the game of checkers.

The approach I use was to **create the rules of the game and the game itself first**, before creating a bot capable of playing it. In order to do that I created classes for a Player, the Pieces, the Board and some other helper classes used to create a game or display the information onscreen.

After I had a playable checkers program, I **introduced the bots**. In order to do that, the **board always exports a list of possible moves**. The idea is that the bot recollects this possible moves, and performs a **minimax algorithm** by checking the ending board states after X number of moves. 

At first, the program took too long to calculate more than 3/4 moves ahead, so I **added alpha-beta pruning to the algorithm in order to speed up the process**.

Finally, I created some classes to be able to play against the bot in a easier way (as easy as a command-line can get!).

## Results 📊

At all stages, I tested the bot making it play against online bots. There were some losses, since some of the bots online are using a more refined version of minimax (implementing better evaluation rules) or by using some sort of montecarlo algorithm. Regardless of that, I was happy to see that some bots lost against the one I created, specially as I increased the deepthness of the search. 

_PS: I thought that it would be a good idea to try the bot against myself, but I stopped after I lost 10 games in a row... So I sticked with the online bots 🙂._

## Experiment 🔬

In order to alter the color of the players or make bots play against each other, modify lines 26 and 29 on main.py.
There you can also modify the depth of the ```CheckersBot```, which determines how many moves in advance will the computer consider. Increase the depth if you want to improve the bot. Watch out though, the program is not the most optimized (sorry!), so higher values will consume more resources on your computer, sometimes to the point of not working.

```
    # Pick both players, User or RandomBot require a Player parameter...
    black_bot = User(Player.black)
    # ...and CheckerBot does too. An optional parameter is an integer
    # that represents the depth for the Bot. By default is 6.
    white_bot = CheckersBot(Player.white, 6)
```

Other parameters can be tweaked in main.py. For example, to test how well does the ```CheckersBot``` with depth 4 against a random bot in 10 consecutive games, use the following code:

```
    # Pick both players, User or RandomBot require a Player parameter...
    black_bot = RandomBot(Player.black)
    # ...and CheckerBot does too. An optional parameter is an integer
    # that represents the depth for the Bot. By default is 6.
    white_bot = CheckersBot(Player.white, 4)

    # Start Game class selecting how many games will be played.
    game = Game(10)

    # Start the program indicating the white player, the black one,
    # a boolean that requests printing on the console (True prints
    # the board), and who will have the first turn.
    game.simulate(white_bot, black_bot, False, Player.white)
```
Result:
```
White wins: 9
Black wins: 0
Ties: 1
```

## Tools used 🛠️

* [Python](https://www.python.org/) - Language used

## Version 📌

1.1

_+ Better user interface added. The one before was too confusing with the coordinates system.

## Authors ✒️

* **Alex Ayza** - *Keys presser* - [aayzaa](https://github.com/aayzaa)

## License 📄

Use any of the code however you want!

---
⌨️ with ❤️ by [aayzaa](https://https://github.com/aayzaa)

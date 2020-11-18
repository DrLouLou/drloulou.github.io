---
layout: post
title: Conway's Game of Life
---

I came across Conway's [Game of Life]([https://playgameoflife.com/](https://playgameoflife.com/)) recently. It's a very simple but infinite simulation occurring on the surface of a shape called a trefoil knot. 
![Trefoil knot Conway's Game of Life](https://upload.wikimedia.org/wikipedia/commons/6/64/Trefoil_knot_conways_game_of_life.gif)
This type of simulation is called a cellular automaton as the simulation consists of a grid of cells which each can be in any one of a finite number of states. In the case of Conway's Game of Life, each cell can either be populated or unpopulated, live or dead depending on the state of its 8 neighbouring cells. And there are rules dictating when each of these states occur. The rules are:

1. a live cell with fewer than two live neighbour cells dies.
2. a live cell with two or three live neighbour cells lives on to the next generation of cells.
3. a live cell with more than three live neighbour cells dies.
4. a dead cell with exactly three live neighbour cells becomes a live cell.

The initial state of cells is set and then these rules are applied infinitely.

These rules were carefully selected by Conway so as to not produce too rapid growth or decay. Conway wanted [three criteria to be met]([http://pi.math.cornell.edu/~lipa/mec/lesson6.html](http://pi.math.cornell.edu/~lipa/mec/lesson6.html)):

- There should be no initial pattern for which there is a simple proof that the population can grow without limit.
- There should be initial patterns that apparently do grow without limit.
- There should be simple initial patterns that grow and change for a considerable period of time before coming to an end in the following possible ways:
    1. Fading away completely (from overcrowding or from becoming too sparse)
    2. Settling into a stable configuration that remains unchanged thereafter, or entering an oscillating phase in which they repeat an endless cycle of two or more periods.

If you follow the link the above, you'll see a basic pattern at the centre of the grid called a _glider_. This is the most basic type of "spaceship". A spaceship is a configuration of cells that moves stably (meaning the configuration reliably returns to previous forms) across the grid over generations. If you click start you will see this.

Other types of configurations include still lifes (those which persist in their exact initial state and do not decay in any way) and oscillators (those which return to their initial state after a finite number of generations).

Some other interesting patterns are:

 the glider gun

![game of life glider gun]([http://www.scholarpedia.org/w/images/4/43/Game-of-life_Glider-gun.gif](http://www.scholarpedia.org/w/images/4/43/Game-of-life_Glider-gun.gif))

which was the first pattern discovered that grows indefinitely. The group of MIT students who found it were awarded $50 by Conway himself

and the puffer train:

![game of life puffer train]([http://www.scholarpedia.org/w/images/c/ca/Game-of-life_Puffer-train.gif](http://www.scholarpedia.org/w/images/c/ca/Game-of-life_Puffer-train.gif))

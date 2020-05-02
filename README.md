# r_shiny_game_template
Simple template for developing keyboard-based interactive games in shiny

Shiny could serve as a starting point for R developers to make simple games. It is interactive, handles reactivity, and R has nice plotting functions for providing visual output.

Two key challenges need to be resolved for any game that involves continual change over time (e.g. to move a player's character about on the screen).

1. A framerate, where the display regularly updates.
2. Continual responsiviness to user input.

Having found these two links:

1. https://nhsrcommunity.com/blog/animating-a-graph-over-time-in-shiny/
2. https://stackoverflow.com/questions/24973549/r-shiny-key-input-binding/61297911#61297911

It appears that `reactiveTimer` in R will let us create a framerate/regular updates. And that Shiny can use JavaScript to listen for key presses/action. This is sufficient for us to develop a template from. This repo is our game template.

This works, but the next challenge is that  plot speed is very slow, making realtime interaction impossible. Delays of 15 seconds between user input (e.g. holding down the left arrow key for 2 seconds) and output (the dot moving across the screen to the left) were common in our initial attempt.

Significant speed ups obtained by:

1. Using a canvas, as per https://www.r-bloggers.com/accelerating-ggplot2-use-a-canvas-to-speed-up-rendering-plots/
2. Only re-plotting when the game-state changes

Most of the improvements come from the second change. User input is checked multiple times a second (we have defaulted to a target refresh rate of 10 Hz). If user input is detected, then it changes the game state and the plot is redrawn.

As a result of this change, the game responds instantly from idle (no user input --> user input). However, continuous input accumulates lag and the game is often slow to return back to idle (continuous user input --> no input).

Given this performance, games that use discrete changes (e.g. each arrow push moves you one square, push three times to move three squares) are likely to perform better than games that use continuous changes (e.g. hold arrow to move smoothly).

# Working prototype
Simplest_game.R is the simplest game we could think of creating. The arrow keys can be used to move the dot around the screen.

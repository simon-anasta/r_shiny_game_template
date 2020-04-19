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

# Working prototype
Simplest_game.R is the simplest game we have created. The arrow keys can be used to move the dot around the screen.

However, the plot speed is very slow. Hence interactivity is no where close to realtime. Delays of 5 seconds between user input (e.g. holding down the left arrow key for 2 seconds) and output (the dot moving across the screen to the left) were not uncommon.

This issue is caused by plotting. The listener template responds to key-up and key-down events without noticible delay. So keyboard input/output is not the issue. Without faster output/plotting our game template is of little use.

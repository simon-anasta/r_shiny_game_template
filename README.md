# r_shiny_game_template
Simple template for developing keyboard-based interactive games in shiny

Shiny could serve as a starting point for R developers to make simple games. It is interactive, handles reactivity, and R has nice plotting functions for providing visual output.

Two key challenges need to be resolved for any game that involves continual change over time (e.g. to move a player's character about on the screen).

1. A framerate, where the display regularly updates.
2. Continual responsiviness to user input.

Having found these two links:

1. https://nhsrcommunity.com/blog/animating-a-graph-over-time-in-shiny/
2. https://stackoverflow.com/questions/24973549/r-shiny-key-input-binding/61297911#61297911

It appears that `reactiveTimer` in R will let us create a framerate/regular updates. And that Shiny can use JavaScript to listen for key presses/action. This is sufficient for us to develop from.


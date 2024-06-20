# Pygame_Pattern_Drawing
This Python code is well-structured and uses Pygame to create a digital kolam maker. Here's a breakdown with explanations:

**Imports:**

- `pygame`: Provides functionalities for creating games and interactive applications.
- `sys`: Offers system-specific functions and variables (used for exiting the program).
- `os`: Provides operating system interaction functionalities (not used in this code).
- `from pygame.locals import *`: Imports commonly used functions and constants from the Pygame library.

**Global Variables:**

- `total_width`, `width`, `height`: Define the dimensions of the game window and the drawing area.
- `dot_gap`: Spacing between dots displayed on the background grid.
- `mouse_pressed`: Tracks whether the mouse button is currently pressed (0 for not pressed, 1 for pressed).
- `last_pressed`: Stores the coordinates of the last clicked dot.
- `lines`: A list containing lines drawn between connected dots, represented as tuples of starting and ending dot coordinates.
- `image_count`: Counts the number of saved images.
- `max_image_count`: Limits the number of images you can save (set to 10 by default).
- `dot_selection_accuracy`: Tolerance for selecting dots (click within this distance from a dot to register a selection).
- `color_selected`: The currently chosen color for drawing lines.
- `color_box`: Index of the selected color in the color list `clrs`.
- `top`, `left`, `bottom`, `right`: Track the minimum and maximum coordinates of drawn lines to determine the area for capturing the kolam image.
- `clrs`: A list of color tuples representing different color options available for drawing.

**Functions:**

- `terminate()`: Ends the game and exits the program using `pygame.quit()` and `sys.exit()`.
- `print_text(text, x, y, size, color)`: Draws text onto the game window at the specified position with font size and color.
- `draw_line(a, b, c, d, size, color)`: Draws a line between two points (`a`, `b`) and (`c`, `d`) with a specified thickness (`size`) and color.
- `colors()`: Displays a color palette on the screen for selecting the drawing color. It draws rectangles for each color and highlights the currently selected color with a border.
- `capture(display, name, pos, size)`: Takes a screenshot of a specific area on the screen defined by `pos` (top-left corner coordinates) and `size` (width and height). It saves the captured image with the provided `name`.
- `min_max(x, y)`: Updates the `top`, `left`, `bottom`, and `right` variables to track the minimum and maximum coordinates encountered while drawing lines. This helps determine the area to capture when saving the kolam image.
- `dots_nxn()`: Draws a grid of dots on the background as a reference for kolam creation. It also creates buttons for undo, save, and clear actions using black rectangles and text labels.
- `undo(x, y)`: Handles the undo button functionality. If clicked within the undo button area (`x` and `y` coordinates within the button's rectangle) and there are lines drawn (`len(lines) > 0`), it removes the last drawn line from the `lines` list and redraws the kolam with the updated lines using `draw_line` with white color (effectively erasing the last line). It then calls `dots_nxn()` to refresh the grid and buttons.
- `save_image(x, y)`: Handles the save button functionality. If clicked within the save button area and there are lines drawn (`len(lines) > 0`), it checks if the maximum image save limit (`max_image_count`) has been reached. If not, it captures the current kolam drawing as an image using `capture()` with appropriate positioning (`left`, `top`) and size adjustments to avoid empty areas around the kolam. It then increments the `image_count` and displays a message when one image save slot remains.
- `get_color(x, y)`: Detects clicks on the color palette area. If the click coordinates (`x` and `y`) fall within the color palette rectangle, it calculates the corresponding color index based on the position and updates the `color_selected` and `color_box` variables to reflect the chosen color. It then calls `colors()` to redraw the color palette with the updated selection.
- `clear_board(x, y)`: Handles the clear button functionality. If clicked within the clear button area, it clears the entire drawing area by filling the game window with white (`GAMEWINDOW.fill(white)`), resets all lines

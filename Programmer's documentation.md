Snake Game Documentation
Introduction: Snake Game is a classic arcade game where the player controls a snake that moves around the game field, consuming food items (apples) to grow longer. The objective of the game is to guide the snake to eat as much food as possible without colliding with the walls or its own body. The game can be played by one or two players simultaneously, and the players can compete to achieve the highest score.

System Requirements:
Linux-based operating system (tested on Debian)
C programming environment
MZ_APO libraries for controlling the peripherals (LEDs, knobs, LCD display, etc.)
MZ_APO microcontroller

Game Components: The Snake Game consists of the following components:
Game Field: The rectangular area where the snake and apples are displayed. The game field dimensions are 480 pixels (width) by 320 pixels (height).
Snake: The player controls a snake that moves within the game field. The snake grows longer as it consumes apples.
Apples: Food items that appear randomly within the game field. The snake must consume these apples to increase its length and score.
Score: The player's current score (left upper corner), which increases as the snake consumes apples.
Menu: The initial screen where the player can select the number of players and difficulty level.
LCD Display: The graphical display that shows the game field, snake, apples, and score.
LEDs: The row of LEDs that indicates the time remaining before a new apple appears.

Code Structure: The Snake Game code is structured into several files, each responsible for a specific task and represents specific functions. The main functionality:

draw_pictures: Draws main objects on the field:
draw_snake: Draws the snake on the screen with the specified color and updates the score display.
draw_apple: Draws the apple on the screen.

end_page_utils: Choose the finish page, depending on a collide type.
choose_the_end_page: Determines the appropriate end page based on various conditions such as wall hit, win, mutual hit, enemy hit, and scores.
print_the_end_page: Prints the end page on the display based on the result and other parameters. It also handles button input for restarting or leaving the game.
print_wall_hit_result: Prints the end page when a player hits the wall, displaying appropriate messages and scores.
print_self_hit_result: Prints the end page when a player hits themselves, displaying appropriate messages and scores.
print_enemy_hit_result: Prints the end page when a player hits the opponent, displaying appropriate messages and scores.
print_draw_result: Prints the end page when the game ends in a draw, displaying appropriate messages and scores.
print_win_result: Prints the end page when a player wins, displaying the winning player number and scores.
draw_the_winner: Draws the text indicating the winning player.
draw_score: Draws the player's score on the end page.
Various helper functions (draw_text_centered) are used to draw text and manipulate the display.

gameplay_utils: Is responsible for the game logic and LCD row.
snake_init: Initializes the snake's properties such as its head, tail, and coordinates.
draw_game_field: Draws the game field on the display, with a black top part and a green bottom part.
compute_movement: Computes the new direction of the snake based on its previous position and current position.
draw_snake: Draws the snake on the display, including its head and body segments.
redraw_snake: Updates the snake's position, checks for collisions, and redraws the snake on the display.
LCD_update: Updates the LCD display by setting the value of the LED lamps and the LCD line.
place_apple: Places an apple randomly on the game field.
update_score: Updates the score displayed on the screen with the given value and color.

pixel_utils: Consists of the basic functions for drawing pixels and chars. 
draw_text_centered: Draws text centered on the screen with the specified parameters such as text content, y-coordinate, color, scale, and letter spacing.
draw_char: Draws a single character on the screen at the specified coordinates with the specified color and scale.
draw_pixel_big: Draws a scaled pixel on the screen at the specified coordinates with the specified color.
draw_pixel: Draws a single pixel on the screen at the specified coordinates with the specified color.
char_width: Returns the width of a character in pixels based on the font descriptor.
hsv2rgb_lcd: Converts an HSV (hue, saturation, value) color value to an RGB color value suitable for the LCD display.

print_words: Prints words in menu and on the right up corner using draw_char:

Snake: Initializes the game (main function):
draw_home_page: This function is responsible for drawing the home page of the game. It reads the knob positions to detect user input for menu navigation, such as selecting the number of players or difficulty level. It continuously updates the display based on the user's input.
draw_game_page: This function is responsible for drawing the game page. It initializes the game variables and displays the game field, snakes, and game information. It also reads the knob positions to detect user input for controlling the snake's movement. It continuously updates the game state and display based on the user's input and game logic.
draw_menu_choice: This function is called by draw_home_page to draw the current menu choice indicator on the screen. It determines the current and previous knob positions to detect the direction of the user's input and updates the current menu choice accordingly.
draw_players_choice: This function is called by draw_home_page to draw an apple icon indicating the number of players selected.
draw_difficulty_choice: This function is called by draw_home_page to draw an apple icon indicating the difficulty level selected.

MZ_APO provided libraries.

Game Controls: The game controls are based on the knob positions on the MZ_APO board:
Knob 2 (Green): Controls the snake's movement direction for player 1. Menu navigation.
Knob 3 (Blue): Controls the snake's movement direction for player 2 (if two-player mode is selected).
Knob 1 (Red): End the game by clicking.
The knobs can be rotated in two positions (clockwise and counterclockwise) to change the snake's movement direction.

Gameplay:
On the home page, the player can select the number of players (1 or 2) and the difficulty level (easy, medium, hard, death) using the Green knob. The snake head indicates the current row, which can be changed by rotating the knob. Clicking the knob confirms the selection when the moving apple highlights the desired option.
Once the game starts, the snake(s) will appear on the game field, and an apple will be randomly placed.
Players control their respective snakes using the knobs. Rotating the knob clockwise changes the snake's direction clockwise and rotating it counterclockwise changes the direction counterclockwise.
The snake(s) move continuously in the selected direction until they collide with the walls, themselves or the opponent’s snake.
The objective is to guide the snake(s) to eat the apples, which increases their length and score.
If a snake collides with the wall or itself, it results in a game over.
The game continues until at least one player has collided, and a "Game Over" screen will be displayed. Or until the player gets the maximum available number of points (impossible). 
The final scores of all players will be shown on the screen.

Scoring:
Each time a snake consumes an apple, its length increases, and the score is incremented.
The score is calculated based on the length of the snake.

Game Over:
When a game is over (at least one player has collided), a "Game Over" screen will be displayed.
The screen will show the result of the game, such as the collision type (wall collision, self-collision) and the final scores of all players.
Players can press any button to return to the menu.

Additional Features:
Two-player mode: Allows two players to compete simultaneously on the same game field.
Difficulty levels: Provides different levels of gameplay challenge, affecting the snake's speed.
LED countdown: The row of LEDs indicates the time remaining before a new apple appears. The LEDs light up progressively to represent the countdown.

Installation and Execution:
Install the required MZ_APO libraries and dependencies.
Compile and run the Snake Game code using a C compiler in the Linux environment (provided Makefile).
Ensure the MZ_APO board is connected and functional. Check its IP, meaning counting the last row of the squares in binary.
Enter the address of the board to Makefile and simply write “make run” into the Terminal (while in project folder).
Use the knobs on the MZ_APO board to control the snake(s) and menu during gameplay.

Conclusion: The Snake Game is an entertaining and challenging arcade game where players navigate a snake to consume apples while avoiding collisions. The game offers single or two-player modes, multiple difficulty levels, and a user-friendly interface using the MZ_APO board. Enjoy playing the Snake Game and aim for the highest scores!

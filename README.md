# Snake Game

This is a simple Snake game implemented in JavaScript. You can control the snake using your keyboard arrow keys or by swiping on a touch screen device.

## Instructions

1. Use the arrow keys on your keyboard to control the snake's direction.
2. Alternatively, swipe on the screen if you're playing on a touch device.

## How to Play

- Eat apples to grow the snake and increase your score.
- Avoid running into the walls or into the snake's body, or the game will end.

## Game Controls

- **Up Arrow**: Move the snake upwards
- **Down Arrow**: Move the snake downwards
- **Left Arrow**: Move the snake to the left
- **Right Arrow**: Move the snake to the right




# Snake Game Movement Logic

This code is part of the `moveSnake` function, which is responsible for moving the snake's body and head in a
 classic Snake game. This explanation provides a breakdown of the core logic involved.

## Iterating Through Snake s Body
The code iterates through the snakes body, starting from the tail and progressing towards the head.
 This iteration is essential for propagating the snakes movement from one segment to the next.

## Updating Segment Positions
During the iteration, the code updates the position of each snake segment based on the direction of the segment
 in front of it. In a typical Snake game, each segment of the snake follows the one in front of it, mimicking its
position and direction.

## User Input for Direction
User input plays a crucial role in determining the direction of the snakes head. The code checks for user input to
 change `snake.head.nextDirection`. However, its important to note that this change only occurs if the new
 direction is perpendicular to the current direction. This condition prevents the snake from abruptly
 turning back on itself if multiple commands are issued in quick succession before the next update.

## Updating Head Direction and Position
Once the `snake.head.nextDirection` is set if it's a valid perpendicular direction), the code updates the `snake.head.direction` to match the `nextDirection`. This is a key step in preparing the snake for its
 next move. After setting the direction, the code proceeds to update the position of the snake's
head accordingly, effectively moving the snake forward in the selected direction.

This code and explanation are vital for controlling the snake's movement in the game, ensuring that it
 responds to user input and moves in a consistent and intuitive manner while also preventing undesirable, self-contradictory movements.

## Game Features

Here are some additional features of the Snake Game:

- **High Score:** The game keeps track of your high score and displays it on the screen. Try to beat your
 own record!
- **Responsive Design:** The game is designed to work on both desktop and mobile devices. Play on the go!
- **Touch Controls:** If you're playing on a touchscreen device, you can swipe to control the snake, making
it a smooth experience.`

Enjoy the Game! Have fun playing this classic Snake game! If you achieve a high score, your achievement
will be displayed as the "High Score."

## License

This game is open-source and available under the MIT License. You are welcome to modify and enhance it.

## Author

This Snake Game was created by bachar alhamada. You can find more of my projects on my GitHub profile.

## Acknowledgments

Special thanks to the developers of the open-source libraries used in this project, including jQuery.

## Contact# snake-game
# snake-game
[![HTML Badge](https://img.shields.io/badge/-HTML-E34F26?style=for-the-badge&labelColor=black&logo=html5&logoColor=E34F26)](#)
[![CSS Badge](https://img.shields.io/badge/-CSS-1572B6?style=for-the-badge&labelColor=black&logo=css3&logoColor=1572B6)](#)
[![JavaScript Badge](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&labelColor=black&logo=javascript&logoColor=F7DF1E)](#)

## Code Snippet and Explanation

```javascript
// moveSnake() function
function moveSnake() {
  for (let i = snake.body.length - 1; i >= 1; i--) {
    let snakeSquare = snake.body[i];
    let nextSnakeSquare = snake.body[i - 1];

    snakeSquare.direction = nextSnakeSquare.direction;

    repositionSquare(snakeSquare, nextSnakeSquare.row, nextSnakeSquare.column);
  }

  /* snake.head.nextDirection is set using keyboard input and only changes if the
  next direction is perpendicular to snake.head.direction. This prevents the 
  snake from turning back on itself if multiple commands are issued before the
  next update.
  
  snake.head.direction is then only set once at the moment the snake is prepared
  to move forward
  */
  snake.head.direction = snake.head.nextDirection;
  if (snake.head.direction === "left") { snake.head.column--; }
  else if (snake.head.direction === "right") { snake.head.column++; }
  else if (snake.head.direction === "up") { snake.head.row--; }
  else if (snake.head.direction === "down") { snake head.row++; }

  repositionSquare(snake.head, snake.head.row, snake.head.column);

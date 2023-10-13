# snakegame
my snake game website
<!DOCTYPE html>
<html>
<head>
  <title>Snake Game</title>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <h1>Snake Game</h1>
  <canvas id="gameCanvas" width="400" height="400"></canvas>
  <button id="startButton">Start Game</button>
  <button id="pauseButton">Pause Game</button>
  <script src="script.js"></script>
</body>
</html>
body {
  text-align: center;
}

canvas {
  border: 4px solid #000;
  margin-top: 20px;
}

var canvas = document.getElementById("gameCanvas");
var ctx = canvas.getContext("2d");

var snake = [{ x: 200, y: 200 }];
var food = { x: 0, y: 0 };
var dx = 10, dy = 0;
var interval;

function drawSnakePart(snakePart) {
  ctx.fillStyle = "green";
  ctx.fillRect(snakePart.x, snakePart.y, 10, 10);
}

function drawSnake() {
  snake.forEach(drawSnakePart);
}

function drawFood() {
  ctx.fillStyle = "red";
  ctx.fillRect(food.x, food.y, 10, 10);
}

function moveSnake() {
  var newHead = { x: snake[0].x + dx, y: snake[0].y + dy };
  snake.unshift(newHead);

  if (newHead.x === food.x && newHead.y === food.y) {
    generateFood();
  } else {
    snake.pop();
  }
}

function generateFood() {
  food.x = Math.floor(Math.random() * 40) * 10;
  food.y = Math.floor(Math.random() * 40) * 10;
}

function gameLoop() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  moveSnake();
  drawSnake();
  drawFood();
}

document.getElementById("startButton").addEventListener("click", function() {
  if (!interval) {
    interval = setInterval(gameLoop, 100);
  }
});

document.getElementById("pauseButton").addEventListener("click", function() {
  clearInterval(interval);
  interval = null;
});

// Initial setup
generateFood();
drawSnake();

git clone <REPO_URL>
cd <REPO_NAME>
# Copy your files here
git add .
git commit -m "Initial commit"
git push origin main







- 👋 Hi, I’m @adnan525gdg
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!--<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tic Tac Toe</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="game-container">
    <h1>Tic Tac Toe</h1>
    <div class="player-info">
      <div class="player" id="playerX">
        <img src="images/playerX.png" alt="Player X" />
        <span>Player X</span>
      </div>
      <div class="player" id="playerO">
        <img src="images/playerO.png" alt="Player O" />
        <span>Player O</span>
      </div>
    </div>
    <div class="board" id="board">
      <div class="cell" data-index="0"></div>
      <div class="cell" data-index="1"></div>
      <div class="cell" data-index="2"></div>
      <div class="cell" data-index="3"></div>
      <div class="cell" data-index="4"></div>
      <div class="cell" data-index="5"></div>
      <div class="cell" data-index="6"></div>
      <div class="cell" data-index="7"></div>
      <div class="cell" data-index="8"></div>
    </div>
    <div class="status" id="status"></div>
    <div class="game-actions">
      <button id="restartBtn">Restart</button>
      <button id="resetScoresBtn">Reset Scores</button>
    </div>
    <div class="scoreboard">
      <h2>Scoreboard</h2>
      <div id="scoreX">Player X: 0</div>
      <div id="scoreO">Player O: 0</div>
    </div>* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background: linear-gradient(120deg, #f6d365 0%, #fda085 100%);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.game-container {
  text-align: center;
}

h1 {
  margin-bottom: 20px;
}

.player-info {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.player {
  display: flex;
  align-items: center;
}

.player img {
  width: 50px;
  height: 50px;
  margin-right: 10px;
}

.board {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 5px;
  margin-bottom: 20px;
}

.cell {
  width: 80px;
  height: 80px;
  background-color: #fff;
  border: 2px solid #333;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
  cursor: pointer;
}

.status {
  font-size: 1.2rem;
  margin-bottom: 20px;
}

button {
  padding: 10px 20px;
  font-size: 1rem;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

.scoreboard {
  margin-top: 20px;
}

.scoreboard h2 {
  margin-bottom: 10px;
}

.scoreboard div {
  font-size: 1rem;
}
const board = document.getElementById('board');
const cells = document.querySelectorAll('.cell');
const statusDisplay = document.getElementById('status');
const restartBtn = document.getElementById('restartBtn');
const resetScoresBtn = document.getElementById('resetScoresBtn');
const scoreXDisplay = document.getElementById('scoreX');
const scoreODisplay = document.getElementById('scoreO');

let currentPlayer = 'X';
let gameActive = true;
let gameState = ['', '', '', '', '', '', '', '', ''];
let scoreX = 0;
let scoreO = 0;

const winningConditions = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6],
];

function handleCellClick(e) {
  const clickedCell = e.target;
  const clickedCellIndex = parseInt(clickedCell.getAttribute('data-index'));

  if (gameState[clickedCellIndex] !== '' || !gameActive) {
    return;
  }

  gameState[clickedCellIndex] = currentPlayer;
  clickedCell.textContent = currentPlayer;

  checkResult();
}

function checkResult() {
  let roundWon = false;

  for (let i = 0; i < winningConditions.length; i++) {
    const [a, b, c] = winningConditions[i];
    if (gameState[a] === '' || gameState[b] === '' || gameState[c] === '') {
      continue;
    }
    if (gameState[a] === gameState[b] && gameState[a] === gameState[c]) {
      roundWon = true;
      break;
    }
  }

  if (roundWon) {
    statusDisplay.textContent = `Player ${currentPlayer} wins!`;
    updateScore(currentPlayer);
    gameActive = false;
    return;
  }

  if (!gameState.includes('')) {
    statusDisplay.textContent = 'It\'s a draw!';
    gameActive = false;
    return;
  }

  currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
  statusDisplay.textContent = `Player ${currentPlayer}'s turn`;
}

function updateScore(winner) {
  if (winner === 'X') {
    scoreX++;
    scoreXDisplay.textContent = `Player X: ${scoreX}`;
  } else {
    scoreO++;
    scoreODisplay.textContent = `Player O: ${scoreO}`;
  }
}

function restartGame() {
  gameActive = true;
  currentPlayer = 'X';
  gameState = ['', '', '', '', '', '', '', '', ''];
  statusDisplay.textContent = `Player ${currentPlayer}'s turn`;

  cells.forEach(cell => {
    cell.textContent = '';
  });
}

function resetScores() {
  scoreX = 0;
  scoreO = 0;
  scoreXDisplay.textContent = `Player X: ${scoreX}`;
  scoreODisplay.textContent = `Player O: ${scoreO}`;
}

cells.forEach(cell => {
  cell.addEventListener('click', handleCellClick);
});

restartBtn.addEventListener('click', restartGame);
resetScoresBtn.addEventListener('click', resetScores);

  </div>
  <script src="script.js"></script>
</body>
</html>
-
adnan525gdg/adnan525gdg is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

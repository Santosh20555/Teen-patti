# Teen-patti
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>One Patti Shuffler</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background: #f8f8f8; }
    h1 { text-align: center; }
    #results { white-space: pre-wrap; background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
    button { padding: 10px 20px; font-size: 16px; margin-bottom: 20px; }
    input { width: 50px; padding: 5px; margin-right: 10px; }
  </style>
</head>
<body>
  <h1>🎴 One Patti – Black Ace Wins</h1>
  <label for="players"># of Players (Max 17):</label>
  <input type="number" id="players" value="17" min="2" max="17" />
  <button onclick="runGame()">Shuffle & Deal</button>
  <div id="results"></div>

  <script>
    function runGame() {
      const numPlayers = Math.min(17, parseInt(document.getElementById('players').value));
      const suits = ['♠', '♥', '♦', '♣']; // Spades, Hearts, Diamonds, Clubs
      const ranks = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A'];
      let deck = [];

      suits.forEach(suit => {
        ranks.forEach(rank => {
          deck.push(`${suit}${rank}`);
        });
      });

      deck = deck.sort(() => 0.5 - Math.random());

      let output = `\n🎴 One Patti – Round Results:\n\n`;
      let winner = null;

      for (let i = 0; i < numPlayers; i++) {
        const card = deck[i];
        const player = `Player ${i + 1}`;
        if (card === '♠A') {
          output += `${player}: ${card} ✅ WINNER!\n`;
          winner = player;
        } else {
          output += `${player}: ${card}\n`;
        }
      }

      if (!winner) {
        output += `\n😢 No Ace of Spades this round. No winner.`;
      } else {
        output += `\n🏆 Winner: ${winner} (♠A)`;
      }

      document.getElementById('results').textContent = output;
    }
  </script>
</body>
</html>

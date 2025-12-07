<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stopwatch App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <div class="container">
    <h1>Stopwatch</h1>
    <div id="display">00:00:00</div>

    <div class="buttons">
      <button id="start">Start</button>
      <button id="pause">Pause</button>
      <button id="reset">Reset</button>
      <button id="lap">Lap</button>
    </div>

    <h3>Lap Times</h3>
    <ul id="laps"></ul>
  </div>

  <script src="script.js"></script>
</body>

body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: #222;
  color: white;
  font-family: Arial, sans-serif;
  margin: 0;
}

.container {
  text-align: center;
}

#display {
  font-size: 4rem;
  margin: 20px 0;
  letter-spacing: 4px;
}

button {
  margin: 8px;
  padding: 10px 20px;
  font-size: 1rem;
  cursor: pointer;
  border: none;
  border-radius: 6px;
}

button:hover {
  opacity: 0.8;
}

#laps {
  list-style: none;
  padding: 0;
  max-height: 150px;
  overflow-y: auto;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: #222;
  color: white;
  font-family: Arial, sans-serif;
  margin: 0;
}

.container {
  text-align: center;
}

#display {
  font-size: 4rem;
  margin: 20px 0;
  letter-spacing: 4px;
}

button {
  margin: 8px;
  padding: 10px 20px;
  font-size: 1rem;
  cursor: pointer;
  border: none;
  border-radius: 6px;
}

button:hover {
  opacity: 0.8;
}

#laps {
  list-style: none;
  padding: 0;
  max-height: 150px;
  overflow-y: auto;
}
let startTime = 0;
let elapsedTime = 0;
let interval;

const display = document.getElementById("display");
const laps = document.getElementById("laps");

function updateTime() {
  const time = Date.now() - startTime + elapsedTime;

  const ms = Math.floor((time % 1000) / 10);
  const s = Math.floor((time / 1000) % 60);
  const m = Math.floor((time / (1000 * 60)) % 60);

  display.textContent =
    `${String(m).padStart(2, '0')}:${String(s).padStart(2, '0')}:${String(ms).padStart(2, '0')}`;
}

document.getElementById("start").onclick = () => {
  startTime = Date.now();
  interval = setInterval(updateTime, 10);
};

document.getElementById("pause").onclick = () => {
  clearInterval(interval);
  elapsedTime += Date.now() - startTime;
};

document.getElementById("reset").onclick = () => {
  clearInterval(interval);
  elapsedTime = 0;
  display.textContent = "00:00:00";
  laps.innerHTML = "";
};

document.getElementById("lap").onclick = () => {
  const li = document.createElement("li");
  li.textContent = display.textContent;
  laps.appendChild(li);
};

</html>


# PRODIGY_AD_03
STOP WATCH

index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Stopwatch</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>Stopwatch</h1>
    <div id="display">00:00:00</div>
    <div class="buttons">
      <button onclick="start()">Start</button>
      <button onclick="stop()">Stop</button>
      <button onclick="reset()">Reset</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>

style.css
body {
  font-family: new york;
  background-color:#f1eada;
  text-align: center;
  margin-top: 100px;
}

.container {
  background: #aaa396;
  padding: 30px;
  border-radius: 15px;
  display: inline-block;
  box-shadow: 5px 5px 20px #584738;
}

#display {
  font-size: 48px;
  margin: 20px 0;
}

button {
  padding: 10px 20px;
  font-size: 19px;
  margin: 5px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-family: bropella;
}

button:hover {
  background-color: #766850;
}

script.js

let [hours, minutes, seconds] = [0, 0, 0];
let display = document.getElementById("display");
let interval = null;
let running = false;

function updateDisplay() {
  let h = hours < 10 ? "0" + hours : hours;
  let m = minutes < 10 ? "0" + minutes : minutes;
  let s = seconds < 10 ? "0" + seconds : seconds;
  display.innerText = `${h}:${m}:${s}`;
}

function start() {
  if (!running) {
    interval = setInterval(() => {
      seconds++;
      if (seconds === 60) {
        seconds = 0;
        minutes++;
        if (minutes === 60) {
          minutes = 0;
          hours++;
        }
      }
      updateDisplay();
    }, 1000);
    running = true;
  }
}

function stop() {
  clearInterval(interval);
  running = false;
}

function reset() {
  clearInterval(interval);
  [hours, minutes, seconds] = [0, 0, 0];
  updateDisplay();
  running = false;
}

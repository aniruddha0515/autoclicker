# autoclicker
my first project
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <meta name="description" content="Free Auto Clicker Web Tool - Click Automatically with Adjustable Speed">
  <meta name="keywords" content="auto clicker, online auto clicker, click automation, free clicker tool">
  <meta name="robots" content="index, follow">
  <title>Auto Clicker Online - Free Tool</title>
  <style>
    body { font-family: sans-serif; text-align: center; margin-top: 50px; }
    h1 { font-size: 2em; }
    input, button { font-size: 1em; padding: 8px; margin: 10px; }
    #clickArea {
      width: 200px;
      height: 100px;
      border: 2px dashed #999;
      margin: 20px auto;
      line-height: 100px;
      cursor: pointer;
      user-select: none;
    }
  </style>
</head>
<body>
  <h1>🖱️ Auto Clicker Online</h1>
  <p>Click speed (ms between clicks):</p>
  <input type="number" id="intervalInput" value="100" min="10" />
  <br/>
  <button onclick="startClicking()">Start Auto Click</button>
  <button onclick="stopClicking()">Stop</button>
  <div id="clickArea">Click Target</div>
  <p id="status">Status: Not started</p>

  <script>
    let clickInterval;

    function simulateClick(el) {
      const event = new MouseEvent('click', {
        bubbles: true,
        cancelable: true,
        view: window
      });
      el.dispatchEvent(event);
    }

    function startClicking() {
      const interval = parseInt(document.getElementById('intervalInput').value);
      const target = document.getElementById('clickArea');
      if (clickInterval) clearInterval(clickInterval);
      clickInterval = setInterval(() => simulateClick(target), interval);
      document.getElementById('status').textContent = "Status: Auto clicking...";
    }

    function stopClicking() {
      clearInterval(clickInterval);
      clickInterval = null;
      document.getElementById('status').textContent = "Status: Stopped";
    }

    // For testing: log clicks
    document.getElementById('clickArea').addEventListener('click', () => {
      console.log("Click!");
    });
  </script>
</body>
</html>

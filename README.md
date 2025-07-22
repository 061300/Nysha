<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Nysha – A Caçadora Tribal</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      background-color: #101010;
      color: #fff;
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      overflow: hidden;
    }
    canvas {
      display: block;
      margin: 0 auto;
      background-color: #222;
      border: 2px solid #fff;
    }
    #controls {
      margin-top: 10px;
    }
    button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      background: #0f0;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Nysha – A Caçadora Tribal</h1>
  <canvas id="gameCanvas" width="800" height="500"></canvas>
  <div id="controls">
    <button onclick="jump()">Pular</button>
  </div>  <script>
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");

    let nysha = {
      x: 100,
      y: 400,
      width: 50,
      height: 80,
      color: "#0f0",
      jumping: false,
      velocityY: 0,
    };

    function drawNysha() {
      ctx.fillStyle = nysha.color;
      ctx.fillRect(nysha.x, nysha.y, nysha.width, nysha.height);
    }

    function update() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      if (nysha.jumping) {
        nysha.velocityY += 1;
        nysha.y += nysha.velocityY;
        if (nysha.y >= 400) {
          nysha.y = 400;
          nysha.jumping = false;
          nysha.velocityY = 0;
        }
      }
      drawNysha();
      requestAnimationFrame(update);
    }

    function jump() {
      if (!nysha.jumping) {
        nysha.jumping = true;
        nysha.velocityY = -15;
      }
    }

    update();
  </script></body>
</html>

# <!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>كود أخضر متحرك</title>
<style>
  body {
    margin: 0;
    background: black;
    overflow: hidden;
  }
  canvas {
    display: block;
  }
</style>
</head>
<body>
<canvas id="matrix"></canvas>
<script>
  const canvas = document.getElementById('matrix');
  const ctx = canvas.getContext('2d');

  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const letters = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ@#$%^&*()*&^%+-/{}[]|~<>؟'.split('');
  const fontSize = 16;
  const columns = Math.floor(canvas.width / fontSize);
  const drops = new Array(columns).fill(0);

  function draw() {
    // خفيف شفافية الخلفية عشان الكود ما يختفي نهائياً
    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = '#0f0';
    ctx.font = fontSize + 'px monospace';

    for(let i = 0; i < drops.length; i++) {
      const text = letters[Math.floor(Math.random() * letters.length)];
      ctx.fillText(text, i * fontSize, drops[i] * fontSize);

      drops[i]++;

      if(drops[i] * fontSize > canvas.height) {
        drops[i] = 0;
      }
    }
  }

  setInterval(draw, 40);
</script>
</body>
</html>

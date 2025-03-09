<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Мои голые фото</title>
  <link href="https://fonts.googleapis.com/css?family=Montserrat:400,700&display=swap" rel="stylesheet">
  <style>
    /* Сброс стилей */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body, html {
      min-height: 100%;
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
      background-size: 400% 400%;
      animation: gradientAnimation 15s ease infinite;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #fff;
    }
    @keyframes gradientAnimation {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    /* Стиль контейнера */
    .container {
      text-align: center;
      background: rgba(0, 0, 0, 0.5);
      padding: 40px;
      border-radius: 15px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.3);
      max-width: 600px;
      width: 90%;
      transition: transform 0.3s ease;
      will-change: transform;
    }
    h1 {
      margin-bottom: 20px;
    }
    p {
      margin: 15px 0;
      line-height: 1.5;
    }
    /* Стиль кнопки */
    .btn {
      background: #fff;
      color: #333;
      border: none;
      padding: 15px 30px;
      font-size: 1.2em;
      border-radius: 30px;
      cursor: pointer;
      transition: background 0.3s, transform 0.3s;
      font-weight: bold;
      letter-spacing: 1px;
      margin-top: 20px;
    }
    .btn:hover {
      background: #f0f0f0;
      transform: translateY(-3px);
    }
    /* Стиль сообщения */
    .message {
      margin-top: 30px;
      font-size: 1.5em;
      opacity: 0;
      transition: opacity 0.5s ease;
      line-height: 1.4;
    }
    .message.show {
      opacity: 1;
    }
    /* Стиль котика */
    .cat {
      width: 80px;
      margin-top: 15px;
    }
  </style>
</head>
<body>
  <div class="container" id="container">
    <h1>Добро пожаловать!</h1>
    <p>Здесь представлены мои голые фото. Наслаждайся просмотром и опытом.</p>
    <p>Нажмите на кнопку, чтобы увидеть больше.</p>
    <button class="btn" id="btn">перейти</button>
    <div class="message" id="message">
      что ты ожидал тут увидеть?
    </div>
    <img class="cat" src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/50/Cat_Grey.svg/100px-Cat_Grey.svg.png" alt="Котик">
  </div>
  <script>
    // Обработчик клика по кнопке: переключение видимости сообщения и смена текста кнопки
    document.getElementById('btn').addEventListener('click', function() {
      var message = document.getElementById('message');
      this.textContent = this.textContent.trim() === "перейти" ? "закрыть" : "перейти";
      message.classList.toggle('show');
    });

    // Интерактивный эффект наклона контейнера при движении мыши
    var container = document.getElementById('container');
    container.addEventListener('mousemove', function(e) {
      const rect = container.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      const centerX = rect.width / 2;
      const centerY = rect.height / 2;
      const deltaX = (x - centerX) / centerX; // нормализованное значение от -1 до 1
      const deltaY = (y - centerY) / centerY; // нормализованное значение от -1 до 1

      const maxTilt = 10; // максимальный угол наклона в градусах
      const tiltX = deltaY * maxTilt;
      const tiltY = -deltaX * maxTilt;

      container.style.transform = `perspective(1000px) rotateX(${tiltX}deg) rotateY(${tiltY}deg) scale(1.02)`;
    });

    container.addEventListener('mouseleave', function() {
      container.style.transform = 'perspective(1000px) rotateX(0deg) rotateY(0deg) scale(1)';
    });
  </script>
</body>
</html>

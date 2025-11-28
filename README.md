index.html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Мои заметки</title>
  <style>
    :root {
      --bg: #ffffff;
      --text: #2c3e50;
      --note-bg: #f8f9fa;
      --note-border: #3498db;
      --link: #2980b9;
    }

    [data-theme="dark"] {
      --bg: #1a1a1a;
      --text: #ecf0f1;
      --note-bg: #2c2c2c;
      --note-border: #3498db;
      --link: #3498db;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      font-family: -apple-system, BlinkMacSystemFont, sans-serif;
      max-width: 760px;
      margin: 40px auto;
      padding: 0 20px;
      line-height: 1.6;
      transition: background-color 0.3s, color 0.3s;
    }

    .note {
      background: var(--note-bg);
      padding: 18px;
      margin: 24px 0;
      border-left: 4px solid var(--note-border);
      border-radius: 0 6px 6px 0;
      transition: background 0.3s;
    }

    .controls {
      text-align: right;
      margin-bottom: 24px;
    }

    button {
      background: none;
      border: 1px solid var(--note-border);
      color: var(--text);
      padding: 6px 12px;
      border-radius: 4px;
      cursor: pointer;
      font-size: 14px;
    }

    button:hover {
      background: var(--note-border);
      color: white;
    }

    a { color: var(--link); text-decoration: none; }
    a:hover { text-decoration: underline; }
  </style>
</head>
<body>
  <div class="controls">
    <button id="theme-toggle">🌓 Тема</button>
  </div>

  <h1>📝 Заметки Максима</h1>
  <p>Личное. Только для меня. Здесь можно — всё.</p>

  <!-- ↓ Сюда просто добавляй новые блоки по мере необходимости -->
  <div class="note">
    <strong>28 ноября 2025</strong><br>
    Запустил сайт. Тема переключается. Чувствую — это будет моё убежище.
  </div>

  <div class="note">
    <strong>Сегодня</strong><br>
    Иногда хочется написать что-то… и стереть через пять минут. И это нормально.
  </div>

  <script>
    const toggle = document.getElementById('theme-toggle');
    const savedTheme = localStorage.getItem('theme') || 'light';
    
    // Устанавливаем тему при загрузке
    document.documentElement.setAttribute('data-theme', savedTheme);
    toggle.textContent = savedTheme === 'dark' ? '☀️ Светлая' : '🌙 Тёмная';

    toggle.addEventListener('click', () => {
      const current = document.documentElement.getAttribute('data-theme');
      const next = current === 'dark' ? 'light' : 'dark';
      
      document.documentElement.setAttribute('data-theme', next);
      localStorage.setItem('theme', next);
      toggle.textContent = next === 'dark' ? '☀️ Светлая' : '🌙 Тёмная';
    });
  </script>
</body>
</html>

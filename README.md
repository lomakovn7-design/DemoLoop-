<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Apple Demo Loop</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body, html {
      width: 100%;
      height: 100%;
      background-color: #000;
      overflow: hidden;
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", sans-serif;
    }

    /* Видео на весь экран */
    video {
      position: absolute;
      top: 50%;
      left: 50%;
      min-width: 100%;
      min-height: 100%;
      width: auto;
      height: auto;
      transform: translate(-50%, -50%);
      object-fit: cover;
      z-index: 1;
    }

    /* Селектор выбора устройства внизу */
    .controls {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 10;
      background: rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      padding: 10px 18px;
      border-radius: 30px;
      border: 1px solid rgba(255, 255, 255, 0.15);
      opacity: 0.3;
      transition: opacity 0.3s ease;
    }

    .controls:hover {
      opacity: 1;
    }

    select {
      background: transparent;
      color: #fff;
      border: none;
      font-size: 14px;
      outline: none;
      cursor: pointer;
    }

    select option {
      background: #1c1c1e;
      color: #fff;
    }
  </style>
</head>
<body>

  <!-- Зацикленное видео во весь экран -->
  <video id="demoVideo" autoplay loop muted playsinline preload="auto">
    <source id="videoSource" src="https://www.dropbox.com/scl/fi/ki4j0x48ydi43q6algch2/ScreenRecording_10-12-2025-8-45-37-PM_1.mov?rlkey=iuzua2f461iatm4uc2vytn9m5&st=zv4s3r4f&dl=1" type="video/mp4">
    Ваш браузер не поддерживает видео.
  </video>

  <!-- Меню выбора модели -->
  <div class="controls">
    <select id="deviceSelect" onchange="changeVideo(this.value)">
      <option value="https://www.dropbox.com/scl/fi/ki4j0x48ydi43q6algch2/ScreenRecording_10-12-2025-8-45-37-PM_1.mov?rlkey=iuzua2f461iatm4uc2vytn9m5&st=zv4s3r4f&dl=1">iPhone 16 Pro</option>
      <option value="https://www.dropbox.com/scl/fi/9n7zh42u1kwqcttix4azy/16_qual.mov?rlkey=5e6chxfx3nw1itkmplh6r2acu&st=mkywp7ag&dl=1">iPhone 16</option>
      <option value="https://www.dropbox.com/scl/fi/5yc3rar7jd6x24j51ek4w/iphone15pro.MP4?rlkey=8zwp6dr2b25p6ganjkad0qd99&st=vyecg5e4&dl=1">iPhone 15 Pro</option>
      <option value="https://www.dropbox.com/scl/fi/sui9zvpfh67xw9uibc2jk/Iphone15.mp4?rlkey=uqyfh202rcpe33p4ozce7v8qc&st=n6jez4c1&dl=1">iPhone 15</option>
      <option value="https://www.dropbox.com/scl/fi/noz4218trwjmzo8ty0dxm/iphone14pro.mp4?rlkey=o7iljuhiua9fhe6uf4ql8prui&st=2jj1mxpq&dl=1">iPhone 14 Pro</option>
      <option value="https://www.dropbox.com/scl/fi/i4fxptfzw7p2w6mbib0if/IPHONE-X.mp4?rlkey=zrjqscaviykwhy6vkrfcyk4wi&st=jfhn5hzj&dl=1">iPhone X</option>
    </select>
  </div>

  <script>
    const video = document.getElementById('demoVideo');
    const source = document.getElementById('videoSource');

    function changeVideo(url) {
      source.src = url;
      video.load();
      video.play();
    }

    // Автостарт при клике в любой точке (если браузер блокирует автоплей со звуком)
    document.body.addEventListener('click', () => {
      if (video.paused) {
        video.play();
      }
    });
  </script>
</body>
</html>

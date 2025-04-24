
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>مشاهدة مباشرة</title>
  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
  <script type='text/javascript' src='//pl26330988.profitableratecpm.com/31/36/42/3136423ba8e56051368cedef08742e2e.js'></script>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background-color: black;
      height: 100%;
      overflow: hidden;
    }
    video {
      width: 100vw;
      height: 100vh;
      object-fit: contain;
      background-color: black;
    }
    #qualitySelector {
      position: absolute;
      top: 10px;
      left: 10px;
      z-index: 999;
      background: rgba(0, 0, 0, 0.7);
      color: white;
      padding: 5px;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <select id="qualitySelector"></select>
  <video id="video" controls autoplay muted></video>

 <div >
  <video id="video" controls autoplay width="100%"></video>
  <div style="position: absolute; bottom: 40px; left: 25%; width: 19%; height: 33px; background: GREEN; opacity: 0.1;"></div>
</div>
<script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
<script>
  var video = document.getElementById('video');
  var container = document.getElementById('videoContainer');
  var overlay = document.getElementById('videoOverlay');

  if (Hls.isSupported()) {
    var hls = new Hls();
    hls.loadSource('https://top1-cdnnew.newkso.ru/top1-cdn/R0tcyrMCFm/mono.m3u8');
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED, function () {
      video.play();
    });
  } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
    video.src = 'https://top1-cdnnew.newkso.ru/top1-cdn/R0tcyrMCFm/mono.m3u8';
    video.addEventListener('loadedmetadata', function () {
      video.play();
    });
  }

  // التعامل مع fullscreen
  function appendOverlayToFullscreen() {
    setTimeout(() => {
      const fullscreenElement = document.fullscreenElement || document.webkitFullscreenElement;
      if (fullscreenElement && fullscreenElement.tagName === 'VIDEO') {
        fullscreenElement.parentElement.appendChild(overlay);
        overlay.style.position = 'fixed';
      } else if (fullscreenElement && fullscreenElement.id === 'videoContainer') {
        container.appendChild(overlay);
        overlay.style.position = 'absolute';
      }
    }, 300);
  }

  document.addEventListener('fullscreenchange', appendOverlayToFullscreen);
  document.addEventListener('webkitfullscreenchange', appendOverlayToFullscreen);
</script>
</body>
</html>

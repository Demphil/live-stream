
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>مشاهدة مباشرة</title>
  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
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

  <script>
    const video = document.getElementById('video');
    const selector = document.getElementById('qualitySelector');
    const streamURL = "https://top1-cdnnew.newkso.ru/top1-cdn/R0tcyrMCFm/mono.m3u8"; // <- عوّضه برابطك الحقيقي

    if (Hls.isSupported()) {
      const hls = new Hls();
      hls.loadSource(streamURL);
      hls.attachMedia(video);

      hls.on(Hls.Events.MANIFEST_PARSED, function () {
        const levels = hls.levels;
        levels.forEach((level, index) => {
          const option = document.createElement("option");
          option.value = index;
          option.text = ${level.height}p;
          selector.appendChild(option);
        });

        selector.addEventListener("change", function () {
          hls.currentLevel = parseInt(this.value);
        });
      });
    } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
      video.src = streamURL;
      video.addEventListener('loadedmetadata', function () {
        video.play();
      });
    } else {
      alert("المتصفح لا يدعم HLS.");
    }
  </script>
</body>
</html>
</html>

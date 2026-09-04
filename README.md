<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Reel Downloader</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #833ab4, #fd1d1d, #fcb045);
      padding: 20px;
    }

    .container {
      width: 100%;
      max-width: 450px;
      background: white;
      padding: 30px 22px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 15px 40px rgba(0,0,0,0.25);
    }

    .logo {
      font-size: 45px;
      margin-bottom: 10px;
    }

    h1 {
      font-size: 28px;
      margin-bottom: 8px;
    }

    .subtitle {
      color: #666;
      font-size: 14px;
      margin-bottom: 25px;
    }

    input {
      width: 100%;
      padding: 15px;
      border: 1px solid #ddd;
      border-radius: 12px;
      font-size: 15px;
      outline: none;
      margin-bottom: 12px;
    }

    input:focus {
      border-color: #833ab4;
    }

    button {
      width: 100%;
      padding: 15px;
      border: none;
      border-radius: 12px;
      background: #111;
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }

    button:hover {
      opacity: 0.9;
    }

    #message {
      margin-top: 18px;
      font-size: 14px;
      color: #555;
      line-height: 1.5;
    }

    .notice {
      margin-top: 22px;
      padding: 12px;
      background: #f5f5f5;
      border-radius: 10px;
      font-size: 12px;
      color: #666;
    }
  </style>
</head>

<body>

  <div class="container">

    <div class="logo">⬇️</div>

    <h1>Reel Downloader</h1>

    <p class="subtitle">
      Paste your Reel link below
    </p>

    <input
      type="url"
      id="reelUrl"
      placeholder="https://www.instagram.com/reel/..."
      autocomplete="off"
    >

    <button onclick="downloadReel()">
      Download Reel
    </button>

    <div id="message"></div>

    <div class="notice">
      Download only videos that you own or have permission to download.
    </div>

  </div>

  <script>
    function downloadReel() {

      const input = document.getElementById("reelUrl");
      const message = document.getElementById("message");

      const url = input.value.trim();

      if (!url) {
        message.innerHTML = "⚠️ Please paste a Reel URL.";
        return;
      }

      try {
        const parsedUrl = new URL(url);

        if (
          parsedUrl.hostname !== "instagram.com" &&
          parsedUrl.hostname !== "www.instagram.com"
        ) {
          message.innerHTML =
            "❌ Please enter a valid Instagram URL.";
          return;
        }

        if (!parsedUrl.pathname.includes("/reel/")) {
          message.innerHTML =
            "❌ Please enter an Instagram Reel URL.";
          return;
        }

        message.innerHTML =
          "✅ Link accepted.<br><br>" +
          "For authorized videos, use Instagram's available download/share options or your own media source.";

      } catch (error) {

        message.innerHTML =
          "❌ Invalid URL. Please check the link.";

      }
    }
  </script>

</body>
</html>

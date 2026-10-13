# 臉部穴位觀察 · Web

開啟網頁 → 按「開始鏡頭」→ 允許權限 → 顯示臉部關鍵點與三個穴位估算。

自己的程式集中在 **index.html**，依序為版面、樣式、模型載入、穴位插值、座標投影、Canvas 繪圖與鏡頭啟停。`lib/` 是固定版本 MediaPipe 0.10.32、WASM 與模型，第三方授權見其 LICENSE 檔案。

本機：`py -m http.server 8781 --bind 127.0.0.1`，開啟 `http://127.0.0.1:8781/`。
經確認後可部署 GitHub Pages：main 分支、根目錄。手機需以 HTTPS 開啟，建議直接使用 Safari 或 Chrome。

與 Python 版共用模型、穴位索引與插值係數、鏡像投影概念；此版以 `getUserMedia` 取像、`detectForVideo` 推論、Canvas 繪圖。同步推論在主執行緒，每秒最多約 10 次；沒有 Python 版的背景執行緒與單幀佇列。低效能裝置可能卡頓，真人手機仍需實測。

離開頁籤會停止鏡頭；回來後可重新啟動。影像在本機處理，不錄影或上傳。穴位是未經專家校準的幾何估算，不作為醫療定位依據。

[Google Web 指南](https://developers.google.com/edge/mediapipe/solutions/vision/face_landmarker/web_js)

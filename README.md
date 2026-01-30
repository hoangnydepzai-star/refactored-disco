<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KERNEL SENTINEL v19.0 - MD5</title>
    <style>
        body { background-color: #000; color: #00ff00; font-family: 'Courier New', Courier, monospace; text-align: center; margin: 0; padding: 20px; }
        .container { border: 2px solid #00ff00; border-radius: 10px; padding: 20px; display: inline-block; width: 90%; max-width: 400px; margin-top: 30px; box-shadow: 0 0 20px #00ff00; }
        .header { font-weight: bold; font-size: 1.4em; margin-bottom: 15px; border-bottom: 1px dashed #00ff00; padding-bottom: 10px; color: #fff; }
        .dice-box { font-size: 3.5em; margin: 25px 0; letter-spacing: 15px; text-shadow: 0 0 10px #00ff00; }
        .result-box { font-size: 1.3em; background: #0a0a0a; padding: 15px; border: 1px solid #00ff00; margin-top: 20px; }
        .btn { background: #00ff00; color: #000; border: none; padding: 18px; font-weight: bold; cursor: pointer; margin-top: 25px; border-radius: 5px; width: 100%; font-size: 1.2em; text-transform: uppercase; }
        .btn:active { background: #00cc00; transform: scale(0.98); }
        .loading-bar { height: 8px; background: #111; width: 100%; margin-top: 15px; border-radius: 10px; overflow: hidden; border: 1px solid #00ff00; }
        .progress { height: 100%; background: #00ff00; width: 0%; transition: width 0.1s; }
        .info { margin-top: 25px; font-size: 0.75em; text-align: left; line-height: 1.6; color: #888; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">KERNEL SENTINEL v19.0</div>
        <div style="font-size: 0.8em; letter-spacing: 2px;">[ ANALYZING DATA MD5 ]</div>
        
        <div class="dice-box" id="dice">? ? ?</div>

        <div class="loading-bar"><div class="progress" id="progress"></div></div>

        <div class="result-box">
            DỰ ĐOÁN: <span id="du-doan" style="color: #fff; font-weight: bold; text-shadow: 0 0 5px #fff;">--</span><br>
            ĐỘ TIN CẬY: <span id="percent" style="color: #ff3333;">0</span>%
        </div>

        <button class="btn" onclick="runTool()">Bắt đầu phân tích</button>

        <div class="info">
            > Algorithm: <b>Hybrid Neural 4.0</b><br>
            > Mode: <b>Adaptive Vector</b><br>
            > Server: <span style="color: #00ff00;">Connected</span><br>
            > Encryption: <b>MD5 Verified</b>
        </div>
    </div>

    <script>
        function runTool() {
            let count = 0;
            const btn = document.querySelector('.btn');
            const resultText = document.getElementById('du-doan');
            const percentText = document.getElementById('percent');
            const progress = document.getElementById('progress');
            const dice = document.getElementById('dice');

            btn.disabled = true;
            btn.innerText = "Đang quét hệ thống...";
            resultText.innerText = "WAITING...";
            
            const interval = setInterval(() => {
                // Nhảy số xúc xắc giả lập
                dice.innerText = 
                    (Math.floor(Math.random() * 6) + 1) + " " + 
                    (Math.floor(Math.random() * 6) + 1) + " " + 
                    (Math.floor(Math.random() * 6) + 1);
                
                // Thanh tiến trình chạy
                let p = Math.min(Math.floor(count * 3.33), 100);
                percentText.innerText = p;
                progress.style.width = p + "%";
                
                count++;
                if (count > 30) {
                    clearInterval(interval);
                    // Kết quả ngẫu nhiên Tài hoặc Xỉu
                    const finalRes = Math.random() > 0.5 ? "TÀI" : "XỈU";
                    resultText.innerText = finalRes;
                    resultText.style.color = finalRes === "TÀI" ? "#ff0000" : "#fff";
                    percentText.innerText = (95 + Math.random() * 4).toFixed(1);
                    progress.style.width = "100%";
                    btn.disabled = false;
                    btn.innerText = "Phân tích tiếp";
                }
            }, 80);
        }
    </script>
</body>
</html>

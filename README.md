<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Máy Bay Giấy và Trái Tim</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: #111;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }
        .container {
            position: relative;
        }
        .maybay {
            width: 150px;
            position: absolute;
            animation: bay 4s infinite ease-in-out;
            cursor: pointer;
        }
        @keyframes bay {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        .heart {
            position: absolute;
            color: red;
            font-size: 20px;
            animation: flyUp 3s linear forwards;
        }
        @keyframes flyUp {
            0% { opacity: 1; transform: translateY(0) scale(0.5); }
            100% { opacity: 0; transform: translateY(-200px) scale(1.5); }
        }
    </style>
</head>
<body>

    <div class="container">
        <img src="may_bay.png" alt="Máy bay giấy" class="maybay" id="maybay">
    </div>

    <audio id="cuteSound" src="https://www.fesliyanstudios.com/play-mp3/4380"></audio>

    <script>
        document.getElementById("maybay").addEventListener("click", function(event) {
            let x = event.clientX;
            let y = event.clientY;

            // Tạo trái tim bay lên
            let heart = document.createElement("div");
            heart.classList.add("heart");
            heart.style.left = x + "px";
            heart.style.top = y + "px";
            heart.innerHTML = "❤️";
            document.body.appendChild(heart);

            // Phát âm thanh
            document.getElementById("cuteSound").play();

            // Xóa trái tim sau khi bay lên
            setTimeout(() => {
                heart.remove();
            }, 3000);
        });
    </script>

</body>
</html>

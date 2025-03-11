# Bmi-Cauculater
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI 計算機</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f4f4f4;
        }
        .container {
            background: white;
            padding: 20px;
            max-width: 300px;
            margin: auto;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            padding: 10px 15px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>BMI 計算機</h2>
        <label>輸入身高（cm）：</label>
        <input type="number" id="height" placeholder="例如：170">
        <br>
        <label>輸入體重（kg）：</label>
        <input type="number" id="weight" placeholder="例如：65">
        <br>
        <button onclick="calculateBMI()">計算 BMI</button>
        <div id="result"></div>
    </div>

    <script>
        function calculateBMI() {
            // 取得輸入值
            let cm = parseFloat(document.getElementById("height").value);
            let kg = parseFloat(document.getElementById("weight").value);

            // 檢查輸入是否有效
            if (isNaN(cm) || isNaN(kg) || cm <= 0 || kg <= 0) {
                document.getElementById("result").innerHTML = "請輸入有效的身高和體重！";
                return;
            }

            // 計算 BMI
            let bmi = kg / ((cm / 100) ** 2);
            let message = "";

            // 判斷 BMI 狀態
            if (bmi <= 18.5) {
                message = "您的體重過輕";
            } else if (bmi <= 24) {
                message = "您的 BMI 值為正常範圍";
            } else if (bmi <= 28) {
                message = "您的 BMI 值為超重";
            } else {
                message = "您的 BMI 為肥胖範圍";
            }

            // 顯示結果
            document.getElementById("result").innerHTML = `您的 BMI 值為：${bmi.toFixed(2)}<br>${message}`;
        }
    </script>
</body>
</html>

# cos7440
바람 체마 소수점 계산기
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>마력 및 체력 계산기</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .calculator {
            margin-bottom: 40px;
        }
        input, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .result span {
            font-weight: bold;
            color: #333;
        }
        h3 {
            margin-bottom: 10px;
            color: #4CAF50;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 마력 계산기 -->
        <div class="calculator">
            <h3>마력 계산기</h3>
            <label for="currentPower">현재 마력</label>
            <input type="number" id="currentPower" placeholder="현재 마력을 입력하세요" required>

            <label for="targetPower">목표 마력</label>
            <input type="number" id="targetPower" placeholder="목표 마력을 입력하세요" required>

            <button onclick="calculatePower()">마력 계산</button>

            <div class="result">
                <p>마력 차이: <span id="powerDifference">-</span></p>
                <p>필요 수치: <span id="requiredPowerUnits">-</span></p>
            </div>
        </div>

        <!-- 체력 계산기 -->
        <div class="calculator">
            <h3>체력 계산기</h3>
            <label for="currentHealth">현재 체력</label>
            <input type="number" id="currentHealth" placeholder="현재 체력을 입력하세요" required>

            <label for="targetHealth">목표 체력</label>
            <input type="number" id="targetHealth" placeholder="목표 체력을 입력하세요" required>

            <button onclick="calculateHealth()">체력 계산</button>

            <div class="result">
                <p>체력 차이: <span id="healthDifference">-</span></p>
                <p>필요 수치: <span id="requiredHealthUnits">-</span></p>
            </div>
        </div>
    </div>

    <script>
        function calculatePower() {
            // 1당 마력 수치 고정
            const powerPerUnit = 25;

            // 입력값 가져오기
            const currentPower = parseFloat(document.getElementById("currentPower").value);
            const targetPower = parseFloat(document.getElementById("targetPower").value);

            // 유효성 검사
            if (isNaN(currentPower) || isNaN(targetPower) || currentPower >= targetPower) {
                alert("유효한 값을 입력해주세요! 현재 마력은 목표 마력보다 작아야 합니다.");
                return;
            }

            // 마력 차이 계산 (소수점 제외)
            const powerDifference = Math.floor(targetPower - currentPower);

            // 필요 수치 계산 (소수점 포함)
            const requiredPowerUnits = (powerDifference / powerPerUnit).toFixed(2);

            // 결과 표시
            document.getElementById("powerDifference").innerText = powerDifference;
            document.getElementById("requiredPowerUnits").innerText = requiredPowerUnits;
        }

        function calculateHealth() {
            // 1당 체력 수치 고정
            const healthPerUnit = 50;

            // 입력값 가져오기
            const currentHealth = parseFloat(document.getElementById("currentHealth").value);
            const targetHealth = parseFloat(document.getElementById("targetHealth").value);

            // 유효성 검사
            if (isNaN(currentHealth) || isNaN(targetHealth) || currentHealth >= targetHealth) {
                alert("유효한 값을 입력해주세요! 현재 체력은 목표 체력보다 작아야 합니다.");
                return;
            }

            // 체력 차이 계산 (소수점 제외)
            const healthDifference = Math.floor(targetHealth - currentHealth);

            // 필요 수치 계산 (소수점 포함)
            const requiredHealthUnits = (healthDifference / healthPerUnit).toFixed(2);

            // 결과 표시
            document.getElementById("healthDifference").innerText = healthDifference;
            document.getElementById("requiredHealthUnits").innerText = requiredHealthUnits;
        }
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator Rasya </title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #141414;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .calculator {
            width: 320px;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            text-align: center;
        }

        #display {
            width: 100%;
            height: 50px;
            text-align: right;
            font-size: 1.5em;
            margin-bottom: 20px;
            padding: 10px;
            border: none;
            background: #eee;
            border-radius: 5px;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            width: 100%;
            height: 60px;
            font-size: 1.2em;
            font-weight: bold;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }

        button:hover {
            opacity: 0.8;
        }

        .number {
            background: hsl(0, 0%, 35%);
            color: white;
        }

        .operator {
            background: #f39c12;
            color: white;
        }

        .clear {
            background: #e74c3c;
            color: white;
        }

        .equal {
            background: #2ecc71;
            color: white;
        }
    </style>
</head>

<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <div class="buttons">
            <button class="number" onclick="appendToDisplay('7')">7</button>
            <button class="number" onclick="appendToDisplay('8')">8</button>
            <button class="number" onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>

            <button class="number" onclick="appendToDisplay('4')">4</button>
            <button class="number" onclick="appendToDisplay('5')">5</button>
            <button class="number" onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>

            <button class="number" onclick="appendToDisplay('1')">1</button>
            <button class="number" onclick="appendToDisplay('2')">2</button>
            <button class="number" onclick="appendToDisplay('3')">3</button>
            <button class="operator" onclick="appendToDisplay('*')">x</button>

            <button class="number" onclick="appendToDisplay('0')">0</button>
            <button class="clear" onclick="hapusLayar()">C</button>
            <button class="equal" onclick="kalkulasi()">=</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
        </div>
    </div>

    <script>
        
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }
    
        
        function kalkulasi() {
            let displayValue = document.getElementById('display').value;
            let result;
    
            try {
                
                let num1 = parseFloat(displayValue.split(/[\+\-\*\/]/)[0]);
                let num2 = parseFloat(displayValue.split(/[\+\-\*\/]/)[1]);
                let operator = displayValue.match(/[\+\-\*\/]/)[0];
    
                if (operator === '+') {
                    result = num1 + num2;
                } else if (operator === '-') {
                    result = num1 - num2;
                } else if (operator === '*') {
                    result = num1 * num2;
                } else if (operator === '/') {
                    
                    if (num2 === 0) {
                        result = "Tidak bisa dibagi 0";
                    } else {
                        result = num1 / num2;
                    }
                }
    
                document.getElementById('display').value = result;
            } catch (error) {
                document.getElementById('display').value = "Tidak bisa dibagi 0";
            }
        }
    
        
        function hapusLayar() {
            document.getElementById('display').value = '';
        }
    </script>
    

</body>

</html>

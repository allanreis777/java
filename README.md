# java
fust calculator.html
<!DOCTYPE html>
<html lang="pt-BR">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Simples</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }

        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            border-radius: 10px;
            background: #ffffff;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
        }

        .calculator {
            width: 400px;
        }

        input[type="text"] {
            width: 100%;
            height: 40px;
            font-size: 24px;
            text-align: right;
            margin-bottom: 10px;
        }

        button {
            width: 23%;
            height: 40px;
            font-size: 20px;
            margin: 5px;
            cursor: pointer;
        }

        .small-button {
            font-size: 14px;
            height: 30px;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="calculator">
            <input type="text" id="display" disabled>
            <div>
                <button class="small-button" onclick="appendToDisplay('M+')">M+</button>
                <button class="small-button" onclick="appendToDisplay('M-')">M-</button>
                <button class="small-button" onclick="appendToDisplay('MR')">MR</button>
                <button class="small-button" onclick="appendToDisplay('MC')">MC</button>
                <button class="small-button" onclick="appendToDisplay('x²')">x²</button>
                <button class="small-button" onclick="appendToDisplay('1/x')">1/x</button>
            </div>
            <div>
                <button onclick="clearDisplay()">C</button>
                <button onclick="appendToDisplay('1')">1</button>
                <button onclick="appendToDisplay('2')">2</button>
                <button onclick="deleteLastCharacter()">⌫</button> <!-- Botão de apagar um caractere -->
                <button onclick="appendToDisplay('3')">3</button>
                <button onclick="appendToDisplay('4')">4</button>
                <button onclick="appendToDisplay('5')">5</button>
                <button onclick="appendToDisplay('6')">6</button>
                <button onclick="appendToDisplay('7')">7</button>
                <button onclick="appendToDisplay('8')">8</button>
                <button onclick="appendToDisplay('9')">9</button>
                <button onclick="appendToDisplay('0')">0</button>
            </div>
            <div>
                <button onclick="appendToDisplay('√(')">√</button>
                <button onclick="appendToDisplay('+')">+</button>
                <button onclick="appendToDisplay('-')">-</button>
                <button onclick="appendToDisplay('×')">×</button>
                <button onclick="appendToDisplay('/')">/</button>
                <button onclick="calculate()">=</button>
            </div>
        </div>
    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function deleteLastCharacter() {
            const display = document.getElementById('display');
            display.value = display.value.slice(0, -1); // Remove o último caractere
        }

        function calculate() {
            const display = document.getElementById('display');
            try {
                // Substituir a função de raiz quadrada e o símbolo × por *
                const result = display.value
                    .replace(/√\((.*?)\)/g, 'Math.sqrt($1)')
                    .replace(/×/g, '*'); // Substitui × por *
                display.value = eval(result);
            } catch (error) {
                display.value = 'Erro';
            }
        }
    </script>
</body>

</html>

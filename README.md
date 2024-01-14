<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f4;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }

        #calculator {
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
            text-align: center;
        }

        #display {
            font-size: 24px;
            margin-bottom: 10px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            font-size: 18px;
            width: 40px;
            height: 40px;
            margin: 5px;
            border: 1px solid #ccc;
            border-radius: 4px;
            cursor: pointer;
            background-color: #f8f8f8;
        }

        button:hover {
            background-color: #e0e0e0;
        }

        button.operator {
            background-color: #ff9900;
            color: #fff;
        }

        button.operator:hover {
            background-color: #e68a00;
        }

        button.equals {
            background-color: #4caf50;
            color: #fff;
        }

        button.equals:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

<div id="calculator">
    <div id="display"></div>
    <button>7</button>
    <button>8</button>
    <button>9</button>
    <button class="operator">/</button>

    <button>4</button>
    <button>5</button>
    <button>6</button>
    <button class="operator">*</button>

    <button>1</button>
    <button>2</button>
    <button>3</button>
    <button class="operator">-</button>

    <button>0</button>
    <button class="operator">.</button>
    <button class="equals">=</button>
    <button class="operator">+</button>
</div>

<script>
    document.addEventListener('DOMContentLoaded', function () {
        const display = document.getElementById('display');
        const buttons = document.querySelectorAll('button');
        let currentInput = '';
        let operator = '';

        buttons.forEach(button => {
            button.addEventListener('click', function () {
                const buttonText = button.textContent;

                if (!isNaN(buttonText) || buttonText === '.') {
                    currentInput += buttonText;
                } else if (buttonText === 'C') {
                    currentInput = '';
                    operator = '';
                } else if (buttonText === '=') {
                    if (currentInput !== '' && operator !== '') {
                        currentInput = eval(currentInput).toString();
                        operator = '';
                    }
                } else {
                    operator = buttonText;
                    currentInput += operator;
                }

                display.textContent = currentInput;
            });
        });
    });
</script>

</body>
</html>

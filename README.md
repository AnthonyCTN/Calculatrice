# Calculatrice

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
   
        
    
    <h1>Calculatrice</h1>
        <form id="calculatorForm">
    
            <p>Cliquez sur le bouton "Générer" pour tirer deux nombres entre -100 et 100</p>
            <label>Nombre 1:</label>
            <input type="text" maxlength="5" id="number1">
    
            <label>Nombre 2:</label>
            <input type="text" maxlength="5" id="number2">
            
            <input type="button" value="Générer" id="generateBtn">
    
        </form>
    
        <div id="calculationArea">
            <fieldset>
                <legend>VOTRE SOLUTION</legend>
                <div class="inputArea">
                    <label>Nombre 1 + Nombre 2</label>
                    <input type="text" maxlength="5" id="addition">
                    <label><span id="correctAddition">Oui</span> / <span id="incorrectAddition">Non</span></label><br>
                    <label>Nombre 1 - Nombre 2</label>
                    <input type="text" maxlength="5" id="subtraction">
                    <label><span id="correctSubtraction">Oui</span> / <span id="incorrectSubtraction">Non</span></label><br>
                    <label>Nombre 1 * Nombre 2</label>
                    <input type="text" maxlength="5" id="multiplication">
                    <label><span id="correctMultiplication">Oui</span> / <span id="incorrectMultiplication">Non</span></label><br>
                    <label>Nombre 1 / Nombre 2</label>
                    <input type="text" maxlength="5" id="division">
                    <label><span id="correctDivision">Oui</span> / <span id="incorrectDivision">Non</span></label><br>
    
                    <input type="button" value="Vérifier" id="verifyBtn">
    
                </div>
            </fieldset>
    
            <fieldset id="solutionField">
                <legend>LA SOLUTION</legend>
                <div class="inputArea">
                    <label>Nombre 1 + Nombre 2</label>
                    <input type="text" maxlength="10" id="solutionAddition" disabled="disabled" value="0"><br>
                    <label>Nombre 1 - Nombre 2</label>
                    <input type="text" maxlength="10" id="solutionSubtraction" disabled="disabled" value="0"><br>
                    <label>Nombre 1 * Nombre 2</label>
                    <input type="text" maxlength="10" id="solutionMultiplication" disabled="disabled" value="0"><br>
                    <label>Nombre 1 / Nombre 2</label>
                    <input type="text" maxlength="10" id="solutionDivision" disabled="disabled" value="0"><br>
    
                    <input type="button" value="SOLUTION" id="solutionBtn">
    
                </div>
            </fieldset>
        </div>
    
    
        <script>
const updateNumbers = () => {
    document.getElementById("number1").value = Math.trunc(200*Math.random() - 100);
    document.getElementById("number2").value = Math.trunc(200*Math.random() - 100);

    ["solutionAddition", "solutionSubtraction", "solutionMultiplication", "solutionDivision"]
        .forEach(id => document.getElementById(id).value = 0);
}

const calculateSolutions = () => {
    const number1 = Number(document.getElementById("number1").value);
    const number2 = Number(document.getElementById("number2").value);

    document.getElementById("solutionAddition").value = number1 + number2;
    document.getElementById("solutionSubtraction").value = number1 - number2;
    document.getElementById("solutionMultiplication").value = number1 * number2;
    document.getElementById("solutionDivision").value = Math.trunc(number1 / number2);
}

const verifySolutions = () => {
    const number1 = Number(document.getElementById("number1").value);
    const number2 = Number(document.getElementById("number2").value);

    const operations = ["addition", "subtraction", "multiplication", "division"];
    const calculations = [number1 + number2, number1 - number2, number1 * number2, Math.trunc(number1 / number2)];

    operations.forEach((operation, index) => {
        const correct = document.querySelector(`#correct${operation.charAt(0).toUpperCase() + operation.slice(1)}`);
        const incorrect = document.querySelector(`#incorrect${operation.charAt(0).toUpperCase() + operation.slice(1)}`);
        if (Number(document.getElementById(operation).value) == calculations[index]) {
            correct.style.color = "green";
            incorrect.style.color = "#F2E9E4";
        } else {
            incorrect.style.color = "red";
            correct.style.color = "#F2E9E4";
        }
    });
}

generateBtn.onclick = updateNumbers;
solutionBtn.onclick = calculateSolutions;
verifyBtn.onclick = verifySolutions;


        </script>
    </body>
    </html>
    
    
    <style>
    body {
        background-color: #f3f3f3;
        color: #333;
        font-family: 'Poppins', sans-serif;
        padding: 20px;
    }
    
    h1 {
        text-align: center;
        color: #008080;
        margin-bottom: 40px;
    }
    
    #calculatorForm, fieldset {
        width: 80%;
        margin: 0 auto;
        padding: 20px;
        box-sizing: border-box;
        background-color: #ffffff;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        border: none;
        border-radius: 15px;
    }
    
    #calculatorForm {
        margin-bottom: 20px;
        background-color: #e8f6f3;
    }
    
    label {
        display: block;
        margin-bottom: 10px;
        color: #008080;
    }
    
    .inputArea input[type=text] {
        width: 100%;
        padding: 10px;
        box-sizing: border-box;
        margin-bottom: 20px;
        border: 1px solid #008080;
        border-radius: 10px;
    }
    
    input[type=button] {
        padding: 10px 20px;
        background-color: #008080;
        color: #fff;
        border: none;
        cursor: pointer;
        transition: background-color 0.2s;
        border-radius: 10px;
    }
    
    input[type=button]:hover {
        background-color: #006666;
    }
    
    #calculationArea {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
    
    #calculationArea fieldset {
        width: 45%;
        margin-bottom: 20px;
        background-color: #e8f6f3;
    }
    
    #correctAddition, #correctSubtraction, #correctMultiplication, #correctDivision {
        color: #228b22;
    }
    
    #incorrectAddition, #incorrectSubtraction, #incorrectMultiplication, #incorrectDivision {
        color: #b22222;
    }
    
    @media screen and (max-width: 807px) {
        #calculatorForm, fieldset {
            width: 100%;
        }
    
        #calculationArea fieldset {
            width: 100%;
        }
    }
    </style>
    




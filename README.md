//HTML Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css">
    <title>Multiplication</title>
</head>
<body>
    <form class="form" id="form">
        <h4 class="score" id="score">score:0</h4>
        <h1 id="question">what is 1 multiply by 1?</h1>
        <input type="text" class="input" id="inp" placeholder="Enter the Answer" autocomplete="off">
        <button type="submit" class="btn" id="btn">Submit</button>
    </form>
    <script src="index.js"></script>
</body>
</html>


//CSS Code
*
{
    padding: 0%;
    margin: 0%;
    box-sizing: border-box;
}
body
{
    display: flex;
    justify-content: center;
    height: 100vh;
    align-items: center;
    text-align: center;
    background-color: yellow;
    line-height: 50px;
    font-family: cursive;
}
.score
{
    text-align: right;
}
.form
{
    width: 40%;
    height: 50%;
    background-color: white;
    box-shadow: 0 4px 8px 0px rgba(0, 0, 0, .7);
    border-radius: 5px;

    padding: 10px;
}
.input
{
    display: block;
    width: 100%;
    padding: 5px;
    text-align: center;
    border: 3px solid black;
}
.btn
{
    color: white;
    background-color: black;
    width: 100%;
    border-radius: 5px;
    font-family: cursive;
    cursor: pointer;
}


//JS Code
const questionElement = document.getElementById("question");

let num1 = Math.floor(Math.random() * 10);
let num2 = Math.floor(Math.random() * 10);
let correctAnswer = num1 * num2;

questionElement.innerText = `What is ${num1} Multiply by ${num2}?`;

const form = document.getElementById('form');
const input = document.getElementById('inp');
let scoreElement = document.getElementById('score');

let score = Number(localStorage.getItem("score"));
if(!score) {
	score = 0;
}

scoreElement.textContent = `score : ${score}`;

form.addEventListener('submit',function() {
	let userAnswer = +input.value;
	if(correctAnswer === userAnswer) {
		score++;
		updateScore();
	}
	else {
		score--;
		updateScore();
	}
});

function updateScore() {
	localStorage.setItem("score",String(score));
}

// Clear Local Storage
// localStorage.removeItem("score");

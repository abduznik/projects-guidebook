---
{"dg-publish":true,"dg-path":"practice/quiz.md","permalink":"/practice/quiz/"}
---

# Quiz

Test your knowledge with this interactive quiz!

<div id="quiz"></div>
<button id="submit">Submit</button>
<div id="results"></div>

<script>
const quizData = [
    {
        question: "What is the correct way to install a library in Python?",
        answers: {
            a: "install library_name",
            b: "pip install library_name",
            c: "python install library_name"
        },
        correctAnswer: "b"
    },
    {
        question: "Which of the following is NOT a valid data type in Python?",
        answers: {
            a: "int",
            b: "float",
            c: "double"
        },
        correctAnswer: "c"
    },
    {
        question: "What is the function of the `Serial.begin()` command in the Arduino IDE?",
        answers: {
            a: "To start the serial communication",
            b: "To end the serial communication",
            c: "To print data to the serial monitor"
        },
        correctAnswer: "a"
    },
    {
        question: "Which pin on the ESP32 is the default for the I2C clock (SCL)?",
        answers: {
            a: "GPIO21",
            b: "GPIO22",
            c: "GPIO23"
        },
        correctAnswer: "b"
    }
];

const quizContainer = document.getElementById('quiz');
const resultsContainer = document.getElementById('results');
const submitButton = document.getElementById('submit');

function buildQuiz(){
    const output = [];
    quizData.forEach((currentQuestion, questionNumber) => {
        const answers = [];
        for(letter in currentQuestion.answers){
            answers.push(
                `<label>
                    <input type="radio" name="question${questionNumber}" value="${letter}">
                    ${letter} : ${currentQuestion.answers[letter]}
                </label>`
            );
        }
        output.push(
            `<div class="question"> ${currentQuestion.question} </div>
            <div class="answers"> ${answers.join('')} </div>`
        );
    });
    quizContainer.innerHTML = output.join('');
}

function showResults(){
    const answerContainers = quizContainer.querySelectorAll('.answers');
    let numCorrect = 0;
    quizData.forEach((currentQuestion, questionNumber) => {
        const answerContainer = answerContainers[questionNumber];
        const selector = `input[name=question${questionNumber}]:checked`;
        const userAnswer = (answerContainer.querySelector(selector) || {}).value;
        if(userAnswer === currentQuestion.correctAnswer){
            numCorrect++;
            answerContainers[questionNumber].style.color = 'lightgreen';
        } else {
            answerContainers[questionNumber].style.color = 'red';
        }
    });
    resultsContainer.innerHTML = `${numCorrect} out of ${quizData.length}`;
}

buildQuiz();

submitButton.addEventListener('click', showResults);
</script>

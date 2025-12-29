# CodeAlpha_ProjectName
TASK 1: Flashcard Quiz App

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Flashcard Quiz App</title>

<style>
:root {
    --bg: #f4f6f8;
    --card-bg: #ffffff;
    --text: #000000;
    --border: #dddddd;
    --btn: #007bff;
    --btn-secondary: #6c757d;
    --btn-delete: #dc3545;
}

.dark {
    --bg: #121212;
    --card-bg: #1e1e1e;
    --text: #ffffff;
    --border: #333;
    --btn: #0d6efd;
    --btn-secondary: #495057;
    --btn-delete: #ff4d4d;
}

body {
    font-family: Arial, sans-serif;
    background: var(--bg);
    color: var(--text);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.app {
    background: var(--card-bg);
    width: 360px;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    text-align: center;
}

.card {
    min-height: 100px;
    padding: 15px;
    border: 1px solid var(--border);
    border-radius: 8px;
    margin-bottom: 15px;
    font-size: 16px;
}

button {
    margin: 5px;
    padding: 8px 12px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background: var(--btn);
    color: #fff;
}

.secondary {
    background: var(--btn-secondary);
}

.delete {
    background: var(--btn-delete);
}

.toggle {
    float: right;
    font-size: 12px;
    padding: 5px 8px;
}

input, textarea {
    width: 100%;
    margin: 5px 0;
    padding: 6px;
    border-radius: 5px;
    border: 1px solid var(--border);
    background: var(--bg);
    color: var(--text);
}
</style>
</head>

<body>

<div class="app">
    <button class="toggle secondary" onclick="toggleDark()">🌙 Dark</button>
    <h3>Flashcard Quiz</h3>

    div class="card" id="cardText">No flashcards</div>
<
    <button onclick="showAnswer()">Show Answer</button><br>

    <button class="secondary" onclick="prevCard()">Previous</button>
    <button class="secondary" onclick="nextCard()">Next</button>

    <hr>

    <h4>Add / Edit Flashcard</h4>
    <input type="text" id="question" placeholder="Question">
    <textarea id="answer" placeholder="Answer"></textarea>

    <button onclick="addOrEditCard()">Save</button>
    <button class="delete" onclick="deleteCard()">Delete</button>
</div>

<script>
let flashcards = [
    { question: "What is AI?", answer: "Artificial Intelligence" },
    { question: "CSS stands for?", answer: "Cascading Style Sheets" }
];

let currentIndex = 0;
let showingAnswer = false;

function renderCard() {
    if (flashcards.length === 0) {
        document.getElementById("cardText").innerText = "No flashcards";
        return;
    }
    document.getElementById("cardText").innerText =
        showingAnswer ? flashcards[currentIndex].answer
                      : flashcards[currentIndex].question;
}

function showAnswer() {
    showingAnswer = !showingAnswer;
    renderCard();
}

function nextCard() {
    if (!flashcards.length) return;
    currentIndex = (currentIndex + 1) % flashcards.length;
    showingAnswer = false;
    loadInputs();
    renderCard();
}

function prevCard() {
    if (!flashcards.length) return;
    currentIndex = (currentIndex - 1 + flashcards.length) % flashcards.length;
    showingAnswer = false;
    loadInputs();
    renderCard();
}

function addOrEditCard() {
    const q = question.value;
    const a = answer.value;
    if (!q || !a) return alert("Enter question and answer");

    flashcards[currentIndex] = { question: q, answer: a };
    renderCard();
}

function deleteCard() {
    if (!flashcards.length) return;
    flashcards.splice(currentIndex, 1);
    currentIndex = Math.max(0, currentIndex - 1);
    loadInputs();
    renderCard();
}

function loadInputs() {
    if (!flashcards.length) {
        question.value = "";
        answer.value = "";
        return;
    }
    question.value = flashcards[currentIndex].question;
    answer.value = flashcards[currentIndex].answer;
}

function toggleDark() {
    document.body.classList.toggle("dark");
}

loadInputs();
renderCard();
</script>

</body>
</html>

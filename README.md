
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Planner ♡</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">୨୧ My Planner</div>
            <p class="subtitle">Маленькие шаги — большие мечты ✨</p>
        </header>

        <section class="welcome">
            <div>
                <h1>Твои планы, твой ритм ♡</h1>
                <p>Сделай сегодняшний день особенным!</p>
            </div>
            <div class="flower">🌷</div>
        </section>

        <section class="stats">
            <div class="stat-card pink">
                <span>Всего задач</span>
                <strong id="total">0</strong>
            </div>
            <div class="stat-card purple">
                <span>Выполнено</span>
                <strong id="completed">0</strong>
            </div>
            <div class="stat-card peach">
                <span>Осталось</span>
                <strong id="remaining">0</strong>
            </div>
        </section>

        <section class="planner">
            <h2>Мой список дел 📝</h2>

            <form id="taskForm">
                <input id="taskInput" type="text"
                    placeholder="Что нужно сделать?" required maxlength="120">

                <input id="taskDate" type="date" aria-label="Дата задачи">

                <select id="priority" aria-label="Приоритет">
                    <option value="low">Не срочно</option>
                    <option value="medium" selected>Обычно</option>
                    <option value="high">Важно!</option>
                </select>

                <button type="submit">+ Добавить</button>
            </form>

            <div class="progress-info">
                <span>Твой прогресс</span>
                <span id="progressText">0%</span>
            </div>
            <div class="progress-bar">
                <div id="progressFill"></div>
            </div>

            <div class="filters">
                <button class="filter active" data-filter="all">Все</button>
                <button class="filter" data-filter="active">В процессе</button>
                <button class="filter" data-filter="done">Готово</button>
            </div>

            <div id="taskList"></div>
            <p id="emptyMessage">Здесь пока пусто. Добавь свою первую задачу 🌸</p>
        </section>

        <footer>С любовью к себе и своим мечтам ♡</footer>
    </div>

    <script src="script.js"></script>
</body>
</html>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800&display=swap');

:root {
    --pink: #f5c9d7;
    --pink-dark: #d77f9e;
    --purple: #e1d7f8;
    --peach: #ffe1d0;
    --cream: #fffaf7;
    --text: #625568;
}

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: 'Nunito', sans-serif;
    color: var(--text);
    background: linear-gradient(135deg, #fff0f4, #f3edff, #fff5eb);
    min-height: 100vh;
    padding: 30px 16px;
}

.container {
    max-width: 850px;
    margin: auto;
}

header {
    text-align: center;
    margin-bottom: 30px;
}

.logo {
    font-size: 28px;
    font-weight: 800;
    color: #bd7b9a;
}

.subtitle {
    color: #9b8ba4;
}

.welcome {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 15px;
    padding: 30px;
    background: rgba(255, 255, 255, 0.8);
    border: 1px solid white;
    border-radius: 28px;
    box-shadow: 0 10px 30px #b99bb31a;
    animation: appear 0.7s ease;
}

.welcome h1 {
    font-size: clamp(23px, 4vw, 34px);
    margin: 0 0 8px;
}

.welcome p {
    margin: 0;
    color: #9b8ba4;
}

.flower {
    font-size: 65px;
    animation: float 3s ease-in-out infinite;
}

.stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    margin: 22px 0;
}

.stat-card {
    padding: 20px;
    border-radius: 22px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    transition: transform 0.2s;
}

.stat-card:hover {
    transform: translateY(-4px);
}

.stat-card span {
    font-size: 14px;
}

.stat-card strong {
    font-size: 30px;
}

.pink { background: #f9dce6; }
.purple { background: #e7defa; }
.peach { background: #ffeadc; }

.planner {
    background: rgba(255, 255, 255, 0.9);
    border-radius: 28px;
    padding: 28px;
    box-shadow: 0 10px 30px #b99bb31a;
}

h2 {
    margin-top: 0;
}

#taskForm {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 25px;
}

input, select, button {
    font: inherit;
    border-radius: 13px;
    border: 1px solid #eee3ef;
    padding: 12px;
}

input, select {
    background: #fffafd;
    color: var(--text);
    min-width: 0;
}

#taskInput {
    flex: 1 1 200px;
}

button {
    cursor: pointer;
    transition: 0.2s ease;
}

#taskForm button {
    background: #e8c5e7;
    border: none;
    color: #634f6d;
    font-weight: 800;
}

#taskForm button:hover {
    background: #dcb1dd;
    transform: translateY(-2px);
}

.progress-info {
    display: flex;
    justify-content: space-between;
    margin-bottom: 9px;
    font-size: 14px;
}

.progress-bar {
    height: 11px;
    border-radius: 20px;
    background: #f3eaf4;
    overflow: hidden;
    margin-bottom: 24px;
}

#progressFill {
    height: 100%;
    width: 0;
    background: linear-gradient(90deg, #f0b8d0, #c9b5f1);
    border-radius: inherit;
    transition: width 0.4s ease;
}

.filters {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 18px;
}

.filter {
    background: #faf4fb;
    color: #95839c;
    border: none;
}

.filter.active {
    background: #e9d9f6;
    color: #695273;
    font-weight: 800;
}

.task {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 15px;
    border: 1px solid #f1e8f2;
    border-radius: 17px;
    margin-bottom: 10px;
    animation: appear 0.3s ease;
    background: #fffdfd;
}

.task-check {
    width: 21px;
    height: 21px;
    accent-color: #cf9dcf;
    flex-shrink: 0;
}

.task-content {
    flex: 1;
    overflow-wrap: anywhere;
}

.task-name {
    font-weight: 700;
}

.task-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 5px;
    font-size: 12px;
    color: #9b8ba4;
}

.priority {
    padding: 3px 9px;
    border-radius: 9px;
    background: #f5eafa;
}

.priority.high { background: #ffe1e4; }
.priority.low { background: #e2f3e7; }

.task.done .task-name {
    text-decoration: line-through;
    color: #b5a9b8;
}

.delete {
    background: #fff0f2;
    border: none;
    color: #c77991;
    padding: 9px 12px;
}

.delete:hover {
    background: #fbd9e1;
}

#emptyMessage {
    text-align: center;
    color: #ad9bb1;
    padding: 18px 0;
}

footer {
    text-align: center;
    padding: 25px 10px 5px;
    color: #a38da9;
    font-size: 14px;
}

@keyframes appear {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes float {
    0%, 100% { transform: translateY(0) rotate(-5deg); }
    50% { transform: translateY(-8px) rotate(5deg); }
}

@media (max-width: 600px) {
    body { padding: 18px 12px; }
    .welcome { padding: 22px; }
    .flower { font-size: 43px; }
    .stats { gap: 8px; }
    .stat-card { padding: 13px 10px; }
    .stat-card span { font-size: 12px; }
    .stat-card strong { font-size: 25px; }
    .planner { padding: 20px 15px; }
    #taskForm input, #taskForm select,
    #taskForm button { width: 100%; }
}


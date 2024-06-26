<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Krishna Gupta's Personal Webpage</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
        }
        header {
            background-color: #0073e6;
            color: white;
            padding: 1rem;
            text-align: center;
        }
        .container {
            padding: 2rem;
        }
        h1, h2 {
            color: #0073e6;
        }
        .bio {
            margin-bottom: 2rem;
        }
        .ai-section {
            margin-bottom: 2rem;
        }
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 1rem;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
        a {
            color: #0073e6;
        }
        .question, .result {
            margin-top: 1rem;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to Krishna Gupta's Personal Webpage</h1>
    </header>
    <div class="container">
        <section class="bio">
            <h2>About Me</h2>
            <p>Hi, I'm Krishna Gupta, a passionate coder with a keen interest in exploring the vast realms of technology. I love solving complex problems and creating innovative solutions through code. My journey in the world of programming has been thrilling, and I'm always eager to learn and grow more each day.</p>
        </section>
        <section class="ai-section">
            <h2>AI on Personal Growth in Studies</h2>
            <p>Welcome to the AI section where we explore personal growth in studies. This AI asks you questions about your performance and provides a detailed analysis.</p>
            <button onclick="startAI()">Start AI Analysis</button>
            <div id="ai-questions" class="question"></div>
            <div id="ai-result" class="result"></div>
            <script>
                const questions = [
                    "How many hours do you study each day?",
                    "Do you take regular breaks during your study sessions?",
                    "How do you rate your focus during study time on a scale of 1-10?",
                    "Do you review and revise your notes regularly?",
                    "How confident do you feel about the material you study on a scale of 1-10?"
                ];
                let answers = [];
                let currentQuestion = 0;

                function startAI() {
                    answers = [];
                    currentQuestion = 0;
                    document.getElementById('ai-questions').innerHTML = `
                        <p>${questions[currentQuestion]}</p>
                        <input type="text" id="answer" />
                        <button onclick="nextQuestion()">Next</button>
                    `;
                    document.getElementById('ai-result').innerHTML = '';
                }

                function nextQuestion() {
                    const answer = document.getElementById('answer').value;
                    if (answer) {
                        answers.push(answer);
                        currentQuestion++;
                        if (currentQuestion < questions.length) {
                            document.getElementById('ai-questions').innerHTML = `
                                <p>${questions[currentQuestion]}</p>
                                <input type="text" id="answer" />
                                <button onclick="nextQuestion()">Next</button>
                            `;
                        } else {
                            displayAnalysis();
                        }
                    } else {
                        alert("Please provide an answer before proceeding.");
                    }
                }

                function displayAnalysis() {
                    let analysis = "<h3>Performance Analysis</h3>";
                    analysis += "<p>Based on your answers, here's a detailed analysis of your study habits:</p>";

                    analysis += `<p><strong>Study Hours:</strong> You study for ${answers[0]} hours each day. `;
                    if (answers[0] < 2) {
                        analysis += "It might be beneficial to increase your study hours to cover more material.</p>";
                    } else {
                        analysis += "Great job maintaining a good study schedule!</p>";
                    }

                    analysis += `<p><strong>Breaks:</strong> You ${answers[1] === 'yes' ? 'do' : 'do not'} take regular breaks. `;
                    if (answers[1] === 'no') {
                        analysis += "Consider taking short breaks to keep your mind fresh and improve productivity.</p>";
                    } else {
                        analysis += "Taking regular breaks is excellent for maintaining focus and energy levels.</p>";
                    }

                    analysis += `<p><strong>Focus Level:</strong> You rated your focus at ${answers[2]} out of 10. `;
                    if (answers[2] < 7) {
                        analysis += "Improving focus can be achieved by minimizing distractions and setting clear goals for each study session.</p>";
                    } else {
                        analysis += "Good job staying focused during your studies!</p>";
                    }

                    analysis += `<p><strong>Review and Revision:</strong> You ${answers[3] === 'yes' ? 'do' : 'do not'} review and revise your notes regularly. `;
                    if (answers[3] === 'no') {
                        analysis += "Regular revision can help reinforce your learning and improve retention.</p>";
                    } else {
                        analysis += "Regularly reviewing and revising notes is a great practice for long-term retention.</p>";
                    }

                    analysis += `<p><strong>Confidence Level:</strong> You rated your confidence at ${answers[4]} out of 10. `;
                    if (answers[4] < 7) {
                        analysis += "Building confidence can be achieved through consistent practice and seeking help when needed.</p>";
                    } else {
                        analysis += "Confidence is key to success, and it seems you're on the right track!</p>";
                    }

                    document.getElementById('ai-questions').innerHTML = '';
                    document.getElementById('ai-result').innerHTML = analysis;
                }
            </script>
        </section>
        <section class="social-media">
            <h2>Connect with Me</h2>
            <p>Follow me on Instagram: <a href="https://instagram.com/krishnagupta614" target="_blank">@krishnagupta614</a></p>
        </section>
    </div>
    <footer>
        <p>&copy; 2024 Krishna Gupta</p>
    </footer>
</body>
</html>

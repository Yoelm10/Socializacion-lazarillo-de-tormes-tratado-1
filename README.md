
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Quién Quiere Ser Millonario? - Lazarillo de Tormes</title>
    <style>
        body {
            font-family: 'Verdana', sans-serif; /* Cambiado a Verdana para un estilo más moderno */
            background-color: #c1e0e4; /* Fondo claro para un aspecto fresco */
            margin: 0;
            padding: 0;
            color: #000000;
        }

        .container {
            width: 80%;
            margin: auto;
            overflow: hidden;
        }

        header {
            background: #92410b; /* Verde oscuro para el encabezado */
            color: #fff;
            padding: 20px;
            text-align: center;
            border-bottom: #914702 3px solid;
        }

        header h1 {
            margin: 0;
            font-size: 2.5em; /* Aumentado para mayor impacto */
        }

        header h2 {
            margin: 0;
            font-size: 1.4em;
        }

        #question-container {
            background: #ffffff;
            padding: 20px;
            margin: 20px 0;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            transition: opacity 0.5s ease-in-out; /* Transición suave */
        }

        #question {
            font-size: 1.8em; /* Tamaño aumentado para mayor legibilidad */
            margin-bottom: 20px;
            color: #049704; /* Color para el texto de la pregunta */
        }

        .answer-button {
            display: block;
            background: #139702; /* Botones en verde oscuro */
            color: #ffffff;
            border: none;
            padding: 15px;
            margin: 10px 0;
            width: 100%;
            font-size: 1.2em;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease, transform 0.3s ease; /* Transiciones suaves */
        }

        .answer-button:hover {
            background: #003d33; /* Cambio de color en hover */
            transform: scale(1.05); /* Efecto de escala */
        }

        #result {
            font-size: 2em; /* Tamaño grande para el texto del resultado */
            margin-top: 20px;
        }

        .correct {
            color: #388e3c; /* Color verde para respuestas correctas */
            font-size: 2em; /* Tamaño grande para respuestas correctas */
        }

        .incorrect {
            color: #d32f2f; /* Color rojo para respuestas incorrectas */
            font-size: 2em; /* Tamaño grande para respuestas incorrectas */
        }

        #score {
            font-size: 1.5em; /* Tamaño del texto del conteo de respuestas */
            margin-top: 20px;
        }

        footer {
            background: #db9861;
            color: #000000;
            padding: 10px;
            text-align: center;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>¿Quién Quiere Un Combo?</h1>
            <h2>Primer Tratado del Lazarillo de Tormes</h2>
        </header>

        <main>
            <div id="question-container">
                <p id="question">¿Cuál es la pregunta?</p>
                <button class="answer-button" onclick="checkAnswer(1)">Respuesta A</button>
                <button class="answer-button" onclick="checkAnswer(2)">Respuesta B</button>
                <button class="answer-button" onclick="checkAnswer(3)">Respuesta C</button>
                <button class="answer-button" onclick="checkAnswer(4)">Respuesta D</button>
            </div>
            <div id="result"></div>
            <div id="score"></div> <!-- Añadido para mostrar la puntuación final -->
        </main>

        <footer>
            <p>Hecho por:
               <center>Yoel Daniel Posada Muñoz.
                Angel Nicolas Monrroy Ardila
                Juan David Delgado García </center> </p>
                <p><center>Grado: 10-5</center></p>
        </footer>
    </div>

    <script>
        const questions = [
            {
                question: "¿Cómo se llama el primer amo de Lázaro en el Primer Tratado?",
                answers: [
                    "El ciego",
                    "El clérigo",
                    "El escudero",
                    "El aguacil"
                ],
                correct: 1
            },
            {
                question: "¿Qué tipo de relación tiene Lázaro con el ciego?",
                answers: [
                    "De amistad",
                    "De hostilidad",
                    "De servidumbre",
                    "De igualdad"
                ],
                correct: 3
            },
            {
                question: "¿Cuál es la estrategia de Lázaro para obtener comida cuando el ciego está ocupado?",
                answers: [
                    "Roba al ciego",
                    "Pide limosna en la calle",
                    "Se esconde y come lo que puede",
                    "Busca ayuda en la iglesia"
                ],
                correct: 3
            },
            {
                question: "¿Qué instrumento utiliza el ciego para ganarse la vida?",
                answers: [
                    "Un bastón",
                    "Una guitarra",
                    "Una trompeta",
                    "Un tambor"
                ],
                correct: 1
            },
            {
                question: "¿Cómo se describe la alimentación de Lázaro bajo el cuidado del ciego?",
                answers: [
                    "Suficiente y variada",
                    "Escasa y poco nutritiva",
                    "Excesiva y lujosa",
                    "Regular y equilibrada"
                ],
                correct: 2
            },
            {
                question: "¿Cómo trata el ciego a Lázaro cuando este se queja del hambre?",
                answers: [
                    "Le da más comida",
                    "Lo ignora",
                    "Le da una reprimenda",
                    "Lo castiga físicamente"
                ],
                correct: 3
            },
            {
                question: "¿Qué tipo de comida le da el ciego a Lázaro?",
                answers: [
                    "Pan y queso",
                    "Frutas y verduras",
                    "Pan y vino",
                    "Arroz y carne"
                ],
                correct: 3
            },
            {
                question: "¿Cuál es el principal conflicto en la relación entre Lázaro y el ciego?",
                answers: [
                    "El desinterés del ciego por la educación de Lázaro",
                    "La avaricia y el maltrato del ciego",
                    "El rechazo del ciego hacia Lázaro por su origen",
                    "La falta de comunicación entre ambos"
                ],
                correct: 2
            },
            {
                question: "¿Cómo se siente Lázaro respecto a su situación con el ciego?",
                answers: [
                    "Contento y agradecido",
                    "Desesperado y hambriento",
                    "Satisfecho y confiado",
                    "Indiferente y resignado"
                ],
                correct: 2
            },
            {
                question: "¿Qué estrategia utiliza Lázaro para evitar el maltrato del ciego?",
                answers: [
                    "Lo desafía abiertamente",
                    "Lo engaña y se esconde",
                    "Pide ayuda a otros",
                    "Se adapta a sus exigencias"
                ],
                correct: 2
            },
            {
                question: "¿Qué lección importante aprende Lázaro durante su tiempo con el ciego?",
                answers: [
                    "La importancia del estudio",
                    "El arte de sobrevivir con poco",
                    "El valor de la obediencia",
                    "La necesidad de tener una red de apoyo"
                ],
                correct: 2
            },
            {
                question: "¿Cómo afecta el maltrato del ciego a la salud de Lázaro?",
                answers: [
                    "Le provoca enfermedades graves",
                    "Le causa estrés y debilidad",
                    "No afecta a su salud",
                    "Le fortalece físicamente"
                ],
                correct: 2
            },
            {
                question: "¿Cuál es la principal fuente de ingreso del ciego?",
                answers: [
                    "Las limosnas que recibe",
                    "El salario de un trabajo fijo",
                    "Las donaciones de la iglesia",
                    "La venta de objetos robados"
                ],
                correct: 1
            },
            {
                question: "¿Cómo cambia la percepción de Lázaro sobre el ciego a lo largo del Primer Tratado?",
                answers: [
                    "Pasa de admiración a resentimiento",
                    "Pasa de confianza a desconfianza",
                    "Pasa de respeto a odio",
                    "Pasa de indiferencia a cariño"
                ],
                correct: 1
            },
            {
                question: "¿Qué reflexión hace Lázaro al final del Primer Tratado sobre su vida?",
                answers: [
                    "La importancia de la educación",
                    "La necesidad de ser astuto para sobrevivir",
                    "El valor de la amistad",
                    "La bondad de las personas"
                ],
                correct: 2
            }
        ];

        let currentQuestionIndex = 0;
        let correctAnswers = 0;
        let incorrectAnswers = 0;

        function showQuestion(index) {
            const question = questions[index];
            document.getElementById('question').innerText = question.question;
            const buttons = document.querySelectorAll('.answer-button');
            buttons.forEach((button, i) => {
                button.innerText = question.answers[i];
            });
        }

        function checkAnswer(answer) {
            const correctAnswer = questions[currentQuestionIndex].correct;
            if (answer === correctAnswer) {
                document.getElementById('result').innerHTML = '<span class="correct">¡Respuesta correcta!</span>';
                correctAnswers++;
            } else {
                document.getElementById('result').innerHTML = '<span class="incorrect">Respuesta incorrecta.</span>';
                incorrectAnswers++;
            }
            currentQuestionIndex++;
            if (currentQuestionIndex < questions.length) {
                setTimeout(() => {
                    showQuestion(currentQuestionIndex);
                    document.getElementById('result').innerHTML = '';
                }, 1000);
            } else {
                setTimeout(() => {
                    document.getElementById('result').innerHTML = `Tu puntuación final es: ${correctAnswers} respuestas correctas y ${incorrectAnswers} respuestas incorrectas.`;
                }, 1000);
            }
            document.getElementById('score').innerText = `Respuestas correctas: ${correctAnswers} | Respuestas incorrectas: ${incorrectAnswers}`;
        }

        showQuestion(currentQuestionIndex);
    </script>
</body>
</html>

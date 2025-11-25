<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mystical Tarot - Daily Readings & Yes/No</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #fce7f3 0%, #ffe4e6 50%, #fce7f3 100%);
            min-height: 100vh;
        }

        header {
            background: linear-gradient(90deg, #ec4899 0%, #f43f5e 100%);
            color: white;
            padding: 2rem;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1rem;
        }

        header p {
            color: #fce7f3;
        }

        .container {
            max-width: 900px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .tab-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            margin-bottom: 2rem;
        }

        .tab-btn {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .tab-btn.active {
            background: #ec4899;
            color: white;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
        }

        .tab-btn:not(.active) {
            background: white;
            color: #ec4899;
        }

        .tab-btn:not(.active):hover {
            background: #fce7f3;
        }

        .section {
            display: none;
        }

        .section.active {
            display: block;
        }

        .card-container {
            background: white;
            border-radius: 1.5rem;
            padding: 2rem;
            box-shadow: 0 8px 16px rgba(0,0,0,0.1);
            border: 4px solid #fbcfe8;
        }

        .section-title {
            color: #ec4899;
            font-size: 2rem;
            text-align: center;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .daily-card-result {
            background: linear-gradient(135deg, #fce7f3 0%, #ffe4e6 100%);
            border-radius: 1rem;
            padding: 1.5rem;
            border: 2px solid #fbcfe8;
            margin: 2rem 0;
        }

        .card-display {
            background: white;
            border-radius: 0.5rem;
            padding: 1rem;
            text-align: center;
            margin-bottom: 1rem;
            height: 350px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .card-display img {
            max-height: 100%;
            max-width: 100%;
            object-fit: contain;
        }

        .card-name {
            color: #9f1239;
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .card-meaning {
            color: #be185d;
            line-height: 1.6;
        }

        .reversed {
            color: #be185d;
            font-style: italic;
            font-size: 0.9rem;
            margin-top: 0.5rem;
        }

        .draw-button {
            width: 100%;
            padding: 1rem 2rem;
            font-size: 1.1rem;
            font-weight: bold;
            color: white;
            background: linear-gradient(90deg, #ec4899 0%, #f43f5e 100%);
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
        }

        .draw-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.3);
        }

        .secondary-button {
            background: #fbcfe8;
            color: #be185d;
            margin-top: 1rem;
        }

        .secondary-button:hover {
            background: #f9a8d4;
        }

        .instruction {
            text-align: center;
            color: #be185d;
            font-size: 1.1rem;
            margin-bottom: 2rem;
        }

        .card-pile {
            display: flex;
            justify-content: center;
            margin: 2rem 0;
            height: 250px;
            align-items: center;
        }

        .pile-card {
            width: 130px;
            height: 200px;
            background: linear-gradient(135deg, #ec4899 0%, #f43f5e 100%);
            border-radius: 0.75rem;
            border: 4px solid #fbcfe8;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            position: relative;
            overflow: hidden;
        }

        .pile-card-inner {
            width: 90%;
            height: 90%;
            background: white;
            border-radius: 0.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
        }

        .pile-card:not(:first-child) {
            margin-left: -70px;
        }

        .pile-card:hover {
            transform: translateY(-20px) scale(1.05);
            z-index: 10;
        }

        .answer-result {
            background: linear-gradient(135deg, #fce7f3 0%, #ffe4e6 100%);
            border-radius: 1rem;
            padding: 2rem;
            border: 2px solid #fbcfe8;
            text-align: center;
        }

        .answer-text {
            font-size: 2.5rem;
            font-weight: bold;
            color: #ec4899;
            margin-bottom: 1rem;
        }

        .answer-message {
            color: #be185d;
            font-size: 1.1rem;
            line-height: 1.6;
        }

        footer {
            background: #ec4899;
            color: white;
            text-align: center;
            padding: 1.5rem;
            margin-top: 3rem;
        }

        footer p {
            color: #fce7f3;
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <header>
        <h1>🌙 Mystical Tarot ⭐</h1>
        <p>Discover your daily guidance and seek answers</p>
    </header>

    <div class="container">
        <div class="tab-buttons">
            <button class="tab-btn active" onclick="showTab('daily')">Daily Card</button>
            <button class="tab-btn" onclick="showTab('yesno')">Yes/No Question</button>
        </div>

        <!-- Daily Card Section -->
        <div id="daily-section" class="section active">
            <div class="card-container">
                <h2 class="section-title">✨ Your Daily Card</h2>
                
                <div id="daily-intro">
                    <p class="instruction">Draw your card for today's guidance and insight</p>
                    <button class="draw-button" onclick="drawDailyCard()">Draw Daily Card</button>
                </div>

                <div id="daily-result" class="hidden">
                    <div class="daily-card-result">
                        <div class="card-display" id="daily-card-icon"></div>
                        <div class="card-name" id="daily-card-name"></div>
                        <div class="card-meaning" id="daily-card-meaning"></div>
                        <div class="reversed hidden" id="daily-card-reversed">(Reversed)</div>
                    </div>
                    <button class="draw-button secondary-button" onclick="drawDailyCard()">Draw Another Card</button>
                </div>
            </div>
        </div>

        <!-- Yes/No Section -->
        <div id="yesno-section" class="section">
            <div class="card-container">
                <h2 class="section-title">✨ Ask Yes or No</h2>
                
                <div id="yesno-intro">
                    <p class="instruction">Think of your question and tap a card...</p>
                    <div class="card-pile">
                        <div class="pile-card" onclick="drawYesNo()">
                            <div class="pile-card-inner">🔮</div>
                        </div>
                        <div class="pile-card" onclick="drawYesNo()">
                            <div class="pile-card-inner">🔮</div>
                        </div>
                        <div class="pile-card" onclick="drawYesNo()">
                            <div class="pile-card-inner">🔮</div>
                        </div>
                        <div class="pile-card" onclick="drawYesNo()">
                            <div class="pile-card-inner">🔮</div>
                        </div>
                        <div class="pile-card" onclick="drawYesNo()">
                            <div class="pile-card-inner">🔮</div>
                        </div>
                    </div>
                </div>

                <div id="yesno-result" class="hidden">
                    <div class="answer-result">
                        <div class="answer-text" id="answer-text"></div>
                        <div class="answer-message" id="answer-message"></div>
                    </div>
                    <button class="draw-button secondary-button" onclick="resetYesNo()">Ask Another Question</button>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <p>✨ Trust your intuition and embrace the journey ✨</p>
    </footer>

    <script>
        const tarotCards = [
            { name: "The Fool", meaning: "New beginnings, innocence, spontaneity, free spirit", code: "ar00" },
            { name: "The Magician", meaning: "Manifestation, resourcefulness, power, inspired action", code: "ar01" },
            { name: "The High Priestess", meaning: "Intuition, sacred knowledge, divine feminine", code: "ar02" },
            { name: "The Empress", meaning: "Femininity, beauty, nature, nurturing, abundance", code: "ar03" },
            { name: "The Emperor", meaning: "Authority, structure, control, fatherhood", code: "ar04" },
            { name: "The Lovers", meaning: "Love, harmony, relationships, values alignment", code: "ar06" },
            { name: "The Chariot", meaning: "Control, willpower, success, determination", code: "ar07" },
            { name: "Strength", meaning: "Strength, courage, patience, compassion", code: "ar08" },
            { name: "The Hermit", meaning: "Soul searching, introspection, inner guidance", code: "ar09" },
            { name: "Wheel of Fortune", meaning: "Good luck, karma, life cycles, destiny", code: "ar10" },
            { name: "Justice", meaning: "Justice, fairness, truth, cause and effect", code: "ar11" },
            { name: "The Hanged Man", meaning: "Pause, surrender, letting go, new perspective", code: "ar12" },
            { name: "Death", meaning: "Endings, change, transformation, transition", code: "ar13" },
            { name: "Temperance", meaning: "Balance, moderation, patience, purpose", code: "ar14" },
            { name: "The Devil", meaning: "Shadow self, attachment, addiction, restriction", code: "ar15" },
            { name: "The Tower", meaning: "Sudden change, upheaval, chaos, revelation", code: "ar16" },
            { name: "The Star", meaning: "Hope, faith, purpose, renewal, spirituality", code: "ar17" },
            { name: "The Moon", meaning: "Illusion, fear, anxiety, subconscious, intuition", code: "ar18" },
            { name: "The Sun", meaning: "Positivity, fun, warmth, success, vitality", code: "ar19" },
            { name: "Judgement", meaning: "Judgement, rebirth, inner calling, absolution", code: "ar20" },
            { name: "The World", meaning: "Completion, accomplishment, travel, fulfillment", code: "ar21" }
        ];

        const yesNoAnswers = [
            { answer: "YES", message: "The cards strongly indicate yes. Trust your path forward." },
            { answer: "NO", message: "The cards suggest no. Perhaps another direction is better." },
            { answer: "MAYBE", message: "The answer is unclear. You may need more time or information." },
            { answer: "YES, BUT...", message: "Yes, but proceed with caution and awareness." },
            { answer: "NOT NOW", message: "The timing isn't right. Wait for a better moment." }
        ];

        function showTab(tab) {
            // Hide all sections
            document.getElementById('daily-section').classList.remove('active');
            document.getElementById('yesno-section').classList.remove('active');
            
            // Remove active class from all buttons
            const buttons = document.querySelectorAll('.tab-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            
            // Show selected section
            if (tab === 'daily') {
                document.getElementById('daily-section').classList.add('active');
                buttons[0].classList.add('active');
            } else {
                document.getElementById('yesno-section').classList.add('active');
                buttons[1].classList.add('active');
            }
        }

        function drawDailyCard() {
            const randomCard = tarotCards[Math.floor(Math.random() * tarotCards.length)];
            const reversed = Math.random() > 0.5;
            
            const cardImage = `https://sacred-texts.com/tarot/pkt/img/${randomCard.code}.jpg`;
            
            document.getElementById('daily-card-icon').innerHTML = `<img src="${cardImage}" alt="${randomCard.name}" style="transform: ${reversed ? 'rotate(180deg)' : 'rotate(0deg)'}">`;
            document.getElementById('daily-card-name').textContent = randomCard.name;
            document.getElementById('daily-card-meaning').textContent = randomCard.meaning;
            
            if (reversed) {
                document.getElementById('daily-card-reversed').classList.remove('hidden');
            } else {
                document.getElementById('daily-card-reversed').classList.add('hidden');
            }
            
            document.getElementById('daily-intro').classList.add('hidden');
            document.getElementById('daily-result').classList.remove('hidden');
        }

        function drawYesNo() {
            const randomAnswer = yesNoAnswers[Math.floor(Math.random() * yesNoAnswers.length)];
            
            document.getElementById('answer-text').textContent = randomAnswer.answer;
            document.getElementById('answer-message').textContent = randomAnswer.message;
            
            document.getElementById('yesno-intro').classList.add('hidden');
            document.getElementById('yesno-result').classList.remove('hidden');
        }

        function resetYesNo() {
            document.getElementById('yesno-intro').classList.remove('hidden');
            document.getElementById('yesno-result').classList.add('hidden');
        }
    </script>
</body>
</html>

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
            position: relative;
        }

        .language-switcher {
            position: absolute;
            top: 1rem;
            right: 1rem;
            display: flex;
            gap: 0.5rem;
        }

        .lang-btn {
            padding: 0.5rem 1rem;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid white;
            border-radius: 20px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .lang-btn.active {
            background: white;
            color: #ec4899;
        }

        .lang-btn:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        .lang-btn.active:hover {
            background: white;
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
            flex-wrap: wrap;
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
            margin-bottom: 1rem;
        }

        .card-prediction {
            background: white;
            padding: 1rem;
            border-radius: 0.5rem;
            color: #9f1239;
            margin-bottom: 1rem;
            border-left: 4px solid #ec4899;
        }

        .card-prediction strong {
            display: block;
            margin-bottom: 0.5rem;
            color: #ec4899;
            font-size: 1.1rem;
        }

        .card-advice {
            background: white;
            padding: 1rem;
            border-radius: 0.5rem;
            color: #9f1239;
            border-left: 4px solid #f43f5e;
        }

        .card-advice strong {
            display: block;
            margin-bottom: 0.5rem;
            color: #f43f5e;
            font-size: 1.1rem;
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

        /* Chat Styles */
        .chat-container {
            background: white;
            border-radius: 1rem;
            padding: 1.5rem;
            max-height: 500px;
            overflow-y: auto;
            margin-bottom: 1rem;
            border: 2px solid #fbcfe8;
        }

        .chat-message {
            margin-bottom: 1rem;
            padding: 1rem;
            border-radius: 0.75rem;
            line-height: 1.6;
        }

        .chat-message.user {
            background: linear-gradient(135deg, #fce7f3 0%, #ffe4e6 100%);
            color: #9f1239;
            margin-left: 2rem;
            border: 1px solid #fbcfe8;
        }

        .chat-message.ai {
            background: white;
            color: #be185d;
            margin-right: 2rem;
            border: 2px solid #fbcfe8;
        }

        .chat-message.ai strong {
            color: #ec4899;
        }

        .chat-input-container {
            display: flex;
            gap: 0.5rem;
        }

        .chat-input {
            flex: 1;
            padding: 0.75rem 1rem;
            border: 2px solid #fbcfe8;
            border-radius: 50px;
            font-size: 1rem;
            outline: none;
        }

        .chat-input:focus {
            border-color: #ec4899;
        }

        .chat-send-btn {
            padding: 0.75rem 1.5rem;
            background: linear-gradient(90deg, #ec4899 0%, #f43f5e 100%);
            color: white;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .chat-send-btn:hover {
            transform: scale(1.05);
        }

        .chat-send-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .chat-intro {
            text-align: center;
            color: #be185d;
            padding: 2rem;
        }

        .chat-intro h3 {
            color: #ec4899;
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }

        .loading-dots {
            display: inline-block;
        }

        .loading-dots::after {
            content: '...';
            animation: dots 1.5s steps(4, end) infinite;
        }

        @keyframes dots {
            0%, 20% { content: '.'; }
            40% { content: '..'; }
            60%, 100% { content: '...'; }
        }
    </style>
</head>
<body>
    <header>
        <div class="language-switcher">
            <button class="lang-btn active" onclick="setLanguage('en')" id="lang-en">EN</button>
            <button class="lang-btn" onclick="setLanguage('th')" id="lang-th">ไทย</button>
        </div>
        <div>
            <h1 id="header-title">🌙 Mystical Tarot ⭐</h1>
            <p id="header-subtitle">Discover your daily guidance and seek answers</p>
        </div>
    </header>

    <div class="container">
        <div class="tab-buttons">
            <button class="tab-btn active" onclick="showTab('daily')" id="tab-daily">Daily Card</button>
            <button class="tab-btn" onclick="showTab('yesno')" id="tab-yesno">Yes/No Question</button>
            <button class="tab-btn" onclick="showTab('chat')" id="tab-chat">AI Tarot Chat</button>
        </div>

        <!-- Daily Card Section -->
        <div id="daily-section" class="section active">
            <div class="card-container">
                <h2 class="section-title" id="daily-title">✨ Your Daily Card</h2>
                
                <div id="daily-intro">
                    <p class="instruction" id="daily-instruction">Draw your card for today's guidance and insight</p>
                    <button class="draw-button" onclick="drawDailyCard()" id="daily-draw-btn">Draw Daily Card</button>
                </div>

                <div id="daily-result" class="hidden">
                    <div class="daily-card-result">
                        <div class="card-display" id="daily-card-icon"></div>
                        <div class="card-name" id="daily-card-name"></div>
                        <div class="card-meaning" id="daily-card-meaning"></div>
                        <div class="card-prediction" id="daily-card-prediction"></div>
                        <div class="card-advice" id="daily-card-advice"></div>
                        <div class="reversed hidden" id="daily-card-reversed">(Reversed)</div>
                    </div>
                    <button class="draw-button secondary-button" onclick="drawDailyCard()" id="daily-another-btn">Draw Another Card</button>
                </div>
            </div>
        </div>

        <!-- Yes/No Section -->
        <div id="yesno-section" class="section">
            <div class="card-container">
                <h2 class="section-title" id="yesno-title">✨ Ask Yes or No</h2>
                
                <div id="yesno-intro">
                    <p class="instruction" id="yesno-instruction">Think of your question and tap a card...</p>
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
                    <button class="draw-button secondary-button" onclick="resetYesNo()" id="yesno-another-btn">Ask Another Question</button>
                </div>
            </div>
        </div>

        <!-- AI Chat Section -->
        <div id="chat-section" class="section">
            <div class="card-container">
                <h2 class="section-title" id="chat-title">🔮 AI Tarot Chat</h2>
                
                <div id="chat-intro" class="chat-intro">
                    <h3 id="chat-intro-title">Talk to Your Tarot Guide</h3>
                    <p id="chat-intro-text">Draw a card and have a personal conversation about your reading. Ask questions, seek clarity, and get guidance tailored to your unique situation.</p>
                    <button class="draw-button" onclick="startChat()" style="margin-top: 1rem;" id="chat-start-btn">Draw Card & Start Chat</button>
                </div>

                <div id="chat-active" class="hidden">
                    <div class="daily-card-result" style="margin-bottom: 1.5rem;">
                        <div style="display: flex; gap: 1rem; align-items: center; margin-bottom: 1rem;">
                            <div style="flex-shrink: 0; width: 100px;">
                                <img id="chat-card-img" src="" alt="Tarot Card" style="width: 100%; border-radius: 0.5rem;">
                            </div>
                            <div>
                                <div class="card-name" id="chat-card-name" style="margin-bottom: 0.5rem;"></div>
                                <div style="color: #be185d; font-size: 0.9rem;" id="chat-card-meaning"></div>
                            </div>
                        </div>
                    </div>

                    <div class="chat-container" id="chat-messages"></div>
                    
                    <div class="chat-input-container">
                        <input 
                            type="text" 
                            id="chat-input" 
                            class="chat-input" 
                            placeholder="Ask about your reading..."
                            onkeypress="if(event.key === 'Enter') sendMessage()"
                        >
                        <button class="chat-send-btn" onclick="sendMessage()" id="send-btn">Send</button>
                    </div>

                    <button class="draw-button secondary-button" onclick="resetChat()" style="margin-top: 1rem;" id="chat-new-btn">Start New Reading</button>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <p id="footer-text">✨ Trust your intuition and embrace the journey ✨</p>
    </footer>

    <script>
        let currentLanguage = 'en';

        const translations = {
            en: {
                headerTitle: "🌙 Mystical Tarot ⭐",
                headerSubtitle: "Discover your daily guidance and seek answers",
                tabDaily: "Daily Card",
                tabYesno: "Yes/No Question",
                tabChat: "AI Tarot Chat",
                dailyTitle: "✨ Your Daily Card",
                dailyInstruction: "Draw your card for today's guidance and insight",
                dailyDrawBtn: "Draw Daily Card",
                dailyAnotherBtn: "Draw Another Card",
                yesnoTitle: "✨ Ask Yes or No",
                yesnoInstruction: "Think of your question and tap a card...",
                yesnoAnotherBtn: "Ask Another Question",
                chatTitle: "🔮 AI Tarot Chat",
                chatIntroTitle: "Talk to Your Tarot Guide",
                chatIntroText: "Draw a card and have a personal conversation about your reading. Ask questions, seek clarity, and get guidance tailored to your unique situation.",
                chatStartBtn: "Draw Card & Start Chat",
                chatPlaceholder: "Ask about your reading...",
                chatSendBtn: "Send",
                chatNewBtn: "Start New Reading",
                footerText: "✨ Trust your intuition and embrace the journey ✨",
                reversed: "(Reversed)",
                predictionLabel: "📖 Today's Prediction:",
                adviceLabel: "💫 Advice for Today:",
                tarotGuide: "✨ Tarot Guide:"
            },
            th: {
                headerTitle: "🌙 ทาโรต์มิสติก ⭐",
                headerSubtitle: "ค้นพบคำแนะนำประจำวันและค้นหาคำตอบ",
                tabDaily: "ไพ่ประจำวัน",
                tabYesno: "ถามใช่หรือไม่",
                tabChat: "แชทกับ AI ทาโรต์",
                dailyTitle: "✨ ไพ่ประจำวันของคุณ",
                dailyInstruction: "จั่วไพ่เพื่อรับคำแนะนำและข้อมูลเชิงลึกสำหรับวันนี้",
                dailyDrawBtn: "จั่วไพ่ประจำวัน",
                dailyAnotherBtn: "จั่วไพ่อีกครั้ง",
                yesnoTitle: "✨ ถามใช่หรือไม่",
                yesnoInstruction: "คิดถึงคำถามของคุณและแตะที่ไพ่...",
                yesnoAnotherBtn: "ถามคำถามอื่น",
                chatTitle: "🔮 แชทกับ AI ทาโรต์",
                chatIntroTitle: "พูดคุยกับผู้นำทางทาโรต์",
                chatIntroText: "จั่วไพ่และเริ่มการสนทนาส่วนตัวเกี่ยวกับการอ่านไพ่ของคุณ ถามคำถาม แสวงหาความชัดเจน และรับคำแนะนำที่เหมาะกับสถานการณ์เฉพาะของคุณ",
                chatStartBtn: "จั่วไพ่และเริ่มแชท",
                chatPlaceholder: "ถามเกี่ยวกับการอ่านไพ่ของคุณ...",
                chatSendBtn: "ส่ง",
                chatNewBtn: "เริ่มการอ่านใหม่",
                footerText: "✨ เชื่อสัญชาตญาณและเปิดรับการเดินทาง ✨",
                reversed: "(กลับด้าน)",
                predictionLabel: "📖 คำทำนายวันนี้:",
                adviceLabel: "💫 คำแนะนำสำหรับวันนี้:",
                tarotGuide: "✨ ผู้นำทางทาโรต์:"
            }
        };

        function setLanguage(lang) {
            currentLanguage = lang;
            
            // Update language buttons
            document.getElementById('lang-en').classList.toggle('active', lang === 'en');
            document.getElementById('lang-th').classList.toggle('active', lang === 'th');
            
            // Update all text
            const t = translations[lang];
            document.getElementById('header-title').textContent = t.headerTitle;
            document.getElementById('header-subtitle').textContent = t.headerSubtitle;
            document.getElementById('tab-daily').textContent = t.tabDaily;
            document.getElementById('tab-yesno').textContent = t.tabYesno;
            document.getElementById('tab-chat').textContent = t.tabChat;
            document.getElementById('daily-title').textContent = t.dailyTitle;
            document.getElementById('daily-instruction').textContent = t.dailyInstruction;
            document.getElementById('daily-draw-btn').textContent = t.dailyDrawBtn;
            document.getElementById('daily-another-btn').textContent = t.dailyAnotherBtn;
            document.getElementById('yesno-title').textContent = t.yesnoTitle;
            document.getElementById('yesno-instruction').textContent = t.yesnoInstruction;
            document.getElementById('yesno-another-btn').textContent = t.yesnoAnotherBtn;
            document.getElementById('chat-title').textContent = t.chatTitle;
            document.getElementById('chat-intro-title').textContent = t.chatIntroTitle;
            document.getElementById('chat-intro-text').textContent = t.chatIntroText;
            document.getElementById('chat-start-btn').textContent = t.chatStartBtn;
            document.getElementById('chat-input').placeholder = t.chatPlaceholder;
            document.getElementById('send-btn').textContent = t.chatSendBtn;
            document.getElementById('chat-new-btn').textContent = t.chatNewBtn;
            document.getElementById('footer-text').textContent = t.footerText;
        }

        const tarotCards = [
            { 
                name: "The Fool", 
                nameTH: "คนโง่",
                meaning: "New beginnings, innocence, spontaneity, free spirit", 
                meaningTH: "จุดเริ่มต้นใหม่ ความไร้เดียงสา ความเป็นธรรมชาติ จิตวิญญาณอิสระ",
                prediction: "Today brings new opportunities and fresh starts. Embrace the unknown with an open heart.",
                predictionTH: "วันนี้นำมาซึ่งโอกาสใหม่และการเริ่มต้นใหม่ เปิดใจรับสิ่งที่ไม่รู้ด้วยหัวใจที่เปิดกว้าง",
                advice: "Take a leap of faith today. Trust your instincts and don't be afraid to try something new, even if it feels uncertain.",
                adviceTH: "กล้าเสี่ยงเชื่อในวันนี้ เชื่อสัญชาตญาณของคุณและอย่ากลัวที่จะลองสิ่งใหม่ แม้มันจะรู้สึกไม่แน่นอน",
                code: "ar00" 
            },
            { 
                name: "The Magician", 
                meaning: "Manifestation, resourcefulness, power, inspired action", 
                prediction: "You have all the tools you need to succeed. Your skills and talents will shine brightly today.",
                advice: "Focus your energy and intentions. Use your creativity and take decisive action toward your goals.",
                code: "ar01" 
            },
            { 
                name: "The High Priestess", 
                meaning: "Intuition, sacred knowledge, divine feminine", 
                prediction: "Hidden knowledge and intuitive insights will come to you. Trust what you feel, not just what you see.",
                advice: "Listen to your inner voice today. Spend time in quiet reflection and trust your intuition over logic.",
                code: "ar02" 
            },
            { 
                name: "The Empress", 
                meaning: "Femininity, beauty, nature, nurturing, abundance", 
                prediction: "A day of growth, creativity, and abundance. Nature and nurturing energy surround you.",
                advice: "Connect with nature and beauty today. Practice self-care and extend kindness to yourself and others.",
                code: "ar03" 
            },
            { 
                name: "The Emperor", 
                meaning: "Authority, structure, control, fatherhood", 
                prediction: "Structure and discipline will bring results. Your leadership qualities are needed today.",
                advice: "Create order from chaos. Set clear boundaries and take charge of your responsibilities with confidence.",
                code: "ar04" 
            },
            { 
                name: "The Lovers", 
                meaning: "Love, harmony, relationships, values alignment", 
                prediction: "Important choices about relationships or values may arise. Harmony and connection are highlighted.",
                advice: "Make decisions that align with your heart and values. Strengthen your important relationships today.",
                code: "ar06" 
            },
            { 
                name: "The Chariot", 
                meaning: "Control, willpower, success, determination", 
                prediction: "Victory is within reach through determination and focused effort. You're moving forward with momentum.",
                advice: "Stay focused on your goals and push through any obstacles. Your willpower will lead you to success.",
                code: "ar07" 
            },
            { 
                name: "Strength", 
                meaning: "Strength, courage, patience, compassion", 
                prediction: "Inner strength and courage will help you overcome challenges with grace and compassion.",
                advice: "Be gentle but firm today. Handle difficult situations with patience and kindness rather than force.",
                code: "ar08" 
            },
            { 
                name: "The Hermit", 
                meaning: "Soul searching, introspection, inner guidance", 
                prediction: "A day for solitude and self-reflection. Important insights will come from within.",
                advice: "Take time alone to reflect and recharge. Seek wisdom from within rather than external sources.",
                code: "ar09" 
            },
            { 
                name: "Wheel of Fortune", 
                meaning: "Good luck, karma, life cycles, destiny", 
                prediction: "Change is coming, and luck is on your side. The wheel is turning in your favor.",
                advice: "Go with the flow and embrace change. What seems like chance today is actually destiny unfolding.",
                code: "ar10" 
            },
            { 
                name: "Justice", 
                meaning: "Justice, fairness, truth, cause and effect", 
                prediction: "Truth and fairness will prevail. What you've sown, you will now reap.",
                advice: "Act with integrity and fairness. Make decisions based on truth and balance, not emotion.",
                code: "ar11" 
            },
            { 
                name: "The Hanged Man", 
                meaning: "Pause, surrender, letting go, new perspective", 
                prediction: "A period of pause brings new understanding. Sometimes you must let go to move forward.",
                advice: "Release your need for control. Look at situations from a different angle and be patient.",
                code: "ar12" 
            },
            { 
                name: "Death", 
                meaning: "Endings, change, transformation, transition", 
                prediction: "An important ending paves the way for a powerful new beginning. Transformation is at hand.",
                advice: "Let go of what no longer serves you. Embrace the changes happening, as they lead to renewal.",
                code: "ar13" 
            },
            { 
                name: "Temperance", 
                meaning: "Balance, moderation, patience, purpose", 
                prediction: "Finding the middle path brings peace. Balance and moderation lead to harmony today.",
                advice: "Practice patience and moderation. Blend different aspects of your life to create harmony.",
                code: "ar14" 
            },
            { 
                name: "The Devil", 
                meaning: "Shadow self, attachment, addiction, restriction", 
                prediction: "Be aware of unhealthy attachments or limiting beliefs. You have the power to break free.",
                advice: "Examine what's holding you back. Release toxic patterns and reclaim your personal power.",
                code: "ar15" 
            },
            { 
                name: "The Tower", 
                meaning: "Sudden change, upheaval, chaos, revelation", 
                prediction: "Unexpected changes shake up your world, but they clear the way for truth and liberation.",
                advice: "Stay grounded during sudden changes. What falls away was built on shaky ground; trust the process.",
                code: "ar16" 
            },
            { 
                name: "The Star", 
                meaning: "Hope, faith, purpose, renewal, spirituality", 
                prediction: "Hope and healing are yours today. Your wishes and dreams are closer than you think.",
                advice: "Keep faith and stay optimistic. Your authentic self shines brightest now; share your gifts with the world.",
                code: "ar17" 
            },
            { 
                name: "The Moon", 
                meaning: "Illusion, fear, anxiety, subconscious, intuition", 
                prediction: "Things may not be as they seem. Trust your intuition to navigate through uncertainty.",
                advice: "Don't make major decisions today. Wait for clarity and pay attention to your dreams and intuition.",
                code: "ar18" 
            },
            { 
                name: "The Sun", 
                meaning: "Positivity, fun, warmth, success, vitality", 
                prediction: "Joy, success, and vitality fill your day. Everything is illuminated by positive energy.",
                advice: "Embrace happiness and share your light with others. Celebrate your achievements and enjoy life.",
                code: "ar19" 
            },
            { 
                name: "Judgement", 
                meaning: "Judgement, rebirth, inner calling, absolution", 
                prediction: "A time of reckoning and renewal. You're being called to a higher purpose or new phase of life.",
                advice: "Reflect on your past and make peace with it. Answer your inner calling and step into your true purpose.",
                code: "ar20" 
            },
            { 
                name: "The World", 
                meaning: "Completion, accomplishment, travel, fulfillment", 
                prediction: "Success and completion are at hand. You've reached an important milestone on your journey.",
                advice: "Celebrate your achievements and take a moment to appreciate how far you've come. The world is yours.",
                code: "ar21" 
            }
        ];

        const yesNoAnswers = [
            { answer: "YES", answerTH: "ใช่", message: "The cards strongly indicate yes. Trust your path forward.", messageTH: "ไพ่บอกว่าใช่อย่างชัดเจน เชื่อมั่นในเส้นทางที่คุณกำลังเดินไป" },
            { answer: "NO", answerTH: "ไม่", message: "The cards suggest no. Perhaps another direction is better.", messageTH: "ไพ่บอกว่าไม่ใช่ บางทีทิศทางอื่นอาจจะดีกว่า" },
            { answer: "MAYBE", answerTH: "อาจจะ", message: "The answer is unclear. You may need more time or information.", messageTH: "คำตอบยังไม่ชัดเจน คุณอาจต้องการเวลาหรือข้อมูลเพิ่มเติม" },
            { answer: "YES, BUT...", answerTH: "ใช่ แต่...", message: "Yes, but proceed with caution and awareness.", messageTH: "ใช่ แต่ดำเนินการด้วยความระมัดระวังและความตระหนัก" },
            { answer: "NOT NOW", answerTH: "ยังไม่ใช่ตอนนี้", message: "The timing isn't right. Wait for a better moment.", messageTH: "ยังไม่ใช่เวลาที่เหมาะสม รอโอกาสที่ดีกว่า" }
        ];

        function showTab(tab) {
            // Hide all sections
            document.getElementById('daily-section').classList.remove('active');
            document.getElementById('yesno-section').classList.remove('active');
            document.getElementById('chat-section').classList.remove('active');
            
            // Remove active class from all buttons
            const buttons = document.querySelectorAll('.tab-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            
            // Show selected section
            if (tab === 'daily') {
                document.getElementById('daily-section').classList.add('active');
                buttons[0].classList.add('active');
            } else if (tab === 'yesno') {
                document.getElementById('yesno-section').classList.add('active');
                buttons[1].classList.add('active');
            } else if (tab === 'chat') {
                document.getElementById('chat-section').classList.add('active');
                buttons[2].classList.add('active');
            }
        }

        function drawDailyCard() {
            const randomCard = tarotCards[Math.floor(Math.random() * tarotCards.length)];
            const reversed = Math.random() > 0.5;
            
            const cardImage = `https://sacred-texts.com/tarot/pkt/img/${randomCard.code}.jpg`;
            const t = translations[currentLanguage];
            const isEn = currentLanguage === 'en';
            
            document.getElementById('daily-card-icon').innerHTML = `<img src="${cardImage}" alt="${randomCard.name}" style="transform: ${reversed ? 'rotate(180deg)' : 'rotate(0deg)'}">`;
            document.getElementById('daily-card-name').textContent = isEn ? randomCard.name : randomCard.nameTH;
            document.getElementById('daily-card-meaning').textContent = isEn ? randomCard.meaning : randomCard.meaningTH;
            document.getElementById('daily-card-prediction').innerHTML = `<strong>${t.predictionLabel}</strong>${isEn ? randomCard.prediction : randomCard.predictionTH}`;
            document.getElementById('daily-card-advice').innerHTML = `<strong>${t.adviceLabel}</strong>${isEn ? randomCard.advice : randomCard.adviceTH}`;
            
            if (reversed) {
                document.getElementById('daily-card-reversed').textContent = t.reversed;
                document.getElementById('daily-card-reversed').classList.remove('hidden');
            } else {
                document.getElementById('daily-card-reversed').classList.add('hidden');
            }
            
            document.getElementById('daily-intro').classList.add('hidden');
            document.getElementById('daily-result').classList.remove('hidden');
        }

        function drawYesNo() {
            const randomAnswer = yesNoAnswers[Math.floor(Math.random() * yesNoAnswers.length)];
            const isEn = currentLanguage === 'en';
            
            document.getElementById('answer-text').textContent = isEn ? randomAnswer.answer : randomAnswer.answerTH;
            document.getElementById('answer-message').textContent = isEn ? randomAnswer.message : randomAnswer.messageTH;
            
            document.getElementById('yesno-intro').classList.add('hidden');
            document.getElementById('yesno-result').classList.remove('hidden');
        }

        function resetYesNo() {
            document.getElementById('yesno-intro').classList.remove('hidden');
            document.getElementById('yesno-result').classList.add('hidden');
        }

        // AI Chat Functions
        let currentCard = null;
        let chatHistory = [];

        async function startChat() {
            // Draw a random card
            currentCard = tarotCards[Math.floor(Math.random() * tarotCards.length)];
            const reversed = Math.random() > 0.5;
            const isEn = currentLanguage === 'en';
            const t = translations[currentLanguage];
            
            const cardImage = `https://sacred-texts.com/tarot/pkt/img/${currentCard.code}.jpg`;
            
            // Display card
            document.getElementById('chat-card-img').src = cardImage;
            document.getElementById('chat-card-img').style.transform = reversed ? 'rotate(180deg)' : 'rotate(0deg)';
            document.getElementById('chat-card-name').textContent = (isEn ? currentCard.name : currentCard.nameTH) + (reversed ? ` ${t.reversed}` : '');
            document.getElementById('chat-card-meaning').textContent = isEn ? currentCard.meaning : currentCard.meaningTH;
            
            // Show chat interface
            document.getElementById('chat-intro').classList.add('hidden');
            document.getElementById('chat-active').classList.remove('hidden');
            
            // Initialize chat with AI greeting
            chatHistory = [];
            const cardName = isEn ? currentCard.name : currentCard.nameTH;
            const prediction = isEn ? currentCard.prediction : currentCard.predictionTH;
            const advice = isEn ? currentCard.advice : currentCard.adviceTH;
            
            const greeting = isEn 
                ? `Hello! I've drawn ${cardName} for you. ${prediction} ${advice}\n\nWhat would you like to know about this reading? Feel free to ask about how it applies to your specific situation.`
                : `สวัสดีค่ะ! ฉันได้จั่วไพ่ ${cardName} ให้คุณ ${prediction} ${advice}\n\nคุณอยากรู้อะไรเกี่ยวกับการอ่านไพ่นี้? อย่าลังเลที่จะถามว่ามันเกี่ยวข้องกับสถานการณ์ของคุณอย่างไร`;
            
            addMessage('ai', greeting);
        }

        function addMessage(sender, text) {
            const messagesDiv = document.getElementById('chat-messages');
            const messageDiv = document.createElement('div');
            messageDiv.className = `chat-message ${sender}`;
            const t = translations[currentLanguage];
            
            if (sender === 'ai') {
                messageDiv.innerHTML = `<strong>${t.tarotGuide}</strong><br>${text}`;
            } else {
                messageDiv.textContent = text;
            }
            
            messagesDiv.appendChild(messageDiv);
            messagesDiv.scrollTop = messagesDiv.scrollHeight;
        }

        async function sendMessage() {
            const input = document.getElementById('chat-input');
            const message = input.value.trim();
            
            if (!message) return;
            
            // Add user message
            addMessage('user', message);
            input.value = '';
            
            // Disable send button
            const sendBtn = document.getElementById('send-btn');
            const t = translations[currentLanguage];
            sendBtn.disabled = true;
            sendBtn.innerHTML = (currentLanguage === 'en' ? 'Thinking' : 'กำลังคิด') + '<span class="loading-dots"></span>';
            
            // Add to history
            chatHistory.push({ role: 'user', content: message });
            
            const isEn = currentLanguage === 'en';
            const cardName = isEn ? currentCard.name : currentCard.nameTH;
            const meaning = isEn ? currentCard.meaning : currentCard.meaningTH;
            const prediction = isEn ? currentCard.prediction : currentCard.predictionTH;
            const advice = isEn ? currentCard.advice : currentCard.adviceTH;
            
            const systemPrompt = isEn 
                ? `You are a wise and compassionate tarot guide. The user has drawn the tarot card "${cardName}". 

Card meaning: ${meaning}
Prediction: ${prediction}
Advice: ${advice}

Previous conversation:
${chatHistory.slice(-4).map(m => `${m.role}: ${m.content}`).join('\n')}

Current question: ${message}

Provide a thoughtful, personalized response that relates the card's wisdom to their specific question. Be warm, insightful, and encouraging. Keep your response under 150 words.`
                : `คุณเป็นผู้นำทางทาโรต์ที่ฉลาดและมีความเมตตา ผู้ใช้ได้จั่วไพ่ทาโรต์ "${cardName}"

ความหมายของไพ่: ${meaning}
คำทำนาย: ${prediction}
คำแนะนำ: ${advice}

การสนทนาก่อนหน้า:
${chatHistory.slice(-4).map(m => `${m.role}: ${m.content}`).join('\n')}

คำถามปัจจุบัน: ${message}

ให้คำตอบที่มีความคิดและเป็นส่วนตัวที่เชื่อมโยงภูมิปัญญาของไพ่กับคำถามเฉพาะของพวกเขา จงอบอุ่น ลึกซึ้ง และให้กำลังใจ ตอบภาษาไทยไม่เกิน 150 คำ`;
            
            try {
                // Call Claude API
                const response = await fetch('https://api.anthropic.com/v1/messages', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        model: 'claude-sonnet-4-20250514',
                        max_tokens: 1000,
                        messages: [
                            {
                                role: 'user',
                                content: systemPrompt
                            }
                        ]
                    })
                });

                const data = await response.json();
                const aiResponse = data.content[0].text;
                
                // Add AI response
                addMessage('ai', aiResponse);
                chatHistory.push({ role: 'assistant', content: aiResponse });
                
            } catch (error) {
                const errorMsg = isEn 
                    ? "I apologize, but I'm having trouble connecting right now. Please try asking your question again in a moment."
                    : "ขออภัยค่ะ ตอนนี้มีปัญหาในการเชื่อมต่อ กรุณาลองถามคำถามอีกครั้งในอีกสักครู่";
                addMessage('ai', errorMsg);
            }
            
            // Re-enable send button
            sendBtn.disabled = false;
            sendBtn.textContent = t.chatSendBtn;
        }

        function resetChat() {
            document.getElementById('chat-intro').classList.remove('hidden');
            document.getElementById('chat-active').classList.add('hidden');
            document.getElementById('chat-messages').innerHTML = '';
            chatHistory = [];
            currentCard = null;
        }
    </script>
</body>
</html>

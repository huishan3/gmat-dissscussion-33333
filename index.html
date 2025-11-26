<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GMAT組長意見收集報告</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Noto+Sans+TC:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <!-- Firebase SDKs -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, onAuthStateChanged, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot, doc, setDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Firebase Configuration
        const firebaseConfig = JSON.parse(__firebase_config);
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';

        // Authentication & Real-time Logic
        const initAuth = async () => {
            if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                await signInWithCustomToken(auth, __initial_auth_token);
            } else {
                await signInAnonymously(auth);
            }
        };

        initAuth();

        onAuthStateChanged(auth, (user) => {
            if (user) {
                console.log("User authenticated:", user.uid);
                setupRealtimeChat(user);
            }
        });

        // Chat Logic
        function setupRealtimeChat(user) {
            const commentsContainer = document.getElementById('comments-list');
            const collectionPath = collection(db, 'artifacts', appId, 'public', 'data', 'gmat_comments');

            // Listen for changes
            onSnapshot(collectionPath, (snapshot) => {
                const messages = [];
                snapshot.forEach((doc) => {
                    messages.push({ id: doc.id, ...doc.data() });
                });

                // Client-side sorting (Rule 2: No complex queries)
                messages.sort((a, b) => b.timestamp - a.timestamp); // Newest first

                renderMessages(messages);
            }, (error) => {
                console.error("Error fetching comments:", error);
            });
        }

        function renderMessages(messages) {
            const container = document.getElementById('comments-list');
            container.innerHTML = '';

            if (messages.length === 0) {
                container.innerHTML = '<p style="text-align:center; color:#aaa; margin-top:20px;">目前尚無討論，歡迎發表第一則意見。</p>';
                return;
            }

            messages.forEach(msg => {
                const date = new Date(msg.timestamp);
                const timeString = date.toLocaleString('zh-TW', { month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit' });
                
                const msgEl = document.createElement('div');
                msgEl.className = 'message-card reveal active'; // Force active to show immediately
                msgEl.innerHTML = `
                    <div class="msg-header">
                        <span class="msg-author"><i class="fa-solid fa-user-circle"></i> ${escapeHtml(msg.sender)}</span>
                        <span class="msg-time">${timeString}</span>
                    </div>
                    <div class="msg-content">${escapeHtml(msg.text).replace(/\n/g, '<br>')}</div>
                `;
                container.appendChild(msgEl);
            });
        }

        // Send Message Function (Exposed to window)
        window.sendMessage = async function() {
            const nameInput = document.getElementById('sender-name');
            const textInput = document.getElementById('message-text');
            const btn = document.getElementById('send-btn');

            const sender = nameInput.value.trim() || '匿名成員';
            const text = textInput.value.trim();

            if (!text) return alert("請輸入留言內容");

            btn.disabled = true;
            btn.innerHTML = '<i class="fa-solid fa-spinner fa-spin"></i> 傳送中...';

            try {
                if (!auth.currentUser) await initAuth();
                
                const collectionPath = collection(db, 'artifacts', appId, 'public', 'data', 'gmat_comments');
                await addDoc(collectionPath, {
                    sender: sender,
                    text: text,
                    timestamp: Date.now(),
                    userId: auth.currentUser.uid
                });

                textInput.value = ''; // Clear text, keep name
            } catch (error) {
                console.error("Error sending message:", error);
                alert("傳送失敗，請稍後再試");
            } finally {
                btn.disabled = false;
                btn.innerHTML = '送出意見 <i class="fa-solid fa-paper-plane"></i>';
            }
        }

        function escapeHtml(text) {
            if (!text) return "";
            return text
                .replace(/&/g, "&amp;")
                .replace(/</g, "&lt;")
                .replace(/>/g, "&gt;")
                .replace(/"/g, "&quot;")
                .replace(/'/g, "&#039;");
        }
    </script>

    <style>
        :root {
            --bg-dark: #050505;
            --bg-card: rgba(30, 30, 30, 0.6);
            --accent-blue: #4d94ff;
            --accent-purple: #9d4dff;
            --text-main: #ffffff;
            --text-muted: #a0a0a0;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            font-family: 'Inter', 'Noto Sans TC', sans-serif;
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* 動態背景 */
        .background-fx {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            background: radial-gradient(circle at 20% 20%, rgba(77, 148, 255, 0.08), transparent 40%),
                        radial-gradient(circle at 80% 80%, rgba(157, 77, 255, 0.05), transparent 40%);
            filter: blur(40px);
        }

        /* 區塊通用設定 */
        section {
            min-height: 80vh; /* Slightly reduced height for better flow */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 60px 20px;
            position: relative;
            max-width: 1000px;
            margin: 0 auto;
        }

        /* 標題樣式 */
        h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 900;
            line-height: 1.2;
            margin-bottom: 2rem;
            text-align: center;
        }

        h1 span {
            background: linear-gradient(to right, var(--accent-blue), var(--accent-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: block;
        }

        h2 {
            font-size: clamp(1.8rem, 3vw, 2.5rem);
            margin-bottom: 2rem;
            position: relative;
            display: inline-block;
            border-bottom: 3px solid var(--accent-blue);
            padding-bottom: 10px;
        }

        p {
            font-size: 1.15rem;
            color: var(--text-muted);
            max-width: 800px;
            margin-bottom: 1.5rem;
        }

        /* 卡片設計 */
        .card {
            background: var(--bg-card);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 16px;
            padding: 30px;
            margin-bottom: 20px;
            width: 100%;
            transition: transform 0.3s ease;
        }

        .card h3 {
            color: #fff;
            margin-bottom: 10px;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card h3 i {
            color: var(--accent-blue);
        }

        /* 列表樣式 */
        .issue-list {
            list-style: none;
            width: 100%;
        }

        .issue-item {
            background: rgba(255, 255, 255, 0.03);
            border-left: 4px solid var(--accent-purple);
            padding: 20px;
            margin-bottom: 15px;
            border-radius: 0 10px 10px 0;
        }

        .issue-item h4 {
            color: #fff;
            margin-bottom: 5px;
            font-size: 1.2rem;
        }

        /* 提問區塊 */
        .question-box {
            background: rgba(77, 148, 255, 0.1);
            border: 1px solid var(--accent-blue);
            padding: 25px;
            border-radius: 12px;
            margin-top: 30px;
            width: 100%;
        }

        .question-box h3 {
            color: var(--accent-blue);
            margin-bottom: 15px;
        }

        /* 留言板樣式 */
        .chat-container {
            width: 100%;
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 30px;
            margin-top: 40px;
        }

        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        input, textarea {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: #fff;
            padding: 12px;
            border-radius: 8px;
            font-size: 1rem;
            font-family: inherit;
        }

        input:focus, textarea:focus {
            outline: none;
            border-color: var(--accent-blue);
            background: rgba(255, 255, 255, 0.1);
        }

        #sender-name {
            flex: 1;
            min-width: 150px;
        }

        #message-text {
            width: 100%;
            min-height: 80px;
            resize: vertical;
        }

        button {
            background: var(--accent-blue);
            color: #fff;
            border: none;
            padding: 10px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            transition: all 0.2s;
            align-self: flex-end;
        }

        button:hover {
            background: #3b7ad6;
            transform: translateY(-2px);
        }
        
        button:disabled {
            background: #555;
            cursor: not-allowed;
            transform: none;
        }

        .comments-list {
            margin-top: 30px;
            max-height: 500px;
            overflow-y: auto;
            padding-right: 10px;
        }

        /* 自定義捲軸 */
        .comments-list::-webkit-scrollbar {
            width: 8px;
        }
        .comments-list::-webkit-scrollbar-track {
            background: rgba(255,255,255,0.05);
        }
        .comments-list::-webkit-scrollbar-thumb {
            background: rgba(255,255,255,0.2);
            border-radius: 4px;
        }

        .message-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            border-left: 3px solid var(--text-muted);
        }

        .msg-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 0.9rem;
            color: var(--accent-blue);
        }
        
        .msg-time {
            color: #666;
            font-size: 0.8rem;
        }

        /* 捲動動畫 Reveal */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 1s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* 導航點 */
        .nav-dots {
            position: fixed;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            gap: 15px;
            z-index: 100;
        }

        .dot {
            width: 10px;
            height: 10px;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
        }

        .dot.active {
            background: var(--accent-blue);
            transform: scale(1.3);
            box-shadow: 0 0 10px var(--accent-blue);
        }

        @media (max-width: 768px) {
            .nav-dots { display: none; }
            section { padding: 40px 20px; min-height: auto; }
        }
    </style>
</head>
<body>

    <!-- 背景特效 -->
    <div class="background-fx"></div>

    <!-- 導航點 -->
    <div class="nav-dots">
        <div class="dot active" onclick="scrollToSection(0)"></div>
        <div class="dot" onclick="scrollToSection(1)"></div>
        <div class="dot" onclick="scrollToSection(2)"></div>
        <div class="dot" onclick="scrollToSection(3)"></div>
        <div class="dot" onclick="scrollToSection(4)"></div>
    </div>

    <!-- Section 1: 封面 -->
    <section id="s1">
        <div class="reveal active" style="text-align: center;">
            <p style="text-transform: uppercase; letter-spacing: 2px; font-size: 0.9rem; margin-bottom: 20px; color: var(--accent-blue);">GMAT TEAM REPORT</p>
            <h1>GMAT組長意見收集<br><span>書面報告</span></h1>
            <p style="margin: 20px auto; color: #fff;">針對近期團長管理爭議之觀察與提議</p>
            <div style="margin-top: 40px;">
                <i class="fa-solid fa-chevron-down" style="font-size: 1.5rem; animation: bounce 2s infinite;"></i>
            </div>
        </div>
    </section>

    <!-- Section 2: 撰寫目的 -->
    <section id="s2">
        <div class="reveal">
            <h2>一、撰寫目的</h2>
            <div class="card">
                <p style="color: #fff; font-size: 1.1rem; line-height: 1.8;">
                    近日因團長擅自更動組員一事，各組組長認為GMAT團長的行為已存在明顯干擾團隊正常運作的現象，因此共同撰寫本文件作為書面提議，提供給顧問了解整體狀況，並尋求後續建議。
                </p>
            </div>
        </div>
    </section>

    <!-- Section 3: 內容 (四大問題) -->
    <section id="s3">
        <div class="reveal" style="width: 100%;">
            <h2>二、不妥行為觀察</h2>
            <p>下列是我們觀察到團長在個別事件中的表現，以及各組組長對於事情的看法：</p>
            
            <div class="issue-list" style="margin-top: 30px;">
                <div class="issue-item">
                    <h4><i class="fa-solid fa-triangle-exclamation"></i> 針對組員異動傳遞不實消息</h4>
                    <p style="font-size: 1rem; margin-bottom: 0;">在解釋異動原因時，說詞反覆或與事實不符，造成內部資訊混亂。</p>
                </div>
                <div class="issue-item">
                    <h4><i class="fa-solid fa-user-slash"></i> 對部分學員態度不佳</h4>
                    <p style="font-size: 1rem; margin-bottom: 0;">缺乏領導者應有的包容與溝通耐心，引發學員反彈。</p>
                </div>
                <div class="issue-item">
                    <h4><i class="fa-solid fa-comments"></i> 對部分顧問態度不佳</h4>
                    <p style="font-size: 1rem; margin-bottom: 0;">在與顧問溝通時態度消極或不禮貌，影響合作關係。</p>
                </div>
                <div class="issue-item">
                    <h4><i class="fa-solid fa-microphone-slash"></i> 主持或串接活動行為不妥</h4>
                    <p style="font-size: 1rem; margin-bottom: 0;">台風與控場能力未達預期，影響活動進行與營隊形象。</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Section 4: 決議與提問 -->
    <section id="s4">
        <div class="reveal" style="width: 100%;">
            <h2>三、決議與顧問諮詢</h2>
            
            <div class="card">
                <h3><i class="fa-solid fa-gavel"></i> 我們的立場</h3>
                <p>本次意見收集僅各組組長參與。組長們認為團長沒有善盡責任，因此認為他<strong>不適任團長一職</strong>。</p>
                <p>但對於「去留」與「接任人選」，我們面臨兩難，需要顧問建議：</p>
            </div>

            <div class="question-box">
                <h3><i class="fa-solid fa-circle-question"></i> 問題一：統籌真空危機</h3>
                <p style="color: #fff;">就現況而言，我們缺乏意見統籌人物，目前非常仰賴諮就組欣璇姐的幫助才能維持運作。</p>
                <p><strong>Q：請問顧問覺得在此情況下是否有必要更換團長呢？</strong></p>
            </div>

            <div class="question-box" style="border-color: var(--accent-purple); background: rgba(157, 77, 255, 0.1);">
                <h3 style="color: var(--accent-purple);"><i class="fa-solid fa-users-gear"></i> 問題二：接任人選疑慮</h3>
                <p style="color: #fff;">若更換，目前無敲定人選。</p>
                <ul style="margin-left: 20px; color: #ccc; margin-bottom: 15px;">
                    <li><strong>副團長接手：</strong>可能僅是「維持現況」，因其在宣傳影片製作中未展現足夠領導力。</li>
                    <li><strong>組長接手：</strong>考量情感層面，現任組長們無法接任。</li>
                </ul>
                <p><strong>Q：我們需要一名主事者來規劃並確認進度，請問顧問對此有何看法？我們該以哪些維度來選擇適合的領導人？</strong></p>
            </div>

            <p style="margin-top: 20px; font-size: 0.9rem;">
                *若希望不更動團長，並透過後續勸說與教育提升團長的能力，我們願意接受安排，但我們的訴求依然是希望能有一位可以盡責統籌幹部的人選。
            </p>
        </div>
    </section>

    <!-- Section 5: 線上討論區 -->
    <section id="s5">
        <div class="reveal" style="width: 100%;">
            <h2 style="border-bottom: none; text-align: center; display: block; margin-bottom: 10px;">線上意見留言區</h2>
            <p style="text-align: center; margin-bottom: 30px;">開放顧問與幹部提供意見，所有擁有連結的人都能即時收到訊息。</p>
            
            <div class="chat-container">
                <!-- 輸入區 -->
                <div class="input-group">
                    <input type="text" id="sender-name" placeholder="您的稱呼 (例：XX顧問、XX組長)" />
                </div>
                <div class="input-group">
                    <textarea id="message-text" placeholder="請輸入您的看法或建議..."></textarea>
                </div>
                <div style="text-align: right;">
                    <button id="send-btn" onclick="sendMessage()">送出意見 <i class="fa-solid fa-paper-plane"></i></button>
                </div>

                <!-- 留言列表 -->
                <div id="comments-list" class="comments-list">
                    <p style="text-align:center; color:#aaa; margin-top:20px;">
                        <i class="fa-solid fa-spinner fa-spin"></i> 載入留言中...
                    </p>
                </div>
            </div>
        </div>
    </section>

    <script>
        // Scroll Reveal Animation
        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.1
        };

        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                    updateNavDots(entry.target.closest('section').id);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.reveal').forEach(el => {
            observer.observe(el);
        });

        // Navigation Logic
        function scrollToSection(index) {
            const sectionId = 's' + (index + 1);
            const section = document.getElementById(sectionId);
            section.scrollIntoView({ behavior: 'smooth' });
        }

        function updateNavDots(sectionId) {
            const index = parseInt(sectionId.substring(1)) - 1;
            document.querySelectorAll('.dot').forEach((dot, i) => {
                if (i === index) {
                    dot.classList.add('active');
                } else {
                    dot.classList.remove('active');
                }
            });
        }

        // CSS Injection for Bounce Animation
        const styleSheet = document.createElement("style");
        styleSheet.innerText = `
            @keyframes bounce {
                0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
                40% {transform: translateY(-10px);}
                60% {transform: translateY(-5px);}
            }
        `;
        document.head.appendChild(styleSheet);
    </script>
</body>
</html>

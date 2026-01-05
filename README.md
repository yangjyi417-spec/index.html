<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nyota | 自在放空，"慢"游生活</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Noto Sans SC', sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            overflow-x: hidden;
        }

        /* 开场页 */
        .intro-page {
            position: relative;
            width: 100vw;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: url('https://s.coze.cn/image/TV3wmJrz-Ss/') repeat center center;
            animation: fadeIn 2s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .intro-logo-container {
            position: absolute;
            top: 20px;
            left: 20px;
            display: flex;
            gap: 20px;
        }

        .intro-logo {
            width: 120px;
        }

        .intro-title {
            font-size: 3rem;
            color: #ffffff;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            margin-bottom: 20px;
            animation: slideInDown 1s ease-out;
        }

        @keyframes slideInDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .intro-subtitle {
            font-size: 1.5rem;
            color: #ffffff;
            margin-bottom: 40px;
            animation: slideInUp 1s ease-out 0.5s both;
        }

        @keyframes slideInUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .start-btn {
            padding: 15px 40px;
            font-size: 1.2rem;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .start-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.3);
        }

        /* 主场景 */
        .main-scene {
            display: none;
            position: relative;
            width: 100vw;
            min-height: 100vh;
            padding: 40px 20px;
        }

        .scene-header {
            text-align: center;
            margin-bottom: 60px;
        }

        .scene-title {
            font-size: 2.5rem;
            color: #333333;
            margin-bottom: 10px;
        }

        .scene-subtitle {
            font-size: 1.2rem;
            color: #666666;
        }

        .scene-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
        }

        .scene-card {
            width: 300px;
            height: 400px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .scene-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .scene-card-img {
            width: 100%;
            height: 250px;
            object-fit: cover;
        }

        .scene-card-content {
            padding: 20px;
        }

        .scene-card-title {
            font-size: 1.5rem;
            color: #333333;
            margin-bottom: 10px;
        }

        .scene-card-desc {
            font-size: 1rem;
            color: #666666;
            line-height: 1.6;
        }

        /* 互动游戏 - 慢游收藏家 */
        .game-section {
            margin: 80px 0;
            text-align: center;
        }

        .game-title {
            font-size: 2rem;
            color: #333333;
            margin-bottom: 40px;
        }

        .game-container {
            width: 80%;
            height: 400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .puzzle-container {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .puzzle-piece {
            width: 150px;
            height: 200px;
            background: #f0f0f0;
            border-radius: 10px;
            transition: all 0.3s ease;
            opacity: 0.5;
        }

        .puzzle-piece.collected {
            opacity: 1;
            background-size: cover;
            background-position: center;
        }

        .puzzle-piece.piece1 {
            background-image: url('https://space.coze.cn/s/t1pEA4z5cqg/?width_height=1170x804');
            background-position: left;
        }

        .puzzle-piece.piece2 {
            background-image: url('https://space.coze.cn/s/t1pEA4z5cqg/?width_height=1170x804');
            background-position: center;
        }

        .puzzle-piece.piece3 {
            background-image: url('https://space.coze.cn/s/t1pEA4z5cqg/?width_height=1170x804');
            background-position: right;
        }

        /* ==================== Nyota翻翻乐游戏样式（React版本 - 使用Nyota图片） ==================== */
        .memory-game-wrapper {
            max-width: 100%;
            padding: 20px;
            margin: 60px 0;
        }

        .memory-game-container {
            max-width: 900px;
            margin: 0 auto;
            background: linear-gradient(135deg, #FAF9F6 0%, #F5F5F5 100%);
            border-radius: 30px;
            padding: 40px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
        }

        .memory-game-header {
            text-align: center;
            padding: 20px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }

        .memory-game-header h2 {
            font-size: 2.5rem;
            color: #333333;
            margin-bottom: 20px;
            font-weight: 500;
        }

        .memory-game-logo {
            max-width: 200px;
            margin-bottom: 20px;
        }

        .memory-game-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            font-size: 1.2rem;
            color: #666666;
        }

        .memory-game-stat-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .memory-game-stat-label {
            font-size: 1rem;
        }

        .memory-game-stat-value {
            font-weight: bold;
            font-size: 1.8rem;
            color: #667eea;
        }

        .memory-game-board {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 15px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 20px;
        }

        .memory-card {
            aspect-ratio: 3/4;
            perspective: 1000px;
            cursor: pointer;
        }

        .memory-card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            border-radius: 15px;
        }

        .memory-card.flipped .memory-card-inner {
            transform: rotateY(180deg);
        }

        .memory-card.matched .memory-card-inner {
            animation: memoryMatchPulse 0.6s ease-out;
        }

        .memory-card-front, .memory-card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .memory-card-front {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            transform: rotateY(180deg);
            border: 3px solid #764ba2;
            overflow: hidden;
        }

        .memory-card-front img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .memory-card-back {
            background: linear-gradient(135deg, #c3cfe2 0%, #f5f7fa 100%);
            border: 3px solid #b3b3b3;
        }

        .memory-card-back::before {
            content: '?';
            font-size: 3rem;
            color: #667eea;
            font-weight: bold;
        }

        @keyframes memoryMatchPulse {
            0% { transform: rotateY(180deg) scale(1); }
            50% { transform: rotateY(180deg) scale(1.1); }
            100% { transform: rotateY(180deg) scale(1); }
        }

        .memory-game-controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }

        .memory-game-btn {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
            font-weight: 500;
        }

        .memory-game-btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        .memory-game-btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(102, 126, 234, 0.6);
        }

        .memory-game-btn-secondary {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            color: #333;
            box-shadow: 0 4px 15px rgba(252, 182, 159, 0.4);
        }

        .memory-game-btn-secondary:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(252, 182, 159, 0.6);
        }

        .memory-game-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .memory-game-modal.show {
            display: flex;
        }

        .memory-game-modal-content {
            background: linear-gradient(135deg, #FAF9F6 0%, #F5F5F5 100%);
            padding: 50px;
            border-radius: 30px;
            text-align: center;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            animation: memoryModalPop 0.5s ease-out;
            max-width: 500px;
        }

        @keyframes memoryModalPop {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .memory-game-modal-content h3 {
            font-size: 2.5rem;
            color: #333333;
            margin-bottom: 20px;
        }

        .memory-game-modal-content p {
            font-size: 1.5rem;
            color: #666666;
            margin-bottom: 30px;
        }

        .memory-game-confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            pointer-events: none;
            animation: memoryConfettiFall 3s linear forwards;
            z-index: 999;
        }

        @keyframes memoryConfettiFall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            pointer-events: none;
            animation: confettiFall 4s ease-out forwards;
            z-index: 1000;
        }

        @keyframes confettiFall {
            0% {
                transform: translateY(-10px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        /* 品牌区 */
        .brand-section {
            margin: 80px 0;
            text-align: center;
        }

        .brand-title {
            font-size: 2rem;
            color: #333333;
            margin-bottom: 40px;
        }

        .brand-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
        }

        .brand-card {
            width: 300px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            padding: 20px;
            transition: all 0.3s ease;
        }

        .brand-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .brand-card-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .brand-card-title {
            font-size: 1.5rem;
            color: #333333;
            margin-bottom: 10px;
        }

        .brand-card-desc {
            font-size: 1rem;
            color: #666666;
            line-height: 1.6;
        }

        .buy-btn {
            padding: 10px 30px;
            font-size: 1rem;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            margin-top: 20px;
            transition: all 0.3s ease;
        }

        .buy-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }

        /* 分享页 */
        .share-page {
            display: none;
            position: relative;
            width: 100vw;
            height: 100vh;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .share-title {
            font-size: 2.5rem;
            color: white;
            margin-bottom: 40px;
        }

        .share-container {
            display: flex;
            gap: 30px;
            margin-bottom: 40px;
        }

        .share-btn {
            width: 80px;
            height: 80px;
            background: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
        }

        .share-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.3);
        }

        .share-btn img {
            width: 50px;
            height: 50px;
        }

        /* 响应式设计 */
        @media (max-width: 768px) {
            .intro-title {
                font-size: 2rem;
            }

            .intro-subtitle {
                font-size: 1.2rem;
            }

            .scene-title {
                font-size: 2rem;
            }

            .game-container {
                width: 100%;
            }

            .memory-game-header h2 {
                font-size: 1.8rem;
            }

            .memory-game-board {
                grid-template-columns: repeat(4, 1fr);
                gap: 10px;
            }

            .memory-card-back::before {
                font-size: 2rem;
            }

            .memory-game-stats {
                gap: 20px;
            }

            .memory-game-stat-value {
                font-size: 1.5rem;
            }

            .memory-game-btn {
                padding: 12px 25px;
                font-size: 1rem;
            }
        }

        @media (max-width: 480px) {
            .memory-game-board {
                grid-template-columns: repeat(4, 1fr);
                gap: 8px;
            }

            .memory-card-back::before {
                font-size: 1.5rem;
            }

            .memory-game-stats {
                font-size: 1rem;
            }

            .memory-game-stat-value {
                font-size: 1.2rem;
            }

            .memory-game-btn {
                padding: 10px 20px;
                font-size: 0.9rem;
            }

            .memory-game-modal-content {
                padding: 30px;
                max-width: 90%;
            }

            .memory-game-modal-content h3 {
                font-size: 1.8rem;
            }

            .memory-game-modal-content p {
                font-size: 1.2rem;
            }
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
</head>
<body>
    <!-- 开场页 -->
    <div class="intro-page">
        <div class="intro-logo-container">
            <img src="https://space.coze.cn/s/wrj5xluyhs4/?width_height=1184x673" alt="泡泡玛特" class="intro-logo">
            <img src="https://space.coze.cn/s/wTXa2ZaQ8bY/?width_height=1185x673" alt="Nyota" class="intro-logo">
        </div>
        <h1 class="intro-title">Nyota</h1>
        <p class="intro-subtitle">自在放空，"慢"游生活</p>
        <button class="start-btn" onclick="startH5()">开始慢游</button>
    </div>

    <!-- 主场景 -->
    <div class="main-scene">
        <div class="scene-header">
            <h2 class="scene-title">Nyota的慢游世界</h2>
            <p class="scene-subtitle">和Nyota一起，找回生活的松弛感</p>
        </div>

        <div class="scene-container">
            <div class="scene-card" onclick="showScene('morning')">
                <img src="https://s.coze.cn/image/pN-jYl_F3xA/" alt="晨间治愈" class="scene-card-img">
                <div class="scene-card-content">
                    <h3 class="scene-card-title">晨间治愈</h3>
                    <p class="scene-card-desc">用一杯咖啡的时间，和自己和解</p>
                </div>
            </div>

            <div class="scene-card" onclick="showScene('afternoon')">
                <img src="https://s.coze.cn/image/ooPLFovP1ac/" alt="午后放空" class="scene-card-img">
                <div class="scene-card-content">
                    <h3 class="scene-card-title">午后放空</h3>
                    <p class="scene-card-desc">让思绪随蒲公英一起飘远</p>
                </div>
            </div>

            <div class="scene-card" onclick="showScene('night')">
                <img src="https://s.coze.cn/image/kvOAFmD4IDY/" alt="夜晚疗愈" class="scene-card-img">
                <div class="scene-card-content">
                    <h3 class="scene-card-title">夜晚疗愈</h3>
                    <p class="scene-card-desc">在星空下，找回内心的宁静</p>
                </div>
            </div>
        </div>

        <!-- 互动游戏 - 慢游收藏家 -->
        <div class="game-section">
            <h2 class="game-title">慢游收藏家</h2>
            <div class="game-container">
                <div class="puzzle-container">
                    <div class="puzzle-piece" id="piece1"></div>
                    <div class="puzzle-piece" id="piece2"></div>
                    <div class="puzzle-piece" id="piece3"></div>
                </div>
                <p id="game-status">点击场景卡片收集拼图碎片</p>
            </div>
        </div>

        <!-- Nyota翻翻乐游戏（React版本 - 使用Nyota图片） -->
        <div class="memory-game-wrapper">
            <div class="memory-game-container">
                <div class="memory-game-header">
                    <img src="/assets/nyota logo.png" alt="Nyota Logo" class="memory-game-logo">
                    <h2>🎮 Nyota翻翻乐 🎮</h2>
                    <div class="memory-game-stats">
                        <div class="memory-game-stat-item">
                            <span class="memory-game-stat-label">配对:</span>
                            <span class="memory-game-stat-value" id="memoryMatches">0/10</span>
                        </div>
                    </div>
                </div>

                <div class="memory-game-board" id="memoryGameBoard"></div>

                <div class="memory-game-controls">
                    <button class="memory-game-btn memory-game-btn-primary" onclick="NyotaMemoryGame.resetGame()">重新开始</button>
                    <button class="memory-game-btn memory-game-btn-secondary" onclick="NyotaMemoryGame.enableSound()">🔊 开启音效</button>
                </div>
            </div>
        </div>

        <div class="memory-game-modal" id="memoryWinModal">
            <div class="memory-game-modal-content">
                <h3>🎉 恭喜胜利！🎉</h3>
                <p>你成功配对了所有Nyota形象！</p>
                <button class="memory-game-btn memory-game-btn-primary" onclick="NyotaMemoryGame.resetGame(); NyotaMemoryGame.closeModal();">再来一局</button>
            </div>
        </div>

        <!-- 品牌区 -->
        <div class="brand-section">
            <h2 class="brand-title">Nyota手办</h2>
            <div class="brand-container">
                <div class="brand-card">
                    <img src="https://s.coze.cn/image/MjM_mb2EsHE/" alt="Nyota手办1" class="brand-card-img">
                    <h3 class="brand-card-title">Nyota 放空时刻</h3>
                    <p class="brand-card-desc">还原Nyota最经典的放空姿势，带你感受松弛的力量</p>
                    <button class="buy-btn" onclick="goToStore()">立即购买</button>
                </div>

                <div class="brand-card">
                    <img src="https://space.coze.cn/s/eT_IPVMyOMc/?width_height=1170x1558" alt="Nyota手办2" class="brand-card-img">
                    <h3 class="brand-card-title">Nyota 猫咪陪伴</h3>
                    <p class="brand-card-desc">Nyota与猫咪的温馨时刻，治愈你的每一天</p>
                    <button class="buy-btn" onclick="goToStore()">立即购买</button>
                </div>

                <div class="brand-card">
                    <img src="https://s.coze.cn/image/HxFe6ca5PN8/" alt="Nyota手办3" class="brand-card-img">
                    <h3 class="brand-card-title">Nyota 星空漫步</h3>
                    <p class="brand-card-desc">在星空下漫步，寻找内心的宁静</p>
                    <button class="buy-btn" onclick="goToStore()">立即购买</button>
                </div>
            </div>
        </div>
    </div>

    <!-- 分享页 -->
    <div class="share-page">
        <h2 class="share-title">分享你的慢游时刻</h2>
        <div class="share-container">
            <div class="share-btn" onclick="share('wechat')">
                <img src="https://example.com/wechat-icon.png" alt="微信分享">
            </div>
            <div class="share-btn" onclick="share('weibo')">
                <img src="https://example.com/weibo-icon.png" alt="微博分享">
            </div>
            <div class="share-btn" onclick="share('xiaohongshu')">
                <img src="https://example.com/xiaohongshu-icon.png" alt="小红书分享">
            </div>
        </div>
        <button class="start-btn" onclick="backToMain()">返回主场景</button>
    </div>

    <script>
        // ==================== 慢游收藏家游戏逻辑 ====================
        let collectedPieces = 0;
        const collectedScenes = new Set();

        function startH5() {
            document.querySelector('.intro-page').style.display = 'none';
            document.querySelector('.main-scene').style.display = 'block';
        }

        function showScene(scene) {
            let story = '';
            if (scene === 'morning') {
                story = '清晨的阳光透过窗户洒在Nyota的脸上，她伸了个懒腰，慢慢睁开眼睛。猫咪已经在床边等着她，尾巴轻轻扫过她的手背。Nyota微笑着起身，给猫咪倒了一杯牛奶，然后自己泡了一杯咖啡。坐在窗边，看着外面的世界慢慢苏醒，Nyota感到无比宁静和满足。';
            } else if (scene === 'afternoon') {
                story = '午后的阳光温暖而慵懒，Nyota带着猫咪来到了公园。她躺在草地上，猫咪蜷缩在她的身边，一起享受着宁静的午后时光。微风轻轻拂过，带着花香和青草的气息。Nyota闭上眼睛，感受着阳光的温暖，听着鸟儿的歌声，仿佛时间都静止了。';
            } else if (scene === 'night') {
                story = '夜晚的星空格外美丽，Nyota带着猫咪来到了屋顶。她躺在躺椅上，猫咪依偎在她的怀里，一起仰望着星空。星星闪烁着，仿佛在诉说着古老的故事。Nyota感到无比放松和治愈，所有的烦恼都随着星空的宁静而消散。';
            }
            
            alert(`你选择了${scene}场景\n\n${story}`);
            
            if (!collectedScenes.has(scene)) {
                collectedScenes.add(scene);
                
                if (scene === 'morning') {
                    document.getElementById('piece1').classList.add('collected', 'piece1');
                } else if (scene === 'afternoon') {
                    document.getElementById('piece2').classList.add('collected', 'piece2');
                } else if (scene === 'night') {
                    document.getElementById('piece3').classList.add('collected', 'piece3');
                }
                
                collectedPieces++;
                
                const gameStatus = document.getElementById('game-status');
                gameStatus.textContent = `已收集${collectedPieces}/3块拼图碎片`;
                
                if (collectedPieces === 3) {
                    gameStatus.textContent = '恭喜你集齐所有拼图！合成Nyota手办形象';
                }
            }
        }

        function goToStore() {
            window.location.href = 'https://www.popmart.com';
        }

        function share(platform) {
            console.log('分享到:', platform);
            alert(`分享到${platform}成功！`);
        }

        function backToMain() {
            document.querySelector('.share-page').style.display = 'none';
            document.querySelector('.main-scene').style.display = 'block';
        }

        // ==================== Nyota翻翻乐游戏逻辑（React版本 - 使用Nyota图片） ====================
        const NyotaMemoryGame = {
            TOTAL_TYPES: 10,
            PAIRS: 2,
            cards: [],
            flippedCards: [],
            matchedPairs: 0,
            isFlipping: false,
            soundEnabled: false,
            audioContext: null,

            // 10个Nyota形象图片文件名
            nyotaImages: [
                "0f7f1759b6a820b790bd67eacb9b9733.png",
                "8e70d5192c2937f9d18550d04ebf8ca5.png",
                "9b87499cf40bdb14bd095dbadefccbaa.png",
                "25b8589d855f13a435034fd71b17b008.png",
                "28d2c46bbebb67fa10b77b17e3167ba6.png",
                "050c47ccd62a7b04a75d5eb3f9108d97.png",
                "64b28ad76f9cffed68f0721654f8e065.png",
                "330ec6028e0d1d45ec76609ad0ee8b2b.png",
                "437bcdb0d6eb81a9330f50b8c9faed14.png",
                "93532ad49b7d091eb1b5025f501280de.png"
            ],

            initAudioContext: function() {
                if (!this.audioContext) {
                    this.audioContext = new (window.AudioContext || window.webkitAudioContext)();
                }
            },

            playTone: function(frequency, duration, type) {
                if (!this.soundEnabled || !this.audioContext) return;
                try {
                    const oscillator = this.audioContext.createOscillator();
                    const gainNode = this.audioContext.createGain();
                    oscillator.connect(gainNode);
                    gainNode.connect(this.audioContext.destination);
                    oscillator.frequency.value = frequency;
                    oscillator.type = type;
                    gainNode.gain.setValueAtTime(0.3, this.audioContext.currentTime);
                    gainNode.gain.exponentialRampToValueAtTime(0.01, this.audioContext.currentTime + duration);
                    oscillator.start(this.audioContext.currentTime);
                    oscillator.stop(this.audioContext.currentTime + duration);
                } catch (e) {
                    console.log('Audio error:', e);
                }
            },

            playFlipSound: function() {
                this.playTone(800, 0.1, 'sine');
            },

            playMatchSound: function() {
                const notes = [523.25, 659.25, 783.99, 1046.50];
                notes.forEach((freq, i) => {
                    setTimeout(() => this.playTone(freq, 0.2, 'sine'), i * 100);
                });
            },

            playWinSound: function() {
                const melody = [523.25, 587.33, 659.25, 698.46, 783.99, 880.00, 987.77, 1046.50];
                melody.forEach((freq, i) => {
                    setTimeout(() => this.playTone(freq, 0.3, 'sine'), i * 150);
                });
            },

            enableSound: function() {
                this.initAudioContext();
                this.soundEnabled = true;
                alert('音效已开启！🎵');
            },

            shuffle: function(array) {
                for (let i = array.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [array[i], array[j]] = [array[j], array[i]];
                }
                return array;
            },

            createCards: function() {
                let cardData = [];
                for (let i = 0; i < this.TOTAL_TYPES * this.PAIRS; i++) {
                    const type = Math.floor(i / this.PAIRS);
                    cardData.push({
                        id: i,
                        type: type,
                        number: i + 1,
                        isFlipped: false,
                        isMatched: false
                    });
                }
                return this.shuffle(cardData);
            },

            renderCards: function() {
                const gameBoard = document.getElementById('memoryGameBoard');
                gameBoard.innerHTML = '';
                this.cards.forEach(card => {
                    const cardElement = document.createElement('div');
                    cardElement.className = `memory-card ${card.isFlipped ? 'flipped' : ''} ${card.isMatched ? 'matched' : ''}`;
                    cardElement.dataset.id = card.id;
                    cardElement.onclick = () => this.flipCard(card.id);
                    cardElement.innerHTML = `
                        <div class="memory-card-inner">
                            <div class="memory-card-front">
                                <img src="/assets/${this.nyotaImages[card.type]}" alt="Nyota" />
                            </div>
                            <div class="memory-card-back"></div>
                        </div>
                    `;
                    gameBoard.appendChild(cardElement);
                });
            },

            flipCard: function(index) {
                if (this.isFlipping) return;

                const card = this.cards[index];
                if (card.isFlipped || card.isMatched) return;

                card.isFlipped = true;
                this.flippedCards.push(index);
                this.playFlipSound();

                const cardElement = document.querySelector(`[data-id="${index}"]`);
                cardElement.classList.add('flipped');

                if (this.flippedCards.length === 2) {
                    this.isFlipping = true;
                    this.checkMatch();
                }
            },

            checkMatch: function() {
                const [index1, index2] = this.flippedCards;
                const card1 = this.cards[index1];
                const card2 = this.cards[index2];

                if (card1.type === card2.type) {
                    // 匹配成功
                    setTimeout(() => {
                        card1.isMatched = true;
                        card2.isMatched = true;
                        this.matchedPairs++;
                        this.playMatchSound();

                        document.querySelector(`[data-id="${index1}"]`).classList.add('matched');
                        document.querySelector(`[data-id="${index2}"]`).classList.add('matched');

                        this.flippedCards = [];
                        this.isFlipping = false;

                        if (this.matchedPairs === this.TOTAL_TYPES) {
                            setTimeout(() => {
                                this.showWinModal();
                                this.playWinSound();
                                this.createConfetti();
                            }, 500);
                        }
                    }, 500);
                } else {
                    // 匹配失败
                    setTimeout(() => {
                        card1.isFlipped = false;
                        card2.isFlipped = false;

                        document.querySelector(`[data-id="${index1}"]`).classList.remove('flipped');
                        document.querySelector(`[data-id="${index2}"]`).classList.remove('flipped');

                        this.flippedCards = [];
                        this.isFlipping = false;
                    }, 1000);
                }

                this.updateStats();
            },

            updateStats: function() {
                document.getElementById('memoryMatches').textContent = `${this.matchedPairs}/${this.TOTAL_TYPES}`;
            },

            showWinModal: function() {
                document.getElementById('memoryWinModal').classList.add('show');
            },

            closeModal: function() {
                document.getElementById('memoryWinModal').classList.remove('show');
            },

            createConfetti: function() {
                const colors = ['#FFB6C1', '#FFDAB9', '#FFFDD0', '#FFE4B5', '#FFA07A', '#F0E68C', '#FF69B4'];
                for (let i = 0; i < 50; i++) {
                    setTimeout(() => {
                        const confetti = document.createElement('div');
                        confetti.className = 'confetti';
                        confetti.style.position = 'fixed';
                        confetti.style.width = '10px';
                        confetti.style.height = '10px';
                        confetti.style.top = '-10px';
                        confetti.style.left = Math.random() * 100 + 'vw';
                        confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                        confetti.style.animation = `confetti ${Math.random() * 2 + 2}s ease-out forwards`;
                        confetti.style.zIndex = '1000';
                        document.body.appendChild(confetti);

                        setTimeout(() => {
                            confetti.remove();
                        }, 4000);
                    }, i * 30);
                }
            },

            resetGame: function() {
                this.cards = this.createCards();
                this.flippedCards = [];
                this.matchedPairs = 0;
                this.isFlipping = false;
                this.updateStats();
                this.renderCards();
            }
        };

        // 页面加载完成后初始化
        window.addEventListener('load', function() {
            NyotaMemoryGame.resetGame();
        });
    </script>
</body>
</html>

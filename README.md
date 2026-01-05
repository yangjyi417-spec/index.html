<html lang="zh-CN">
<head>
    <meta charset="UTF-8">assets/
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

        /* 开场页 - 云朵主题 */
        .intro-page {
            position: relative;
            width: 100vw;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(180deg, #e0f7fa 0%, #ffffff 50%, #fff3e0 100%);
            overflow: hidden;
            animation: fadeIn 2s ease-in;
        }

        /* 云朵背景装饰 */
        .intro-page::before,
        .intro-page::after {
            content: '';
            position: absolute;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            filter: blur(20px);
        }

        .intro-page::before {
            width: 300px;
            height: 150px;
            top: 10%;
            left: 10%;
            animation: cloudFloat 20s ease-in-out infinite;
        }

        .intro-page::after {
            width: 400px;
            height: 200px;
            top: 20%;
            right: 10%;
            animation: cloudFloat 25s ease-in-out infinite 5s;
        }

        @keyframes cloudFloat {
            0%, 100% { transform: translateX(0); }
            50% { transform: translateX(50px); }
        }

        .cloud-decoration {
            position: absolute;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 50%;
            filter: blur(10px);
        }

        .cloud-1 {
            width: 200px;
            height: 100px;
            bottom: 20%;
            left: 5%;
            animation: cloudFloat 15s ease-in-out infinite 2s;
        }

        .cloud-2 {
            width: 250px;
            height: 125px;
            bottom: 15%;
            right: 15%;
            animation: cloudFloat 18s ease-in-out infinite 3s;
        }

        .cloud-3 {
            width: 180px;
            height: 90px;
            bottom: 30%;
            left: 50%;
            animation: cloudFloat 22s ease-in-out infinite 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .intro-logo-container {
            position: absolute;
            top: 30px;
            left: 30px;
            display: flex;
            gap: 20px;
            z-index: 10;
        }

        .intro-logo {
            width: 100px;
        }

        .intro-title {
            font-size: 3rem;
            color: #5c6bc0;
            text-shadow: 2px 2px 4px rgba(255, 255, 255, 0.8);
            margin-bottom: 20px;
            animation: slideInDown 1s ease-out;
            position: relative;
            z-index: 10;
        }

        @keyframes slideInDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .intro-subtitle {
            font-size: 1.5rem;
            color: #7986cb;
            margin-bottom: 40px;
            animation: slideInUp 1s ease-out 0.5s both;
            position: relative;
            z-index: 10;
        }

        @keyframes slideInUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* 可爱按钮样式 */
        .start-btn {
            padding: 18px 50px;
            font-size: 1.3rem;
            background: linear-gradient(135deg, #ffd1dc 0%, #ffb6c1 100%);
            color: #8b5a5a;
            border: 3px solid #fff;
            border-radius: 40px;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(255, 182, 193, 0.4);
            transition: all 0.3s ease;
            animation: pulse 2s infinite;
            font-family: inherit;
            font-weight: 600;
            position: relative;
            z-index: 10;
        }

        .start-btn::before {
            content: '☁️';
            margin-right: 8px;
        }

        .start-btn:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 12px 30px rgba(255, 182, 193, 0.6);
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.03); }
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
            margin: 40px 0;
            text-align: center;
            padding: 0 15px;
        }

        .game-title {
            font-size: 2rem;
            color: #333333;
            margin-bottom: 30px;
        }

        .game-container {
            width: 90%;
            max-width: 800px;
            height: auto;
            min-height: 300px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            padding: 30px 20px;
        }

        .puzzle-container {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .puzzle-piece {
            width: 120px;
            height: 160px;
            background: #f0f0f0;
            border-radius: 10px;
            transition: all 0.3s ease;
            opacity: 0.5;
            flex-shrink: 0;
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

        #game-status {
            font-size: 1.1rem;
            color: #666666;
            padding: 10px;
            word-wrap: break-word;
        }

        /* ==================== Nyota翻翻乐游戏样式（React版本 - 使用Nyota图片） ==================== */
        .memory-game-wrapper {
            width: 100%;
            padding: 40px 20px;
            margin: 60px 0;
        }

        .memory-game-container {
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
            background: linear-gradient(135deg, #FAF9F6 0%, #F5F5F5 100%);
            border-radius: 20px;
            padding: 30px;
            border: 2px solid #e0e0e0;
        }

        .memory-game-header {
            text-align: center;
            padding: 20px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }

        .memory-game-header h2 {
            font-size: 2rem;
            color: #333333;
            margin-bottom: 15px;
            font-weight: 500;
        }

        .memory-game-logo {
            max-width: 150px;
            margin-bottom: 15px;
        }

        .memory-game-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            font-size: 1.1rem;
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
            font-size: 1.5rem;
            color: #667eea;
        }

        .memory-game-board {
            display: grid;
            grid-template-columns: repeat(10, 1fr);
            gap: 8px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 15px;
        }

        .memory-card {
            aspect-ratio: 1;
            perspective: 1000px;
            cursor: pointer;
        }

        .memory-card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            border-radius: 8px;
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
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .memory-card-front {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            transform: rotateY(180deg);
            border: 2px solid #764ba2;
            overflow: hidden;
        }

        .memory-card-front img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .memory-card-back {
            background: linear-gradient(135deg, #c3cfe2 0%, #f5f7fa 100%);
            border: 2px solid #b3b3b3;
            background-image: url('public/assets/nyota logo.png');
            background-size: contain;
            background-position: center;
            background-repeat: no-repeat;
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
            padding: 15px 45px;
            font-size: 1.2rem;
            border: 3px solid #fff;
            border-radius: 35px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
            font-weight: 600;
            position: relative;
            overflow: hidden;
        }

        .memory-game-btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .memory-game-btn:hover::after {
            width: 300px;
            height: 300px;
        }

        .memory-game-btn-primary {
            background: linear-gradient(135deg, #ffd1dc 0%, #ffb6c1 100%);
            color: #8b5a5a;
            box-shadow: 0 6px 20px rgba(255, 182, 193, 0.4);
        }

        .memory-game-btn-primary:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 8px 25px rgba(255, 182, 193, 0.6);
        }

        .memory-game-btn-secondary {
            background: linear-gradient(135deg, #fff9c4 0%, #ffeb3b 100%);
            color: #8b7a5a;
            box-shadow: 0 6px 20px rgba(255, 235, 59, 0.4);
        }

        .memory-game-btn-secondary:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 8px 25px rgba(255, 235, 59, 0.6);
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

        /* 场景故事模态框 */
        .scene-story-modal {
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

        .scene-story-modal.show {
            display: flex;
        }

        .scene-story-content {
            background: linear-gradient(135deg, #FAF9F6 0%, #F5F5F5 100%);
            padding: 50px;
            border-radius: 30px;
            text-align: center;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            animation: storyModalPop 0.5s ease-out;
            max-width: 700px;
            max-height: 80vh;
            overflow-y: auto;
        }

        @keyframes storyModalPop {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .scene-story-content h3 {
            font-size: 2rem;
            color: #333333;
            margin-bottom: 20px;
        }

        .scene-story-content p {
            font-size: 1.2rem;
            color: #666666;
            line-height: 1.8;
            margin-bottom: 30px;
        }

        /* 提示消息模态框 */
        .message-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 1001;
        }

        .message-modal.show {
            display: flex;
        }

        .message-modal-content {
            background: linear-gradient(135deg, #fff9c4 0%, #fffde7 100%);
            padding: 40px;
            border-radius: 25px;
            text-align: center;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
            animation: messagePop 0.3s ease-out;
            max-width: 450px;
            border: 3px solid #fff;
        }

        @keyframes messagePop {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .message-modal-content p {
            font-size: 1.2rem;
            color: #555555;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .message-modal-content .miniprogram-hint {
            font-size: 1rem;
            color: #888888;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px dashed #ccc;
        }

        /* 响应式设计 */
        @media (max-width: 768px) {
            .intro-logo {
                width: 80px;
            }

            .start-btn {
                padding: 15px 35px;
                font-size: 1.1rem;
            }

            .intro-title {
                font-size: 2rem;
            }

            .intro-subtitle {
                font-size: 1.2rem;
            }

            .scene-title {
                font-size: 2rem;
            }

            .scene-container {
                gap: 20px;
            }

            .scene-card {
                width: 280px;
                height: 380px;
            }

            .scene-card-img {
                height: 200px;
            }

            .game-section {
                margin: 40px 0;
                padding: 0 10px;
            }

            .game-title {
                font-size: 1.5rem;
                margin-bottom: 20px;
            }

            .game-container {
                width: 95%;
                padding: 20px 15px;
            }

            .puzzle-piece {
                width: 90px;
                height: 120px;
                margin: 0 5px;
            }

            #game-status {
                font-size: 1rem;
            }

            .memory-game-header h2 {
                font-size: 1.5rem;
            }

            .memory-game-header h2 {
                font-size: 1.5rem;
            }

            .memory-game-board {
                grid-template-columns: repeat(5, 1fr);
                gap: 6px;
            }

            .memory-game-stats {
                gap: 20px;
            }

            .memory-game-stat-value {
                font-size: 1.3rem;
            }

            .memory-game-btn {
                padding: 12px 30px;
                font-size: 1rem;
            }

            .scene-story-content {
                padding: 30px;
                max-width: 90%;
            }

            .scene-story-content h3 {
                font-size: 1.5rem;
            }

            .scene-story-content p {
                font-size: 1rem;
            }
        }

        @media (max-width: 480px) {
            .memory-game-board {
                grid-template-columns: repeat(4, 1fr);
                gap: 5px;
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
                padding: 10px 25px;
                font-size: 0.95rem;
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

            .scene-story-content {
                padding: 25px;
            }

            .scene-story-content h3 {
                font-size: 1.3rem;
            }

            .scene-story-content p {
                font-size: 0.95rem;
            }
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
</head>
<body>
    <!-- 开场页 -->
    <div class="intro-page">
        <div class="cloud-decoration cloud-1"></div>
        <div class="cloud-decoration cloud-2"></div>
        <div class="cloud-decoration cloud-3"></div>

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
                    <button class="memory-game-btn memory-game-btn-secondary" onclick="NyotaMemoryGame.toggleMusic()">🔊 播放音乐</button>
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

        <!-- 场景故事模态框 -->
        <div class="scene-story-modal" id="sceneStoryModal">
            <div class="scene-story-content">
                <h3 id="sceneStoryTitle">场景标题</h3>
                <p id="sceneStoryText">场景故事内容</p>
                <button class="memory-game-btn memory-game-btn-primary" onclick="closeSceneModal()">确定</button>
            </div>
        </div>

        <!-- 消息提示模态框 -->
        <div class="message-modal" id="messageModal">
            <div class="message-modal-content">
                <p id="messageText">消息内容</p>
                <div id="messageHint" class="miniprogram-hint"></div>
                <button class="memory-game-btn memory-game-btn-primary" onclick="closeMessageModal()">确定</button>
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
            let title = '';
            if (scene === 'morning') {
                title = '晨间治愈';
                story = '清晨的阳光透过窗户洒在Nyota的脸上，她伸了个懒腰，慢慢睁开眼睛。猫咪已经在床边等着她，尾巴轻轻扫过她的手背。Nyota微笑着起身，给猫咪倒了一杯牛奶，然后自己泡了一杯咖啡。坐在窗边，看着外面的世界慢慢苏醒，Nyota感到无比宁静和满足。';
            } else if (scene === 'afternoon') {
                title = '午后放空';
                story = '午后的阳光温暖而慵懒，Nyota带着猫咪来到了公园。她躺在草地上，猫咪蜷缩在她的身边，一起享受着宁静的午后时光。微风轻轻拂过，带着花香和青草的气息。Nyota闭上眼睛，感受着阳光的温暖，听着鸟儿的歌声，仿佛时间都静止了。';
            } else if (scene === 'night') {
                title = '夜晚疗愈';
                story = '夜晚的星空格外美丽，Nyota带着猫咪来到了屋顶。她躺在躺椅上，猫咪依偎在她的怀里，一起仰望着星空。星星闪烁着，仿佛在诉说着古老的故事。Nyota感到无比放松和治愈，所有的烦恼都随着星空的宁静而消散。';
            }
            
            document.getElementById('sceneStoryTitle').textContent = title;
            document.getElementById('sceneStoryText').textContent = story;
            document.getElementById('sceneStoryModal').classList.add('show');
            
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

        function closeSceneModal() {
            document.getElementById('sceneStoryModal').classList.remove('show');
        }

        function goToStore() {
            // 直接跳转到微信小程序（URL Scheme）
            const miniProgramUrl = 'weixin://dl/business/?t=Ltcq1cyK7kb';

            // 尝试直接打开小程序
            try {
                window.location.href = miniProgramUrl;
            } catch (e) {
                console.log('跳转失败:', e);
            }
        }

        function share(platform) {
            console.log('分享到:', platform);
            document.getElementById('messageText').textContent = `分享到${platform}成功！`;
            document.getElementById('messageModal').classList.add('show');
        }

        function closeMessageModal() {
            document.getElementById('messageModal').classList.remove('show');
            // 清空小程序提示
            document.getElementById('messageHint').textContent = '';
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
            musicPlaying: false,
            backgroundMusic: null,

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

            initBackgroundMusic: function() {
                if (!this.backgroundMusic) {
                    this.backgroundMusic = new Audio('/assets/放松 露营 周末 轻快 旅行 vlog日常 做饭 治愈_爱给网_aigei_com.mp3');
                    this.backgroundMusic.loop = true;
                    this.backgroundMusic.volume = 0.5;

                    // 监听音乐播放结束事件（虽然设置了loop，但某些浏览器可能需要）
                    this.backgroundMusic.addEventListener('ended', function() {
                        this.currentTime = 0;
                        this.play();
                    });

                    // 监听播放错误
                    this.backgroundMusic.addEventListener('error', function(e) {
                        console.log('背景音乐播放错误:', e);
                        NyotaMemoryGame.musicPlaying = false;
                        NyotaMemoryGame.updateMusicButton();
                    });
                }
            },

            toggleMusic: function() {
                this.initBackgroundMusic();

                // 移动端需要用户交互才能播放
                if (this.backgroundMusic.paused) {
                    const playPromise = this.backgroundMusic.play();

                    if (playPromise !== undefined) {
                        playPromise.then(() => {
                            this.musicPlaying = true;
                            document.getElementById('messageText').textContent = '背景音乐已开启 🎵✨';
                            document.getElementById('messageModal').classList.add('show');
                            this.updateMusicButton();
                        }).catch(error => {
                            console.log('播放音乐失败:', error);
                            document.getElementById('messageText').textContent = '音乐播放失败，请重试';
                            document.getElementById('messageModal').classList.add('show');
                        });
                    }
                } else {
                    this.backgroundMusic.pause();
                    this.musicPlaying = false;
                    document.getElementById('messageText').textContent = '背景音乐已暂停';
                    document.getElementById('messageModal').classList.add('show');
                    this.updateMusicButton();
                }
            },

            updateMusicButton: function() {
                const btn = document.querySelector('.memory-game-btn-secondary');
                if (btn) {
                    if (this.musicPlaying) {
                        btn.innerHTML = '🔇 暂停音乐';
                    } else {
                        btn.innerHTML = '🔊 播放音乐';
                    }
                }
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
                let idCounter = 0;

                // 为每种类型创建2张卡牌
                for (let type = 0; type < this.TOTAL_TYPES; type++) {
                    for (let pair = 0; pair < this.PAIRS; pair++) {
                        cardData.push({
                            id: idCounter,
                            type: type,
                            number: type + 1,
                            isFlipped: false,
                            isMatched: false
                        });
                        idCounter++;
                    }
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

                    // 使用事件委托或直接绑定，保存cardId到闭包
                    const cardId = card.id;
                    cardElement.onclick = function() {
                        NyotaMemoryGame.flipCard(cardId);
                    };

                    const front = document.createElement('div');
                    front.className = 'memory-card-front';

                    const img = document.createElement('img');
                    img.src = '/assets/' + this.nyotaImages[card.type];
                    img.alt = 'Nyota';
                    front.appendChild(img);

                    const back = document.createElement('div');
                    back.className = 'memory-card-back';

                    const inner = document.createElement('div');
                    inner.className = 'memory-card-inner';
                    inner.appendChild(front);
                    inner.appendChild(back);

                    cardElement.appendChild(inner);
                    gameBoard.appendChild(cardElement);
                });
            },

            flipCard: function(index) {
                if (this.isFlipping) return;

                const card = this.cards[index];
                if (!card || card.isFlipped || card.isMatched) return;

                // 更新卡牌状态
                this.cards[index].isFlipped = true;
                this.flippedCards.push(index);

                // 更新DOM
                const cardElement = document.querySelector(`[data-id="${index}"]`);
                if (cardElement) {
                    cardElement.classList.add('flipped');
                }

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
                        this.cards[index1].isMatched = true;
                        this.cards[index2].isMatched = true;
                        this.matchedPairs++;

                        const cardElement1 = document.querySelector(`[data-id="${index1}"]`);
                        const cardElement2 = document.querySelector(`[data-id="${index2}"]`);
                        if (cardElement1) cardElement1.classList.add('matched');
                        if (cardElement2) cardElement2.classList.add('matched');

                        this.flippedCards = [];
                        this.isFlipping = false;

                        if (this.matchedPairs === this.TOTAL_TYPES) {
                            setTimeout(() => {
                                this.showWinModal();
                                this.createConfetti();
                            }, 500);
                        }
                    }, 500);
                } else {
                    // 匹配失败
                    setTimeout(() => {
                        this.cards[index1].isFlipped = false;
                        this.cards[index2].isFlipped = false;

                        const cardElement1 = document.querySelector(`[data-id="${index1}"]`);
                        const cardElement2 = document.querySelector(`[data-id="${index2}"]`);
                        if (cardElement1) cardElement1.classList.remove('flipped');
                        if (cardElement2) cardElement2.classList.remove('flipped');

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
                // 确保按钮状态正确
                this.updateMusicButton();
            }
        };

        // 页面加载完成后初始化
        window.addEventListener('load', function() {
            NyotaMemoryGame.resetGame();
        });
    </script>
</body>
</html>

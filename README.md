<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nyota | 自在放空，“慢”游生活</title>
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

        /* 互动游戏 */
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
        <p class="intro-subtitle">自在放空，“慢”游生活</p>
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

        <!-- 互动游戏 -->
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
        let collectedPieces = 0;
        const collectedScenes = new Set();

        function startH5() {
            document.querySelector('.intro-page').style.display = 'none';
            document.querySelector('.main-scene').style.display = 'block';
        }

        function showScene(scene) {
            // 这里可以添加场景切换的动画效果
            console.log('显示场景:', scene);
            
            // 显示小故事
            let story = '';
            if (scene === 'morning') {
                story = '清晨的阳光透过窗户洒在Nyota的脸上，她伸了个懒腰，慢慢睁开眼睛。猫咪已经在床边等着她，尾巴轻轻扫过她的手背。Nyota微笑着起身，给猫咪倒了一杯牛奶，然后自己泡了一杯咖啡。坐在窗边，看着外面的世界慢慢苏醒，Nyota感到无比宁静和满足。';
            } else if (scene === 'afternoon') {
                story = '午后的阳光温暖而慵懒，Nyota带着猫咪来到了公园。她躺在草地上，猫咪蜷缩在她的身边，一起享受着宁静的午后时光。微风轻轻拂过，带着花香和青草的气息。Nyota闭上眼睛，感受着阳光的温暖，听着鸟儿的歌声，仿佛时间都静止了。';
            } else if (scene === 'night') {
                story = '夜晚的星空格外美丽，Nyota带着猫咪来到了屋顶。她躺在躺椅上，猫咪依偎在她的怀里，一起仰望着星空。星星闪烁着，仿佛在诉说着古老的故事。Nyota感到无比放松和治愈，所有的烦恼都随着星空的宁静而消散。';
            }
            
            alert(`你选择了${scene}场景\n\n${story}`);
            
            // 检查是否已经收集过该场景
            if (!collectedScenes.has(scene)) {
                collectedScenes.add(scene);
                
                // 收集拼图碎片
                if (scene === 'morning') {
                    document.getElementById('piece1').classList.add('collected', 'piece1');
                } else if (scene === 'afternoon') {
                    document.getElementById('piece2').classList.add('collected', 'piece2');
                } else if (scene === 'night') {
                    document.getElementById('piece3').classList.add('collected', 'piece3');
                }
                
                collectedPieces++;
                
                // 更新游戏状态
                const gameStatus = document.getElementById('game-status');
                gameStatus.textContent = `已收集${collectedPieces}/3块拼图碎片`;
                
                // 检查是否集齐所有拼图
                if (collectedPieces === 3) {
                    gameStatus.textContent = '恭喜你集齐所有拼图！合成Nyota手办形象';
                    // 可以添加合成动画效果
                }
            }
        }

        function goToStore() {
            // 跳转到泡泡玛特抽盒机小程序
            window.location.href = 'https://www.popmart.com';
        }

        function share(platform) {
            // 分享功能
            console.log('分享到:', platform);
            alert(`分享到${platform}成功！`);
        }

        function backToMain() {
            document.querySelector('.share-page').style.display = 'none';
            document.querySelector('.main-scene').style.display = 'block';
        }

        function startGame() {
            alert('慢游收藏家游戏开始！点击场景卡片收集碎片');
        }

        // 页面加载完成后初始化
        window.addEventListener('load', function() {
            // 可以添加一些初始化逻辑
        });
    </script>
</body>
</html>

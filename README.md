<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Garena Free Fire - Free Diamonds Generator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            min-height: 100vh;
            font-family: 'Arial', sans-serif;
            overflow-x: hidden;
            position: relative;
        }

        /* Gaming Background Effects */
        .ocean-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 80%, rgba(255, 107, 53, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(255, 255, 255, 0.1) 0%, transparent 50%),
                linear-gradient(135deg, #ff6b35 0%, #f7931e 50%, #ff1744 100%);
            z-index: -2;
        }

        .bubbles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        .bubble {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 6s infinite ease-in-out;
        }

        @keyframes float {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100px) scale(1); opacity: 0; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            margin-bottom: 3rem;
            color: white;
        }

        .header h1 {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            animation: wave 3s ease-in-out infinite;
        }

        @keyframes wave {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
        }

        /* Login Form Container */
        .net-container {
            background: rgba(0, 0, 0, 0.8);
            border-radius: 20px;
            padding: 3rem;
            margin: 2rem 0;
            backdrop-filter: blur(10px);
            border: 2px solid #FFD700;
            box-shadow: 0 8px 32px rgba(255, 215, 0, 0.3);
            max-width: 500px;
            margin: 2rem auto;
        }

        .login-form {
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .fishing-net:hover {
            background-size: 45px 45px;
            transform: scale(1.02);
        }

        @keyframes netSway {
            0%, 100% { transform: translateX(0) rotateZ(0deg); }
            25% { transform: translateX(5px) rotateZ(1deg); }
            75% { transform: translateX(-5px) rotateZ(-1deg); }
        }

        /* Login Form Styles */
        .login-container {
            background: rgba(0,0,0,0.7);
            border: 2px solid #FFD700;
            border-radius: 15px;
            padding: 2rem;
            max-width: 500px;
            margin: 2rem auto;
        }

        .input-group {
            margin-bottom: 1.5rem;
        }

        .input-group label {
            display: block;
            color: #FFD700;
            margin-bottom: 0.5rem;
        }

        .input-group input,
        .input-group select {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            border: 1px solid #FFD700;
            background: rgba(0,0,0,0.5);
            color: white;
        }

        .claim-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(to right, #FFD700, #FF8C00);
            border: none;
            border-radius: 8px;
            color: #000;
            font-weight: bold;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
        }

        .claim-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255,215,0,0.4);
        }

        .social-login {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .fb-login, .google-login {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .fb-login {
            background: #1877F2;
            color: white;
            border: none;
        }

        .google-login {
            background: white;
            color: #444;
            border: 1px solid #ddd;
        }

        .fb-login:hover, .google-login:hover {
            transform: translateY(-3px);
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
        }
        
        .divider {
            text-align: center;
            color: #FFD700;
            margin: 1.5rem 0;
            position: relative;
        }
        
        .divider::before, .divider::after {
            content: "";
            flex: 1;
            border-bottom: 1px solid #FFD700;
            opacity: 0.3;
            position: absolute;
            top: 50%;
            width: 45%;
        }
        
        .divider::before {
            left: 0;
        }
        
        .divider::after {
            right: 0;
        }

        .fish {
            position: absolute;
            width: 60px;
            height: 40px;
            background: linear-gradient(45deg, #FFD700, #FFA500);
            border-radius: 50% 0 50% 0;
            animation: swim 3s ease-in-out infinite;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .fish::before {
            content: '';
            position: absolute;
            right: -15px;
            top: 50%;
            transform: translateY(-50%);
            width: 0;
            height: 0;
            border-left: 20px solid #FFA500;
            border-top: 10px solid transparent;
            border-bottom: 10px solid transparent;
        }

        .fish::after {
            content: '';
            position: absolute;
            left: 10px;
            top: 10px;
            width: 8px;
            height: 8px;
            background: #000;
            border-radius: 50%;
        }

        @keyframes swim {
            0%, 100% { transform: translateX(0) translateY(0) rotate(0deg); }
            25% { transform: translateX(10px) translateY(-5px) rotate(2deg); }
            75% { transform: translateX(-10px) translateY(5px) rotate(-2deg); }
        }

        .fish:hover {
            transform: scale(1.1) rotate(5deg);
            filter: brightness(1.2);
        }

        /* Interactive Controls */
        .controls {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin: 2rem 0;
            flex-wrap: wrap;
        }

        .control-btn {
            background: linear-gradient(145deg, #4a90e2, #357abd);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(74, 144, 226, 0.3);
        }

        .control-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(74, 144, 226, 0.4);
            background: linear-gradient(145deg, #357abd, #2c6aa0);
        }

        .control-btn:active {
            transform: translateY(0);
        }

        /* Stats Display */
        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin: 2rem 0;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 1.5rem;
            border-radius: 15px;
            text-align: center;
            color: white;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.15);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #FFD700;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

        .stat-label {
            font-size: 1rem;
            opacity: 0.9;
            margin-top: 0.5rem;
        }

        /* New Sections Styles */
        .character-section, .codes-section {
            background: rgba(0,0,0,0.7);
            border: 2px solid #FFD700;
            border-radius: 15px;
            padding: 1.5rem;
            margin: 2rem auto;
            max-width: 500px;
        }
        
        .code-card {
            background: rgba(0,0,0,0.5);
            padding: 1rem;
            border-radius: 10px;
        }
        
        .code-card ul {
            color: white;
            padding-left: 1.5rem;
            margin-top: 0.5rem;
        }
        
        .code-card li {
            margin-bottom: 0.5rem;
        }

        /* Success Page Styles */
        .success-page {
            display: none;
            text-align: center;
            background: rgba(0,0,0,0.8);
            padding: 2rem;
            border-radius: 15px;
            max-width: 500px;
            margin: 2rem auto;
            border: 2px solid #FFD700;
        }
        
        .success-icon {
            font-size: 4rem;
            color: #FFD700;
            margin-bottom: 1rem;
        }
        
        .success-message {
            font-size: 1.2rem;
            color: white;
            margin-bottom: 1.5rem;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2rem;
            }
            
            .fishing-net {
                height: 400px;
                background-size: 30px 30px;
            }
            
            .controls {
                flex-direction: column;
                align-items: center;
            }
            
            .control-btn {
                width: 200px;
            }
        }

        /* Additional Visual Effects */
        .net-shadow {
            position: absolute;
            bottom: -20px;
            left: 10%;
            right: 10%;
            height: 40px;
            background: radial-gradient(ellipse, rgba(0, 0, 0, 0.3) 0%, transparent 70%);
            border-radius: 50%;
            filter: blur(10px);
        }

        .splash-effect {
            position: absolute;
            width: 20px;
            height: 20px;
            background: rgba(255, 255, 255, 0.6);
            border-radius: 50%;
            pointer-events: none;
            animation: splash 1s ease-out forwards;
        }

        @keyframes splash {
            0% {
                transform: scale(0);
                opacity: 1;
            }
            100% {
                transform: scale(3);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div class="ocean-bg"></div>
    <div class="bubbles" id="bubbles"></div>

    <div class="container">
        <div class="header">
            <h1>🔥 FREE FIRE GENERATOR 🔥</h1>
            <p>Get unlimited Diamonds & exclusive Gun Skins - 100% Free!</p>
            <div class="youtube-promo" style="background: rgba(255,215,0,0.1); padding: 1rem; border-radius: 10px; margin-top: 1rem;">
                <p style="color:#FFD700; margin-bottom: 0.5rem;">🎁 Subscribe to get bonus diamonds! 🎁</p>
                <a href="https://www.youtube.com/@y.sgameff9858" target="_blank" class="subscribe-btn" 
                   style="display: inline-block; background: #ff0000; color: white; padding: 10px 15px; 
                   border-radius: 5px; text-decoration: none; font-weight: bold;">
                   ▶ Subscribe Now
                </a>
            </div>
        </div>

        <div class="login-container">
            <form class="login-form">
                <div class="input-group">
                    <label>Player ID:</label>
                    <input type="text" placeholder="Enter your Free Fire ID">
                </div>
                <div class="input-group">
                    <label>Username:</label>
                    <input type="text" placeholder="Your in-game name">
                </div>
                <div class="input-group">
                    <label>Diamonds:</label>
                    <select>
                        <option>1000 Diamonds</option>
                        <option>5000 Diamonds</option>
                        <option>10000 Diamonds</option>
                    </select>
                </div>
                <button type="submit" class="claim-btn">CLAIM NOW</button>
                
                <div class="divider">OR CONNECT WITH</div>
                
                <div class="social-login">
                    <button type="button" class="fb-login">
                        <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/d321cc40-fc80-4c37-96f1-c45ff78a8cc7.png" alt="Facebook" style="width:20px;height:20px;">
                        Continue with Facebook
                    </button>
                    <button type="button" class="google-login">
                        <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/c58c598f-2503-4e12-b37c-266908ae5df1.png" alt="Google" style="width:20px;height:20px;">
                        Continue with Google
                    </button>
                </div>
            </form>
        </div>

        <div class="features" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1rem; margin: 3rem 0;">
            <div class="feature-card" style="background: rgba(0,0,0,0.7); padding: 1.5rem; border-radius: 15px; text-align: center; border: 1px solid #FFD700;">
                <div style="font-size: 2rem; margin-bottom: 1rem;">💎</div>
                <h3 style="color: #FFD700; margin-bottom: 0.5rem;">Free Diamonds</h3>
                <p style="color: white; font-size: 0.9rem;">Get unlimited diamonds instantly without spending real money</p>
            </div>
            <div class="feature-card" style="background: rgba(0,0,0,0.7); padding: 1.5rem; border-radius: 15px; text-align: center; border: 1px solid #FFD700;">
                <div style="font-size: 2rem; margin-bottom: 1rem;">🔫</div>
                <h3 style="color: #FFD700; margin-bottom: 0.5rem;">Exclusive Skins</h3>
                <p style="color: white; font-size: 0.9rem;">Unlock rare weapon skins that cost hundreds of dollars</p>
            </div>
            <div class="feature-card" style="background: rgba(0,0,0,0.7); padding: 1.5rem; border-radius: 15px; text-align: center; border: 1px solid #FFD700;">
                <div style="font-size: 2rem; margin-bottom: 1rem;">⚡</div>
                <h3 style="color: #FFD700; margin-bottom: 0.5rem;">Instant Delivery</h3>
                <p style="color: white; font-size: 0.9rem;">Receive your rewards immediately after generation</p>
            </div>
        </div>

        <!-- DJ Alok Character Section -->
        <div class="character-section">
            <h2 style="color:#FFD700;text-align:center;margin:2rem 0;">🎧 GET DJ ALOK CHARACTER 🎧</h2>
            <div class="character-card">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/adfbad97-94de-4f8f-9306-9d2539396c70.png" alt="DJ Alok character" style="width:100%;border-radius:10px;">
                <button class="claim-btn" style="margin-top:1rem;">🔓 UNLOCK DJ ALOK NOW</button>
            </div>
        </div>

        <!-- Redeem Codes Section -->
        <div class="codes-section">
            <h2 style="color:#FFD700;text-align:center;margin:2rem 0;">🎁 CURRENT REDEEM CODES 🎁</h2>
            <div class="code-card">
                <h3 style="color:#FFD700;">Google Play Codes:</h3>
                <ul>
                    <li>FF123GOOGLE</li>
                    <li>GARENA2023</li>
                    <li>FREEFIREX</li>
                </ul>
                <h3 style="color:#FFD700;margin-top:1rem;">Steam Codes:</h3>
                <ul>
                    <li>STEAMFF2023</li>
                    <li>FFSTEAM99</li>
                </ul>
                <h3 style="color:#FFD700;margin-top:1rem;">Minecraft Codes:</h3>
                <ul>
                    <li>MINECRAFT2023</li>
                    <li>CREATIVEMC</li>
                    <li>BLCRAFTX</li>
                </ul>
            </div>
        </div>

        <!-- Countdown Timer -->
        <div class="countdown" style="background: rgba(255,0,0,0.2); padding: 1rem; border-radius: 10px; 
             max-width: 500px; margin: 2rem auto; text-align: center; border: 1px solid red;">
            <h3 style="color:#FFD700">⏰ Claim Offer Ends In:</h3>
            <div id="countdown-timer" style="font-size: 1.8rem; color: white; font-weight: bold;">
                24:00:00
            </div>
            <p style="color:#FFD700; margin-top: 0.5rem;">Subscribe now before claim period ends!</p>
        </div>

        <div class="stats">
            <div class="stat-card">
                <div class="stat-number">24,589</div>
                <div class="stat-label">Users Today</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">1.2M</div>
                <div class="stat-label">Diamonds Sent</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">99.7%</div>
                <div class="stat-label">Success Rate</div>
            </div>
        </div>

        <!-- Success Page -->
        <div class="success-page" id="successPage">
            <div class="success-icon">✅</div>
            <h2 style="color:#FFD700">Successfully Redeemed!</h2>
            <p class="success-message">
                Your diamonds will be added to your account shortly.<br>
                Please restart Free Fire to see your rewards.
            </p>
            <button class="claim-btn" onclick="window.location.reload()">CLAIM AGAIN</button>
        </div>
    </div>

    <script>
        // Create floating bubbles for effect
        function createBubbles() {
            const bubblesContainer = document.getElementById('bubbles');
            
            for (let i = 0; i < 10; i++) {
                setTimeout(() => {
                    const bubble = document.createElement('div');
                    bubble.className = 'bubble';
                    bubble.style.left = Math.random() * 100 + '%';
                    bubble.style.width = bubble.style.height = Math.random() * 20 + 10 + 'px';
                    bubble.style.animationDelay = Math.random() * 4 + 's';
                    bubble.style.animationDuration = (Math.random() * 2 + 3) + 's';
                    bubblesContainer.appendChild(bubble);

                    setTimeout(() => {
                        if (bubble.parentNode) {
                            bubble.parentNode.removeChild(bubble);
                        }
                    }, 6000);
                }, i * 300);
            }

            setTimeout(createBubbles, 4000);
        }

        // Handle form submission
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const playerId = document.getElementById('playerId').value;
            const username = document.getElementById('username').value;
            const diamonds = document.getElementById('diamonds').value;
            const skin = document.querySelector('input[name="skin"]:checked');
            
            if (!playerId || !username || !diamonds || !skin) {
                alert('Please fill in all fields!');
                return;
            }
            
            // Simulate loading process
            const submitBtn = e.target.querySelector('button[type="submit"]');
            const originalText = submitBtn.innerHTML;
            
            submitBtn.innerHTML = '🔄 GENERATING...';
            submitBtn.disabled = true;
            
            // Simulate generation process
            setTimeout(() => {
                submitBtn.innerHTML = '✅ COMPLETED!';
                setTimeout(() => {
                    // Hide form and show success page
                    document.getElementById('loginForm').style.display = 'none';
                    document.getElementById('successPage').style.display = 'block';
                    
                    // Reset form
                    document.getElementById('loginForm').reset();
                    submitBtn.innerHTML = originalText;
                    submitBtn.disabled = false;
                }, 1000);
            }, 3000);
        });

        // Animate numbers in stats
        function animateNumbers() {
            const users = document.getElementById('usersCount');
            const diamonds = document.getElementById('diamondsGiven');
            
            let userCount = 47392;
            let diamondCount = 2.4;
            
            setInterval(() => {
                userCount += Math.floor(Math.random() * 3) + 1;
                users.textContent = userCount.toLocaleString();
            }, 5000);
            
            setInterval(() => {
                diamondCount += 0.1;
                diamonds.textContent = diamondCount.toFixed(1) + 'M';
            }, 8000);
        }

        // Social login handlers
        document.querySelector('.fb-login').addEventListener('click', function() {
            alert('Facebook login would be implemented here\nWe would redirect to Facebook OAuth');
        });
        
        document.querySelector('.google-login').addEventListener('click', function() {
            alert('Google login would be implemented here\nWe would redirect to Google OAuth');
        });

        // Countdown Timer
        function startCountdown() {
            let hours = 24;
            let minutes = 0;
            let seconds = 0;
            
            const timer = setInterval(function() {
                if (seconds === 0) {
                    if (minutes === 0) {
                        if (hours === 0) {
                            clearInterval(timer);
                            document.getElementById('countdown-timer').textContent = "OFFER ENDED!";
                            return;
                        }
                        hours--;
                        minutes = 59;
                    } else {
                        minutes--;
                    }
                    seconds = 59;
                } else {
                    seconds--;
                }
                
                document.getElementById('countdown-timer').textContent = 
                    `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            }, 1000);
        }

        // Initialize when page loads
        window.addEventListener('load', function() {
            createBubbles();
            animateNumbers();
            startCountdown();
        });
    </script>
</body>
</html>


\\\

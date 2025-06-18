<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>كرار </title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800&display=swap" rel="stylesheet">
    <!-- Font Awesome for social media icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* Base styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            /* Existing orange gradient + new subtle black gradient on top */
            background: 
                linear-gradient(to top, rgba(0, 0, 0, 0.2), transparent), /* Subtle black gradient from bottom up */
                linear-gradient(180deg, #ff8c00 0%, #ffa500 30%, #ffb84d 70%, #ffd700 100%); /* Original orange gradient */
            min-height: 100vh;
            padding: 30px 0;
            color: #000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .container {
            max-width: 420px;
            width: 100%;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            flex-direction: column;
            align-items: center; /* Center items horizontally */
            text-align: center; /* Center text within the container */
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            width: 100%; /* Ensure header takes full width */
        }

        .title {
            font-size: 42px;
            font-weight: 800;
            color: white;
            margin-bottom: 25px;
            text-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            font-family: 'Arial', sans-serif;
        }

        .image-container {
            width: 100%;
            margin-bottom: 40px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.25);
            position: relative;
            background: #000;
        }

        .profile-image {
            width: 100%;
            height: 280px;
            object-fit: cover;
            display: block;
        }

        .links-section {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-bottom: 30px;
            width: 100%; /* Ensure links section takes full width */
        }

        .link-button {
            background: linear-gradient(145deg, #ffffff, #f0f0f0);
            border: none;
            border-radius: 25px;
            padding: 22px 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            color: #000;
            font-weight: 700;
            font-size: 20px;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15), 
                        inset 0 1px 0 rgba(255, 255, 255, 0.8), 
                        inset 0 -1px 0 rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
            transform: translateZ(0);
        }

        /* تأثير الضوء المتحرك من الجوانب */
        .link-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, 
                transparent, 
                rgba(255, 255, 255, 0.4) 30%,
                rgba(255, 255, 255, 0.8) 50%,
                rgba(255, 255, 255, 0.4) 70%,
                transparent);
            transition: left 0.8s ease-in-out;
            z-index: 1;
        }

        /* تأثير النبضة عند الضغط */
        .link-button::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.6) 0%, transparent 70%);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: all 0.5s ease-out;
            z-index: 1;
        }

        /* عند المرور بالماوس - الضوء يمر من اليسار لليمين */
        .link-button:hover::before {
            left: 100%;
        }

        /* عند الضغط - نبضة من المركز */
        .link-button:active::after {
            width: 300px;
            height: 300px;
            opacity: 0;
        }

        .link-button:hover {
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25), 
                        inset 0 1px 0 rgba(255, 255, 255, 0.9), 
                        inset 0 -1px 0 rgba(0, 0, 0, 0.15);
            filter: brightness(1.1);
        }

        .link-button:active {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 12px 25px rgba(0, 0, 0, 0.2);
        }

        /* تأثير إضافي للنص والأيقونة */
        .link-text {
            position: relative;
            z-index: 2;
            transition: all 0.3s ease;
        }

        .link-button:hover .link-text {
            transform: scale(1.05);
            text-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        }

        .link-text {
            display: flex;
            align-items: center;
            gap: 18px;
            font-size: 20px;
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
        }

        /* Styling for Font Awesome icons */
        .platform-icon .fab {
            font-size: 26px; /* Adjust size for Font Awesome icons */
            filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.2));
            color: inherit; /* Ensure icon color matches button text */
        }

        /* Platform-specific styling */
        .instagram-btn {
            background: linear-gradient(145deg, #ffeef7, #f8d7da);
        }

        .telegram-btn {
            background: linear-gradient(145deg, #e3f2ff, #cce7ff);
        }

        .tiktok-btn {
            background: linear-gradient(145deg, #fff0f0, #ffe6e6);
        }

        .youtube-btn {
            background: linear-gradient(145deg, #ffeeee, #ffe0e0);
        }

        .footer {
            text-align: center;
            color: white;
            font-size: 16px;
            font-weight: 500;
            margin-top: 30px;
            padding-top: 15px; 
            padding-bottom: 15px; 
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
            width: 100%;
            /* Removed gradient from footer as it's now on the body */
            /* Added consistent rounded corners for styling */
            border-radius: 15px; 
            overflow: hidden; 
        }

        /* Responsive adjustments */
        @media (max-width: 480px) {
            body {
                padding: 20px 0;
            }
            .container {
                padding: 0 15px;
            }
            .title {
                font-size: 36px;
            }
            .profile-image {
                height: 220px;
            }
            .link-button {
                padding: 20px 25px;
                font-size: 18px;
            }
            .link-text {
                font-size: 18px;
                gap: 15px;
            }
            .platform-icon .fab {
                font-size: 24px;
            }
        }

        @media (max-width: 360px) {
            .profile-image {
                height: 200px;
            }
            .title {
                font-size: 32px;
            }
            .link-button {
                padding: 18px 20px;
                font-size: 16px;
            }
            .link-text {
                font-size: 16px;
                gap: 12px;
            }
            .platform-icon .fab {
                font-size: 22px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1 class="title">كرار حيدر</h1>
        </div>

        <div class="image-container">
            <img src="https://i.imgur.com/nbBUnRi.jpg" alt="كرار حيدر" class="profile-image">
        </div>

        <div class="links-section">
            <a href="https://instagram.com/k9x9i" class="link-button instagram-btn">
                <div class="link-text">
                    <span class="platform-icon"><i class="fab fa-instagram"></i></span>
                    <span>إنستغرام</span>
                </div>
            </a>

            <a href="https://t.me/k1_ar1" class="link-button telegram-btn">
                <div class="link-text">
                    <span class="platform-icon"><i class="fab fa-telegram-plane"></i></span>
                    <span>تيليغرام</span>
                </div>
            </a>

            <a href="https://tiktok.com/@c3_i2" class="link-button tiktok-btn">
                <div class="link-text">
                    <span class="platform-icon"><i class="fab fa-tiktok"></i></span>
                    <span>تيك توك</span>
                </div>
            </a>

            <a href="https://www.youtube.com/@U1QO1" class="link-button youtube-btn">
                <div class="link-text">
                    <span class="platform-icon"><i class="fab fa-youtube"></i></span>
                    <span>يوتيوب</span>
                </div>
            </a>
        </div>

        <div class="footer">
            جميع الحقوق محفوظة 2024©️
        </div>
    </div>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fancy Animated Book Homepage</title>
    <style>
        /* Import a fancy font for elegance */
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Dancing+Script:wght@400;700&display=swap');

        /* Basic page styling with enhanced background */
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            font-family: 'Dancing Script', cursive;
            overflow: hidden;
            position: relative;
        }

        /* Floating particles for magic effect */
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(2px 2px at 20px 30px, #fff, transparent),
                radial-gradient(2px 2px at 40px 70px, rgba(255,255,255,0.8), transparent),
                radial-gradient(1px 1px at 90px 40px, #fff, transparent),
                radial-gradient(1px 1px at 130px 80px, rgba(255,255,255,0.6), transparent);
            background-repeat: repeat;
            background-size: 200px 100px;
            animation: sparkle 20s linear infinite;
            opacity: 0.3;
        }

        @keyframes sparkle {
            from { transform: translateY(0px); }
            to { transform: translateY(-100px); }
        }

        /* Book container with enhanced perspective */
        .book {
            perspective: 1200px;
            width: 350px;
            height: 500px;
            position: relative;
            cursor: pointer;
            animation: bookFloat 3s ease-in-out infinite alternate;
        }

        @keyframes bookFloat {
            0% { transform: translateY(0px) rotateX(0deg); }
            100% { transform: translateY(-10px) rotateX(2deg); }
        }

        /* Book wrapper for overall structure */
        .book-wrapper {
            position: relative;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 1.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .book.flipped .book-wrapper {
            transform: rotateY(-180deg);
        }

        /* Spine of the book */
        .spine {
            position: absolute;
            left: -10px;
            top: 0;
            width: 20px;
            height: 100%;
            background: linear-gradient(to right, #8B4513, #A0522D);
            border-radius: 10px 0 0 10px;
            box-shadow: -5px 0 10px rgba(0, 0, 0, 0.2);
            z-index: 3;
        }

        /* Front cover with fancy leather texture and gold accents */
        .cover {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(145deg, #8B4513 0%, #654321 100%);
            border-radius: 0 10px 10px 0;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.1);
            transition: transform 1.5s;
            display: flex;
            justify-content: center;
            align-items: center;
            backface-visibility: hidden;
            border: 3px solid #DAA520; /* Gold border */
        }

        .front {
            transform-origin: left;
            z-index: 2;
            padding-left: 10px; /* Account for spine */
        }

        .back {
            transform: rotateY(180deg);
            background: linear-gradient(145deg, #A0522D 0%, #8B4513 100%);
            z-index: 1;
            border-radius: 10px 0 0 10px;
            padding-right: 10px;
        }

        /* Flip animation */
        .book:hover .front,
        .book.flipped .front {
            transform: rotateY(-180deg);
        }

        .book:hover .back,
        .book.flipped .back {
            transform: rotateY(0deg);
        }

        /* Fancy title on front cover */
        .title {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-family: 'Cinzel', serif;
            font-size: 24px;
            color: #DAA520;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            letter-spacing: 2px;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 2px 2px 4px rgba(0,0,0,0.5), 0 0 10px #DAA520; }
            to { text-shadow: 2px 2px 4px rgba(0,0,0,0.5), 0 0 20px #FFD700; }
        }

        /* Enhanced cake design with layers and details - FIXED */
        .cake {
            width: 180px;
            height: 200px; /* Increased height for better stacking */
            position: relative;
            animation: cakeBounce 2s ease-in-out infinite;
        }

        @keyframes cakeBounce {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        /* Cake layers - positioned from bottom for proper stacking */
        .layer1 {
            position: absolute;
            bottom: 105px;
            left: 22%;
            transform: rotate(180deg);
            width: 100px;
            height: 40px;
            background: #DEB887; /* Light brown cake */
            border-radius: 0 0 50px 50px;
            box-shadow: inset 0 -5px 10px rgba(0,0,0,0.1);
        }

        .layer2 {
            position: absolute;
            bottom: 80px; /* On top of layer1 */
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            height: 40px; /* Slightly taller for balance */
            background: #CD853F; /* Deeper cake layer */
            border-radius: 50px 50px 20px 20px; /* Adjusted for stacking */
            box-shadow: inset 0 -5px 10px rgba(0,0,0,0.1);
        }

        .layer3 { /* Added a third layer for more cake-like appearance */
            position: absolute;
            bottom: 55px; /* On top of layer2 */
            left: 50%;
            transform: translateX(-50%);
            width: 140px;
            height: 35px;
            background: #D2691E; /* Chocolate layer */
            border-radius: 70px 70px 15px 15px;
            box-shadow: inset 0 -5px 10px rgba(0,0,0,0.1);
        }

        .frosting {
            position: absolute;
            bottom: 20px; /* On top of layer3 */
            left: 50%;
            transform: translateX(-50%);
            width: 160px;
            height: 45px;
            background: linear-gradient(to bottom, #FF69B4, #FFB6C1);
            border-radius: 80px 80px 20px 20px;
            box-shadow: 0 5px 10px rgba(255,105,180,0.3);
        }

        /* Candles with flames - positioned on frosting */
        .candle1{
            position: absolute;
            bottom: 138px; /* Above frosting */
            width: 8px;
            height: 30px;
            background: linear-gradient(to top, #F4A460, #FFF8DC);
            border-radius: 2px 2px 3px 3px;
            box-shadow: 0 0 5px rgba(255,255,255,0.5);
        }

        .candle1 { left: 48%; }
        

        .flame1{
            position: absolute;
            bottom: 30px; /* At top of candle */
            left: 50%;
            transform: translateX(-50%);
            width: 6px;
            height: 12px;
            background: radial-gradient(ellipse, #FFD700 0%, #FF4500 50%, #FF0000 100%);
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            animation: flicker 1.5s infinite alternate;
            box-shadow: 0 0 10px #FFD700, inset 0 0 3px rgba(255,255,255,0.5);
        }

        /* Specific flames inherit positioning but add slight offset for realism */
        .flame1 { animation-delay: 0s; }
        .flame2 { animation-delay: 0.5s; }

        @keyframes flicker {
            0% { 
                opacity: 1; 
                transform: translateX(-50%) scale(1) rotate(-1deg); 
                box-shadow: 0 0 10px #FFD700;
            }
            100% { 
                opacity: 0.8; 
                transform: translateX(-50%) scale(1.1) rotate(1deg); 
                box-shadow: 0 0 15px #FF4500;
            }
        }

        /* Optional: Sprinkles on frosting for extra detail */
        .sprinkle1, .sprinkle2, .sprinkle3 {
            position: absolute;
            bottom: 130px;
            width: 4px;
            height: 4px;
            border-radius: 50%;
            animation: sprinkleWiggle 2s ease-in-out infinite;
        }

        .sprinkle1 { left: 40%; background: #FF0000; animation-delay: 0s; }
        .sprinkle2 { left: 49%; background: #00FF00; animation-delay: 0.7s; }
        .sprinkle3 { left: 59%; background: #0000FF; animation-delay: 1.4s; }

        @keyframes sprinkleWiggle {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-2px) rotate(5deg); }
        }

        /* Inner pages with paper texture and curl effect */
        .pages {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, #FFF8DC 0%, #F5F5DC 50%, #FFF8DC 100%);
            border-radius: 0 10px 10px 0;
            padding: 30px;
            box-sizing: border-box;
            transform: rotateY(180deg);
            backface-visibility: hidden;
            z-index: 0;
            opacity: 0;
            transition: opacity 1.5s, transform 1.5s;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.1);
            border-left: 3px solid #DAA520; /* Gold edge */
        }

        .book:hover .pages,
        .book.flipped .pages {
            opacity: 1;
            transform: rotateY(180deg) translateZ(1px); /* Slight 3D pop */
        }

        /* Page curl simulation on open */
        .pages::before {
            content: '';
            position: absolute;
            top: 10px;
            right: 10px;
            width: 50px;
            height: 100%;
            background: linear-gradient(to right, transparent, rgba(255,255,255,0.8));
            border-radius: 50px;
            transform: skewY(-10deg);
            opacity: 0;
            transition: opacity 1.5s;
        }

        .book:hover .pages::before,
        .book.flipped .pages::before {
            opacity: 1;
        }

        /* Fancy animated message with multiple effects */
        .message {
            text-align: center;
            font-size: 13px;
            color: #4B0082; /* Indigo for elegance */
            font-weight: 700;
            margin: 0;
            animation: fadeInOut 4s ease-in-out infinite, slideUp 4s ease-in-out infinite;
            opacity: 0;
            transform: translateY(20px);
        }

        .book:hover .message,
        .book.flipped .message {
            opacity: 1;
            transform: translateY(0);
            animation: fadeInOut 4s ease-in-out infinite, slideUp 4s ease-in-out infinite;
        }

        @keyframes fadeInOut {
            0%, 100% { opacity: 0.7; }
            50% { opacity: 1; }
        }

        @keyframes slideUp {
            0% { transform: translateY(20px); }
            50% { transform: translateY(-5px); }
            100% { transform: translateY(20px); }
        }

        /* Confetti burst on open (simple CSS version) */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: #FF69B4;
            animation: confettiFall 3s linear infinite;
            opacity: 0;
            pointer-events: none;
        }

        .confetti:nth-child(1) { left: 20%; background: #FFD700; animation-delay: 0.5s; }
        .confetti:nth-child(2) { left: 40%; background: #FF4500; animation-delay: 1s; }
        .confetti:nth-child(3) { left: 60%; background: #32CD32; animation-delay: 1.5s; }
        .confetti:nth-child(4) { left: 80%; background: #00BFFF; animation-delay: 2s; }

        @keyframes confettiFall {
            0% { transform: translateY(-100px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(500px) rotate(720deg); opacity: 0; }
        }

        .book.flipped .confetti {
            opacity: 1;
            animation-play-state: running;
        }
    </style>
</head>
<body>
    <div class="book" id="book">
        <div class="spine"></div>
        <div class="book-wrapper">
            <div class="cover front">
                <h2 class="title">HI BABIII HAPPY BIRTHDAYYYY!!!!</h2>
                <div class="cake">
                    <div class="layer1"></div>
                    <div class="layer2"></div>
                    <div class="layer3"></div>
                    <div class="frosting"></div>
                    <div class="candle1">
                        <div class="flame1"></div>
                    </div>
                    <div class="candle2">
                        <div class="flame2"></div>
                    </div>
                    <div class="sprinkle1"></div>
                    <div class="sprinkle2"></div>
              
                    <div class="sprinkle3"></div>
                </div>
            </div>
            <div class="cover back">
                <div style="text-align: center; color: #DAA520; font-family: 'Cinzel', serif; margin-top: 200px;">
                    <h3>click mo to bab</h3>
                </div>
            </div>
            <div class="pages">
                <div class="confetti"></div>
                <div class="confetti"></div>
                <div class="confetti"></div>
                <div class="confetti"></div>
                <p class="message"> babi siguro pag nabasa mo to birthday mo na. gusto ko lang sabihin sayo gurang kana HAHAHAAHAHAHAA, EME LANG. jokes aside babi, HAPPY HAPPY BIRTHDAY SAYOOO LOVE LOVE KOOO nawa'y maging masaya ka sa araw ng kaarawan mooo, tinatype ko to ng wala pakong tulog kasi kakauwi ko lang HAHAHA pero babi gusto ko lang malaman mo na love na love kita kaya wish ko sayo (wish??!! e ikaw ung may birthdayyy charis) sana maging masaya ka today maraming blessings pa ang matatanggap mo at higit sa lahat GOOD HEALTH PAK NA PAK YAN at syempre hindi magpapahuli ang sana makapasa ka sa scholarship mooooo, SARANGHEEEEEE (okay na'to, koreanong hilaw) ienjoy mo ang birthday mo ngayon babi ahhh with your friends or familyyyy. sana ngayong araw di ka mapagalitan o masumbatan HAHAHA, pls sana may exemption today, pasensya kana babi eto muna maeeffort ko naubos pera ko sa projects huhuhuhu... anyways HAPI NA BERTDEY MO PA HAPI NA BERTDEY MO PA, smile babi ah alwayss. lagi mong tatandaan na sa hirap at ginhawa nandito lang ako palagiii haAA "PALAGI AKONG NANDITO" wag mo sanang kakalimutan na may nagmamahal at naniniwala pa sayo so dont lose hope kurutin ko singit mo talaga pag nagkita tayo, virtual cake muna for today bbubbbyy kooooooo aaaa babawi ako sa susunod pramissssssssssss I LOVE YOU MY LOVEEEEEEE!!!!!! always remember that. pray always and most importantly may GOD BLESS YOU!!!!!!! 🎂✨</p> 
    
            </div>
        </div>
    </div>

    <script>
        // Toggle flip on click for interactive experience
        const book = document.getElementById('book');
        book.addEventListener('click', () => {
            book.classList.toggle('flipped');
        });

        // Optional: Auto-flip after a delay for demo (remove if not wanted)
        // setTimeout(() => book.classList.add('flipped'), 2000);
    </script>
</body>
</html>

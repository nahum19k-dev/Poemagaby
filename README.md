<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Princesita</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Times New Roman', serif;
            background: linear-gradient(135deg, #f5f1eb 0%, #e8ddd4 50%, #f0e6d6 100%);
            min-height: 100vh;
            overflow-x: hidden;
            color: #5a4a3a;
            position: relative;
        }

        /* Fondo animado de flores y corazones */
        .animated-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
            overflow: hidden;
        }

        .floating-element {
            position: absolute;
            font-size: 1.5rem;
            animation: floatAround 15s linear infinite;
            opacity: 0.6;
        }

        .floating-element.heart {
            color: #f8a5c2;
            animation-duration: 20s;
        }

        .floating-element.flower {
            color: #f4c2c2;
            animation-duration: 25s;
        }

        .floating-element.sparkle {
            color: #d4af8c;
            animation-duration: 18s;
        }

        @keyframes floatAround {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.6;
            }
            90% {
                opacity: 0.6;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Corazones pulsantes en las esquinas */
        .corner-hearts {
            position: fixed;
            pointer-events: none;
            z-index: 2;
        }

        .corner-heart {
            position: absolute;
            font-size: 2rem;
            color: #f8a5c2;
            animation: pulse 3s ease-in-out infinite;
            opacity: 0.7;
        }

        .corner-heart.top-left {
            top: 20px;
            left: 20px;
            animation-delay: 0s;
        }

        .corner-heart.top-right {
            top: 20px;
            right: 20px;
            animation-delay: 1s;
        }

        .corner-heart.bottom-left {
            bottom: 20px;
            left: 20px;
            animation-delay: 2s;
        }

        .corner-heart.bottom-right {
            bottom: 20px;
            right: 20px;
            animation-delay: 1.5s;
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
                opacity: 0.7;
            }
            50% {
                transform: scale(1.2);
                opacity: 1;
            }
        }
        
        .page {
            width: 100vw;
            min-height: 100vh;
            display: flex;
            align-items: flex-start;
            justify-content: center;
            position: relative;
            transition: transform 0.8s ease-in-out;
            padding: 20px;
            z-index: 10;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
            position: relative;
        }
        
        /* Página de preguntas (página inicial) */
        .questions-page {
            display: flex;
        }
        
        .letter-container {
            background: rgba(254, 252, 247, 0.95);
            border-radius: 15px;
            box-shadow: 
                0 20px 40px rgba(90, 74, 58, 0.15),
                inset 0 1px 0 rgba(255, 255, 255, 0.9);
            padding: 40px;
            position: relative;
            border: 2px solid rgba(139, 118, 93, 0.2);
            max-width: 700px;
            margin: 0 auto;
            min-height: 80vh;
            backdrop-filter: blur(10px);
        }
        
        .letter-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: 
                radial-gradient(circle at 15% 15%, rgba(248, 165, 194, 0.1) 0%, transparent 25%),
                radial-gradient(circle at 85% 85%, rgba(244, 194, 194, 0.1) 0%, transparent 25%),
                radial-gradient(circle at 50% 50%, rgba(212, 175, 140, 0.05) 0%, transparent 30%);
            pointer-events: none;
        }

        .welcome-message {
            background: linear-gradient(145deg, rgba(248, 165, 194, 0.1), rgba(244, 194, 194, 0.1));
            border: 2px solid rgba(248, 165, 194, 0.3);
            border-radius: 20px;
            padding: 25px;
            margin-bottom: 30px;
            position: relative;
            z-index: 10;
            animation: gentleGlow 3s ease-in-out infinite;
            opacity: 1;
        }

        .welcome-message::before {
            content: '💝';
            position: absolute;
            top: -15px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(254, 252, 247, 0.95);
            padding: 5px 15px;
            border-radius: 50%;
            font-size: 1.5rem;
            border: 2px solid rgba(248, 165, 194, 0.3);
        }

        .welcome-title {
            font-size: 1.3rem;
            color: #8b765d;
            margin-bottom: 15px;
            font-weight: bold;
            letter-spacing: 1px;
        }

        .welcome-subtitle {
            font-size: 1rem;
            color: #a0896f;
            font-style: italic;
            line-height: 1.5;
        }

        @keyframes gentleGlow {
            0%, 100% {
                box-shadow: 0 0 20px rgba(248, 165, 194, 0.2);
            }
            50% {
                box-shadow: 0 0 30px rgba(248, 165, 194, 0.4);
            }
        }
        
        .questions-title {
            font-size: 2.2rem;
            color: #8b765d;
            margin-bottom: 20px;
            text-align: center;
            position: relative;
            z-index: 10;
            font-weight: normal;
            letter-spacing: 1px;
        }
        
        .questions-subtitle {
            font-size: 1rem;
            color: #a0896f;
            margin-bottom: 30px;
            font-style: italic;
            text-align: center;
            position: relative;
            z-index: 10;
        }
        
        .questions-container {
            max-width: 600px;
            margin: 0 auto;
            position: relative;
            z-index: 10;
        }
        
        .question-item {
            background: rgba(245, 222, 179, 0.15);
            border: 2px solid rgba(139, 118, 93, 0.25);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 20px;
            transition: all 0.3s ease;
            opacity: 0.4;
            pointer-events: none;
            position: relative;
        }

        .question-item::before {
            content: '';
            position: absolute;
            top: -10px;
            right: -10px;
            width: 30px;
            height: 30px;
            background: linear-gradient(45deg, #f8a5c2, #f4c2c2);
            border-radius: 50%;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .question-item.active::before {
            opacity: 1;
            animation: pulse 2s ease-in-out infinite;
        }
        
        .question-item.active {
            opacity: 1;
            pointer-events: all;
            transform: scale(1.02);
            background: rgba(245, 222, 179, 0.2);
            border-color: rgba(248, 165, 194, 0.4);
            box-shadow: 0 10px 30px rgba(248, 165, 194, 0.2);
        }
        
        .question-item.completed {
            background: rgba(106, 139, 71, 0.15);
            border-color: rgba(106, 139, 71, 0.4);
            opacity: 0.8;
            pointer-events: none;
        }
        
        .question-item:hover {
            background: rgba(245, 222, 179, 0.25);
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(248, 165, 194, 0.3);
        }
        
        .question {
            font-size: 1.2rem;
            color: #8b765d;
            margin-bottom: 15px;
            font-weight: bold;
            text-align: center;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 15px 0;
        }
        
        .option {
            display: flex;
            align-items: center;
            padding: 12px 15px;
            background: rgba(254, 252, 247, 0.8);
            border: 2px solid rgba(196, 154, 117, 0.25);
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.95rem;
            color: #5a4a3a;
            backdrop-filter: blur(5px);
        }
        
        .option:hover {
            background: rgba(248, 165, 194, 0.1);
            border-color: rgba(248, 165, 194, 0.5);
            transform: translateX(8px);
            box-shadow: 0 5px 15px rgba(248, 165, 194, 0.2);
        }
        
        .option input[type="radio"] {
            margin-right: 12px;
            transform: scale(1.2);
            accent-color: #f8a5c2;
        }
        
        .option-text {
            font-family: 'Times New Roman', serif;
            flex: 1;
        }
        
        .option.selected {
            background: rgba(248, 165, 194, 0.15);
            border-color: #f8a5c2;
        }
        
        .option.correct {
            background: rgba(106, 139, 71, 0.15);
            border-color: #6a8b47;
            animation: correctAnswer 0.8s ease;
        }
        
        .option.incorrect {
            background: rgba(184, 84, 80, 0.15);
            border-color: #b85450;
            animation: shake 0.5s ease;
        }
        
        .result {
            text-align: center;
            margin-top: 15px;
            font-size: 1rem;
            font-weight: bold;
            min-height: 25px;
        }
        
        .correct {
            color: #6a8b47;
            animation: correctAnswer 0.6s ease;
        }
        
        .incorrect {
            color: #b85450;
            animation: shake 0.5s ease;
        }
        
        .progress-bar {
            width: 100%;
            height: 8px;
            background: rgba(139, 118, 93, 0.15);
            border-radius: 4px;
            margin-bottom: 30px;
            overflow: hidden;
            position: relative;
        }

        .progress-bar::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, 
                rgba(248, 165, 194, 0.3) 0%, 
                rgba(244, 194, 194, 0.3) 50%, 
                rgba(248, 165, 194, 0.3) 100%);
            animation: shimmer 3s ease-in-out infinite;
        }

        @keyframes shimmer {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 0.6; }
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #f8a5c2, #f4c2c2, #d4af8c);
            width: 0%;
            transition: width 0.8s ease;
            border-radius: 4px;
            position: relative;
            z-index: 1;
        }
        
        .final-questions-message {
            text-align: center;
            margin-top: 40px;
            padding: 30px;
            background: linear-gradient(145deg, 
                rgba(248, 165, 194, 0.2), 
                rgba(244, 194, 194, 0.15),
                rgba(216, 191, 216, 0.1));
            border: 3px solid rgba(248, 165, 194, 0.4);
            border-radius: 20px;
            animation: finalGlow 3s ease infinite alternate;
            display: none;
            position: relative;
        }

        .final-questions-message::before {
            content: '👑';
            position: absolute;
            top: -20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(254, 252, 247, 0.95);
            padding: 10px 20px;
            border-radius: 50%;
            font-size: 2rem;
            border: 3px solid rgba(248, 165, 194, 0.4);
            animation: bounce 2s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-10px); }
        }
        
        .congratulations {
            font-size: 1.3rem;
            color: #8b765d;
            line-height: 1.8;
            margin-bottom: 20px;
        }
        
        .congratulations small {
            font-size: 1rem;
            color: #a0896f;
            font-style: italic;
            display: block;
            margin-top: 15px;
        }
        
        .unlock-btn {
            background: linear-gradient(145deg, #f8a5c2, #f4c2c2, #d4af8c);
            color: #fff;
            border: none;
            padding: 15px 35px;
            font-size: 1.1rem;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 
                0 8px 25px rgba(248, 165, 194, 0.4),
                inset 0 2px 0 rgba(255, 255, 255, 0.3);
            font-family: 'Times New Roman', serif;
            letter-spacing: 1px;
            animation: magicPulse 2s ease infinite;
            font-weight: bold;
        }

        @keyframes magicPulse {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 8px 25px rgba(248, 165, 194, 0.4);
            }
            50% {
                transform: scale(1.05);
                box-shadow: 0 12px 35px rgba(248, 165, 194, 0.6);
            }
        }
        
        .unlock-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(248, 165, 194, 0.6);
        }
        
        /* Portada */
        .cover-page {
            display: none;
        }
        
        .cover {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 
                0 15px 40px rgba(139, 118, 93, 0.2),
                inset 0 2px 0 rgba(255, 255, 255, 0.9);
            padding: 40px 30px;
            position: relative;
            overflow: hidden;
            border: 2px solid rgba(248, 165, 194, 0.3);
            backdrop-filter: blur(10px);
        }
        
        .cover::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: 
                radial-gradient(circle at 20% 20%, rgba(248, 165, 194, 0.2) 0%, transparent 30%),
                radial-gradient(circle at 80% 80%, rgba(244, 194, 194, 0.15) 0%, transparent 30%),
                radial-gradient(circle at 50% 10%, rgba(212, 175, 140, 0.1) 0%, transparent 25%);
            pointer-events: none;
        }
        
        .title {
            font-size: 2.8rem;
            color: #8b765d;
            margin-bottom: 20px;
            font-weight: normal;
            letter-spacing: 2px;
            position: relative;
            z-index: 10;
        }
        
        .subtitle {
            font-size: 1.1rem;
            color: #a0896f;
            margin-bottom: 30px;
            font-style: italic;
            position: relative;
            z-index: 10;
            letter-spacing: 1px;
        }
        
        .photo-container {
            width: 250px;
            height: 250px;
            margin: 0 auto 25px;
            position: relative;
            z-index: 10;
            border-radius: 15px;
            overflow: hidden;
            border: 3px solid rgba(248, 165, 194, 0.4);
            box-shadow: 0 10px 30px rgba(248, 165, 194, 0.3);
            transition: transform 0.3s ease;
        }
        
        .photo-container:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 40px rgba(248, 165, 194, 0.4);
        }
        
        .couple-photo {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: center;
        }
        
        .next-btn {
            background: linear-gradient(145deg, #f8a5c2, #f4c2c2);
            color: #fff;
            border: none;
            padding: 15px 35px;
            font-size: 1rem;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 
                0 8px 25px rgba(248, 165, 194, 0.4),
                inset 0 2px 0 rgba(255, 255, 255, 0.3);
            position: relative;
            z-index: 10;
            margin-top: 20px;
            font-family: 'Times New Roman', serif;
            letter-spacing: 1px;
            font-weight: bold;
        }
        
        .next-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 30px rgba(248, 165, 194, 0.5);
        }
        
        /* Página del poema */
        .poem-page {
            display: none;
            position: relative;
        }
        
        .letter-header {
            text-align: right;
            margin-bottom: 30px;
            position: relative;
            z-index: 10;
        }
        
        .date {
            font-size: 0.95rem;
            color: #a0896f;
            font-style: italic;
            margin-bottom: 8px;
        }
        
        .greeting {
            font-size: 1.1rem;
            color: #8b765d;
            font-style: italic;
        }
        
        .poem-title {
            font-size: 2.2rem;
            color: #8b765d;
            margin-bottom: 30px;
            text-align: center;
            position: relative;
            z-index: 10;
            font-weight: normal;
            letter-spacing: 1px;
        }
        
        .poem-content {
            font-size: 1rem;
            line-height: 1.8;
            color: #5a4a3a;
            text-align: justify;
            position: relative;
            z-index: 10;
            font-family: 'Times New Roman', serif;
            padding: 0 10px;
        }
        
        .poem-verse {
            margin-bottom: 25px;
            position: relative;
            opacity: 1;
            transform: translateY(0);
            transition: all 1s ease;
            text-indent: 20px;
            padding: 12px;
            border-left: 3px solid rgba(248, 165, 194, 0.3);
            background: rgba(248, 165, 194, 0.05);
            border-radius: 0 10px 10px 0;
        }
        
        .poem-verse.animate {
            opacity: 1;
            transform: translateY(0);
        }
        
        .poem-verse:not(.animate) {
            opacity: 0;
            transform: translateY(20px);
        }
        
        .poem-verse::first-letter {
            font-size: 1.4rem;
            font-weight: bold;
            color: #f8a5c2;
            float: left;
            margin-right: 5px;
            margin-top: 2px;
        }
        
        .signature-section {
            margin-top: 50px;
            text-align: right;
            position: relative;
            z-index: 10;
        }
        
        .signature {
            font-size: 1.3rem;
            color: #8b765d;
            font-style: italic;
            font-family: 'Brush Script MT', cursive;
        }
        
        .back-btn {
            background: rgba(248, 165, 194, 0.15);
            color: #8b765d;
            border: 2px solid rgba(248, 165, 194, 0.4);
            padding: 10px 25px;
            font-size: 0.95rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: absolute;
            top: 20px;
            left: 20px;
            z-index: 10;
            backdrop-filter: blur(10px);
            font-weight: bold;
        }
        
        .back-btn:hover {
            background: rgba(248, 165, 194, 0.25);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(248, 165, 194, 0.3);
        }
        
        .flower-decoration {
            position: absolute;
            pointer-events: none;
            z-index: 5;
        }
        
        .flower-top-right {
            top: 20px;
            right: 20px;
            width: 80px;
            height: 80px;
            background: radial-gradient(circle, rgba(248, 165, 194, 0.4) 0%, rgba(244, 194, 194, 0.3) 50%, transparent 70%);
            border-radius: 50%;
            animation: pulse 4s ease-in-out infinite;
        }
        
        .flower-top-right::before {
            content: '🌸';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 2rem;
        }
        
        .flower-bottom-left {
            bottom: 20px;
            left: 20px;
            width: 60px;
            height: 60px;
            background: radial-gradient(circle, rgba(212, 175, 140, 0.4) 0%, rgba(196, 154, 117, 0.3) 50%, transparent 70%);
            border-radius: 50%;
            animation: pulse 5s ease-in-out infinite;
            animation-delay: 2s;
        }
        
        .flower-bottom-left::before {
            content: '🌿';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.8rem;
        }
        
        .poem-controls {
            text-align: center;
            margin-top: 30px;
            z-index: 10;
            position: relative;
        }
        
        .control-btn {
            background: rgba(248, 165, 194, 0.15);
            color: #8b765d;
            border: 2px solid rgba(248, 165, 194, 0.4);
            padding: 8px 20px;
            margin: 0 6px;
            font-size: 0.95rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(5px);
            font-weight: bold;
        }
        
        .control-btn:hover {
            background: rgba(248, 165, 194, 0.25);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(248, 165, 194, 0.3);
        }

        @media (max-width: 768px) {
            .letter-container {
                padding: 25px 15px;
                margin: 10px;
                min-height: auto;
            }
            
            .title, .questions-title {
                font-size: 2rem;
            }
            
            .photo-container {
                width: 200px;
                height: 200px;
            }
            
            .poem-content {
                font-size: 0.95rem;
                line-height: 1.7;
            }
            
            .poem-verse {
                text-indent: 10px;
                margin-bottom: 20px;
                padding: 10px;
            }
            
            .cover {
                padding: 30px 20px;
            }
            
            .page {
                padding: 40px 10px;
            }

            .welcome-message {
                padding: 20px;
                margin-bottom: 20px;
            }

            .welcome-title {
                font-size: 1.1rem;
            }

            .welcome-subtitle {
                font-size: 0.9rem;
            }

            .poem-title {
                font-size: 1.8rem;
            }

            .letter-header {
                margin-bottom: 20px;
            }

            .date, .greeting {
                font-size: 0.9rem;
            }

            .signature {
                font-size: 1.1rem;
            }
        }
        
        .subtle-animation {
            animation: gentleFloat 6s ease-in-out infinite;
        }
        
        @keyframes gentleFloat {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-5px); }
        }
        
        @keyframes correctAnswer {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-8px); }
            75% { transform: translateX(8px); }
        }
        
        @keyframes finalGlow {
            0% { 
                box-shadow: 0 0 25px rgba(248, 165, 194, 0.3);
                border-color: rgba(248, 165, 194, 0.4);
            }
            100% { 
                box-shadow: 0 0 40px rgba(248, 165, 194, 0.6);
                border-color: rgba(248, 165, 194, 0.6);
            }
        }
    </style>
</head>
<body>
    <!-- Música de fondo -->
    <audio id="background-music" loop>
        <source src="https://dl.dropboxusercontent.com/scl/fi/vcgbuoxum4w1v2pkoq1pg/Rindete-Bray-On-Videoclip-Oficial.mp3?rlkey=yp7tjax3mhpyeol5i3st2e8bq" type="audio/mp3">
        Tu navegador no soporta el elemento de audio.
    </audio>

    <!-- Fondo animado -->
    <div class="animated-background" id="animated-background"></div>
    
    <!-- Corazones en las esquinas -->
    <div class="corner-hearts">
        <div class="corner-heart top-left">💕</div>
        <div class="corner-heart top-right">💖</div>
        <div class="corner-heart bottom-left">💝</div>
        <div class="corner-heart bottom-right">💗</div>
    </div>

    <!-- Página de preguntas (página inicial) -->
    <div class="page questions-page" id="questions-page">
        <div class="container">
            <div class="letter-container">
                <div class="flower-decoration flower-top-right"></div>
                <div class="flower-decoration flower-bottom-left"></div>
                
                <div class="welcome-message">
                    <div class="welcome-title">¡Hola mi Princesa! 👑</div>
                    <div class="welcome-subtitle">
                        Responde estas preguntas especiales<br>
                        para poder desbloquear tu sorpresa de amor...
                    </div>
                </div>
                
                <h1 class="questions-title">Para Mi Princesita 💕</h1>
                
                <div class="progress-bar">
                    <div class="progress-fill" id="progress-fill"></div>
                </div>
                
                <div class="questions-container">
                    <div class="question-item active" id="question1">
                        <div class="question">¿Cuándo es mi fecha de cumpleaños?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="q1" value="a" onchange="selectOption(1, 'a', true)">
                                <span class="option-text">a. 24 de mayo</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="q1" value="b" onchange="selectOption(1, 'b', false)">
                                <span class="option-text">b. 12 de mayo</span>
                            </label>
                        </div>
                        <div class="result" id="result1"></div>
                    </div>
                    
                    <div class="question-item" id="question2">
                        <div class="question">¿Qué café me gusta más?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="q2" value="a" onchange="selectOption(2, 'a', false)">
                                <span class="option-text">a. El capuchino</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="q2" value="b" onchange="selectOption(2, 'b', true)">
                                <span class="option-text">b. El café de tus ojos</span>
                            </label>
                        </div>
                        <div class="result" id="result2"></div>
                    </div>
                    
                    <div class="question-item" id="question3">
                        <div class="question">¿Cuál es mi postre favorito?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="q3" value="a" onchange="selectOption(3, 'a', false)">
                                <span class="option-text">a. El arroz con leche</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="q3" value="b" onchange="selectOption(3, 'b', true)">
                                <span class="option-text">b. Tus besos jeje</span>
                            </label>
                        </div>
                        <div class="result" id="result3"></div>
                    </div>
                    
                    <div class="final-questions-message" id="final-questions-message">
                        <div class="congratulations">
                            ¡Perfecto, mi princesita! 🌹<br>
                            Conoces todos mis secretos del corazón ♡<br>
                            <small>Ya puedes ver tu sorpresa especial...</small>
                        </div>
                        <button class="unlock-btn" onclick="unlockSurprise()">
                            ✨ Ver mi sorpresa ✨
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Portada -->
    <div class="page cover-page" id="cover-page">
        <div class="container">
            <div class="cover subtle-animation">
                <h1 class="title">Mi Princesita</h1>
                <p class="subtitle">Un poema de amor para ti</p>
                
                <div class="photo-container">
                    <img src="https://dl.dropboxusercontent.com/scl/fi/7cwqiv9o6le36udyz5cb2/image.jpg?rlkey=eo16e8hvu6943alevcxsrwpoi" alt="Nuestra foto juntos" class="couple-photo" id="couple-photo">
                </div>
                
                <button class="next-btn" onclick="showPoem()">
                    Leer el poema
                </button>
            </div>
        </div>
    </div>
    
    <!-- Página del poema -->
    <div class="page poem-page" id="poem-page">
        <div class="container">
            <button class="back-btn" onclick="showCover()">← Volver</button>
            
            <div class="letter-container">
                <div class="flower-decoration flower-top-right"></div>
                <div class="flower-decoration flower-bottom-left"></div>
                
                <div class="letter-header">
                    <div class="date">Con amor, siempre</div>
                    <div class="greeting">Para mi princesita...</div>
                </div>
                
                <h2 class="poem-title">Poema de Amor</h2>
                
                <div class="poem-content" id="poem-content">
                    <div class="poem-verse" data-verse="1">
                        En Abai comenzó la historia,<br>
                        entre auriculares y voces al aire,<br>
                        pero fue tu risa, princesita,<br>
                        la que convirtió la rutina en paisaje.
                    </div>
                    
                    <div class="poem-verse" data-verse="2">
                        Entre clases y miradas robadas,<br>
                        descubrí que los minutos contigo<br>
                        valen más que cualquier jornada,<br>
                        porque hasta el silencio suena bonito.
                    </div>
                    
                    <div class="poem-verse" data-verse="3">
                        Dicen que los ángeles habitan el cielo,<br>
                        pero yo los encontré en tu mirar,<br>
                        y desde entonces, princesita mía,<br>
                        mi café favorito son tus ojos al despertar.
                    </div>
                    
                    <div class="poem-verse" data-verse="4">
                        Me encantó caminar de la mano a tu casa,<br>
                        esperar tus besos de despedida al final de la jornada,<br>
                        y ese beso que me diste de sorpresa,<br>
                        cuando estaba en llamada y no lo esperaba.
                    </div>
                    
                    <div class="poem-verse" data-verse="5">
                        Y aunque ahora el dolor toque tu puerta,<br>
                        quiero que sepas que aquí estaré,<br>
                        sosteniendo tu mano en cada tormenta,<br>
                        siendo abrigo cuando te falte la fe.
                    </div>
                    
                    <div class="poem-verse" data-verse="6">
                        Porque más que un beso robado,<br>
                        más que un juego o un te extraño,<br>
                        yo quiero ser en tu vida,<br>
                        ese amor que se queda a tu lado.
                    </div>
                </div>
                
                <div class="signature-section">
                    <div class="signature">Con todo mi amor,<br>Para siempre tuyo ♡</div>
                </div>
                
                <div class="poem-controls">
                    <button class="control-btn" onclick="animatePoem()">✨ Leer poema</button>
                    <button class="control-btn" onclick="resetAnimation()">🔄 Releer</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        let currentQuestion = 1;
        let correctAnswers = 0;
        const totalQuestions = 3;
        let musicPlayed = false;
        
        // Crear elementos flotantes de fondo
        function createFloatingElements() {
            const background = document.getElementById('animated-background');
            const elements = ['💕', '💖', '💗', '💝', '🌸', '🌺', '🌹', '✨', '💫', '⭐'];
            
            function addFloatingElement() {
                const element = document.createElement('div');
                element.className = 'floating-element';
                element.style.left = Math.random() * 100 + 'vw';
                element.style.animationDelay = Math.random() * 5 + 's';
                element.textContent = elements[Math.floor(Math.random() * elements.length)];
                
                if (['💕', '💖', '💗', '💝'].includes(element.textContent)) {
                    element.classList.add('heart');
                } else if (['🌸', '🌺', '🌹'].includes(element.textContent)) {
                    element.classList.add('flower');
                } else {
                    element.classList.add('sparkle');
                }
                
                background.appendChild(element);
                
                setTimeout(() => {
                    if (element.parentNode) {
                        element.parentNode.removeChild(element);
                    }
                }, 25000);
            }
            
            for (let i = 0; i < 8; i++) {
                setTimeout(addFloatingElement, i * 1000);
            }
            
            setInterval(addFloatingElement, 3000);
        }
        
        function selectOption(questionNum, option, isCorrect) {
            const questionItem = document.getElementById(`question${questionNum}`);
            const resultDiv = document.getElementById(`result${questionNum}`);
            const allOptions = questionItem.querySelectorAll('.option');
            
            if (questionNum !== currentQuestion) return;
            
            allOptions.forEach(opt => opt.classList.remove('selected', 'correct', 'incorrect'));
            const selectedOption = questionItem.querySelector(`input[value="${option}"]`).closest('.option');
            selectedOption.classList.add('selected');
            
            questionItem.querySelectorAll('input[type="radio"]').forEach(input => {
                input.disabled = true;
            });
            
            setTimeout(() => {
                if (isCorrect) {
                    selectedOption.classList.add('correct');
                    resultDiv.innerHTML = '✅ ¡Correcto, mi amor!';
                    resultDiv.className = 'result correct';
                    questionItem.classList.remove('active');
                    questionItem.classList.add('completed');
                    
                    correctAnswers++;
                    updateProgress();
                    
                    if (currentQuestion < totalQuestions) {
                        currentQuestion++;
                        setTimeout(() => {
                            document.getElementById(`question${currentQuestion}`).classList.add('active');
                        }, 800);
                    } else {
                        setTimeout(() => {
                            document.getElementById('final-questions-message').style.display = 'block';
                            document.getElementById('final-questions-message').scrollIntoView({ behavior: 'smooth' });
                        }, 1000);
                    }
                    
                } else {
                    selectedOption.classList.add('incorrect');
                    resultDiv.innerHTML = '❌ Intenta de nuevo, princesita';
                    resultDiv.className = 'result incorrect';
                    
                    setTimeout(() => {
                        questionItem.querySelectorAll('input[type="radio"]').forEach(input => {
                            input.disabled = false;
                            input.checked = false;
                        });
                        allOptions.forEach(opt => opt.classList.remove('selected', 'incorrect'));
                        resultDiv.innerHTML = '';
                    }, 2000);
                }
            }, 200);
        }
        
        function updateProgress() {
            const progressPercentage = (correctAnswers / totalQuestions) * 100;
            document.getElementById('progress-fill').style.width = progressPercentage + '%';
        }
        
        function unlockSurprise() {
            document.getElementById('questions-page').style.display = 'none';
            document.getElementById('cover-page').style.display = 'flex';
            
            setTimeout(() => {
                document.querySelector('.cover').style.animation = 'gentleFloat 6s ease-in-out infinite';
            }, 300);
        }
        
        function showPoem() {
            document.getElementById('cover-page').style.display = 'none';
            document.getElementById('poem-page').style.display = 'flex';
            
            const verses = document.querySelectorAll('.poem-verse');
            verses.forEach(verse => {
                verse.classList.add('animate');
            });
            
            setTimeout(() => {
                document.querySelector('.poem-verse[data-verse="1"]').scrollIntoView({ 
                    behavior: 'smooth', 
                    block: 'start' 
                });
            }, 100);
        }
        
        function showCover() {
            document.getElementById('poem-page').style.display = 'none';
            document.getElementById('cover-page').style.display = 'flex';
            resetAnimation();
        }
        
        function animatePoem() {
            const verses = document.querySelectorAll('.poem-verse');
            verses.forEach((verse, index) => {
                verse.classList.remove('animate');
                setTimeout(() => {
                    verse.classList.add('animate');
                    if (index === 0) {
                        verse.scrollIntoView({ behavior: 'smooth', block: 'start' });
                    }
                }, index * 1200);
            });
        }
        
        function resetAnimation() {
            const verses = document.querySelectorAll('.poem-verse');
            verses.forEach(verse => {
                verse.classList.remove('animate');
                verse.style.opacity = '1';
            });
        }
        
        function loadPhoto() {
            const photo = document.getElementById('couple-photo');
            const imageUrl = 'https://dl.dropboxusercontent.com/scl/fi/7cwqiv9o6le36udyz5cb2/image.jpg?rlkey=eo16e8hvu6943alevcxsrwpoi';
            photo.src = imageUrl;
            
            photo.onerror = () => {
                photo.style.display = 'none';
                document.querySelector('.photo-container').innerHTML = `
                    <div style="width: 100%; height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; background: linear-gradient(45deg, #f8a5c2, #f4c2c2); color: #fff; font-size: 1rem; text-align: center; font-style: italic;">
                        💕<br>
                        Nuestra foto<br>
                        especial<br>
                        💕
                    </div>
                `;
            };
        }

        // Reproducir música al hacer clic en la pantalla
        document.addEventListener('click', function() {
            if (!musicPlayed) {
                const audio = document.getElementById('background-music');
                audio.play().catch(error => {
                    console.log('Error al reproducir:', error);
                });
                musicPlayed = true;
            }
        });
        
        window.addEventListener('load', () => {
            createFloatingElements();
            loadPhoto();
            
            setTimeout(() => {
                document.querySelector('.welcome-message').style.opacity = '1';
                document.getElementById('question1').scrollIntoView({ behavior: 'smooth' });
            }, 500);
        });
    </script>
</body>
</html>

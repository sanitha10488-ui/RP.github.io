<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RaguPravin's Gallery</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Press+Start+2P&display=swap" rel="stylesheet">
    <style>
        /* General Body Styles */
        body {
            font-family: 'Montserrat', sans-serif;
            background-color: #0a0a0a; /* Very dark background for neon effect */
            color: #e0e0e0;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        /* Header and Navigation */
        header {
            background-color: #1a1a1a;
            padding: 20px 0;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        /* Neon Banner Effect */
        .neon-banner {
            font-family: 'Press+Start+2P', cursive; /* A pixelated/retro font often works well with neon */
            font-size: 3.5em; /* Larger text */
            color: #fff; /* White base for the glow */
            text-shadow:
                0 0 7px #fff,    /* Inner white glow */
                0 0 10px #fff,
                0 0 21px #fff,
                0 0 42px #0fa,   /* Aqua blue outer glow */
                0 0 82px #0fa,
                0 0 92px #0fa,
                0 0 102px #0fa,
                0 0 151px #0fa;
            animation: neon-flicker 1.5s infinite alternate; /* Subtle flicker effect */
            text-transform: uppercase;
            letter-spacing: 5px;
            margin: 0;
            padding: 0;
        }

        @keyframes neon-flicker {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.9; text-shadow:
                0 0 5px #fff,
                0 0 8px #fff,
                0 0 15px #fff,
                0 0 30px #0fa,
                0 0 60px #0fa,
                0 0 70px #0fa;
            }
        }

        /* Main Content Area */
        main {
            padding: 40px 20px;
            max-width: 1200px;
            margin: 20px auto;
            background-color: #1c1c1c;
            border-radius: 10px;
            box-shadow: 0 0 25px rgba(0, 0, 0, 0.6);
        }

        h2 {
            text-align: center;
            color: #0fa; /* Match neon color */
            margin-bottom: 40px;
            font-size: 2.5em;
            text-shadow: 0 0 10px #0fa;
        }

        /* Gallery Grid */
        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); /* Responsive grid */
            gap: 30px; /* Space between gallery items */
            padding: 20px;
        }

        .gallery-item {
            background-color: #2a2a2a;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
            border: 1px solid #333; /* Subtle border */
        }

        .gallery-item:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.7);
        }

        .gallery-item img {
            width: 100%;
            height: 300px; /* Fixed height for consistency */
            display: block;
            object-fit: cover; /* Ensures images fill the container without distortion */
            transition: opacity 0.3s ease-in-out;
        }

        .gallery-item:hover img {
            opacity: 0.9;
        }

        .gallery-item .caption {
            padding: 15px;
            text-align: center;
            color: #bbb;
            font-size: 0.9em;
            background-color: #222;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 30px 20px;
            background-color: #1a1a1a;
            color: #777;
            margin-top: 40px;
            box-shadow: 0 -4px 8px rgba(0, 0, 0, 0.4);
        }

        /* Responsive Adjustments */
        @media (max-width: 768px) {
            .neon-banner {
                font-size: 2.5em;
            }
            .gallery-container {
                grid-template-columns: 1fr; /* Stack images vertically on small screens */
                padding: 15px;
            }
            main {
                margin: 10px auto;
                padding: 20px 10px;
            }
            h2 {
                font-size: 2em;
            }
        }

        @media (max-width: 480px) {
            .neon-banner {
                font-size: 1.8em;
                letter-spacing: 2px;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1 class="neon-banner">RaguPravin</h1>
    </header>

    <main>
        <h2>My Gallery</h2>

        <div class="gallery-container">
            
            <div class="gallery-item">
                <img src="55932.jpg" alt="RaguPravin with phone on pink background">
                <div class="caption">A casual selfie on a vibrant background.</div>
            </div>

            <div class="gallery-item">
                <img src="55943.webp" alt="RaguPravin in front of a red car at sunset">
                <div class="caption">With the ride at sunset, road ahead.</div>
            </div>

            <!-- START: NEW PHOTO EXAMPLE -->
            <!-- Just copy and paste this block for each new photo -->
            <div classs="gallery-item">
                <!-- 1. Change the src="YOUR-NEW-IMAGE.jpg" -->
                <img src="https://placehold.co/600x400/0fa/white?text=New+Photo" alt="Description of your new photo">
                
                <!-- 2. Change the caption text -->
                <div class="caption">This is the caption for my new photo!</div>
            </div>
            <!-- END: NEW PHOTO EXAMPLE -->

        </div>
    </main>

    <footer>
        <p>&copy; 2024 RaguPravin. All rights reserved.</p>
    </footer>

</body>
</html>



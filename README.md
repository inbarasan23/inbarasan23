<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inbarasan | No‑JS Animated Portfolio</title>
    <style>
        /* ========== GLOBAL RESET & THEME ========== */
        *, *::before, *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --neon-cyan: #00F7FF;
            --neon-purple: #8A2BE2;
            --deep-bg: #0a0c10;
            --card-bg: rgba(15, 20, 30, 0.8);
            --text-light: #e0e0e0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: var(--deep-bg);
            color: var(--text-light);
            overflow-x: hidden;
            line-height: 1.6;
            position: relative;
            min-height: 100vh;
        }

        /* ========== ANIMATED BACKGROUND (NO JS) ========== */
        .bg-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: radial-gradient(ellipse at 30% 40%, #0b1120 0%, #02040a 100%);
            animation: bgShift 20s infinite alternate ease-in-out;
        }
        @keyframes bgShift {
            0% { background: radial-gradient(ellipse at 30% 40%, #0b1120 0%, #02040a 100%); }
            100% { background: radial-gradient(ellipse at 70% 60%, #0b1120 0%, #02040a 100%); }
        }

        /* Floating orbs */
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(90px);
            opacity: 0.25;
            z-index: -1;
            animation: floatOrb 14s infinite alternate;
        }
        .orb1 {
            width: 450px;
            height: 450px;
            background: var(--neon-cyan);
            top: -120px;
            left: -120px;
        }
        .orb2 {
            width: 550px;
            height: 550px;
            background: var(--neon-purple);
            bottom: -150px;
            right: -150px;
            animation-duration: 18s;
        }
        @keyframes floatOrb {
            0% { transform: translate(0, 0) scale(1); opacity: 0.25; }
            100% { transform: translate(35px, -45px) scale(1.2); opacity: 0.4; }
        }

        /* ========== STAGGERED FADE-IN ON LOAD ========== */
        .fade-in-section {
            animation: fadeUp 1s ease forwards;
            opacity: 0;
        }
        .fade-in-section:nth-child(1) { animation-delay: 0.2s; }
        .fade-in-section:nth-child(2) { animation-delay: 0.4s; }
        .fade-in-section:nth-child(3) { animation-delay: 0.6s; }
        .fade-in-section:nth-child(4) { animation-delay: 0.8s; }
        .fade-in-section:nth-child(5) { animation-delay: 1.0s; }
        .fade-in-section:nth-child(6) { animation-delay: 1.2s; }
        .fade-in-section:nth-child(7) { animation-delay: 1.4s; }
        .fade-in-section:nth-child(8) { animation-delay: 1.6s; }
        .fade-in-section:nth-child(9) { animation-delay: 1.8s; }
        .fade-in-section:nth-child(10) { animation-delay: 2.0s; }

        @keyframes fadeUp {
            0% { opacity: 0; transform: translateY(40px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        /* ========== CONTAINER ========== */
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 0;
            position: relative;
            z-index: 2;
        }

        /* ========== HERO SECTION ========== */
        .hero {
            text-align: center;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }
        .hero h1 {
            font-size: 5rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--neon-cyan), var(--neon-purple));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 20px rgba(0,247,255,0.4);
            margin-bottom: 1rem;
            animation: glowPulse 2.5s infinite alternate;
        }
        @keyframes glowPulse {
            from { filter: drop-shadow(0 0 10px var(--neon-cyan)); }
            to { filter: drop-shadow(0 0 25px var(--neon-purple)); }
        }

        .typing-img {
            display: block;
            margin: 0 auto 2rem;
            max-width: 700px;
            width: 100%;
            height: auto;
            filter: drop-shadow(0 0 12px var(--neon-cyan));
            animation: pulseShadow 2s infinite alternate;
        }
        @keyframes pulseShadow {
            from { filter: drop-shadow(0 0 8px var(--neon-cyan)); }
            to { filter: drop-shadow(0 0 20px var(--neon-purple)); }
        }

        .profile-views {
            display: inline-block;
            background: rgba(0,247,255,0.12);
            border: 1px solid var(--neon-cyan);
            border-radius: 50px;
            padding: 0.6rem 2rem;
            font-weight: 500;
            backdrop-filter: blur(12px);
            animation: badgeGlow 2.5s infinite alternate;
        }
        @keyframes badgeGlow {
            from { box-shadow: 0 0 10px var(--neon-cyan); }
            to { box-shadow: 0 0 28px var(--neon-cyan); }
        }

        /* ========== SECTION TITLES ========== */
        .section-title {
            text-align: center;
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 2.5rem;
            background: linear-gradient(to right, var(--neon-cyan), var(--neon-purple));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
            animation: titleGlow 2s infinite alternate;
        }
        @keyframes titleGlow {
            from { filter: drop-shadow(0 0 5px var(--neon-cyan)); }
            to { filter: drop-shadow(0 0 15px var(--neon-purple)); }
        }
        .section-title::after {
            content: '';
            display: block;
            width: 70px;
            height: 4px;
            background: var(--neon-cyan);
            margin: 0.6rem auto 0;
            border-radius: 2px;
            animation: barWidth 2.5s infinite alternate;
        }
        @keyframes barWidth {
            from { width: 70px; background: var(--neon-cyan); }
            to { width: 150px; background: var(--neon-purple); }
        }

        /* ========== ABOUT GRID ========== */
        .about-grid {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 2rem;
        }
        .about-text {
            flex: 1 1 500px;
        }
        .about-text p {
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }
        .about-gif {
            flex: 1 1 300px;
            text-align: center;
        }
        .about-gif img {
            max-width: 100%;
            border-radius: 20px;
            box-shadow: 0 0 25px rgba(0,247,255,0.4);
            transition: transform 0.4s cubic-bezier(0.23, 1, 0.32, 1);
        }
        .about-gif img:hover {
            transform: scale(1.06);
            box-shadow: 0 0 45px rgba(138,43,226,0.6);
        }

        /* ========== SKILLS & TOOLS ========== */
        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.8rem;
        }
        .skill-icon {
            width: 75px;
            height: 75px;
            transition: all 0.35s ease;
            cursor: pointer;
            filter: drop-shadow(0 0 6px rgba(0,247,255,0.5));
            animation: floatIcon 4s infinite alternate;
        }
        .skill-icon:nth-child(odd) { animation-duration: 3.5s; }
        .skill-icon:nth-child(even) { animation-duration: 4.5s; animation-delay: 0.2s; }

        @keyframes floatIcon {
            0% { transform: translateY(0px); }
            100% { transform: translateY(-10px); }
        }
        .skill-icon:hover {
            transform: translateY(-14px) scale(1.15);
            filter: drop-shadow(0 0 22px var(--neon-purple));
        }

        /* ========== PROJECT CARDS ========== */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
        }
        .project-card {
            background: var(--card-bg);
            border-radius: 24px;
            padding: 2rem 1.8rem;
            backdrop-filter: blur(18px);
            border: 1px solid rgba(0,247,255,0.2);
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative;
            overflow: hidden;
            transform-style: preserve-3d;
            perspective: 800px;
            animation: cardGlow 2.5s infinite alternate;
        }
        @keyframes cardGlow {
            from { box-shadow: 0 8px 20px rgba(0,247,255,0.15); }
            to { box-shadow: 0 15px 35px rgba(138,43,226,0.25); }
        }
        .project-card::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(0,247,255,0.15) 0%, rgba(138,43,226,0.15) 100%);
            opacity: 0;
            transition: opacity 0.45s;
            border-radius: 24px;
            z-index: 0;
        }
        .project-card:hover {
            transform: translateY(-12px) rotateX(4deg) rotateY(-3deg);
            border-color: var(--neon-cyan);
            box-shadow: 0 25px 45px rgba(0,247,255,0.3), 0 0 30px rgba(138,43,226,0.35);
        }
        .project-card:hover::before {
            opacity: 1;
        }
        .project-card > * {
            position: relative;
            z-index: 1;
        }
        .project-card h3 {
            font-size: 1.9rem;
            margin-bottom: 0.5rem;
            background: linear-gradient(to right, var(--neon-cyan), var(--neon-purple));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* ========== STATS / TROPHIES / GRAPH ========== */
        .stats-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 3rem;
        }
        .stats-card {
            background: var(--card-bg);
            border-radius: 18px;
            padding: 1.5rem;
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255,255,255,0.08);
            transition: transform 0.35s, box-shadow 0.35s;
        }
        .stats-card:hover {
            transform: scale(1.04);
            box-shadow: 0 0 35px rgba(0,247,255,0.5);
        }
        .stats-card img {
            width: 100%;
            height: auto;
            display: block;
        }

        .graph-container img,
        .trophies-grid img,
        .snake-container img {
            width: 100%;
            max-width: 100%;
            display: block;
            margin: 0 auto;
            border-radius: 15px;
            transition: transform 0.4s, box-shadow 0.4s;
        }
        .graph-container img:hover,
        .trophies-grid img:hover,
        .snake-container img:hover {
            transform: scale(1.02);
            box-shadow: 0 0 45px rgba(138,43,226,0.6);
        }

        /* ========== CONNECT BUTTONS ========== */
        .connect-buttons {
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
        }
        .connect-btn {
            display: flex;
            align-items: center;
            gap: 0.6rem;
            background: rgba(0,247,255,0.08);
            border: 1px solid var(--neon-cyan);
            border-radius: 50px;
            padding: 0.8rem 2.2rem;
            font-size: 1.2rem;
            color: var(--neon-cyan);
            text-decoration: none;
            transition: all 0.35s;
            backdrop-filter: blur(10px);
            font-weight: 500;
            animation: btnPulse 3s infinite alternate;
        }
        @keyframes btnPulse {
            from { box-shadow: 0 0 8px rgba(0,247,255,0.2); }
            to { box-shadow: 0 0 22px rgba(138,43,226,0.4); }
        }
        .connect-btn:hover {
            background: var(--neon-cyan);
            color: #0a0c10;
            box-shadow: 0 0 40px var(--neon-cyan);
            transform: translateY(-5px);
        }
        .connect-btn img {
            width: 26px;
            height: 26px;
        }

        /* ========== FOOTER ========== */
        .footer-wave img {
            width: 100%;
            display: block;
        }
        .footer-text {
            text-align: center;
            padding: 2.5rem;
            font-size: 1.8rem;
            color: var(--neon-cyan);
            animation: softPulse 2.2s infinite alternate;
        }
        @keyframes softPulse {
            from { opacity: 0.6; text-shadow: 0 0 8px var(--neon-cyan); }
            to { opacity: 1; text-shadow: 0 0 22px var(--neon-purple); }
        }

        /* ========== RESPONSIVE ========== */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.6rem;
            }
            .section-title {
                font-size: 2.2rem;
            }
            .skill-icon {
                width: 55px;
                height: 55px;
            }
        }
    </style>
</head>
<body>
    <!-- Background effects -->
    <div class="bg-particles"></div>
    <div class="orb orb1"></div>
    <div class="orb orb2"></div>

    <!-- ========== HERO ========== -->
    <header class="hero fade-in-section">
        <h1>👋 Hey, I'm Inbarasan</h1>
        <!-- Typing SVG from readme-typing-svg (animated, no JS needed) -->
        <img class="typing-img" src="https://readme-typing-svg.herokuapp.com?font=Poppins&size=28&duration=3000&pause=1000&color=00F7FF&center=true&vCenter=true&width=700&lines=Frontend+Developer;React+Developer;JavaScript+Enthusiast;Building+Awesome+Web+Applications;Always+Learning+New+Technologies" alt="Typing SVG" />
        <div class="profile-views">👁️ Profile Views: 1.5k+</div>
    </header>

    <!-- ========== ABOUT ME ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🚀 About Me</h2>
        <div class="about-grid">
            <div class="about-text">
                <p>💻 <strong>Frontend Developer</strong> passionate about crafting beautiful, responsive web experiences.</p>
                <p>🌱 Currently diving deep into <span style="color:var(--neon-cyan);">React.js</span>, <span style="color:var(--neon-cyan);">Node.js</span>, <span style="color:var(--neon-cyan);">Express.js</span>, and <span style="color:var(--neon-cyan);">MongoDB</span>.</p>
                <p>🎯 Goal: Become a Professional <strong>MERN Stack Developer</strong>.</p>
                <p>🔥 I love building responsive websites, React applications, UI designs, and full‑stack projects.</p>
                <p>📫 <strong>inbadharma2312@gmail.com</strong></p>
            </div>
            <div class="about-gif">
                <img src="https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif" alt="Coding animation" loading="lazy">
            </div>
        </div>
    </section>

    <!-- ========== TECH STACK ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🚀 Tech Stack</h2>
        <div class="skills-grid">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=html" alt="HTML5">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=css" alt="CSS3">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=js" alt="JavaScript">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=react" alt="React">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=nodejs" alt="Node.js">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=express" alt="Express">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=mongodb" alt="MongoDB">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=bootstrap" alt="Bootstrap">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=git" alt="Git">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=github" alt="GitHub">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=vscode" alt="VS Code">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=npm" alt="npm">
        </div>
    </section>

    <!-- ========== FEATURED PROJECTS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🚀 Featured Projects</h2>
        <div class="projects-grid">
            <div class="project-card">
                <h3>🎬 MoviesSelections</h3>
                <p>Movie Recommendation Website</p>
                <ul style="margin-top:1rem;">
                    <li>✔ Search Movies</li>
                    <li>✔ Categories</li>
                    <li>✔ Responsive Design</li>
                    <li>✔ JavaScript</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>🎫 Ticket Management</h3>
                <p>MERN Stack Project</p>
                <ul style="margin-top:1rem;">
                    <li>✔ JWT Authentication</li>
                    <li>✔ Role Based Login</li>
                    <li>✔ MongoDB</li>
                    <li>✔ React + Express</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>🛒 E-Commerce</h3>
                <p>Shopping Website</p>
                <ul style="margin-top:1rem;">
                    <li>✔ Product Listing</li>
                    <li>✔ Cart</li>
                    <li>✔ Search</li>
                    <li>✔ Responsive UI</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>👨‍💻 Portfolio</h3>
                <p>Modern Personal Portfolio</p>
                <ul style="margin-top:1rem;">
                    <li>✔ Responsive</li>
                    <li>✔ Animation</li>
                    <li>✔ Modern UI</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>📅 TimeTable</h3>
                <p>Responsive Timetable</p>
                <ul style="margin-top:1rem;">
                    <li>✔ HTML & CSS</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- ========== LANGUAGES & TOOLS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🚀 Languages & Tools</h2>
        <div class="skills-grid">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=html" alt="HTML">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=css" alt="CSS">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=javascript" alt="JS">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=react" alt="React">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=nodejs" alt="Node">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=express" alt="Express">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=mongodb" alt="Mongo">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=git" alt="Git">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=github" alt="GitHub">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=vscode" alt="VSCode">
        </div>
    </section>

    <!-- ========== GITHUB STATISTICS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">📊 GitHub Statistics</h2>
        <div class="stats-grid">
            <div class="stats-card">
                <img src="https://github-readme-stats.vercel.app/api?username=inbarasan23&show_icons=true&theme=tokyonight" alt="GitHub Stats" loading="lazy">
            </div>
            <div class="stats-card">
                <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=inbarasan23&layout=compact&theme=tokyonight" alt="Top Languages" loading="lazy">
            </div>
        </div>
        <div class="graph-container">
            <img src="https://github-readme-streak-stats.herokuapp.com/?user=inbarasan23&theme=tokyonight" alt="GitHub Streak" loading="lazy">
        </div>
    </section>

    <!-- ========== GITHUB TROPHIES ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🏆 GitHub Trophies</h2>
        <div class="trophies-grid">
            <img src="https://github-profile-trophy.vercel.app/?username=inbarasan23&theme=algolia&row=2&column=4" alt="Trophies" loading="lazy">
        </div>
    </section>

    <!-- ========== CONTRIBUTION GRAPH ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">📈 Contribution Graph</h2>
        <div class="graph-container">
            <img src="https://github-readme-activity-graph.vercel.app/graph?username=inbarasan23&theme=tokyo-night" alt="Contribution Graph" loading="lazy">
        </div>
    </section>

    <!-- ========== SNAKE EATING CONTRIBUTIONS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🐍 Snake Eating Contributions</h2>
        <div class="snake-container">
            <!-- The snake SVG may be animated internally; we display it as an image. -->
            <img src="https://github.com/inbarasan23/inbarasan23/blob/output/github-contribution-grid-snake.svg" alt="Snake animation" loading="lazy">
        </div>
    </section>

    <!-- ========== CONNECT WITH ME ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🌎 Connect With Me</h2>
        <div class="connect-buttons">
            <a href="mailto:inbadharma2312@gmail.com" class="connect-btn">
                <img src="https://skillicons.dev/icons?i=gmail" alt="Gmail"> Email
            </a>
            <a href="https://github.com/inbarasan23" target="_blank" rel="noopener" class="connect-btn">
                <img src="https://skillicons.dev/icons?i=github" alt="GitHub"> GitHub
            </a>
        </div>
    </section>

    <!-- ========== FOOTER ========== -->
    <footer>
        <div class="footer-wave">
            <img src="https://capsule-render.vercel.app/api?type=waving&height=120&color=0:00F7FF,100:8A2BE2&section=footer" alt="wave footer">
        </div>
        <div class="footer-text">💙 Thanks for Visiting</div>
    </footer>
</body>
</html>

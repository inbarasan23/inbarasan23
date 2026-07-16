<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inbarasan | Cute Animated Portfolio</title>
    <style>
        /* ========== CUTE GLOBAL RESET & VARIABLES ========== */
        *, *::before, *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --cute-pink: #ffb3d9;
            --cute-blue: #b3e0ff;
            --cute-purple: #d9b3ff;
            --cute-yellow: #fff5b3;
            --cute-green: #b3ffcc;
            --neon-cyan: #00F7FF;
            --neon-purple: #8A2BE2;
            --deep-bg: #1a0a1e;
            --card-bg: rgba(255, 255, 255, 0.08);
            --text-light: #f5f0ff;
            --soft-shadow: 0 8px 30px rgba(0,0,0,0.15);
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: var(--deep-bg);
            color: var(--text-light);
            overflow-x: hidden;
            line-height: 1.6;
            position: relative;
            min-height: 100vh;
            cursor: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20'><circle cx='10' cy='10' r='8' fill='%23ffb3d9' opacity='0.8'/></svg>") 10 10, auto;
        }

        /* ========== CUTE ANIMATED BACKGROUND ========== */
        .bg-cute {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -3;
            background: radial-gradient(circle at 20% 30%, #3a0d45 0%, #0a0210 70%);
            animation: bgMove 25s infinite alternate ease-in-out;
        }

        @keyframes bgMove {
            0% { background-position: 0% 0%; }
            100% { background-position: 100% 100%; }
        }

        /* floating pastel bubbles */
        .bubbles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            overflow: hidden;
        }

        .bubble {
            position: absolute;
            border-radius: 50%;
            opacity: 0.3;
            animation: floatBubble 20s infinite linear;
        }

        .bubble:nth-child(1) { width: 120px; height: 120px; left: 5%; top: 80%; background: var(--cute-pink); animation-duration: 18s; animation-delay: 0s; }
        .bubble:nth-child(2) { width: 80px; height: 80px; left: 25%; top: 20%; background: var(--cute-blue); animation-duration: 22s; animation-delay: 2s; }
        .bubble:nth-child(3) { width: 100px; height: 100px; left: 70%; top: 10%; background: var(--cute-purple); animation-duration: 20s; animation-delay: 4s; }
        .bubble:nth-child(4) { width: 60px; height: 60px; left: 90%; top: 60%; background: var(--cute-yellow); animation-duration: 25s; animation-delay: 1s; }
        .bubble:nth-child(5) { width: 150px; height: 150px; left: 40%; top: 50%; background: var(--cute-green); animation-duration: 28s; animation-delay: 3s; }
        .bubble:nth-child(6) { width: 50px; height: 50px; left: 10%; top: 10%; background: var(--cute-pink); animation-duration: 15s; animation-delay: 5s; }
        .bubble:nth-child(7) { width: 130px; height: 130px; left: 80%; top: 30%; background: var(--cute-blue); animation-duration: 30s; animation-delay: 0s; }
        .bubble:nth-child(8) { width: 70px; height: 70px; left: 30%; top: 70%; background: var(--cute-purple); animation-duration: 24s; animation-delay: 6s; }

        @keyframes floatBubble {
            0% { transform: translateY(0) scale(1) rotate(0deg); opacity: 0.3; }
            50% { transform: translateY(-200px) scale(1.3) rotate(180deg); opacity: 0.6; }
            100% { transform: translateY(0) scale(1) rotate(360deg); opacity: 0.3; }
        }

        /* ========== UNIVERSAL FADE IN ========== */
        .fade-in-section {
            animation: fadeInUp 1s cubic-bezier(0.23, 1, 0.32, 1) forwards;
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

        @keyframes fadeInUp {
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

        /* ========== CUTE HERO ========== */
        .hero {
            text-align: center;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        .hero h1 {
            font-size: 5.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--cute-pink), var(--cute-blue), var(--cute-purple));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 20px rgba(255,179,217,0.6));
            margin-bottom: 1.5rem;
            animation: cuteTextGlow 3s infinite alternate;
        }
        @keyframes cuteTextGlow {
            0% { filter: drop-shadow(0 0 10px var(--cute-pink)); }
            100% { filter: drop-shadow(0 0 35px var(--cute-blue)); }
        }

        .typing-img {
            display: block;
            margin: 0 auto 2rem;
            max-width: 750px;
            width: 100%;
            height: auto;
            filter: drop-shadow(0 0 15px var(--cute-purple));
            animation: softPulse 2s infinite alternate;
        }
        @keyframes softPulse {
            from { transform: scale(1); }
            to { transform: scale(1.03); }
        }

        .profile-views {
            display: inline-block;
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(15px);
            border: 1px solid var(--cute-pink);
            border-radius: 50px;
            padding: 0.7rem 2.5rem;
            font-weight: 600;
            font-size: 1.1rem;
            color: var(--cute-pink);
            animation: badgeBounce 2s infinite;
        }
        @keyframes badgeBounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        /* ========== SECTION TITLES ========== */
        .section-title {
            text-align: center;
            font-size: 3.2rem;
            font-weight: 700;
            margin-bottom: 2.5rem;
            background: linear-gradient(45deg, var(--cute-pink), var(--cute-blue), var(--cute-purple));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
        }
        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: var(--cute-pink);
            margin: 0.8rem auto 0;
            border-radius: 10px;
            animation: titleBar 2s infinite alternate;
        }
        @keyframes titleBar {
            from { width: 80px; background: var(--cute-pink); }
            to { width: 180px; background: var(--cute-blue); }
        }

        /* ========== ABOUT ========== */
        .about-grid {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 2rem;
        }
        .about-text {
            flex: 1 1 500px;
            font-size: 1.2rem;
        }
        .about-text p {
            margin-bottom: 1.2rem;
            padding: 0.8rem 1.2rem;
            background: rgba(255,255,255,0.04);
            border-radius: 20px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255,179,217,0.2);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .about-text p:hover {
            transform: translateX(10px);
            box-shadow: 0 0 25px rgba(255,179,217,0.4);
        }
        .about-gif {
            flex: 1 1 300px;
            text-align: center;
        }
        .about-gif img {
            max-width: 100%;
            border-radius: 30px;
            box-shadow: 0 0 40px rgba(255,179,217,0.5);
            transition: transform 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
        }
        .about-gif img:hover {
            transform: rotate(-3deg) scale(1.08);
            box-shadow: 0 0 70px rgba(179,224,255,0.8);
        }

        /* ========== SKILLS ========== */
        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.8rem;
        }
        .skill-icon {
            width: 80px;
            height: 80px;
            filter: drop-shadow(0 0 8px var(--cute-blue));
            transition: all 0.4s;
            animation: cuteFloat 4s infinite alternate;
        }
        .skill-icon:nth-child(odd) { animation-duration: 3.5s; }
        .skill-icon:nth-child(even) { animation-duration: 4.5s; animation-delay: 0.3s; }
        @keyframes cuteFloat {
            0% { transform: translateY(0) rotate(0deg); }
            100% { transform: translateY(-12px) rotate(5deg); }
        }
        .skill-icon:hover {
            transform: translateY(-15px) scale(1.2) rotate(0deg);
            filter: drop-shadow(0 0 25px var(--cute-purple));
        }

        /* ========== PROJECT CARDS ========== */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
        }
        .project-card {
            background: var(--card-bg);
            border-radius: 30px;
            padding: 2rem;
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255,179,217,0.25);
            transition: all 0.6s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative;
            overflow: hidden;
            animation: cardFloat 6s infinite alternate;
        }
        @keyframes cardFloat {
            0% { transform: translateY(0); }
            100% { transform: translateY(-5px); }
        }
        .project-card:nth-child(2) { animation-delay: 0.5s; }
        .project-card:nth-child(3) { animation-delay: 1s; }
        .project-card:nth-child(4) { animation-delay: 1.5s; }
        .project-card:nth-child(5) { animation-delay: 2s; }

        .project-card::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(255,179,217,0.2), rgba(179,224,255,0.2));
            opacity: 0;
            transition: opacity 0.4s;
            border-radius: 30px;
            z-index: 0;
        }
        .project-card:hover {
            transform: translateY(-15px) scale(1.03);
            border-color: var(--cute-pink);
            box-shadow: 0 20px 45px rgba(255,179,217,0.4), 0 0 35px rgba(179,224,255,0.3);
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
            background: linear-gradient(to right, var(--cute-pink), var(--cute-blue));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .project-card ul {
            list-style: none;
        }
        .project-card li {
            padding: 0.3rem 0;
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
            background: rgba(255,255,255,0.05);
            border-radius: 25px;
            padding: 1.5rem;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,179,217,0.3);
            transition: transform 0.4s, box-shadow 0.4s;
        }
        .stats-card:hover {
            transform: scale(1.05);
            box-shadow: 0 0 45px rgba(255,179,217,0.6);
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
            border-radius: 25px;
            transition: transform 0.4s, box-shadow 0.4s;
        }
        .graph-container img:hover,
        .trophies-grid img:hover,
        .snake-container img:hover {
            transform: scale(1.02);
            box-shadow: 0 0 60px rgba(179,224,255,0.7);
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
            gap: 0.7rem;
            background: rgba(255,255,255,0.05);
            border: 2px solid var(--cute-pink);
            border-radius: 50px;
            padding: 0.9rem 2.5rem;
            font-size: 1.2rem;
            color: var(--cute-pink);
            text-decoration: none;
            backdrop-filter: blur(12px);
            font-weight: 600;
            transition: all 0.4s;
            animation: btnGlow 2.5s infinite alternate;
        }
        @keyframes btnGlow {
            from { box-shadow: 0 0 10px rgba(255,179,217,0.3); }
            to { box-shadow: 0 0 30px rgba(179,224,255,0.5); }
        }
        .connect-btn:hover {
            background: var(--cute-pink);
            color: #1a0a1e;
            border-color: var(--cute-blue);
            transform: translateY(-5px);
            box-shadow: 0 0 50px var(--cute-pink);
        }
        .connect-btn img {
            width: 28px;
            height: 28px;
        }

        /* ========== FOOTER ========== */
        .footer-wave img {
            width: 100%;
            display: block;
        }
        .footer-text {
            text-align: center;
            padding: 2.5rem;
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(45deg, var(--cute-pink), var(--cute-blue));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: footerPulse 2s infinite alternate;
        }
        @keyframes footerPulse {
            from { filter: drop-shadow(0 0 8px var(--cute-pink)); }
            to { filter: drop-shadow(0 0 25px var(--cute-blue)); }
        }

        /* ========== CUTE EXTRAS (hearts, sparkles) ========== */
        .cute-decoration {
            position: absolute;
            pointer-events: none;
            animation: spin 10s linear infinite;
        }
        .cute-decoration.top-left {
            top: 10%;
            left: 5%;
            font-size: 3rem;
            opacity: 0.6;
        }
        .cute-decoration.bottom-right {
            bottom: 15%;
            right: 5%;
            font-size: 4rem;
            opacity: 0.5;
            animation-direction: reverse;
        }
        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* RESPONSIVE */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.8rem; }
            .section-title { font-size: 2.2rem; }
            .skill-icon { width: 60px; height: 60px; }
        }
    </style>
</head>
<body>
    <!-- Cute animated background -->
    <div class="bg-cute"></div>
    <div class="bubbles">
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
    </div>
    <div class="cute-decoration top-left">🌸</div>
    <div class="cute-decoration bottom-right">🌟</div>

    <!-- ========== HERO ========== -->
    <header class="hero fade-in-section">
        <h1>👋 Hey, I'm Inbarasan</h1>
        <img class="typing-img" src="https://readme-typing-svg.herokuapp.com?font=Poppins&size=28&duration=3000&pause=1000&color=ffb3d9&center=true&vCenter=true&width=700&lines=Frontend+Developer;React+Developer;JavaScript+Enthusiast;Building+Awesome+Web+Applications;Always+Learning+New+Technologies" alt="typing" />
        <div class="profile-views">✨ Profile Views: 2.3k+</div>
    </header>

    <!-- ========== ABOUT ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🌸 About Me</h2>
        <div class="about-grid">
            <div class="about-text">
                <p>💻 <strong>Frontend Developer</strong> who loves crafting cute, responsive web experiences.</p>
                <p>🌱 Currently learning <span style="color:var(--cute-pink);">React.js</span>, <span style="color:var(--cute-blue);">Node.js</span>, <span style="color:var(--cute-purple);">Express</span> & <span style="color:var(--cute-green);">MongoDB</span>.</p>
                <p>🎯 Goal: Become a Professional <strong>MERN Stack Developer</strong>.</p>
                <p>🔥 I adore building responsive websites, React apps, UI designs & full-stack projects.</p>
                <p>📫 <strong>inbadharma2312@gmail.com</strong></p>
            </div>
            <div class="about-gif">
                <img src="https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif" alt="cute coding" loading="lazy">
            </div>
        </div>
    </section>

    <!-- ========== TECH STACK ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🍭 Tech Stack</h2>
        <div class="skills-grid">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=html" alt="HTML">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=css" alt="CSS">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=js" alt="JS">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=react" alt="React">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=nodejs" alt="Node">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=express" alt="Express">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=mongodb" alt="MongoDB">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=bootstrap" alt="Bootstrap">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=git" alt="Git">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=github" alt="GitHub">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=vscode" alt="VSCode">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=npm" alt="npm">
        </div>
    </section>

    <!-- ========== FEATURED PROJECTS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🎀 Featured Projects</h2>
        <div class="projects-grid">
            <div class="project-card">
                <h3>🎬 MoviesSelections</h3>
                <p>Movie Recommendation Website</p>
                <ul>
                    <li>✔ Search Movies</li>
                    <li>✔ Categories</li>
                    <li>✔ Responsive Design</li>
                    <li>✔ JavaScript</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>🎫 Ticket Management</h3>
                <p>MERN Stack Project</p>
                <ul>
                    <li>✔ JWT Authentication</li>
                    <li>✔ Role Based Login</li>
                    <li>✔ MongoDB</li>
                    <li>✔ React + Express</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>🛒 E-Commerce</h3>
                <p>Shopping Website</p>
                <ul>
                    <li>✔ Product Listing</li>
                    <li>✔ Cart</li>
                    <li>✔ Search</li>
                    <li>✔ Responsive UI</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>👨‍💻 Portfolio</h3>
                <p>Modern Personal Portfolio</p>
                <ul>
                    <li>✔ Responsive</li>
                    <li>✔ Animation</li>
                    <li>✔ Modern UI</li>
                </ul>
            </div>
            <div class="project-card">
                <h3>📅 TimeTable</h3>
                <p>Responsive Timetable</p>
                <ul>
                    <li>✔ HTML & CSS</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- ========== LANGUAGES & TOOLS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🧁 Languages & Tools</h2>
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

    <!-- ========== GITHUB STATS ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">📊 GitHub Statistics</h2>
        <div class="stats-grid">
            <div class="stats-card">
                <img src="https://github-readme-stats.vercel.app/api?username=inbarasan23&show_icons=true&theme=tokyonight" alt="stats" loading="lazy">
            </div>
            <div class="stats-card">
                <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=inbarasan23&layout=compact&theme=tokyonight" alt="languages" loading="lazy">
            </div>
        </div>
        <div class="graph-container">
            <img src="https://github-readme-streak-stats.herokuapp.com/?user=inbarasan23&theme=tokyonight" alt="streak" loading="lazy">
        </div>
    </section>

    <!-- ========== TROPHIES ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🏆 GitHub Trophies</h2>
        <div class="trophies-grid">
            <img src="https://github-profile-trophy.vercel.app/?username=inbarasan23&theme=algolia&row=2&column=4" alt="trophies" loading="lazy">
        </div>
    </section>

    <!-- ========== CONTRIBUTION GRAPH ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">📈 Contribution Graph</h2>
        <div class="graph-container">
            <img src="https://github-readme-activity-graph.vercel.app/graph?username=inbarasan23&theme=tokyo-night" alt="graph" loading="lazy">
        </div>
    </section>

    <!-- ========== SNAKE ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🐍 Snake Eating Contributions</h2>
        <div class="snake-container">
            <img src="https://github.com/inbarasan23/inbarasan23/blob/output/github-contribution-grid-snake.svg" alt="snake" loading="lazy">
        </div>
    </section>

    <!-- ========== CONNECT ========== -->
    <section class="container fade-in-section">
        <h2 class="section-title">🌎 Connect With Me</h2>
        <div class="connect-buttons">
            <a href="mailto:inbadharma2312@gmail.com" class="connect-btn">
                <img src="https://skillicons.dev/icons?i=gmail" alt="gmail"> Email
            </a>
            <a href="https://github.com/inbarasan23" target="_blank" rel="noopener" class="connect-btn">
                <img src="https://skillicons.dev/icons?i=github" alt="github"> GitHub
            </a>
        </div>
    </section>

    <!-- ========== FOOTER ========== -->
    <footer>
        <div class="footer-wave">
            <img src="https://capsule-render.vercel.app/api?type=waving&height=120&color=0:ffb3d9,100:b3e0ff&section=footer" alt="wave">
        </div>
        <div class="footer-text">💖 Thanks for Visiting 💖</div>
    </footer>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inbarasan - Animated Portfolio</title>
    <!-- Typed.js from CDN for the dynamic typing effect -->
    <script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.12"></script>
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
            --card-bg: rgba(15, 20, 30, 0.85);
            --text-light: #e0e0e0;
            --glow-cyan: 0 0 15px var(--neon-cyan), 0 0 30px var(--neon-cyan);
            --glow-purple: 0 0 15px var(--neon-purple), 0 0 30px var(--neon-purple);
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: var(--deep-bg);
            color: var(--text-light);
            overflow-x: hidden;
            line-height: 1.6;
            position: relative;
        }

        /* Animated background particles (CSS only) */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: radial-gradient(ellipse at 20% 50%, #0a0f1e 0%, #02040a 100%);
        }
        .particles::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(circle at 30% 40%, rgba(0,247,255,0.08) 0%, transparent 50%),
                radial-gradient(circle at 70% 60%, rgba(138,43,226,0.08) 0%, transparent 50%);
            animation: particleDrift 20s infinite alternate ease-in-out;
        }
        @keyframes particleDrift {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(-2%, 2%) scale(1.05); }
        }

        /* Floating orbs */
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.3;
            z-index: -1;
            animation: floatOrb 12s infinite alternate;
        }
        .orb1 {
            width: 400px;
            height: 400px;
            background: var(--neon-cyan);
            top: -100px;
            left: -100px;
        }
        .orb2 {
            width: 500px;
            height: 500px;
            background: var(--neon-purple);
            bottom: -150px;
            right: -150px;
            animation-duration: 18s;
        }
        @keyframes floatOrb {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(30px, -40px) scale(1.2); }
        }

        /* ========== SCROLL ANIMATIONS ========== */
        .fade-up {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }
        .fade-up.visible {
            opacity: 1;
            transform: translateY(0);
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
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 0 20px rgba(0,247,255,0.5);
            margin-bottom: 1rem;
            animation: glowPulse 2s infinite alternate;
        }
        @keyframes glowPulse {
            from { filter: drop-shadow(0 0 10px var(--neon-cyan)); }
            to { filter: drop-shadow(0 0 25px var(--neon-purple)); }
        }

        .typing-container {
            font-size: 2rem;
            min-height: 3.5rem;
            color: var(--neon-cyan);
            margin-bottom: 2rem;
            font-weight: 300;
        }

        .profile-views {
            display: inline-block;
            background: rgba(0,247,255,0.15);
            border: 1px solid var(--neon-cyan);
            border-radius: 50px;
            padding: 0.5rem 1.5rem;
            font-weight: 500;
            backdrop-filter: blur(10px);
            animation: badgeGlow 2s infinite alternate;
        }
        @keyframes badgeGlow {
            from { box-shadow: 0 0 10px var(--neon-cyan); }
            to { box-shadow: 0 0 25px var(--neon-cyan); }
        }

        /* ========== SECTION TITLES ========== */
        .section-title {
            text-align: center;
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 3rem;
            background: linear-gradient(to right, var(--neon-cyan), var(--neon-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
        }
        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: var(--neon-cyan);
            margin: 0.5rem auto 0;
            border-radius: 2px;
            animation: barWidth 2s infinite alternate;
        }
        @keyframes barWidth {
            from { width: 80px; }
            to { width: 150px; }
        }

        /* ========== ABOUT SECTION ========== */
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
            box-shadow: var(--glow-cyan);
            transition: transform 0.3s ease;
        }
        .about-gif img:hover {
            transform: scale(1.05);
        }

        /* ========== SKILLS & TOOLS ========== */
        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.5rem;
        }
        .skill-icon {
            width: 70px;
            height: 70px;
            transition: all 0.3s ease;
            cursor: pointer;
            filter: drop-shadow(0 0 6px rgba(0,247,255,0.5));
        }
        .skill-icon:hover {
            transform: translateY(-8px) scale(1.15);
            filter: drop-shadow(0 0 18px var(--neon-purple));
        }

        /* ========== PROJECT CARDS ========== */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }
        .project-card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 2rem;
            backdrop-filter: blur(15px);
            border: 1px solid rgba(0,247,255,0.2);
            transition: all 0.4s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative;
            overflow: hidden;
            transform-style: preserve-3d;
            perspective: 1000px;
        }
        .project-card::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(0,247,255,0.1) 0%, rgba(138,43,226,0.1) 100%);
            opacity: 0;
            transition: opacity 0.4s;
            border-radius: 20px;
            z-index: 0;
        }
        .project-card:hover {
            transform: translateY(-10px) rotateX(5deg) rotateY(-3deg);
            box-shadow: 0 20px 40px rgba(0,247,255,0.25), 0 0 30px rgba(138,43,226,0.3);
            border-color: var(--neon-cyan);
        }
        .project-card:hover::before {
            opacity: 1;
        }
        .project-card > * {
            position: relative;
            z-index: 1;
        }
        .project-card h3 {
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
            background: linear-gradient(to right, var(--neon-cyan), var(--neon-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* ========== STATS & TROPHIES ========== */
        .stats-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 3rem;
        }
        .stats-card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 1.5rem;
            backdrop-filter: blur(10px);
            transition: transform 0.3s;
            text-align: center;
            border: 1px solid rgba(255,255,255,0.1);
        }
        .stats-card:hover {
            transform: scale(1.05);
            box-shadow: var(--glow-cyan);
        }
        .stats-card img {
            width: 100%;
            height: auto;
            display: block;
        }

        .trophies-grid img {
            max-width: 100%;
            border-radius: 15px;
            transition: transform 0.4s;
        }
        .trophies-grid img:hover {
            transform: scale(1.03);
            box-shadow: var(--glow-purple);
        }

        .graph-container img {
            width: 100%;
            max-width: 800px;
            display: block;
            margin: 0 auto;
            border-radius: 15px;
            transition: transform 0.4s;
        }
        .graph-container img:hover {
            transform: scale(1.02);
            box-shadow: var(--glow-cyan);
        }

        /* ========== SNAKE ANIMATION ========== */
        .snake-animation {
            text-align: center;
            margin: 3rem 0;
        }
        .snake-animation img {
            max-width: 100%;
            border-radius: 15px;
            box-shadow: 0 0 30px rgba(0,247,255,0.3);
            animation: snakePulse 3s infinite alternate;
        }
        @keyframes snakePulse {
            from { filter: brightness(1); }
            to { filter: brightness(1.2) drop-shadow(0 0 15px var(--neon-cyan)); }
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
            gap: 0.5rem;
            background: rgba(0,247,255,0.1);
            border: 1px solid var(--neon-cyan);
            border-radius: 50px;
            padding: 0.8rem 2rem;
            font-size: 1.2rem;
            color: var(--neon-cyan);
            text-decoration: none;
            transition: all 0.3s;
            backdrop-filter: blur(5px);
            font-weight: 500;
        }
        .connect-btn:hover {
            background: var(--neon-cyan);
            color: #000;
            box-shadow: 0 0 30px var(--neon-cyan);
            transform: translateY(-3px);
        }
        .connect-btn img {
            width: 24px;
            height: 24px;
        }

        /* ========== FOOTER ========== */
        .footer-wave {
            margin-top: 5rem;
        }
        .footer-wave img {
            width: 100%;
            display: block;
        }

        .footer-text {
            text-align: center;
            padding: 2rem;
            font-size: 1.5rem;
            color: var(--neon-cyan);
            animation: softPulse 2s infinite alternate;
        }
        @keyframes softPulse {
            from { opacity: 0.7; }
            to { opacity: 1; text-shadow: 0 0 10px var(--neon-cyan); }
        }

        /* ========== RESPONSIVE ========== */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.8rem;
            }
            .typing-container {
                font-size: 1.4rem;
            }
            .section-title {
                font-size: 2.2rem;
            }
        }
    </style>
</head>
<body>

    <!-- Background Effects -->
    <div class="particles"></div>
    <div class="orb orb1"></div>
    <div class="orb orb2"></div>

    <!-- ========== HERO ========== -->
    <header class="hero">
        <div class="fade-up">
            <h1>👋 Hey, I'm Inbarasan</h1>
        </div>
        <div class="typing-container fade-up">
            <span id="typed"></span>
        </div>
        <div class="profile-views fade-up">
            👁️ Profile Views: 1.2k+
        </div>
    </header>

    <!-- ========== ABOUT ME ========== -->
    <section class="container fade-up" id="about">
        <h2 class="section-title">🚀 About Me</h2>
        <div class="about-grid">
            <div class="about-text">
                <p>💻 <strong>Frontend Developer</strong> passionate about crafting beautiful, responsive web experiences.</p>
                <p>🌱 Currently diving deep into <span style="color:var(--neon-cyan);">React.js</span>, <span style="color:var(--neon-cyan);">Node.js</span>, <span style="color:var(--neon-cyan);">Express.js</span>, and <span style="color:var(--neon-cyan);">MongoDB</span>.</p>
                <p>🎯 Goal: Become a Professional <strong>MERN Stack Developer</strong>.</p>
                <p>🔥 I love building responsive websites, React applications, UI designs, and full-stack projects.</p>
                <p>📫 <strong>inbadharma2312@gmail.com</strong></p>
            </div>
            <div class="about-gif">
                <img src="https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif" alt="Coding gif" loading="lazy">
            </div>
        </div>
    </section>

    <!-- ========== TECH STACK ========== -->
    <section class="container fade-up">
        <h2 class="section-title">🚀 Tech Stack</h2>
        <div class="skills-grid">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=html" alt="HTML" title="HTML5">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=css" alt="CSS" title="CSS3">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=js" alt="JavaScript" title="JavaScript">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=react" alt="React" title="React">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=nodejs" alt="Node.js" title="Node.js">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=express" alt="Express" title="Express">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=mongodb" alt="MongoDB" title="MongoDB">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=bootstrap" alt="Bootstrap" title="Bootstrap">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=git" alt="Git" title="Git">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=github" alt="GitHub" title="GitHub">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=vscode" alt="VS Code" title="VS Code">
            <img class="skill-icon" src="https://skillicons.dev/icons?i=npm" alt="npm" title="npm">
        </div>
    </section>

    <!-- ========== FEATURED PROJECTS ========== -->
    <section class="container fade-up">
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
                    <li>✔ Cart Functionality</li>
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

    <!-- ========== LANGUAGES & TOOLS (Alternative display) ========== -->
    <section class="container fade-up">
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
    <section class="container fade-up">
        <h2 class="section-title">📊 GitHub Statistics</h2>
        <div class="stats-grid">
            <div class="stats-card">
                <img src="https://github-readme-stats.vercel.app/api?username=inbarasan23&show_icons=true&theme=tokyonight" alt="GitHub Stats" loading="lazy">
            </div>
            <div class="stats-card">
                <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=inbarasan23&layout=compact&theme=tokyonight" alt="Top Languages" loading="lazy">
            </div>
        </div>
        <div class="graph-container" style="text-align:center; margin-top:2rem;">
            <img src="https://github-readme-streak-stats.herokuapp.com/?user=inbarasan23&theme=tokyonight" alt="GitHub Streak" loading="lazy">
        </div>
    </section>

    <!-- ========== GITHUB TROPHIES ========== -->
    <section class="container fade-up">
        <h2 class="section-title">🏆 GitHub Trophies</h2>
        <div class="trophies-grid" style="text-align:center;">
            <img src="https://github-profile-trophy.vercel.app/?username=inbarasan23&theme=algolia&row=2&column=4" alt="Trophies" loading="lazy">
        </div>
    </section>

    <!-- ========== CONTRIBUTION GRAPH ========== -->
    <section class="container fade-up">
        <h2 class="section-title">📈 Contribution Graph</h2>
        <div class="graph-container">
            <img src="https://github-readme-activity-graph.vercel.app/graph?username=inbarasan23&theme=tokyo-night" alt="Contribution Graph" loading="lazy">
        </div>
    </section>

    <!-- ========== SNAKE EATING CONTRIBUTIONS ========== -->
    <section class="container fade-up">
        <h2 class="section-title">🐍 Snake Eating Contributions</h2>
        <div class="snake-animation">
            <img src="https://github.com/inbarasan23/inbarasan23/blob/output/github-contribution-grid-snake.svg" alt="Snake animation" loading="lazy">
        </div>
    </section>

    <!-- ========== CONNECT WITH ME ========== -->
    <section class="container fade-up">
        <h2 class="section-title">🌎 Connect With Me</h2>
        <div class="connect-buttons">
            <a href="mailto:inbadharma2312@gmail.com" class="connect-btn">
                <img src="https://skillicons.dev/icons?i=gmail" alt="Gmail"> Email
            </a>
            <a href="https://github.com/inbarasan23" target="_blank" class="connect-btn">
                <img src="https://skillicons.dev/icons?i=github" alt="GitHub"> GitHub
            </a>
        </div>
    </section>

    <!-- ========== FOOTER ========== -->
    <footer>
        <div class="footer-wave">
            <img src="https://capsule-render.vercel.app/api?type=waving&height=120&color=0:00F7FF,100:8A2BE2&section=footer" alt="wave">
        </div>
        <div class="footer-text">💙 Thanks for Visiting</div>
    </footer>

    <!-- ========== SCRIPTS ========== -->
    <script>
        // Typed.js dynamic text
        const typed = new Typed('#typed', {
            strings: [
                'Frontend Developer',
                'React Developer',
                'JavaScript Enthusiast',
                'Building Awesome Web Applications',
                'Always Learning New Technologies'
            ],
            typeSpeed: 60,
            backSpeed: 40,
            backDelay: 1500,
            loop: true,
            showCursor: true,
            cursorChar: '|',
        });

        // Intersection Observer for fade-up animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.2 });

        document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

        // Add a subtle 3D tilt effect to project cards on mouse move (desktop only)
        document.querySelectorAll('.project-card').forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                const rotateX = ((y - centerY) / centerY) * -8; // max 8deg
                const rotateY = ((x - centerX) / centerX) * 8;
                card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateY(-10px)`;
            });
            card.addEventListener('mouseleave', () => {
                card.style.transform = 'perspective(1000px) rotateX(0) rotateY(0) translateY(0)';
            });
        });
    </script>
</body>
</html>

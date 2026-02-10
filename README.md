<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shekhar Lalu Hotkar - Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-color: #00d4ff;
            --secondary-color: #7b2ff7;
            --accent-color: #f72585;
            --text-dark: #ffffff;
            --text-light: #b8c1ec;
            --bg-dark: #0a0e27;
            --card-bg: rgba(15, 23, 42, 0.8);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-dark);
            overflow-x: hidden;
            background: var(--bg-dark);
        }

        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .content-wrapper {
            position: relative;
            z-index: 1;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Navigation */
        .navbar {
            background: rgba(10, 14, 39, 0.9);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0, 212, 255, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .navbar .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 20px;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-light);
            font-weight: 500;
            transition: all 0.3s;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-color);
            transition: width 0.3s;
        }

        .nav-links a:hover {
            color: var(--primary-color);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .hamburger {
            display: none;
            flex-direction: column;
            cursor: pointer;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background: var(--primary-color);
            margin: 3px 0;
            transition: 0.3s;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 150px 0 100px;
        }

        .hero-content {
            text-align: center;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color), var(--accent-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: fadeInUp 1s ease;
        }

        .subtitle {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            color: var(--text-light);
            animation: fadeInUp 1s ease 0.2s both;
        }

        .description {
            font-size: 1.1rem;
            max-width: 700px;
            margin: 0 auto 2rem;
            color: var(--text-light);
            animation: fadeInUp 1s ease 0.4s both;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease 0.6s both;
        }

        .btn {
            padding: 14px 35px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            box-shadow: 0 5px 25px rgba(0, 212, 255, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 35px rgba(0, 212, 255, 0.5);
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
        }

        .btn-secondary:hover {
            background: var(--primary-color);
            color: white;
            transform: translateY(-3px);
        }

        .social-links {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            animation: fadeInUp 1s ease 0.8s both;
        }

        .social-links a {
            color: var(--text-light);
            font-size: 1.8rem;
            transition: all 0.3s;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.05);
        }

        .social-links a:hover {
            transform: translateY(-5px);
            color: var(--primary-color);
            background: rgba(0, 212, 255, 0.1);
        }

        /* Section Styles */
        section {
            padding: 100px 0;
            position: relative;
        }

        .section-title {
            text-align: center;
            font-size: 3rem;
            margin-bottom: 3rem;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
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
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            margin: 1rem auto 0;
            border-radius: 2px;
        }

        /* About Section */
        .about-text p {
            font-size: 1.2rem;
            color: var(--text-light);
            margin-bottom: 1.5rem;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            text-align: center;
        }

        .about-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat {
            text-align: center;
            padding: 2.5rem;
            background: var(--card-bg);
            border-radius: 20px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
            transition: all 0.3s;
        }

        .stat:hover {
            transform: translateY(-10px);
            border-color: var(--primary-color);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.3);
        }

        .stat h3 {
            font-size: 3rem;
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }

        .stat p {
            color: var(--text-light);
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .skill-category {
            background: var(--card-bg);
            padding: 2.5rem;
            border-radius: 20px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
            transition: all 0.3s;
        }

        .skill-category:hover {
            transform: translateY(-10px);
            border-color: var(--primary-color);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.3);
        }

        .skill-category h3 {
            color: var(--primary-color);
            margin-bottom: 1.5rem;
            font-size: 1.4rem;
        }

        .skill-category i {
            margin-right: 0.5rem;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
        }

        .tag {
            background: rgba(0, 212, 255, 0.1);
            padding: 0.6rem 1.2rem;
            border-radius: 25px;
            font-size: 0.9rem;
            color: var(--text-light);
            border: 1px solid rgba(0, 212, 255, 0.3);
            transition: all 0.3s;
        }

        .tag:hover {
            background: rgba(0, 212, 255, 0.2);
            border-color: var(--primary-color);
            color: var(--primary-color);
            transform: scale(1.05);
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            gap: 2.5rem;
        }

        .project-card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 2.5rem;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
            transition: all 0.3s;
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary-color);
            box-shadow: 0 15px 50px rgba(0, 212, 255, 0.3);
        }

        .project-header h3 {
            color: var(--primary-color);
            font-size: 1.8rem;
            margin-bottom: 1rem;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem;
            margin-bottom: 1.5rem;
        }

        .project-tech span {
            background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
            color: white;
            padding: 0.4rem 1rem;
            border-radius: 20px;
            font-size: 0.85rem;
            box-shadow: 0 3px 10px rgba(123, 47, 247, 0.3);
        }

        .project-body ul {
            list-style-position: inside;
            color: var(--text-light);
        }

        .project-body li {
            margin-bottom: 1rem;
            padding-left: 1rem;
        }

        /* Education Section */
        .education-content {
            max-width: 900px;
            margin: 0 auto;
        }

        .education-card {
            display: flex;
            gap: 2rem;
            background: var(--card-bg);
            padding: 2.5rem;
            border-radius: 20px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
            margin-bottom: 3rem;
            transition: all 0.3s;
        }

        .education-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.3);
        }

        .education-icon {
            font-size: 3.5rem;
            color: var(--primary-color);
        }

        .education-details h3 {
            color: var(--text-dark);
            margin-bottom: 0.5rem;
            font-size: 1.5rem;
        }

        .institution {
            font-weight: 600;
            color: var(--text-light);
        }

        .location, .duration, .grade {
            color: var(--text-light);
            font-size: 0.95rem;
        }

        .certifications h3 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--text-dark);
            text-align: center;
        }

        .cert-list {
            display: grid;
            gap: 1.5rem;
        }

        .cert-item {
            display: flex;
            gap: 1.5rem;
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 20px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
            transition: all 0.3s;
        }

        .cert-item:hover {
            transform: translateX(10px);
            border-color: var(--primary-color);
            box-shadow: 0 5px 30px rgba(0, 212, 255, 0.3);
        }

        .cert-item i {
            font-size: 2.5rem;
            color: var(--accent-color);
        }

        .cert-item h4 {
            color: var(--text-dark);
            margin-bottom: 0.3rem;
        }

        .cert-item p {
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .cert-desc {
            margin-top: 0.5rem;
        }

        /* Contact Section */
        .contact-content {
            max-width: 900px;
            margin: 0 auto;
        }

        .contact-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .contact-item {
            display: flex;
            gap: 1.5rem;
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 20px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
            transition: all 0.3s;
        }

        .contact-item:hover {
            transform: translateY(-10px);
            border-color: var(--primary-color);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.3);
        }

        .contact-item i {
            font-size: 2.5rem;
            color: var(--primary-color);
        }

        .contact-item h4 {
            margin-bottom: 0.5rem;
            color: var(--text-dark);
        }

        .contact-item a {
            color: var(--text-light);
            text-decoration: none;
            transition: color 0.3s;
        }

        .contact-item a:hover {
            color: var(--primary-color);
        }

        .contact-item p {
            color: var(--text-light);
        }

        /* Footer */
        .footer {
            background: rgba(10, 14, 39, 0.9);
            backdrop-filter: blur(10px);
            color: var(--text-light);
            text-align: center;
            padding: 2rem 0;
            border-top: 1px solid rgba(0, 212, 255, 0.2);
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-links {
                position: fixed;
                left: -100%;
                top: 70px;
                flex-direction: column;
                background: rgba(10, 14, 39, 0.98);
                backdrop-filter: blur(10px);
                width: 100%;
                text-align: center;
                transition: 0.3s;
                padding: 2rem 0;
                border-top: 1px solid rgba(0, 212, 255, 0.2);
            }

            .nav-links.active {
                left: 0;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .subtitle {
                font-size: 1.3rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .education-card {
                flex-direction: column;
            }

            .cert-item {
                flex-direction: column;
            }

            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div id="canvas-container"></div>
    <div class="content-wrapper">
    <!-- Navigation -->
    <nav class="navbar">
        <div class="container">
            <div class="logo">Shekhar Hotkar</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#education">Education</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Hi, I'm <span class="highlight">Shekhar Lalu Hotkar</span></h1>
                <p class="subtitle">Full-Stack Web Developer</p>
                <p class="description">Enthusiastic and detail-oriented Software Engineering student with hands-on experience in building full-stack web applications using React, Node.js, Express, and MongoDB.</p>
                <div class="hero-buttons">
                    <a href="#projects" class="btn btn-primary">View Projects</a>
                    <a href="#contact" class="btn btn-secondary">Contact Me</a>
                </div>
                <div class="social-links">
                    <a href="mailto:shekharhotkar2002@gmail.com" target="_blank"><i class="fas fa-envelope"></i></a>
                    <a href="https://github.com/Shekhar582-cyber" target="_blank"><i class="fab fa-github"></i></a>
                    <a href="tel:+919356670051"><i class="fas fa-phone"></i></a>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>I'm a passionate Software Engineering student from Sankh, India, currently pursuing my B.E. in Artificial Intelligence and Data Science at Government Engineering College Nargund.</p>
                    <p>I specialize in creating efficient, scalable, and user-friendly software solutions. I'm eager to contribute to teams and continue learning emerging technologies.</p>
                    <div class="about-stats">
                        <div class="stat">
                            <h3>3+</h3>
                            <p>Projects Completed</p>
                        </div>
                        <div class="stat">
                            <h3>4+</h3>
                            <p>Certifications</p>
                        </div>
                        <div class="stat">
                            <h3>8.1</h3>
                            <p>SGPA</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills">
        <div class="container">
            <h2 class="section-title">Skills</h2>
            <div class="skills-grid">
                <div class="skill-category">
                    <h3><i class="fas fa-code"></i> Programming</h3>
                    <div class="skill-tags">
                        <span class="tag">Java</span>
                        <span class="tag">JavaScript</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h3><i class="fas fa-laptop-code"></i> Web Technologies</h3>
                    <div class="skill-tags">
                        <span class="tag">HTML5</span>
                        <span class="tag">CSS3</span>
                        <span class="tag">React.js</span>
                        <span class="tag">Node.js</span>
                        <span class="tag">Express.js</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h3><i class="fas fa-database"></i> Databases</h3>
                    <div class="skill-tags">
                        <span class="tag">MongoDB</span>
                        <span class="tag">SQL</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h3><i class="fas fa-tools"></i> Tools</h3>
                    <div class="skill-tags">
                        <span class="tag">Git</span>
                        <span class="tag">GitHub</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects">
        <div class="container">
            <h2 class="section-title">Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-header">
                        <h3>Student Review System</h3>
                        <div class="project-tech">
                            <span>HTML</span>
                            <span>CSS</span>
                            <span>JavaScript</span>
                            <span>Node.js</span>
                            <span>Express</span>
                            <span>MongoDB</span>
                        </div>
                    </div>
                    <div class="project-body">
                        <ul>
                            <li>Built a web application where students submit feedback and ratings for teachers</li>
                            <li>Implemented REST endpoints using Node.js and Express to support create/read operations</li>
                            <li>Added basic JavaScript form validation and dynamic page updates</li>
                            <li>Designed a clean, responsive UI using HTML and CSS</li>
                        </ul>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <h3>CricketApp (GECN Premier League)</h3>
                        <div class="project-tech">
                            <span>Node.js</span>
                            <span>Express</span>
                            <span>MongoDB</span>
                            <span>HTML</span>
                            <span>CSS</span>
                            <span>JavaScript</span>
                        </div>
                    </div>
                    <div class="project-body">
                        <ul>
                            <li>Created a web-based system to manage cricket tournament details including teams, matches, schedules, and scores</li>
                            <li>Designed Express routes and APIs to handle match scheduling, results updates, and data retrieval</li>
                            <li>Used MongoDB for data storage and implemented basic frontend pages for viewing tournament information</li>
                            <li>Strengthened backend development skills and database connectivity through end-to-end implementation</li>
                        </ul>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <h3>Drip Agency Website</h3>
                        <div class="project-tech">
                            <span>HTML</span>
                            <span>CSS</span>
                            <span>JavaScript</span>
                        </div>
                    </div>
                    <div class="project-body">
                        <ul>
                            <li>Developed a static, responsive website for a digital agency with modern layout and structured sections</li>
                            <li>Implemented grid-based layouts and responsive styling using CSS for improved UX across devices</li>
                            <li>Added basic JavaScript interactivity to enhance navigation and page engagement</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Education Section -->
    <section id="education" class="education">
        <div class="container">
            <h2 class="section-title">Education & Certifications</h2>
            <div class="education-content">
                <div class="education-card">
                    <div class="education-icon">
                        <i class="fas fa-graduation-cap"></i>
                    </div>
                    <div class="education-details">
                        <h3>B.E. in Artificial Intelligence and Data Science</h3>
                        <p class="institution">Government Engineering College Nargund</p>
                        <p class="location">Nargund</p>
                        <p class="duration">12/2022 - 12/2026</p>
                        <p class="grade">Current SGPA: 8.1 / 10</p>
                    </div>
                </div>

                <div class="certifications">
                    <h3>Certifications</h3>
                    <div class="cert-list">
                        <div class="cert-item">
                            <i class="fas fa-certificate"></i>
                            <div>
                                <h4>Infosys Springboard - HTML5: The Language</h4>
                                <p>June 12, 2025</p>
                                <p class="cert-desc">Learned HTML structure, tags, attributes, semantics, and responsive webpage fundamentals</p>
                            </div>
                        </div>
                        <div class="cert-item">
                            <i class="fas fa-certificate"></i>
                            <div>
                                <h4>Infosys Springboard - CSS3</h4>
                                <p>June 20, 2025</p>
                                <p class="cert-desc">Practiced CSS selectors, box model, positioning, and responsive UI styling techniques</p>
                            </div>
                        </div>
                        <div class="cert-item">
                            <i class="fas fa-certificate"></i>
                            <div>
                                <h4>React.js for Beginners - Udemy</h4>
                                <p>September 6, 2025</p>
                                <p class="cert-desc">Learned React fundamentals including components, JSX, props, state, and reusable UI patterns</p>
                            </div>
                        </div>
                        <div class="cert-item">
                            <i class="fas fa-certificate"></i>
                            <div>
                                <h4>The Complete MySQL Bootcamp: Learn SQL Step by Step - Udemy</h4>
                                <p>October 21, 2025</p>
                                <p class="cert-desc">Covered SQL CRUD, joins, aggregations, subqueries, and database design concepts</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <div class="contact-content">
                <div class="contact-info">
                    <div class="contact-item">
                        <i class="fas fa-envelope"></i>
                        <div>
                            <h4>Email</h4>
                            <a href="mailto:shekharhotkar2002@gmail.com">shekharhotkar2002@gmail.com</a>
                        </div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-phone"></i>
                        <div>
                            <h4>Phone</h4>
                            <a href="tel:+919356670051">+91 9356670051</a>
                        </div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-map-marker-alt"></i>
                        <div>
                            <h4>Location</h4>
                            <p>Sankh, India</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <i class="fab fa-github"></i>
                        <div>
                            <h4>GitHub</h4>
                            <a href="https://github.com/Shekhar582-cyber" target="_blank">github.com/Shekhar582-cyber</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <p>&copy; 2026 Shekhar Lalu Hotkar. All rights reserved.</p>
        </div>
    </footer>

    <script src="script.js"></script>
</body>
</html>

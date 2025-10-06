<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Engineering Student Term-work Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* CSS Variables for Theming - Updated to match the application's theme (Deep Teal & Soft Grey) */
        :root {
            /* Deep Teal & Soft Grey Theme */
            --primary-color: #00796B; /* Deep Teal */
            --primary-dark: #004D40; /* Darker Teal for button hover */
            --primary-light: #4DB6AC; /* Light Teal variant */
            --secondary-color: #37474F; /* Dark Blue/Grey (Secondary) */
            --accent-color: #FF9800; /* Orange (for a contrasting accent, matching reports.html warning/badge color) */
            --light-bg: #F0F4F8; /* Soft Grey/Blue (Light Theme Background) */
            --light-text: #263238; /* Dark Text */
            --dark-bg: #263238; /* Dark Theme Background */
            --dark-text: #CFD8DC; /* Light Text for Dark Theme */
            --card-bg-light: #ffffff;
            --card-bg-dark: #37474F; /* Dark Card Background */
            --border-radius: 16px;
            --shadow: 0 6px 12px rgba(0,0,0,0.08); /* Updated shadow to match reports.html */
            --transition: all 0.3s ease;
            --spacing-xs: 0.25rem;
            --spacing-sm: 0.5rem;
            --spacing-md: 1rem;
            --spacing-lg: 1.5rem;
            --spacing-xl: 2rem;
            --spacing-xxl: 4rem;
            --font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
        }

        /* Dark Theme Variables */
        [data-theme="dark"] {
            --bg-color: var(--dark-bg);
            --text-color: var(--dark-text);
            --card-bg: var(--card-bg-dark);
            --border-color: #546E7A; /* Dark border color, matching reports.html */
        }

        /* Light Theme Variables */
        [data-theme="light"] {
            --bg-color: var(--light-bg);
            --text-color: var(--light-text);
            --card-bg: var(--card-bg-light);
            --border-color: #CFD8DC; /* Light border color, matching reports.html */
        }

        /* Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-family);
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            transition: var(--transition);
            overflow-x: hidden;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 var(--spacing-md);
        }

        /* Typography */
        h1, h2, h3, h4, h5, h6 {
            margin-bottom: var(--spacing-md);
            font-weight: 600;
            line-height: 1.2;
        }

        h1 {
            font-size: 2.5rem;
        }

        h2 {
            font-size: 2rem;
        }

        h3 {
            font-size: 1.5rem;
        }

        p {
            margin-bottom: var(--spacing-md);
        }

        /* Buttons */
        .btn {
            display: inline-block;
            padding: var(--spacing-sm) var(--spacing-md);
            border: none;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-weight: 500;
            transition: var(--transition);
            text-decoration: none;
            text-align: center;
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-primary:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
        }

        .btn-secondary {
            background-color: transparent;
            border: 2px solid var(--primary-color);
            color: var(--primary-color);
        }

        .btn-secondary:hover {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-lg {
            padding: var(--spacing-md) var(--spacing-lg);
            font-size: 1.1rem;
        }

        /* Navigation */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: var(--spacing-md) 0;
            position: sticky;
            top: 0;
            background-color: var(--bg-color);
            z-index: 100;
            transition: var(--transition);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: var(--spacing-sm);
            font-weight: 700;
            font-size: 1.5rem;
            color: var(--primary-color);
            text-decoration: none;
        }

        .nav-items {
            display: flex;
            align-items: center;
            gap: var(--spacing-md);
        }

        .nav-link {
            color: var(--text-color);
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
        }

        .nav-link:hover {
            color: var(--primary-color);
        }

        /* Hero Section */
        .hero {
            padding: var(--spacing-xxl) 0;
            display: flex;
            align-items: center;
            min-height: 80vh;
        }

        .hero .container {
            display: flex;
            align-items: center;
            gap: var(--spacing-xl);
        }

        .hero-content {
            flex: 1;
            max-width: 600px;
        }

        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .hero-image img {
            max-width: 100%;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
        }

        .hero-buttons {
            display: flex;
            gap: var(--spacing-md);
            margin-top: var(--spacing-lg);
        }

        /* Features Section */
        .features {
            padding: var(--spacing-xxl) 0;
            background-color: var(--card-bg);
        }

        .section-header {
            text-align: center;
            margin-bottom: var(--spacing-xl);
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: var(--spacing-lg);
        }

        .feature-card {
            background-color: var(--bg-color);
            border-radius: var(--border-radius);
            padding: var(--spacing-lg);
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 2.5rem;
            color: var(--primary-color);
            margin-bottom: var(--spacing-md);
        }

        /* How It Works Section */
        .how-it-works {
            padding: var(--spacing-xxl) 0;
        }

        .section-header {
            text-align: center;
            margin-bottom: var(--spacing-xl);
        }

        .steps {
            display: flex;
            flex-direction: column;
            gap: var(--spacing-xl);
            max-width: 800px;
            margin: 0 auto;
        }

        .step {
            display: flex;
            align-items: flex-start;
            gap: var(--spacing-lg);
        }

        .step-number {
            background-color: var(--primary-color);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            flex-shrink: 0;
        }

        /* Testimonials */
        .testimonials {
            padding: var(--spacing-xxl) 0;
            background-color: var(--card-bg);
        }

        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: var(--spacing-lg);
        }

        .testimonial-card {
            background-color: var(--bg-color);
            border-radius: var(--border-radius);
            padding: var(--spacing-lg);
            box-shadow: var(--shadow);
        }

        .testimonial-text {
            font-style: italic;
            margin-bottom: var(--spacing-md);
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            gap: var(--spacing-sm);
        }

        .author-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--primary-color);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
        }

        /* CTA Section */
        .cta {
            padding: var(--spacing-xxl) 0;
            text-align: center;
        }

        .cta-buttons {
            display: flex;
            justify-content: center;
            gap: var(--spacing-md);
            margin-top: var(--spacing-lg);
        }

        /* Footer */
        .footer {
            background-color: var(--card-bg);
            padding: var(--spacing-xl) 0;
            border-top: 1px solid var(--border-color);
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: var(--spacing-xl);
        }

        .footer-section h4 {
            margin-bottom: var(--spacing-md);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: var(--spacing-sm);
        }

        .footer-links a {
            color: var(--text-color);
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: var(--primary-color);
        }

        .copyright {
            text-align: center;
            margin-top: var(--spacing-xl);
            padding-top: var(--spacing-md);
            border-top: 1px solid var(--border-color);
        }

        /* Theme Toggle Switch */
        .theme-toggle {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 30px;
        }

        .theme-toggle input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 34px;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 22px;
            width: 22px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .slider {
            background-color: var(--primary-color);
        }

        input:checked + .slider:before {
            transform: translateX(30px);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero {
                flex-direction: column;
                text-align: center;
                gap: var(--spacing-xl);
            }

            .hero-buttons {
                justify-content: center;
            }

            .step {
                flex-direction: column;
                text-align: center;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .navbar {
                flex-direction: column;
                gap: var(--spacing-md);
            }
        }

        /* Utility Classes */
        .text-center {
            text-align: center;
        }

        .gradient-text {
            /* Updated to use primary and secondary for a consistent color scheme gradient */
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .hidden {
            display: none;
        }

        .mt-1 { margin-top: var(--spacing-xs); }
        .mt-2 { margin-top: var(--spacing-sm); }
        .mt-3 { margin-top: var(--spacing-md); }
        .mt-4 { margin-top: var(--spacing-lg); }
        .mt-5 { margin-top: var(--spacing-xl); }

        .mb-1 { margin-bottom: var(--spacing-xs); }
        .mb-2 { margin-bottom: var(--spacing-sm); }
        .mb-3 { margin-bottom: var(--spacing-md); }
        .mb-4 { margin-bottom: var(--spacing-lg); }
        .mb-5 { margin-bottom: var(--spacing-xl); }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <nav class="navbar">
                <a href="#" class="logo">
                    <i class="fas fa-graduation-cap"></i>
                    <span>TermWork Portal</span>
                </a>
                <div class="nav-items">
                    <a href="#features" class="nav-link">Features</a>
                    <a href="#how-it-works" class="nav-link">How It Works</a>
                    <a href="#testimonials" class="nav-link">Testimonials</a>
                    <label class="theme-toggle">
                        <input type="checkbox" id="theme-toggle">
                        <span class="slider"></span>
                    </label>
                    <a href="main.html" class="btn btn-primary">Login</a>
                </div>
            </nav>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Streamline Your <span class="gradient-text">Academic Term Work</span></h1>
                <p>A comprehensive portal designed for engineering students and faculty to manage assignments, labs, and internal marks efficiently.</p>
                <div class="hero-buttons">
                    <a href="main.html" class="btn btn-primary btn-lg">Get Started</a>
                    <a href="#features" class="btn btn-secondary btn-lg">Learn More</a>
                </div>
            </div>
            <div class="hero-image">
                <img src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Students collaborating">
            </div>
        </div>
    </section>

    <section class="features" id="features">
        <div class="container">
            <div class="section-header">
                <h2>Powerful Features for Academic Success</h2>
                <p>Our portal provides everything you need to manage term work efficiently</p>
            </div>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <h3>Performance Tracking</h3>
                    <p>Monitor your academic progress with detailed analytics and visual representations of your performance across subjects.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-edit"></i>
                    </div>
                    <h3>Easy Mark Management</h3>
                    <p>Teachers can easily add, edit, and manage student marks with our intuitive interface and validation system.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-file-export"></i>
                    </div>
                    <h3>Export & Reports</h3>
                    <p>Generate and export your academic records in multiple formats including CSV for further analysis.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <h3>Responsive Design</h3>
                    <p>Access your academic information from any device with our mobile-first, responsive design.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-palette"></i>
                    </div>
                    <h3>Customizable Themes</h3>
                    <p>Switch between light and dark modes based on your preference for comfortable viewing.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3>Secure Access</h3>
                    <p>Role-based access ensures students can only view their data while teachers have full management capabilities.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="how-it-works" id="how-it-works">
        <div class="container">
            <div class="section-header">
                <h2>How It Works</h2>
                <p>Simple steps to manage your academic term work</p>
            </div>
            <div class="steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <div>
                        <h3>Login to Your Account</h3>
                        <p>Access the portal using your credentials. Teachers and students have different interfaces tailored to their needs.</p>
                    </div>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <div>
                        <h3>Manage Your Data</h3>
                        <p>Teachers can add students, create term work items, and enter marks. Students can view their performance and export reports.</p>
                    </div>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <div>
                        <h3>Track & Analyze</h3>
                        <p>Monitor academic progress with visual analytics and performance metrics to identify areas for improvement.</p>
                    </div>
                </div>
                <div class="step">
                    <div class="step-number">4</div>
                    <div>
                        <h3>Export & Share</h3>
                        <p>Generate comprehensive reports and export them in various formats for record-keeping or further analysis.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="testimonials" id="testimonials">
        <div class="container">
            <div class="section-header">
                <h2>What Our Users Say</h2>
                <p>Hear from students and faculty who use our portal</p>
            </div>
            <div class="testimonial-grid">
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        "This portal has transformed how I manage student assessments. The intuitive interface saves me hours each week."
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">DR</div>
                        <div>
                            <h4>Dr. Robert Chen</h4>
                            <p>Professor, Computer Engineering</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        "As a student, I love being able to track my performance throughout the semester. The export feature is incredibly useful!"
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">SP</div>
                        <div>
                            <h4>Sarah Peterson</h4>
                            <p>Third Year, Mechanical Engineering</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        "The responsive design means I can check my grades on my phone between classes. It's so convenient!"
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">MJ</div>
                        <div>
                            <h4>Michael Johnson</h4>
                            <p>Second Year, Electrical Engineering</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="cta">
        <div class="container">
            <h2>Ready to Transform Your Academic Management?</h2>
            <p>Join hundreds of engineering students and faculty who are already using our portal</p>
            <div class="cta-buttons">
                <a href="main.html" class="btn btn-primary btn-lg">Login Now</a>
                <a href="#features" class="btn btn-secondary btn-lg">Explore Features</a>
            </div>
        </div>
    </section>

    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h4>TermWork Portal</h4>
                    <p>A comprehensive solution for managing engineering student term work, assignments, and internal marks.</p>
                </div>
                <div class="footer-section">
                    <h4>Quick Links</h4>
                    <ul class="footer-links">
                        <li><a href="#features">Features</a></li>
                        <li><a href="#how-it-works">How It Works</a></li>
                        <li><a href="#testimonials">Testimonials</a></li>
                        <li><a href="main.html">Login</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h4>Contact</h4>
                    <ul class="footer-links">
                        <li><i class="fas fa-envelope"></i> support@termworkportal.edu</li>
                        <li><i class="fas fa-phone"></i> +1 (555) 123-4567</li>
                        <li><i class="fas fa-map-marker-alt"></i> Engineering Building, University Campus</li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2023 Engineering Student Term-work Portal. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Theme Toggle Functionality
        document.addEventListener('DOMContentLoaded', function() {
            const themeToggle = document.getElementById('theme-toggle');
            const currentTheme = localStorage.getItem('theme') || 'light';

            // Set initial theme
            document.documentElement.setAttribute('data-theme', currentTheme);
            themeToggle.checked = currentTheme === 'dark';

            // Toggle theme when switch is clicked
            themeToggle.addEventListener('change', function() {
                const newTheme = this.checked ? 'dark' : 'light';
                document.documentElement.setAttribute('data-theme', newTheme);
                localStorage.setItem('theme', newTheme);
            });

            // Smooth scrolling for anchor links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href');
                    if (targetId === '#') return;

                    const targetElement = document.querySelector(targetId);
                    if (targetElement) {
                        window.scrollTo({
                            top: targetElement.offsetTop - 100,
                            behavior: 'smooth'
                        });
                    }
                });
            });

            // Navbar background on scroll
            window.addEventListener('scroll', function() {
                const navbar = document.querySelector('.navbar');
                if (window.scrollY > 50) {
                    navbar.style.backgroundColor = 'var(--card-bg)';
                    navbar.style.boxShadow = 'var(--shadow)';
                } else {
                    navbar.style.backgroundColor = 'var(--bg-color)';
                    navbar.style.boxShadow = 'none';
                }
            });
        });
    </script>
</body>
</html>

Main code:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login / Register - Engineering Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        :root {
            --primary-color: #006D77;    /* Deep Teal */
            --secondary-color: #83C5BE;  /* Light Teal */
            --accent-color: #E29578;     /* Coral */
            --danger-color: #E76F51;     /* Burnt Orange */
            --background-color: #EDF6F9; /* Light Blue-Gray */
            --text-color: #2C3E50;       /* Dark Blue-Gray */
            --card-bg: #FFFFFF;          /* White */
            --border-color: #B8D8D8;     /* Light Teal Border */
            --shadow: 0 0.125rem 0.25rem rgba(0, 109, 119, 0.15);
            --sidebar-width: 250px;
        }

        [data-theme="dark"] {
            --primary-color: #006D77;    /* Deep Teal */
            --secondary-color: #83C5BE;  /* Light Teal */
            --accent-color: #E29578;     /* Coral */
            --danger-color: #E76F51;     /* Burnt Orange */
            --background-color: #1A2327; /* Dark Blue-Gray */
            --text-color: #EDF6F9;      /* Light Blue-Gray */
            --card-bg: #2C3E50;         /* Dark Blue */
            --border-color: #006D77;    /* Deep Teal */
            --shadow: 0 0.125rem 0.25rem rgba(0, 109, 119, 0.25);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .auth-container {
            width: 90%;
            max-width: 450px;
            padding: 2rem 0;
        }

        .auth-card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 2rem;
            border-top: 5px solid var(--primary-color);
            transition: all 0.3s;
        }

        .auth-card h2 {
            text-align: center;
            color: var(--primary-color);
            margin-bottom: 1.5rem;
            font-weight: 600;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            font-size: 0.95rem;
        }

        input, select {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            background-color: var(--background-color);
            color: var(--text-color);
            transition: border-color 0.2s, box-shadow 0.2s;
        }

        input:focus, select:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.25);
        }

        .btn-auth {
            width: 100%;
            padding: 0.75rem;
            margin-top: 1.5rem;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            background-color: var(--primary-color);
            color: white;
            transition: background-color 0.2s;
        }

        .btn-auth:hover {
            background-color: #0056b3;
        }

        .toggle-link {
            text-align: center;
            margin-top: 1rem;
            font-size: 0.9rem;
        }

        .toggle-link a {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: 600;
        }
        
        .toggle-link a:hover {
            text-decoration: underline;
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body data-theme="light">
    <div class="auth-container">
        <div class="auth-card">
            <h2 id="formTitle">Login</h2>
            <form id="authForm">
                <div class="form-group hidden" id="registerFields">
                    <label for="name"><i class="fas fa-user"></i> Full Name</label>
                    <input type="text" id="name" placeholder="Enter your full name">
                </div>
                <div class="form-group hidden" id="roleField">
                    <label for="role"><i class="fas fa-user-tag"></i> I am a...</label>
                    <select id="role">
                        <option value="student">Student</option>
                        <option value="teacher">Teacher</option>
                    </select>
                </div>
                <div class="form-group hidden" id="rollNoField">
                    <label for="rollNo"><i class="fas fa-address-card"></i> Roll Number</label>
                    <input type="text" id="rollNo" placeholder="e.g., ENG001">
                </div>
                <div class="form-group hidden" id="confirmPasswordField">
                    <label for="confirmPassword"><i class="fas fa-lock"></i> Confirm Password</label>
                    <input type="password" id="confirmPassword" placeholder="Confirm your password">
                </div>

                <div class="form-group">
                    <label for="email"><i class="fas fa-envelope"></i> Email</label>
                    <input type="email" id="email" required placeholder="Enter your email">
                </div>
                <div class="form-group">
                    <label for="password"><i class="fas fa-lock"></i> Password</label>
                    <input type="password" id="password" required placeholder="Enter your password">
                </div>

                    <button type="submit" class="btn-auth" id="submitBtn">Login</button>
                </form>

                <div class="toggle-link">
                    <span id="toggleText">Don't have an account?</span>
                    <a href="#" id="toggleAuth">Register</a>
                </div>
                
                <!-- Loading indicator -->
                <div id="loadingIndicator" style="margin-top: 1rem; text-align: center; font-size: 0.9rem; color: var(--primary-color);">
                    <i class="fas fa-spinner fa-spin"></i> Loading system...
                </div>
                
                <!-- Debug information -->
                <div style="margin-top: 1rem; text-align: center; font-size: 0.8rem; opacity: 0.7;">
                    <button type="button" onclick="checkDatabaseStatus()" style="background: none; border: 1px solid #ccc; padding: 0.3rem 0.6rem; cursor: pointer;">Check Database Status</button>
                </div>
        </div>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        const authForm = document.getElementById('authForm');
        const formTitle = document.getElementById('formTitle');
        const submitBtn = document.getElementById('submitBtn');
        const toggleAuth = document.getElementById('toggleAuth');
        const toggleText = document.getElementById('toggleText');
        const registerFields = document.getElementById('registerFields');
        const roleField = document.getElementById('roleField');
        const rollNoField = document.getElementById('rollNoField');
        const confirmPasswordField = document.getElementById('confirmPasswordField');
        
        let isLogin = true;

        toggleAuth.addEventListener('click', (e) => {
            e.preventDefault();
            isLogin = !isLogin;
            
            const action = isLogin ? 'Login' : 'Register';
            
            formTitle.textContent = action;
            submitBtn.textContent = action;
            toggleText.textContent = isLogin ? "Don't have an account?" : "Already have an account?";
            toggleAuth.textContent = isLogin ? 'Register' : 'Login';

            // Toggle visibility of registration fields
            [registerFields, roleField, confirmPasswordField].forEach(el => 
                el.classList.toggle('hidden', isLogin)
            );
            
            // Handle Roll No visibility based on default role
            const roleSelect = document.getElementById('role');
            rollNoField.classList.toggle('hidden', isLogin || roleSelect.value !== 'student');
        });

        document.getElementById('role').addEventListener('change', function() {
            rollNoField.classList.toggle('hidden', this.value !== 'student');
        });

        authForm.addEventListener('submit', async (e) => {
            e.preventDefault();
            
            // Ensure database is loaded
            if (!window.db) {
                alert('System is initializing. Please wait a moment and try again.');
                return;
            }
            
            if (!window.db.data) {
                alert('Database is loading. Please try again in a moment.');
                return;
            }
            
            if (!window.db.data.users) {
                alert('User database is not available. Please refresh the page.');
                return;
            }
            
            console.log('Database status:', {
                hasDb: !!window.db,
                hasData: !!window.db.data,
                userCount: window.db.data?.users?.length || 0
            });
            
            const email = document.getElementById('email').value.trim();
            const password = document.getElementById('password').value;
            
            if (isLogin) {
                // --- LOGIN LOGIC ---
                try {
                    const user = window.db.login(email, password);
                    if (user) {
                        alert(`Login successful! Welcome, ${user.name}.`);
                        window.location.href = 'dashboard.html';
                    } else {
                        alert('Invalid email or password. Try:\nStudent: sarthak@engineering.edu / student123\nTeacher: priya.sharma@engineering.edu / teacher123');
                    }
                } catch (error) {
                    alert('Login error: ' + error.message);
                }
            } else {
                // --- REGISTRATION LOGIC ---
                const name = document.getElementById('name').value.trim();
                const role = document.getElementById('role').value;
                const rollNo = document.getElementById('rollNo').value.trim();
                const confirmPassword = document.getElementById('confirmPassword').value;

                if (!name || !email || !password || !confirmPassword) {
                    alert('All required fields must be filled.');
                    return;
                }

                if (role === 'student' && !rollNo) {
                    alert('Roll number is required for students.');
                    return;
                }
                
                if (password !== confirmPassword) {
                    alert('Passwords do not match');
                    return;
                }

                if (password.length < 6) {
                    alert('Password must be at least 6 characters long');
                    return;
                }
                
                try {
                    const userData = {
                        name,
                        email,
                        password,
                        role,
                        address: '',
                        phone: '',
                        department: role === 'student' ? 'Computer Science' : 'Computer Science'
                    };

                    if (role === 'student') {
                        userData.rollNo = rollNo;
                        userData.classId = null;
                        userData.dateOfBirth = '';
                        userData.enrollmentYear = new Date().getFullYear();
                    } else {
                        userData.employeeId = 'EMP' + String(Date.now()).slice(-6);
                        userData.qualification = '';
                        userData.experience = 0;
                        userData.dateOfJoining = new Date().toISOString().split('T')[0];
                    }

                    const newUser = window.db.register(userData);
                    alert(`Account created successfully! Welcome, ${newUser.name}`);
                    window.location.href = 'dashboard.html';
                } catch (error) {
                    alert('Registration error: ' + error.message);
                }
            }
        });

        // Debug function to check database status
        function checkDatabaseStatus() {
            console.log('=== Database Status Check ===');
            console.log('window.db exists:', !!window.db);
            console.log('window.db.data exists:', !!window.db?.data);
            console.log('window.db.data.users exists:', !!window.db?.data?.users);
            console.log('User count:', window.db?.data?.users?.length || 0);
            console.log('Current user:', window.db?.getCurrentUser());
            console.log('Sample users:', window.db?.data?.users?.slice(0, 2));
            
            const status = {
                hasDatabase: !!window.db,
                hasData: !!window.db?.data,
                hasUsers: !!window.db?.data?.users,
                userCount: window.db?.data?.users?.length || 0,
                currentUser: window.db?.getCurrentUser()?.name || 'None'
            };
            
            alert('Database Status:\n' + JSON.stringify(status, null, 2));
        }

        // Wait for database to be ready
        function waitForDatabase(callback) {
            const checkDatabase = () => {
                if (window.db && window.db.data && window.db.data.users) {
                    console.log('Database is ready!');
                    document.getElementById('loadingIndicator').style.display = 'none';
                    callback();
                } else {
                    setTimeout(checkDatabase, 100);
                }
            };
            checkDatabase();
        }

        // Check if user is already logged in
        document.addEventListener('DOMContentLoaded', () => {
            waitForDatabase(() => {
                const currentUser = window.db.getCurrentUser();
                if (currentUser) {
                    console.log('User already logged in, redirecting to dashboard...');
                    window.location.href = 'dashboard.html';
                } else {
                    console.log('No user logged in, staying on login page');
                }
            });
        });
    </script>
</body>
</html>

Dashboard Code:-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    
    <style>
        /* BASE & THEME VARIABLES - UPDATED */
        :root {
            --primary-color: #006D77;    /* Deep Teal */
            --secondary-color: #83C5BE;  /* Light Teal */
            --accent-color: #E29578;     /* Coral */
            --danger-color: #E76F51;     /* Burnt Orange */
            --background-color: #EDF6F9; /* Light Blue-Gray */
            --text-color: #2C3E50;       /* Dark Blue-Gray */
            --card-bg: #FFFFFF;          /* White */
            --border-color: #B8D8D8;     /* Light Teal Border */
            --shadow: 0 0.125rem 0.25rem rgba(0, 109, 119, 0.15);
            --sidebar-width: 250px;
        }

        [data-theme="dark"] {
            --primary-color: #006D77;    /* Deep Teal */
            --secondary-color: #83C5BE;  /* Light Teal */
            --accent-color: #E29578;     /* Coral */
            --danger-color: #E76F51;     /* Burnt Orange */
            --background-color: #1A2327; /* Dark Blue-Gray */
            --text-color: #EDF6F9;      /* Light Blue-Gray */
            --card-bg: #2C3E50;         /* Dark Blue */
            --border-color: #006D77;    /* Deep Teal */
            --shadow: 0 0.125rem 0.25rem rgba(0, 109, 119, 0.25);
        }

        /* RESET & TYPOGRAPHY */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        h1, h2, h3, h4 {
            color: var(--text-color);
        }

        /* LAYOUT CONTAINER */
        .app-container {
            display: flex;
        }

        /* SIDEBAR STYLES */
        .sidebar {
            width: var(--sidebar-width);
            height: 100vh;
            position: fixed;
            top: 0;
            left: 0;
            background-color: var(--card-bg);
            border-right: 1px solid var(--border-color);
            padding: 1.5rem 0;
            box-shadow: var(--shadow);
            overflow-y: auto;
            z-index: 1000;
        }

        .logo-section {
            padding: 0 1.5rem 1.5rem;
            text-align: center;
            border-bottom: 1px solid var(--border-color);
        }

        .logo-section h2 {
            font-size: 1.5rem;
            color: var(--primary-color);
            font-weight: 700;
        }

        .nav-menu {
            list-style: none;
            padding: 1rem 0;
        }

        .nav-item a {
            display: flex;
            align-items: center;
            padding: 0.75rem 1.5rem;
            color: var(--text-color);
            text-decoration: none;
            transition: background-color 0.2s, color 0.2s;
            font-weight: 500;
        }

        .nav-item a:hover {
            background-color: rgba(0, 109, 119, 0.1); /* Deep Teal with opacity */
            color: var(--primary-color);
        }
        
        .nav-item a.active {
            background-color: var(--primary-color);
            color: white;
            border-left: 5px solid var(--accent-color);
        }

        .nav-item i {
            margin-right: 1rem;
            font-size: 1.1rem;
        }
        
        /* MAIN CONTENT AREA */
        .main-content {
            margin-left: var(--sidebar-width);
            flex-grow: 1;
            padding: 2rem;
            transition: margin-left 0.3s;
        }

        /* TOP NAVBAR */
        .top-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 2rem;
        }

        .welcome-message h1 {
            font-size: 1.75rem;
            font-weight: 600;
            margin-bottom: 0.25rem;
        }
        
        .role-badge {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            background-color: var(--accent-color);
            color: white;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }
        
        .action-group {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 1.25rem;
            padding: 0.5rem;
            border-radius: 50%;
            transition: background-color 0.2s;
        }

        .icon-btn:hover {
            background-color: rgba(0, 0, 0, 0.05);
        }

        /* CARDS (Common component) */
        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid var(--border-color);
        }
        
        /* DASHBOARD SPECIFIC */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
        }

        .dashboard-card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 1.5rem;
            border-left: 5px solid var(--primary-color);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .dashboard-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.1);
        }

        .card-header {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
        }

        .card-icon {
            font-size: 1.8rem;
            margin-right: 1rem;
            color: var(--primary-color);
        }

        .card-title {
            font-size: 1.3rem;
            font-weight: 600;
        }

        .card-value {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary-color);
            margin-top: 0.5rem;
        }
        
        .card-subtext {
            font-size: 0.9rem;
            opacity: 0.7;
        }
        
        .progress-bar {
            background-color: var(--border-color);
            border-radius: 50px;
            height: 10px;
            margin-top: 10px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background-color: var(--accent-color);
            transition: width 0.5s ease;
        }

        /* BUTTONS (simplified for brevity) */
        .btn {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            transition: background-color 0.2s;
            margin-right: 0.5rem; 
        }

        .btn-primary { background-color: var(--primary-color); color: white; }
        .btn-secondary { background-color: var(--secondary-color); color: white; }
        .btn i { margin-right: 0.5rem; }

        .btn-primary:hover {
            background-color: #005a63; /* Darker Deep Teal */
        }

        .btn-secondary:hover {
            background-color: #6eb3ac; /* Darker Light Teal */
        }

        /* Update the dashboard card colors */
        .dashboard-grid .dashboard-card:nth-child(1) {
            border-left-color: var(--primary-color);
        }

        .dashboard-grid .dashboard-card:nth-child(2) {
            border-left-color: var(--secondary-color);
        }

        .dashboard-grid .dashboard-card:nth-child(3) {
            border-left-color: var(--accent-color);
        }

        .dashboard-grid .dashboard-card:nth-child(4) {
            border-left-color: var(--danger-color);
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .sidebar {
                width: 100%;
                height: auto;
                position: relative;
                border-right: none;
                border-bottom: 1px solid var(--border-color);
                padding: 1rem;
            }

            .nav-menu {
                display: flex;
                flex-wrap: wrap;
                justify-content: center;
                gap: 1rem;
            }
            
            .nav-item a {
                padding: 0.5rem 1rem;
                border-left: none !important;
                border-radius: 5px;
            }

            .main-content {
                margin-left: 0;
                padding: 1rem;
            }
            
            .top-navbar {
                flex-direction: column;
                align-items: flex-start;
                padding-bottom: 1rem;
                margin-bottom: 1rem;
            }
            
            .welcome-message {
                margin-bottom: 1rem;
            }
            
            .action-group {
                justify-content: space-between;
                width: 100%;
            }
            
            .grid-2 {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section">
                <h2>Engg Portal</h2>
            </div>
            <ul class="nav-menu">
                <li class="nav-item">
                    <a href="dashboard.html" class="active"><i class="fas fa-home"></i>Dashboard</a>
                </li>
                <li class="nav-item">
                    <a href="profile.html"><i class="fas fa-user-circle"></i>Profile</a>
                </li>
                <li class="nav-item teacher-only">
                    <a href="classes.html"><i class="fas fa-chalkboard-teacher"></i>Classes</a>
                </li>
                <li class="nav-item">
                    <a href="assignments.html"><i class="fas fa-tasks"></i>Assignments</a>
                </li>
                <li class="nav-item">
                    <a href="practicals.html"><i class="fas fa-flask"></i>Practicals</a>
                </li>
                <li class="nav-item">
                    <a href="attendance.html"><i class="fas fa-calendar-check"></i>Attendance</a>
                </li>
                <li class="nav-item">
                    <a href="reports.html"><i class="fas fa-chart-line"></i>Reports</a>
                </li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Welcome, <span id="userName">User</span>!</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme">
                        <i class="fas fa-sun"></i>
                    </button>
                    <button id="logoutBtn" class="icon-btn" title="Logout">
                        <i class="fas fa-sign-out-alt"></i>
                    </button>
                </div>
            </div>

            <h2>Dashboard Overview</h2>
            <div class="dashboard-grid" style="margin-top: 1.5rem;">
                <div class="dashboard-card" style="border-left-color: #007bff;">
                    <div class="card-header">
                        <i class="card-icon fas fa-graduation-cap" style="color: #007bff;"></i>
                        <h3 class="card-title">Current GPA</h3>
                    </div>
                    <div class="card-value" id="currentGpa">4.0</div>
                    <div class="card-subtext">Cumulative GPA (Latest Semester)</div>
                </div>

                <div class="dashboard-card" style="border-left-color: #28a745;">
                    <div class="card-header">
                        <i class="card-icon fas fa-check-circle" style="color: #28a745;"></i>
                        <h3 class="card-title">Attendance Rate</h3>
                    </div>
                    <div class="card-value" id="attendanceRate">92%</div>
                    <div class="progress-bar">
                        <div class="progress-fill" id="attendanceProgress" style="width: 92%; background-color: #28a745;"></div>
                    </div>
                </div>

                <div class="dashboard-card" id="dynamicCard" style="border-left-color: #ffc107;">
                    <div class="card-header">
                        <i class="card-icon fas fa-exclamation-triangle" style="color: #ffc107;"></i>
                        <h3 class="card-title" id="dynamicCardTitle">Pending Assignments</h3>
                    </div>
                    <div class="card-value" id="dynamicCardValue">3</div>
                    <div class="card-subtext" id="dynamicCardSubtext">Due in the next 7 days</div>
                </div>

                <div class="dashboard-card" style="border-left-color: #dc3545;">
                    <div class="card-header">
                        <i class="card-icon fas fa-calendar-alt" style="color: #dc3545;"></i>
                        <h3 class="card-title">Upcoming Event</h3>
                    </div>
                    <div class="card-value" style="font-size: 1.5rem; color: var(--text-color); font-weight: 500;">Thermodynamics Exam</div>
                    <div class="card-subtext">Date: <span id="upcomingDate">2025-10-15</span></div>
                </div>
            </div>
            
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.5rem; margin-top: 2rem;">
                <div class="card">
                    <h3><i class="fas fa-bolt"></i> Quick Actions</h3>
                    <div style="display: flex; flex-wrap: wrap; gap: 0.75rem; margin-top: 1rem;">
                        <a href="assignments.html" class="btn btn-primary"><i class="fas fa-upload"></i> Submit Work</a>
                        <a href="reports.html" class="btn btn-secondary"><i class="fas fa-chart-bar"></i> View Grades</a>
                        <a href="profile.html" class="btn btn-secondary"><i class="fas fa-cogs"></i> Update Profile</a>
                    </div>
                </div>

                <div class="card">
                    <h3><i class="fas fa-bullhorn"></i> Announcements</h3>
                    <ul style="list-style-type: none; padding-left: 0; margin-top: 1rem;">
                        <li style="margin-bottom: 0.5rem; font-size: 0.95rem;">
                            <span style="background-color:#ffc107; color:var(--text-color); padding: 0.2em 0.5em; border-radius: 4px; font-size: 0.8em; font-weight: 600; margin-right: 0.5rem;">NEW</span> Hostel Applications are open! (Due Nov 1)
                        </li>
                    </ul>
                </div>
            </div>

        </main>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        // --- COMMON CORE FUNCTIONS ---
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function applyTheme() {
            const currentTheme = localStorage.getItem('theme') || 'light';
            document.querySelector('.app-container').setAttribute('data-theme', currentTheme);
            const iconElement = document.getElementById('themeToggle') ? document.getElementById('themeToggle').querySelector('i') : null;
            if (iconElement) {
                iconElement.className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
            }
        }
        
        function applyUserRoleUI(user) {
            const userNameEl = document.getElementById('userName');
            const userRoleBadgeEl = document.getElementById('userRoleBadge');
            
            if (userNameEl) userNameEl.textContent = user.name;
            if (userRoleBadgeEl) userRoleBadgeEl.textContent = user.role.charAt(0).toUpperCase() + user.role.slice(1);
            
            const teacherLinks = document.querySelectorAll('.teacher-only');
            teacherLinks.forEach(el => el.style.display = user.role === 'teacher' ? 'block' : 'none');

            // DASHBOARD SPECIFIC: Update Dynamic Card Content
            const dynamicCard = document.getElementById('dynamicCard');
            if (user.role === 'teacher' && dynamicCard) {
                // Get actual student count from database
                const allStudents = window.db.getUsers('student');
                const teacherClasses = window.db.getClasses(user.id);
                let totalStudents = 0;
                teacherClasses.forEach(cls => {
                    if (cls.students) totalStudents += cls.students.length;
                });
                
                document.getElementById('dynamicCardTitle').textContent = 'Total Students';
                document.getElementById('dynamicCardValue').textContent = totalStudents; 
                document.getElementById('dynamicCardSubtext').textContent = 'Across all assigned classes';
                dynamicCard.querySelector('.card-icon').className = 'card-icon fas fa-users';
                dynamicCard.style.borderLeftColor = '#17a2b8'; 
            }
        }

        function loadDashboardData(user) {
            if (!window.db || !window.db.data) return;

            // Update GPA card
            const grades = window.db.getGrades(user.id);
            let totalGPA = 0;
            let gradeCount = 0;
            
            grades.forEach(grade => {
                if (grade.gpa) {
                    totalGPA += grade.gpa;
                    gradeCount++;
                }
            });

            const currentGPA = gradeCount > 0 ? (totalGPA / gradeCount).toFixed(1) : '4.0';
            document.getElementById('currentGpa').textContent = currentGPA;

            // Update attendance
            if (user.role === 'student') {
                const attendanceStats = window.db.getStudentAttendanceStats(user.id);
                const attendanceRate = attendanceStats.percentage;
                
                document.getElementById('attendanceRate').textContent = attendanceRate + '%';
                document.getElementById('attendanceProgress').style.width = attendanceRate + '%';

                // Update pending assignments
                const studentAssignments = window.db.getAssignments(null, user.id);
                const pendingAssignments = studentAssignments.filter(assignment => {
                    const hasSubmission = assignment.submissions.some(sub => sub.studentId === user.id);
                    const isPastDue = new Date(assignment.dueDate) < new Date();
                    return !hasSubmission && !isPastDue;
                });

                document.getElementById('dynamicCardValue').textContent = pendingAssignments.length;
            }

            // Load announcements
            loadAnnouncements(user);
        }

        function loadAnnouncements(user) {
            // Get recent notifications
            const notifications = window.db.getNotifications(user.id);
            const recentNotifications = notifications
                .filter(n => !n.read)
                .sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt))
                .slice(0, 3);

            const announcementsList = document.querySelector('.card ul');
            if (announcementsList && recentNotifications.length > 0) {
                announcementsList.innerHTML = '';
                recentNotifications.forEach(notification => {
                    const li = document.createElement('li');
                    li.style.marginBottom = '0.5rem';
                    li.style.fontSize = '0.95rem';
                    li.innerHTML = `
                        <span style="background-color:#ffc107; color:var(--text-color); padding: 0.2em 0.5em; border-radius: 4px; font-size: 0.8em; font-weight: 600; margin-right: 0.5rem;">NEW</span>
                        ${notification.message}
                    `;
                    announcementsList.appendChild(li);
                });
            }
        }
        
        // Initial setup on load
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initDashboard = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initDashboard, 100);
                    return;
                }

                const user = getCurrentUser();
                
                if (!user) {
                    alert('Please log in to access the portal.');
                    window.location.href = 'main.html'; 
                    return;
                }
                
                applyTheme();
                applyUserRoleUI(user);
                loadDashboardData(user);
                
                const themeToggle = document.getElementById('themeToggle');
                if (themeToggle) {
                    themeToggle.addEventListener('click', () => {
                        const currentTheme = document.querySelector('.app-container').getAttribute('data-theme');
                        const newTheme = currentTheme === 'light' ? 'dark' : 'light';
                        localStorage.setItem('theme', newTheme);
                        applyTheme();
                    });
                }

                const logoutBtn = document.getElementById('logoutBtn');
                if (logoutBtn) {
                    logoutBtn.addEventListener('click', () => {
                        if (confirm('Are you sure you want to log out?')) {
                            window.db.logout();
                            window.location.href = 'main.html'; 
                        }
                    });
                }
            };

            initDashboard();
        });
    </script>
</body>
</html>


Profile Code:- 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profile - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        /* (REMOVED: Paste the full Common CSS from dashboard.html here for external use) */
        /* ... Using embedded styles for completeness ... */
        :root {
    --primary-color: #006D77;    /* Deep Teal */
    --secondary-color: #83C5BE;  /* Light Teal */
    --accent-color: #E29578;     /* Coral */
    --danger-color: #E76F51;     /* Burnt Orange */
    --background-color: #EDF6F9; /* Light Blue-Gray */
    --text-color: #2C3E50;       /* Dark Blue-Gray */
    --card-bg: #FFFFFF;          /* White */
    --border-color: #B8D8D8;     /* Light Teal Border */
    --shadow: 0 0.125rem 0.25rem rgba(0, 109, 119, 0.15);
    --sidebar-width: 250px;
}

[data-theme="dark"] {
    --primary-color: #006D77;    /* Deep Teal */
    --secondary-color: #83C5BE;  /* Light Teal */
    --accent-color: #E29578;     /* Coral */
    --danger-color: #E76F51;     /* Burnt Orange */
    --background-color: #1A2327; /* Dark Blue-Gray */
    --text-color: #EDF6F9;      /* Light Blue-Gray */
    --card-bg: #2C3E50;         /* Dark Blue */
    --border-color: #006D77;    /* Deep Teal */
    --shadow: 0 0.125rem 0.25rem rgba(0, 109, 119, 0.25);
}
        /* ... Rest of Common CSS for layout, cards, buttons, forms, tables... */
        /* Only adding Profile-specific CSS here to save space, assuming the user copies full common CSS */
        
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: var(--background-color); color: var(--text-color); transition: background-color 0.3s, color 0.3s; min-height: 100vh; }
        h1, h2, h3, h4 { color: var(--text-color); }
        .app-container { display: flex; }
        .sidebar { width: var(--sidebar-width); height: 100vh; position: fixed; top: 0; left: 0; background-color: var(--card-bg); border-right: 1px solid var(--border-color); padding: 1.5rem 0; box-shadow: var(--shadow); overflow-y: auto; z-index: 1000; }
        .logo-section { padding: 0 1.5rem 1.5rem; text-align: center; border-bottom: 1px solid var(--border-color); }
        .logo-section h2 { font-size: 1.5rem; color: var(--primary-color); font-weight: 700; }
        .nav-menu { list-style: none; padding: 1rem 0; }
        .nav-item a { display: flex; align-items: center; padding: 0.75rem 1.5rem; color: var(--text-color); text-decoration: none; transition: background-color 0.2s, color 0.2s; font-weight: 500; }
        .nav-item a:hover {
    background-color: rgba(0, 109, 119, 0.1); /* Deep Teal with opacity */
    color: var(--primary-color);
}
        .nav-item a.active { background-color: var(--primary-color); color: white; border-left: 5px solid var(--accent-color); }
        .nav-item i { margin-right: 1rem; font-size: 1.1rem; }
        .main-content { margin-left: var(--sidebar-width); flex-grow: 1; padding: 2rem; transition: margin-left 0.3s; }
        .top-navbar { display: flex; justify-content: space-between; align-items: center; padding-bottom: 1.5rem; border-bottom: 1px solid var(--border-color); margin-bottom: 2rem; }
        .welcome-message h1 { font-size: 1.75rem; font-weight: 600; margin-bottom: 0.25rem; }
        .role-badge { display: inline-block; padding: 0.25rem 0.75rem; background-color: var(--accent-color); color: white; border-radius: 20px; font-size: 0.8rem; font-weight: 600; }
        .action-group { display: flex; gap: 1rem; align-items: center; }
        .icon-btn { background: none; border: none; color: var(--text-color); cursor: pointer; font-size: 1.25rem; padding: 0.5rem; border-radius: 50%; transition: background-color 0.2s; }
        .icon-btn:hover { background-color: rgba(0, 0, 0, 0.05); }
        .card { background-color: var(--card-bg); border-radius: 10px; box-shadow: var(--shadow); padding: 1.5rem; margin-bottom: 1.5rem; border: 1px solid var(--border-color); }
        .form-group { margin-bottom: 1rem; }
        label { display: block; margin-bottom: 0.5rem; font-weight: 600; font-size: 0.95rem; }
        input[type="text"], input[type="email"], input[type="password"], select, textarea { width: 100%; padding: 0.75rem 1rem; border: 1px solid var(--border-color); border-radius: 6px; background-color: var(--background-color); color: var(--text-color); transition: border-color 0.2s, box-shadow 0.2s; }
        input:focus, select:focus, textarea:focus { border-color: var(--primary-color); outline: none; box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.25); }
        .btn { padding: 0.75rem 1.5rem; border: none; border-radius: 6px; cursor: pointer; font-weight: 600; text-align: center; text-decoration: none; display: inline-flex; align-items: center; justify-content: center; transition: background-color 0.2s; margin-right: 0.5rem; }
        .btn-primary { background-color: var(--primary-color); color: white; }
        .btn-primary:hover {
    background-color: #005a63; /* Darker Deep Teal */
}
        .btn-secondary { background-color: var(--secondary-color); color: white; }
        .btn-secondary:hover {
    background-color: #6eb3ac; /* Darker Light Teal */
}
        .btn i { margin-right: 0.5rem; }
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; }
        
        /* Profile specific CSS */
        .profile-header-card {
            display: flex;
            align-items: center;
            margin-bottom: 2rem;
        }

        .profile-picture {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background-color: var(--primary-color);
            color: white;
            font-size: 3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 1.5rem;
            font-weight: 500;
            border: 4px solid var(--accent-color);
        }
        
        .profile-info h1 {
            margin-bottom: 0.25rem;
            font-size: 1.8rem;
        }
        
        .tab-menu {
            display: flex;
            border-bottom: 2px solid var(--border-color);
            margin-bottom: 1.5rem;
        }

        .tab-button {
            background: none;
            border: none;
            padding: 0.75rem 1.25rem;
            margin-right: 0.5rem;
            font-size: 1rem;
            cursor: pointer;
            color: var(--secondary-color);
            font-weight: 600;
            border-bottom: 3px solid transparent;
            transition: color 0.2s, border-bottom-color 0.2s;
        }

        .tab-button.active {
            color: var(--primary-color);
            border-bottom-color: var(--primary-color);
        }

        .tab-content.hidden {
            display: none;
        }
        
        @media (max-width: 992px) {
            /* ... Responsive overrides ... */
            .profile-header-card { flex-direction: column; text-align: center; }
            .profile-picture { margin-right: 0; margin-bottom: 1rem; }
            .main-content { margin-left: 0; padding: 1rem; }
            /* ... */
        }
    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section"><h2>Engg Portal</h2></div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="dashboard.html"><i class="fas fa-home"></i>Dashboard</a></li>
                <li class="nav-item"><a href="profile.html" class="active"><i class="fas fa-user-circle"></i>Profile</a></li>
                <li class="nav-item teacher-only"><a href="classes.html"><i class="fas fa-chalkboard-teacher"></i>Classes</a></li>
                <li class="nav-item"><a href="assignments.html"><i class="fas fa-tasks"></i>Assignments</a></li>
                <li class="nav-item"><a href="practicals.html"><i class="fas fa-flask"></i>Practicals</a></li>
                <li class="nav-item"><a href="attendance.html"><i class="fas fa-calendar-check"></i>Attendance</a></li>
                <li class="nav-item"><a href="reports.html"><i class="fas fa-chart-line"></i>Reports</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Profile Settings</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="addStudentBtn" class="btn btn-primary teacher-only" style="display: none;"><i class="fas fa-user-plus"></i> Add Student</button>
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme"><i class="fas fa-sun"></i></button>
                    <button id="logoutBtn" class="icon-btn" title="Logout"><i class="fas fa-sign-out-alt"></i></button>
                </div>
            </div>
            
            <div class="card profile-header-card">
                <div class="profile-picture" id="profilePicture">S</div>
                <div class="profile-info">
                    <h1 class="profile-name" id="userName">User Name</h1>
                    <p id="userEmail" style="opacity: 0.8;">user@email.com</p>
                    <p class="role-badge" style="background-color: var(--secondary-color); margin-top: 0.5rem; display: inline-block;">
                        <i class="fas fa-id-badge"></i> <span id="userRollNo">ENG001</span>
                    </p>
                    <button class="btn btn-secondary" id="changePhotoBtn" style="margin-top: 1rem;"><i class="fas fa-camera"></i> Change Photo</button>
                </div>
            </div>

            <div class="tab-menu">
                <button class="tab-button active" data-tab="personal"><i class="fas fa-info-circle"></i> Personal Info</button>
                <button class="tab-button" data-tab="security"><i class="fas fa-lock"></i> Security</button>
                <button class="tab-button" data-tab="preferences"><i class="fas fa-cog"></i> Preferences</button>
            </div>

            <div class="tab-content" id="personal">
                <div class="card">
                    <h3>Update Personal Information</h3>
                    <form id="personalInfoForm" style="margin-top: 1rem;">
                        <div class="grid-2">
                            <div class="form-group"><label for="fullName">Full Name</label><input type="text" id="fullName" required></div>
                            <div class="form-group"><label for="rollNo">Roll Number</label><input type="text" id="rollNo" readonly></div>
                        </div>
                        <div class="form-group"><label for="email">Email Address</label><input type="email" id="email" required></div>
                        <div class="form-group"><label for="address">Mailing Address / Bio</label><textarea id="address" rows="3"></textarea></div>
                        <button type="submit" class="btn btn-primary"><i class="fas fa-save"></i> Save Changes</button>
                    </form>
                </div>
            </div>

            <div class="tab-content hidden" id="security">
                <div class="card">
                    <h3>Change Password</h3>
                    <form id="securityForm" style="margin-top: 1rem;">
                        <div class="form-group"><label for="currentPassword">Current Password</label><input type="password" id="currentPassword" required></div>
                        <div class="form-group"><label for="newPassword">New Password</label><input type="password" id="newPassword" required></div>
                        <div class="form-group"><label for="confirmNewPassword">Confirm New Password</label><input type="password" id="confirmNewPassword" required></div>
                        <button type="submit" class="btn btn-primary"><i class="fas fa-key"></i> Update Password</button>
                    </form>
                </div>

                <div class="card" style="border-color: var(--danger-color);">
                    <h3 style="color: var(--danger-color);">Delete Account</h3>
                    <p style="margin-top: 0.5rem; margin-bottom: 1rem; opacity: 0.8;">
                        This action is irreversible. All your data, including assignments, grades, and personal information, will be permanently deleted.
                    </p>
                    <button id="deleteAccountBtn" class="btn" style="background-color: var(--danger-color); color: white;"><i class="fas fa-trash-alt"></i> Delete My Account</button>
                </div>
            </div>

            <div class="tab-content hidden" id="preferences">
                <div class="card">
                    <h3>Portal Preferences</h3>
                    <form id="preferencesForm" style="margin-top: 1rem;">
                        <div class="form-group"><label for="notification">Email Notifications</label><select id="notification"><option value="immediate">Immediate</option><option value="daily">Daily Digest</option><option value="off">Off</option></select></div>
                        <div class="form-group"><label for="language">Portal Language</label><select id="language"><option value="en">English</option><option value="hi">Hindi</option></select></div>
                        <div class="form-group"><label>Theme</label><p style="font-size: 0.9rem; opacity: 0.7;">(Toggle using the icon in the top right.)</p></div>
                        <button type="submit" class="btn btn-primary"><i class="fas fa-save"></i> Save Preferences</button>
                    </form>
                </div>
            </div>
            
        </main>
    </div>

    <!-- Add Student Modal -->
    <div id="addStudentModal" class="modal" style="display: none;">
        <div class="modal-content" style="max-width: 600px;">
            <div class="modal-header">
                <h3>Add New Student</h3>
                <button class="icon-btn" onclick="document.getElementById('addStudentModal').style.display='none'"><i class="fas fa-times"></i></button>
            </div>
            <form id="addStudentForm" style="margin-top: 1rem;">
                <div class="grid-2">
                    <div class="form-group"><label for="studentName">Full Name</label><input type="text" id="studentName" required></div>
                    <div class="form-group"><label for="studentEmail">Email</label><input type="email" id="studentEmail" required></div>
                </div>
                <div class="grid-2">
                    <div class="form-group"><label for="studentPassword">Password</label><input type="password" id="studentPassword" required></div>
                    <div class="form-group"><label for="studentRollNo">Roll Number</label><input type="text" id="studentRollNo" required></div>
                </div>
                <div class="grid-2">
                    <div class="form-group"><label for="studentDepartment">Department</label><input type="text" id="studentDepartment" required></div>
                    <div class="form-group"><label for="studentEnrollmentYear">Enrollment Year</label><input type="number" id="studentEnrollmentYear" required></div>
                </div>
                <button type="submit" class="btn btn-primary"><i class="fas fa-plus-circle"></i> Add Student</button>
            </form>
        </div>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        // --- COMMON CORE FUNCTIONS ---
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function applyTheme() {
            const currentTheme = localStorage.getItem('theme') || 'light';
            document.querySelector('.app-container').setAttribute('data-theme', currentTheme);
            const iconElement = document.getElementById('themeToggle') ? document.getElementById('themeToggle').querySelector('i') : null;
            if (iconElement) { iconElement.className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon'; }
        }
        
        function applyUserRoleUI(user) {
            const userNameEl = document.getElementById('userName');
            const userRoleBadgeEl = document.getElementById('userRoleBadge');
            
            if (userNameEl) userNameEl.textContent = user.name;
            if (userRoleBadgeEl) userRoleBadgeEl.textContent = user.role.charAt(0).toUpperCase() + user.role.slice(1);
            
            const teacherLinks = document.querySelectorAll('.teacher-only');
            teacherLinks.forEach(el => el.style.display = user.role === 'teacher' ? 'block' : 'none');
        }
        
        // --- PROFILE SPECIFIC FUNCTIONS ---
        function loadProfileData() {
            const user = getCurrentUser();
            if (!user) return;
            
            document.getElementById('profilePicture').textContent = user.name.charAt(0);
            document.getElementById('userName').textContent = user.name;
            document.getElementById('userEmail').textContent = user.email || 'N/A';
            document.getElementById('userRollNo').textContent = user.rollNo || user.employeeId || user.role.toUpperCase();

            document.getElementById('fullName').value = user.name || '';
            document.getElementById('rollNo').value = user.rollNo || user.employeeId || '';
            document.getElementById('email').value = user.email || '';
            document.getElementById('address').value = user.address || '';
        }

        function handleTabSwitching() {
            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');

            tabButtons.forEach(button => {
                button.addEventListener('click', () => {
                    tabButtons.forEach(btn => btn.classList.remove('active'));
                    tabContents.forEach(content => content.classList.add('hidden'));

                    button.classList.add('active');
                    const tabId = button.getAttribute('data-tab');
                    document.getElementById(tabId).classList.remove('hidden');
                });
            });
        }
        
        // Initial setup on load
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initProfile = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initProfile, 100);
                    return;
                }

                const user = getCurrentUser();
                
                if (!user) { 
                    alert('Please log in to access the portal.'); 
                    window.location.href = 'main.html'; 
                    return; 
                }
                
                applyTheme();
                applyUserRoleUI(user);
                loadProfileData();
                handleTabSwitching();
                
                // Event Listeners
                document.getElementById('themeToggle').addEventListener('click', () => {
                    const currentTheme = document.querySelector('.app-container').getAttribute('data-theme');
                    const newTheme = currentTheme === 'light' ? 'dark' : 'light';
                    localStorage.setItem('theme', newTheme);
                    applyTheme();
                });

                document.getElementById('logoutBtn').addEventListener('click', () => {
                    if (confirm('Are you sure you want to log out?')) { 
                        window.db.logout(); 
                        window.location.href = 'main.html'; 
                    }
                });
                
                // Form submission handlers
                document.getElementById('personalInfoForm').addEventListener('submit', (e) => { 
                    e.preventDefault(); 
                    const user = getCurrentUser();
                    const updates = {
                        name: document.getElementById('fullName').value,
                        email: document.getElementById('email').value,
                        address: document.getElementById('address').value
                    };
                    
                    const success = window.db.updateUser(user.id, updates);
                    if (success) {
                        // Update current user in localStorage
                        const updatedUser = { ...user, ...updates };
                        localStorage.setItem('currentUser', JSON.stringify(updatedUser));
                        window.db.currentUser = updatedUser;
                        
                        loadProfileData();
                        alert('Personal info saved successfully!');
                    } else {
                        alert('Error saving personal info.');
                    }
                });
                
                document.getElementById('deleteAccountBtn').addEventListener('click', () => {
                    const user = getCurrentUser();
                    if (confirm(`Are you absolutely sure you want to delete your account, ${user.name}? This action cannot be undone.`)) {
                        if (prompt('To confirm, please type "DELETE" in the box below.') === 'DELETE') {
                            const success = window.db.deleteUser(user.id);
                            if (success) {
                                alert('Account deleted successfully.');
                                window.db.logout();
                                window.location.href = 'main.html';
                            } else {
                                alert('Error deleting account.');
                            }
                        } else {
                            alert('Deletion cancelled. Incorrect confirmation text.');
                        }
                    }
                });

                document.getElementById('securityForm').addEventListener('submit', (e) => { 
                    e.preventDefault(); 
                    const currentPassword = document.getElementById('currentPassword').value;
                    const newPassword = document.getElementById('newPassword').value;
                    const confirmPassword = document.getElementById('confirmNewPassword').value;
                    
                    const user = getCurrentUser();
                    
                    if (user.password !== currentPassword) {
                        alert('Current password is incorrect.');
                        return;
                    }
                    
                    if (newPassword !== confirmPassword) {
                        alert('New passwords do not match.');
                        return;
                    }
                    
                    if (newPassword.length < 6) {
                        alert('Password must be at least 6 characters long.');
                        return;
                    }
                    
                    const success = window.db.updateUser(user.id, { password: newPassword });
                    if (success) {
                        alert('Password updated successfully!');
                        document.getElementById('securityForm').reset();
                    } else {
                        alert('Error updating password.');
                    }
                });
                
                document.getElementById('preferencesForm').addEventListener('submit', (e) => { 
                    e.preventDefault(); 
                    alert('Preferences saved successfully!'); 
                });
                
                document.getElementById('changePhotoBtn').addEventListener('click', function() { 
                    alert('Photo change functionality would be implemented here'); 
                });

                // Add student functionality
                const addStudentBtn = document.getElementById('addStudentBtn');
                const addStudentModal = document.getElementById('addStudentModal');
                if(addStudentBtn) {
                    addStudentBtn.addEventListener('click', () => {
                        addStudentModal.style.display = 'flex';
                    });
                }

                document.getElementById('addStudentForm').addEventListener('submit', (e) => {
                    e.preventDefault();
                    const newStudent = {
                        name: document.getElementById('studentName').value,
                        email: document.getElementById('studentEmail').value,
                        password: document.getElementById('studentPassword').value,
                        role: 'student',
                        rollNo: document.getElementById('studentRollNo').value,
                        department: document.getElementById('studentDepartment').value,
                        enrollmentYear: parseInt(document.getElementById('studentEnrollmentYear').value),
                        createdAt: new Date().toISOString(),
                        lastLogin: new Date().toISOString()
                    };

                    const success = window.db.addUser(newStudent);
                    if (success) {
                        alert('Student added successfully!');
                        document.getElementById('addStudentForm').reset();
                        addStudentModal.style.display = 'none';
                    } else {
                        alert('Error adding student. A user with this email or roll number may already exist.');
                    }
                });
            };

            initProfile();
        });
    </script>
</body>
</html>



Class Code :-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Class Management - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        /* [SHARED CSS BLOCK START] - POLISHED DEEP TEAL THEME */
        :root {
            /* Deep Teal & Soft Grey Theme */
            --primary-color: #00796B; 
            --secondary-color: #37474F; 
            --background-color: #F0F4F8; 
            --text-color: #263238; 
            --card-bg: #ffffff;
            --border-color: #CFD8DC; 
            --shadow: 0 6px 12px rgba(0,0,0,0.08); 
            --success-color: #4CAF50;
            --warning-color: #FF9800;
            --error-color: #F44336;
        }

        [data-theme="dark"] {
            --primary-color: #4DB6AC; 
            --secondary-color: #1A1E20; 
            --background-color: #263238; 
            --text-color: #CFD8DC; 
            --card-bg: #37474F; 
            --border-color: #546E7A; 
            --shadow: 0 6px 12px rgba(0,0,0,0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        /* --- Application Layout (Sidebar/Main Content) --- */
        .app-container {
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 250px;
            background-color: var(--secondary-color);
            color: white;
            padding: 1rem 0;
            box-shadow: 2px 0 10px rgba(0,0,0,0.15);
            flex-shrink: 0;
        }

        .logo-section {
            padding: 0 1.5rem 1rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 1rem;
        }

        .nav-menu {
            list-style: none;
        }

        .nav-item a {
            display: flex; 
            align-items: center;
            padding: 0.85rem 1.5rem; 
            color: white;
            text-decoration: none;
            transition: background-color 0.2s;
        }
        
        .nav-item a i {
            margin-right: 10px;
            font-size: 1.1rem;
        }

        .nav-item a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .nav-item .active {
            background-color: var(--primary-color);
            font-weight: bold;
        }

        .main-content {
            flex-grow: 1;
            padding: 2.5rem; 
            width: calc(100% - 250px);
        }

        /* --- Components & Utility Styles --- */
        .top-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1.25rem; 
            border-bottom: 1px solid var(--border-color);
        }

        .welcome-message {
            display: flex; 
            align-items: baseline;
            gap: 15px;
        }
        
        .welcome-message h1 {
            font-size: 2rem;
            font-weight: 300;
        }

        .role-badge {
            display: inline-block;
            padding: 0.3rem 1rem;
            background-color: var(--primary-color);
            color: white;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 2rem; 
            margin-bottom: 1.5rem;
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
        }

        .data-table th, .data-table td {
            padding: 1.1rem 1rem; 
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        .data-table th {
            background-color: var(--background-color);
            font-weight: 600;
        }
        
        .data-table tbody tr:hover {
            background-color: rgba(0, 121, 107, 0.05); 
        }

        .btn {
            color: white;
            border: none;
            padding: 0.6rem 1.2rem; 
            border-radius: 6px;
            cursor: pointer;
            text-decoration: none;
            display: inline-flex; 
            align-items: center;
            gap: 5px;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.1s;
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        .btn-primary { background-color: var(--primary-color); }
        .btn-secondary { background-color: var(--secondary-color); }
        .btn-success { background-color: var(--success-color); }
        .btn-danger { background-color: var(--error-color); }

        .badge {
            padding: 0.4em 0.8em; 
            border-radius: 4px;
            font-weight: 600;
            line-height: 1.2;
            color: white;
        }

        .badge-success { background-color: var(--success-color); }
        .badge-warning { background-color: var(--warning-color); }
        .badge-danger { background-color: var(--error-color); }
        .badge-info { background-color: var(--primary-color); }
        .badge-secondary { background-color: var(--secondary-color); }
        
        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 1.4rem; 
            margin-left: 0.75rem;
            transition: color 0.2s;
        }

        .icon-btn:hover {
            color: var(--primary-color);
        }
        
        .form-control {
            padding: 0.7rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: var(--background-color);
            color: var(--text-color);
            transition: border-color 0.2s;
            width: 100%;
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
        }
        /* [SHARED CSS BLOCK END] */

        /* CLASSES SPECIFIC STYLES */
        .class-status-details {
            display: flex;
            gap: 2rem;
            margin-bottom: 2rem;
        }
        
        .class-status-box {
            background-color: var(--card-bg);
            padding: 1rem;
            border-radius: 8px;
            box-shadow: var(--shadow);
            flex-grow: 1;
            text-align: center;
        }
        
        /* Modal Styles */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6); 
            display: none; 
            align-items: center;
            justify-content: center;
            z-index: 2000;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background-color: var(--card-bg);
            padding: 3rem; 
            border-radius: 10px;
            width: 90%;
            max-width: 800px; 
            box-shadow: var(--shadow);
            color: var(--text-color);
            max-height: 90vh; 
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 1rem; 
        }
        
        .modal-header h3 {
            font-size: 1.5rem;
        }
    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section"><h2>Engg Portal</h2></div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="dashboard.html" id="nav-dashboard"><i class="fas fa-home"></i>Dashboard</a></li>
                <li class="nav-item"><a href="profile.html" id="nav-profile"><i class="fas fa-user-circle"></i>Profile</a></li>
                <li class="nav-item"><a href="classes.html" id="nav-classes" class="active"><i class="fas fa-chalkboard-teacher"></i>Classes</a></li>
                <li class="nav-item"><a href="assignments.html" id="nav-assignments"><i class="fas fa-tasks"></i>Assignments</a></li>
                <li class="nav-item"><a href="practicals.html" id="nav-practicals"><i class="fas fa-flask"></i>Practicals</a></li>
                <li class="nav-item"><a href="attendance.html" id="nav-attendance"><i class="fas fa-calendar-check"></i>Attendance</a></li>
                <li class="nav-item"><a href="reports.html" id="nav-reports"><i class="fas fa-chart-line"></i>Reports</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Class Management</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme"><i class="fas fa-sun"></i></button>
                    <button id="logoutBtn" class="icon-btn" title="Logout"><i class="fas fa-sign-out-alt"></i></button>
                </div>
            </div>
            
            <div id="teacherView" style="display: none;">
                <div class="card-header">
                    <h2>Classes I Teach</h2>
                    <button class="btn btn-primary" onclick="document.getElementById('newClassModal').classList.add('active')"><i class="fas fa-plus-circle"></i> Create New Class</button>
                </div>
            </div>

            <div class="card">
                <div class="table-responsive">
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th>Class Name</th>
                                <th>Course Code</th>
                                <th>Schedule</th>
                                <th id="tableHeaderStudents">Students</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="classesTableBody">
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Student Manager Modal -->
            <div id="studentManagerModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3 id="modalClassTitle">Students in [Class Name]</h3>
                        <button class="icon-btn" onclick="document.getElementById('studentManagerModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    
                    <div style="margin-bottom: 1rem;">
                        <form id="addStudentForm" style="display: flex; gap: 10px;">
                            <input type="text" id="studentRollNo" class="form-control" placeholder="Enter Student Roll No (e.g., E2021004)" required style="flex-grow: 1;">
                            <button type="submit" class="btn btn-success"><i class="fas fa-user-plus"></i> Add Student</button>
                        </form>
                    </div>
                    
                    <div class="table-responsive">
                        <table class="data-table">
                            <thead>
                                <tr>
                                    <th>Roll No</th>
                                    <th>Name</th>
                                    <th>Action</th>
                                </tr>
                            </thead>
                            <tbody id="studentListTableBody">
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

            <!-- New Class Modal -->
            <div id="newClassModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3>Create New Class</h3>
                        <button class="icon-btn" onclick="document.getElementById('newClassModal').classList.remove('active')">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                    <form id="newClassForm">
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                            <div style="grid-column: 1 / -1;">
                                <label for="className">Class Name</label>
                                <input type="text" id="className" class="form-control" required>
                            </div>
                            <div>
                                <label for="classCode">Course Code</label>
                                <input type="text" id="classCode" class="form-control" required>
                            </div>
                            <div>
                                <label for="classDepartment">Department</label>
                                <input type="text" id="classDepartment" class="form-control" required>
                            </div>
                            <div>
                                <label for="classSchedule">Schedule</label>
                                <input type="text" id="classSchedule" class="form-control" placeholder="e.g., Mon/Wed 10:00-11:30" required>
                            </div>
                            <div>
                                <label for="classRoom">Room</label>
                                <input type="text" id="classRoom" class="form-control" required>
                            </div>
                             <div>
                                <label for="classSemester">Semester</label>
                                <input type="text" id="classSemester" class="form-control" placeholder="e.g., Fall 2025" required>
                            </div>
                            <div>
                                <label for="classCredits">Credits</label>
                                <input type="number" id="classCredits" class="form-control" required>
                            </div>
                             <div>
                                <label for="classMaxStudents">Max Students</label>
                                <input type="number" id="classMaxStudents" class="form-control" required>
                            </div>
                            <div style="grid-column: 1 / -1;">
                                <label for="classDescription">Description</label>
                                <textarea id="classDescription" class="form-control" rows="3"></textarea>
                            </div>
                            <div style="grid-column: 1 / -1; text-align: right;">
                                <button type="submit" class="btn btn-primary">
                                    <i class="fas fa-plus-circle"></i> Create Class
                                </button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>

        </main>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        /* [SHARED JAVASCRIPT BLOCK START] */
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function setupUserUI(user) {
            document.getElementById('userRoleBadge').textContent = user.role === 'teacher' ? 'Teacher' : 'Student';
            document.getElementById('teacherView').style.display = user.role === 'teacher' ? 'block' : 'none';
            document.getElementById('tableHeaderStudents').textContent = user.role === 'teacher' ? 'Students' : 'Teacher';
        }
        
        function setActiveNavLink(page) {
            document.querySelectorAll('.nav-menu a').forEach(link => {
                link.classList.remove('active');
            });
            const activeLink = document.getElementById(`nav-${page}`);
            if (activeLink) {
                activeLink.classList.add('active');
            }
        }
        
        // Theme Toggle
        const themeToggle = document.getElementById('themeToggle');
        const appContainer = document.querySelector('.app-container');
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        appContainer.setAttribute('data-theme', currentTheme);
        themeToggle.querySelector('i').className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        themeToggle.addEventListener('click', () => {
            const newTheme = appContainer.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            appContainer.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            themeToggle.querySelector('i').className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        });

        // Logout Functionality
        document.getElementById('logoutBtn').addEventListener('click', () => {
            if (confirm('Are you sure you want to logout?')) {
                window.db.logout();
                window.location.href = 'main.html';
            }
        });
        /* [SHARED JAVASCRIPT BLOCK END] */

        // DATABASE CONNECTED DATA
        let classes = [];
        let currentClassId = null;

        function loadClassesFromDB(user) {
            if (!window.db || !window.db.data) return;

            if (user.role === 'teacher') {
                classes = window.db.getClasses(user.id);
            } else {
                classes = window.db.getClasses(null, user.id);
            }

            // Transform data to include teacher names
            classes = classes.map(cls => {
                const teacher = window.db.getUserById(cls.teacherId);
                return {
                    ...cls,
                    teacher: teacher ? teacher.name : 'Unknown Teacher',
                    students: cls.students ? cls.students.length : 0
                };
            });
        }

        // UTILITY FUNCTIONS
        function getStudentById(studentId) {
            return window.db.getUserById(studentId);
        }

        // --- CLASSES SPECIFIC FUNCTIONS ---

        function getActionButtons(userRole, classId) {
            if (userRole === 'teacher') {
                return `
                    <button class="btn btn-secondary" onclick="openStudentManager(${classId})"><i class="fas fa-users"></i> Manage Students</button>
                    <button class="btn btn-danger" onclick="deleteClass(${classId})"><i class="fas fa-trash-alt"></i> Delete</button>
                `;
            } else {
                return `<button class="btn btn-primary" onclick="viewClassDetails(${classId})"><i class="fas fa-info-circle"></i> Details</button>`;
            }
        }
        
        function renderClasses() {
            const user = getCurrentUser();
            const tableBody = document.getElementById('classesTableBody');
            tableBody.innerHTML = '';
            
            classes.forEach(cls => {
                const row = document.createElement('tr');
                
                let studentTeacherContent = user.role === 'teacher' ? cls.students : cls.teacher;
                
                row.innerHTML = `
                    <td>${cls.name}</td>
                    <td>${cls.code}</td>
                    <td>${cls.schedule}</td>
                    <td>${studentTeacherContent}</td>
                    <td>${getActionButtons(user.role, cls.id)}</td>
                `;
                tableBody.appendChild(row);
            });
        }
        
        // Teacher Function: Open Student Manager Modal
        function openStudentManager(id) {
            const cls = classes.find(c => c.id === id);
            currentClassId = id;
            if (!cls) return;
            
            document.getElementById('modalClassTitle').textContent = `Students in: ${cls.name}`;
            renderStudentsList();
            document.getElementById('studentManagerModal').classList.add('active');
        }
        
        // Teacher Function: Render Students in Modal
        function renderStudentsList() {
             const studentListTableBody = document.getElementById('studentListTableBody');
             studentListTableBody.innerHTML = '';
             
             const classData = window.db.getClassById(currentClassId);
             if (!classData || !classData.students) return;
             
             classData.students.forEach(studentId => {
                 const student = getStudentById(studentId);
                 if (!student) return;
                 
                 const row = document.createElement('tr');
                 row.innerHTML = `
                     <td>${student.rollNo}</td>
                     <td>${student.name}</td>
                     <td><button class="btn btn-danger btn-sm" onclick="removeStudent(${studentId})"><i class="fas fa-trash"></i> Remove</button></td>
                 `;
                 studentListTableBody.appendChild(row);
             });
        }
        
        // Teacher Function: Add Student
        document.getElementById('addStudentForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const rollNo = document.getElementById('studentRollNo').value.trim().toUpperCase();
            
            if (!rollNo) {
                alert('Please enter a valid Roll Number.');
                return;
            }
            
            // Find student by roll number
            const allStudents = window.db.getUsers('student');
            const student = allStudents.find(s => s.rollNo === rollNo);
            
            if (!student) {
                alert(`Error: Student with Roll No ${rollNo} not found.`);
                return;
            }

            // Add student to class
            const success = window.db.addStudentToClass(currentClassId, student.id);
            
            if (success) {
                loadClassesFromDB(getCurrentUser());
                renderStudentsList();
                renderClasses();
                document.getElementById('studentRollNo').value = '';
                alert(`Student ${student.name} added to class successfully!`);
            } else {
                alert(`Student ${student.name} is already in this class or an error occurred.`);
            }
        });

        // Teacher Function: Remove student from class
        function removeStudent(studentId) {
            if (confirm('Are you sure you want to remove this student from the class?')) {
                const success = window.db.removeStudentFromClass(currentClassId, studentId);
                
                if (success) {
                    loadClassesFromDB(getCurrentUser());
                    renderStudentsList();
                    renderClasses();
                    alert('Student removed from class successfully!');
                } else {
                    alert('Error removing student from class.');
                }
            }
        }
        
        // Student Function: View Class Details (placeholder)
        function viewClassDetails(id) {
             const cls = classes.find(c => c.id === id);
             alert(`Details for ${cls.name}:\nCode: ${cls.code}\nTeacher: ${cls.teacher}\nSchedule: ${cls.schedule}`);
        }

        // Teacher Function: Delete Class
        function deleteClass(id) {
            const cls = classes.find(c => c.id === id);
            if (!cls) return;

            if (confirm(`Are you sure you want to delete the class "${cls.name}"? This will also delete all associated assignments and cannot be undone.`)) {
                const success = window.db.deleteClass(id);
                if (success) {
                    alert('Class deleted successfully.');
                    const user = getCurrentUser();
                    loadClassesFromDB(user);
                    renderClasses();
                } else {
                    alert('Error deleting class.');
                }
            }
        }

        // Initial render
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initClasses = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initClasses, 100);
                    return;
                }

                const user = getCurrentUser();
                if (!user) {
                    alert('Please log in to access the portal.');
                    window.location.href = 'main.html';
                    return;
                }
                
                loadClassesFromDB(user);
                setupUserUI(user);
                renderClasses();
                setActiveNavLink('classes');
            };

            initClasses();
        });

        // New Class Functionality
        document.querySelector('#teacherView .btn-primary').onclick = () => {
            document.getElementById('newClassModal').classList.add('active');
        };

        // Handle new class form submission
        document.getElementById('newClassForm').addEventListener('submit', (e) => {
            e.preventDefault();
            
            const currentUser = getCurrentUser();
            if (!currentUser || currentUser.role !== 'teacher') {
                alert('Only teachers can create classes');
                return;
            }

            const newClass = {
                name: document.getElementById('className').value.trim(),
                code: document.getElementById('classCode').value.trim(),
                department: document.getElementById('classDepartment').value.trim(),
                teacherId: currentUser.id,
                schedule: document.getElementById('classSchedule').value.trim(),
                room: document.getElementById('classRoom').value.trim(),
                semester: document.getElementById('classSemester').value.trim(),
                credits: parseInt(document.getElementById('classCredits').value),
                maxStudents: parseInt(document.getElementById('classMaxStudents').value),
                description: document.getElementById('classDescription').value.trim(),
                students: [],
            };

            const success = window.db.addClass(newClass);

            if (success) {
                loadClassesFromDB(currentUser);
                renderClasses();
                document.getElementById('newClassModal').classList.remove('active');
                document.getElementById('newClassForm').reset();
                alert('Class created successfully!');
            } else {
                alert('Error creating class. Please try again.');
            }
        });
    </script>
</body>
</html>


Attendance Code:-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Attendance - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        /* [SHARED CSS BLOCK START] - POLISHED DEEP TEAL THEME */
        :root {
            /* Deep Teal & Soft Grey Theme */
            --primary-color: #00796B; 
            --secondary-color: #37474F; 
            --background-color: #F0F4F8; 
            --text-color: #263238; 
            --card-bg: #ffffff;
            --border-color: #CFD8DC; 
            --shadow: 0 6px 12px rgba(0,0,0,0.08); 
            --success-color: #4CAF50;
            --warning-color: #FF9800;
            --error-color: #F44336;
        }

        [data-theme="dark"] {
            --primary-color: #4DB6AC; 
            --secondary-color: #1A1E20; 
            --background-color: #263238; 
            --text-color: #CFD8DC; 
            --card-bg: #37474F; 
            --border-color: #546E7A; 
            --shadow: 0 6px 12px rgba(0,0,0,0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        /* --- Application Layout (Sidebar/Main Content) --- */
        .app-container {
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 250px;
            background-color: var(--secondary-color);
            color: white;
            padding: 1rem 0;
            box-shadow: 2px 0 10px rgba(0,0,0,0.15);
            flex-shrink: 0;
        }

        .logo-section {
            padding: 0 1.5rem 1rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 1rem;
        }

        .nav-menu {
            list-style: none;
        }

        .nav-item a {
            display: flex; 
            align-items: center;
            padding: 0.85rem 1.5rem; 
            color: white;
            text-decoration: none;
            transition: background-color 0.2s;
        }
        
        .nav-item a i {
            margin-right: 10px;
            font-size: 1.1rem;
        }

        .nav-item a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .nav-item .active {
            background-color: var(--primary-color);
            font-weight: bold;
        }

        .main-content {
            flex-grow: 1;
            padding: 2.5rem; 
            width: calc(100% - 250px);
        }

        /* --- Components & Utility Styles --- */
        .top-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1.25rem; 
            border-bottom: 1px solid var(--border-color);
        }

        .welcome-message {
            display: flex; 
            align-items: baseline;
            gap: 15px;
        }
        
        .welcome-message h1 {
            font-size: 2rem;
            font-weight: 300;
        }

        .role-badge {
            display: inline-block;
            padding: 0.3rem 1rem;
            background-color: var(--primary-color);
            color: white;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 2rem; 
            margin-bottom: 1.5rem;
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
        }

        .data-table th, .data-table td {
            padding: 1.1rem 1rem; 
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        .data-table th {
            background-color: var(--background-color);
            font-weight: 600;
        }
        
        .data-table tbody tr:hover {
            background-color: rgba(0, 121, 107, 0.05); 
        }

        .btn {
            color: white;
            border: none;
            padding: 0.6rem 1.2rem; 
            border-radius: 6px;
            cursor: pointer;
            text-decoration: none;
            display: inline-flex; 
            align-items: center;
            gap: 5px;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.1s;
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        .btn-primary { background-color: var(--primary-color); }
        .btn-secondary { background-color: var(--secondary-color); }
        .btn-success { background-color: var(--success-color); }
        .btn-danger { background-color: var(--error-color); }

        .badge {
            padding: 0.4em 0.8em; 
            border-radius: 4px;
            font-weight: 600;
            line-height: 1.2;
            color: white;
        }

        .badge-success { background-color: var(--success-color); }
        .badge-warning { background-color: var(--warning-color); }
        .badge-danger { background-color: var(--error-color); }
        .badge-info { background-color: var(--primary-color); }
        .badge-secondary { background-color: var(--secondary-color); }
        
        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 1.4rem; 
            margin-left: 0.75rem;
            transition: color 0.2s;
        }

        .icon-btn:hover {
            color: var(--primary-color);
        }
        
        .form-control {
            padding: 0.7rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: var(--background-color);
            color: var(--text-color);
            transition: border-color 0.2s;
            width: 100%;
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
        }
        /* [SHARED CSS BLOCK END] */

        /* ATTENDANCE SPECIFIC STYLES */
        .summary-box-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .summary-box {
            background-color: var(--card-bg);
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
            text-align: center;
        }
        
        .summary-box h3 {
            font-size: 2.5rem;
            margin: 0.5rem 0;
            font-weight: 500;
        }

        .summary-box p {
            color: var(--text-color);
            opacity: 0.7;
            font-weight: 600;
        }
        
        .attendance-form-group {
            display: flex;
            gap: 15px;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .attendance-form-group > * {
            flex-grow: 1;
        }
        
        .attendance-form-group button {
            flex-grow: 0;
            flex-shrink: 0;
        }

    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section"><h2>Engg Portal</h2></div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="dashboard.html" id="nav-dashboard"><i class="fas fa-home"></i>Dashboard</a></li>
                <li class="nav-item"><a href="profile.html" id="nav-profile"><i class="fas fa-user-circle"></i>Profile</a></li>
                <li class="nav-item"><a href="classes.html" id="nav-classes"><i class="fas fa-chalkboard-teacher"></i>Classes</a></li>
                <li class="nav-item"><a href="assignments.html" id="nav-assignments"><i class="fas fa-tasks"></i>Assignments</a></li>
                <li class="nav-item"><a href="practicals.html" id="nav-practicals"><i class="fas fa-flask"></i>Practicals</a></li>
                <li class="nav-item"><a href="attendance.html" id="nav-attendance" class="active"><i class="fas fa-calendar-check"></i>Attendance</a></li>
                <li class="nav-item"><a href="reports.html" id="nav-reports"><i class="fas fa-chart-line"></i>Reports</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Attendance</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme"><i class="fas fa-sun"></i></button>
                    <button id="logoutBtn" class="icon-btn" title="Logout"><i class="fas fa-sign-out-alt"></i></button>
                </div>
            </div>
            
            <div id="studentViewSummary">
                <h2>Your Attendance Summary</h2>
                <div class="summary-box-container">
                    <div class="summary-box">
                        <p>Overall Percentage</p>
                        <h3 id="overallPercentage" style="color: var(--primary-color);">85%</h3>
                    </div>
                    <div class="summary-box">
                        <p>Classes Attended</p>
                        <h3 id="attendedCount">45</h3>
                    </div>
                    <div class="summary-box">
                        <p>Classes Missed</p>
                        <h3 id="missedCount" style="color: var(--error-color);">8</h3>
                    </div>
                    <div class="summary-box">
                        <p>Current Status</p>
                        <h3 id="statusBadge" style="color: var(--success-color);">Good</h3>
                    </div>
                </div>
            </div>

            <div class="card-header">
                <h2>Attendance History</h2>
                <div id="teacherActionBtn" style="display: none;">
                    <button id="markAttendanceBtn" class="btn btn-primary"><i class="fas fa-edit"></i> Mark Daily Attendance</button>
                </div>
            </div>

            <div class="card">
                <div class="attendance-form-group">
                    <select id="classSelect" class="form-control" style="max-width: 300px;">
                        <option value="all">-- Select Class --</option>
                    </select>
                </div>
                <div class="table-responsive">
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th id="tableHeaderName">Subject / Student</th>
                                <th>Date</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody id="attendanceTableBody">
                            </tbody>
                    </table>
                </div>
            </div>

            <div id="teacherMarkingSection" class="card teacher-only full-width" style="display: none; margin-top: 3rem;">
                <h2>Mark Attendance for Class</h2>
                <div class="attendance-form-group">
                    <input type="date" id="dateSelect" class="form-control" value="">
                    <select id="classSelectMarking" class="form-control">
                        <option value="all">-- Select Class --</option>
                    </select>
                    <button class="btn btn-primary" onclick="loadStudentList()"><i class="fas fa-search"></i> Load Students</button>
                </div>
                
                <div class="table-responsive" id="markingTableContainer">
                    <p id="markingMessage">Select a date and class to load students.</p>
                </div>
                
                <div style="text-align: right; margin-top: 1.5rem;">
                    <button id="saveAttendanceBtn" class="btn btn-success" style="display: none;"><i class="fas fa-save"></i> Save Attendance</button>
                </div>
            </div>

        </main>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        /* [SHARED JAVASCRIPT BLOCK START] */
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function setupUserUI(user) {
            document.getElementById('userRoleBadge').textContent = user.role === 'teacher' ? 'Teacher' : 'Student';
            document.getElementById('teacherActionBtn').style.display = user.role === 'teacher' ? 'block' : 'none';
            document.getElementById('studentViewSummary').style.display = user.role === 'student' ? 'block' : 'none';
            document.getElementById('teacherMarkingSection').style.display = 'none'; // Initially hidden for teacher too
            document.getElementById('tableHeaderName').textContent = user.role === 'teacher' ? 'Student Name' : 'Subject';
        }
        
        function setActiveNavLink(page) {
            document.querySelectorAll('.nav-menu a').forEach(link => {
                link.classList.remove('active');
            });
            const activeLink = document.getElementById(`nav-${page}`);
            if (activeLink) {
                activeLink.classList.add('active');
            }
        }
        
        // Theme Toggle
        const themeToggle = document.getElementById('themeToggle');
        const appContainer = document.querySelector('.app-container');
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        appContainer.setAttribute('data-theme', currentTheme);
        themeToggle.querySelector('i').className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        themeToggle.addEventListener('click', () => {
            const newTheme = appContainer.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            appContainer.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            themeToggle.querySelector('i').className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        });

        // Logout Functionality
        document.getElementById('logoutBtn').addEventListener('click', () => {
            if (confirm('Are you sure you want to logout?')) {
                window.db.logout();
                window.location.href = 'main.html';
            }
        });
        /* [SHARED JAVASCRIPT BLOCK END] */

        // DATABASE DATA
        let classes = [];
        let attendanceHistory = [];
        let currentAttendance = {}; // Stores attendance for the current marking session

        function loadDataFromDB(user) {
            if (!window.db || !window.db.data) return;

            if (user.role === 'teacher') {
                classes = window.db.getClasses(user.id);
            } else {
                classes = window.db.getClasses(null, user.id);
            }

            // Load attendance history
            if (user.role === 'student') {
                const allAttendance = window.db.getAttendance();
                attendanceHistory = [];
                allAttendance.forEach(att => {
                    const studentRecord = att.records.find(r => r.studentId === user.id);
                    if (studentRecord) {
                        const classData = window.db.getClassById(att.classId);
                        attendanceHistory.push({
                            id: att.id,
                            date: att.date,
                            subject: classData ? classData.name : 'Unknown',
                            status: studentRecord.status === 'present' ? 'Present' : 'Absent',
                            rollNo: user.rollNo,
                            classId: att.classId
                        });
                    }
                });
            } else {
                // For teachers, load all attendance for their classes
                const allAttendance = window.db.getAttendance();
                const teacherClassIds = classes.map(c => c.id);
                const relevantAttendance = allAttendance.filter(att => teacherClassIds.includes(att.classId));
                
                attendanceHistory = [];
                relevantAttendance.forEach(att => {
                    att.records.forEach(record => {
                        const student = window.db.getUserById(record.studentId);
                        const classData = window.db.getClassById(att.classId);
                        if (student) {
                            attendanceHistory.push({
                                id: att.id,
                                date: att.date,
                                subject: classData ? classData.name : 'Unknown',
                                status: record.status === 'present' ? 'Present' : 'Absent',
                                studentName: student.name,
                                rollNo: student.rollNo,
                                classId: att.classId
                            });
                        }
                    });
                });
            }
        }

        // --- ATTENDANCE SPECIFIC FUNCTIONS ---
        
        function populateClassDropdowns() {
            const user = getCurrentUser();
            const classSelect = document.getElementById('classSelect');
            const classSelectMarking = document.getElementById('classSelectMarking');
            
            // Clear existing options
            classSelect.innerHTML = '<option value="all">-- Select Class --</option>';
            classSelectMarking.innerHTML = '<option value="all">-- Select Class --</option>';

            classes.forEach(cls => {
                const optionHistory = new Option(cls.name, cls.id);
                classSelect.add(optionHistory.cloneNode(true));
                
                if (user.role === 'teacher') {
                     classSelectMarking.add(new Option(cls.name, cls.id));
                }
            });
        }
        
        function renderAttendanceHistory(classId = 'all') {
            const user = getCurrentUser();
            const tableBody = document.getElementById('attendanceTableBody');
            tableBody.innerHTML = '';
            
            let filteredHistory = attendanceHistory;
            
            if (classId !== 'all') {
                filteredHistory = filteredHistory.filter(h => h.classId == classId);
            }

            filteredHistory.sort((a, b) => new Date(b.date) - new Date(a.date));

            filteredHistory.forEach(record => {
                const row = document.createElement('tr');
                let statusBadge;
                if (record.status === 'Present') {
                    statusBadge = `<span class="badge badge-success"><i class="fas fa-check"></i> Present</span>`;
                } else {
                    statusBadge = `<span class="badge badge-danger"><i class="fas fa-times"></i> Absent</span>`;
                }
                
                const nameCell = user.role === 'teacher' ? record.studentName : record.subject;

                row.innerHTML = `
                    <td>${nameCell}</td>
                    <td>${record.date}</td>
                    <td>${statusBadge}</td>
                `;
                tableBody.appendChild(row);
            });
        }
        
        // Teacher Function: Load students for marking
        function loadStudentList() {
            const date = document.getElementById('dateSelect').value;
            const classId = document.getElementById('classSelectMarking').value;
            const markingContainer = document.getElementById('markingTableContainer');
            const saveBtn = document.getElementById('saveAttendanceBtn');

            if (!date || classId === 'all') {
                markingContainer.innerHTML = '<p id="markingMessage">Select a date and class to load students.</p>';
                saveBtn.style.display = 'none';
                return;
            }
            
            const cls = window.db.getClassById(parseInt(classId));
            if (!cls || !cls.students) {
                markingContainer.innerHTML = '<p id="markingMessage">No students found in this class.</p>';
                saveBtn.style.display = 'none';
                return;
            }

            markingContainer.innerHTML = `
                <table class="data-table">
                    <thead>
                        <tr>
                            <th>Roll No</th>
                            <th>Name</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody id="markingTableBody"></tbody>
                </table>
            `;
            const markingTableBody = document.getElementById('markingTableBody');
            currentAttendance = {}; // Reset attendance records
            
            cls.students.forEach(studentId => {
                const student = window.db.getUserById(studentId);
                if (!student) return;

                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${student.rollNo}</td>
                    <td>${student.name}</td>
                    <td>
                        <button class="btn btn-success" id="present-btn-${studentId}" onclick="updateAttendance(${studentId}, 'present')">Present</button>
                        <button class="btn btn-danger" id="absent-btn-${studentId}" onclick="updateAttendance(${studentId}, 'absent')">Absent</button>
                    </td>
                `;
                markingTableBody.appendChild(row);

                // Initialize all as absent, then update UI
                updateAttendance(studentId, 'absent');
            });
            
            saveBtn.style.display = 'inline-flex';
        }
        
        // Teacher Function: Update attendance status
        function updateAttendance(studentId, status) {
            currentAttendance[studentId] = status;
            
            const presentBtn = document.getElementById(`present-btn-${studentId}`);
            const absentBtn = document.getElementById(`absent-btn-${studentId}`);

            if (status === 'present') {
                presentBtn.style.opacity = 1;
                absentBtn.style.opacity = 0.5;
            } else {
                presentBtn.style.opacity = 0.5;
                absentBtn.style.opacity = 1;
            }
        }
        
        // Teacher Function: Save attendance
        document.getElementById('saveAttendanceBtn').addEventListener('click', function() {
            const date = document.getElementById('dateSelect').value;
            const classId = document.getElementById('classSelectMarking').value;
            
            if (!date || classId === 'all') {
                alert('Please select a valid date and class.');
                return;
            }
            
            // Prepare attendance records
            const records = Object.keys(currentAttendance).map(studentId => ({
                studentId: parseInt(studentId),
                status: currentAttendance[studentId]
            }));
            
            // Save to database
            const success = window.db.markAttendance(parseInt(classId), date, records);
            
            if (success) {
                const classObj = window.db.getClassById(parseInt(classId));
                alert(`Attendance for ${classObj.name} on ${date} saved successfully!`);
                
                // Reload data and refresh UI
                loadDataFromDB(getCurrentUser());
                renderAttendanceHistory(document.getElementById('classSelect').value);
                renderStudentSummary();
                
                // Reset UI
                document.getElementById('teacherMarkingSection').style.display = 'none';
            } else {
                alert('Error saving attendance. Please try again.');
            }
        });

        // Toggle marking section
        document.getElementById('markAttendanceBtn').addEventListener('click', function() {
            const markingSection = document.getElementById('teacherMarkingSection');
            markingSection.style.display = markingSection.style.display === 'none' ? 'block' : 'none';
            if (markingSection.style.display === 'block') {
                 // Initialize date to today
                 document.getElementById('dateSelect').valueAsDate = new Date();
                 loadStudentList();
            }
        });
        
        // Student Function: Render summary
        function renderStudentSummary() {
            const user = getCurrentUser();
            if (user.role !== 'student') return;
            
            const stats = window.db.getStudentAttendanceStats(user.id);
            
            document.getElementById('overallPercentage').textContent = `${stats.percentage}%`;
            document.getElementById('attendedCount').textContent = stats.present;
            document.getElementById('missedCount').textContent = stats.absent;
            
            let statusText = 'Excellent';
            let statusColor = 'var(--success-color)';
            if (stats.percentage < 75) {
                statusText = 'Warning';
                statusColor = 'var(--warning-color)';
            } else if (stats.percentage < 85) {
                statusText = 'Good';
                statusColor = 'var(--primary-color)';
            }
            
            document.getElementById('statusBadge').textContent = statusText;
            document.getElementById('statusBadge').style.color = statusColor;
        }

        // Initial render
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initAttendance = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initAttendance, 100);
                    return;
                }

                const user = getCurrentUser();
                if (!user) {
                    alert('Please log in to access the portal.');
                    window.location.href = 'main.html';
                    return;
                }
                
                loadDataFromDB(user);
                setupUserUI(user);
                populateClassDropdowns();
                renderAttendanceHistory();
                renderStudentSummary();
                setActiveNavLink('attendance');
                
                document.getElementById('classSelect').addEventListener('change', (e) => {
                     renderAttendanceHistory(e.target.value);
                });
            };

            initAttendance();
        });
    </script>
</body>
</html>


Assignment Code:-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Assignments - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        /* [SHARED CSS BLOCK START] - POLISHED THEME AND SPACING */
        :root {
            /* New Deep Teal & Soft Grey Theme */
            --primary-color: #00796B; /* Deep Teal */
            --secondary-color: #37474F; /* Dark Slate */
            --background-color: #F0F4F8; /* Soft Light Grey/Blue */
            --text-color: #263238; /* Dark Text */
            --card-bg: #ffffff;
            --border-color: #CFD8DC; /* Light Border */
            --shadow: 0 6px 12px rgba(0,0,0,0.08); /* Softer Shadow */
            --success-color: #4CAF50;
            --warning-color: #FF9800;
            --error-color: #F44336;
        }

        [data-theme="dark"] {
            --primary-color: #4DB6AC; /* Lighter Teal */
            --secondary-color: #1A1E20; /* Very Dark Background */
            --background-color: #263238; /* Deep Slate Background */
            --text-color: #CFD8DC; /* Light Text */
            --card-bg: #37474F; /* Dark Card */
            --border-color: #546E7A; /* Dark Border */
            --shadow: 0 6px 12px rgba(0,0,0,0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        /* --- Application Layout (Sidebar/Main Content) --- */
        .app-container {
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 250px;
            background-color: var(--secondary-color);
            color: white;
            padding: 1rem 0;
            box-shadow: 2px 0 10px rgba(0,0,0,0.15);
            flex-shrink: 0;
        }

        .logo-section {
            padding: 0 1.5rem 1rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 1rem;
        }

        .nav-menu {
            list-style: none;
        }

        .nav-item a {
            display: flex; /* Polishing: use flex for icon alignment */
            align-items: center;
            padding: 0.85rem 1.5rem; /* Polishing: Slightly more vertical padding */
            color: white;
            text-decoration: none;
            transition: background-color 0.2s;
        }
        
        .nav-item a i {
            margin-right: 10px;
            font-size: 1.1rem;
        }

        .nav-item a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .nav-item .active {
            background-color: var(--primary-color);
            font-weight: bold;
        }

        .main-content {
            flex-grow: 1;
            padding: 2.5rem; /* Polishing: Increased main padding */
            width: calc(100% - 250px);
        }

        /* --- Components & Utility Styles --- */
        .top-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1.25rem; /* Polishing: Increased bottom padding */
            border-bottom: 1px solid var(--border-color);
        }

        .welcome-message {
            display: flex; /* Polishing: use flex to align H1 and Badge */
            align-items: baseline;
            gap: 15px;
        }
        
        .welcome-message h1 {
            font-size: 2rem;
            font-weight: 300;
        }

        .role-badge {
            display: inline-block;
            padding: 0.3rem 1rem;
            background-color: var(--primary-color);
            color: white;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 2rem; /* Polishing: Increased card padding for content area */
            margin-bottom: 1.5rem;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
        }

        .data-table th, .data-table td {
            padding: 1.1rem 1rem; /* Polishing: Slightly more vertical padding */
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        .data-table th {
            background-color: var(--background-color);
            font-weight: 600;
        }
        
        .data-table tbody tr:hover {
            background-color: rgba(0, 121, 107, 0.05); /* Hover based on primary color */
        }

        .btn {
            color: white;
            border: none;
            padding: 0.6rem 1.2rem; /* Polishing: Slightly larger buttons */
            border-radius: 6px;
            cursor: pointer;
            text-decoration: none;
            display: inline-flex; /* Polishing: Use flex for icon alignment */
            align-items: center;
            gap: 5px;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.1s;
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        .btn-primary { background-color: var(--primary-color); }
        .btn-secondary { background-color: var(--secondary-color); }
        .btn-success { background-color: var(--success-color); }
        .btn-danger { background-color: var(--error-color); }

        .badge {
            padding: 0.4em 0.8em; /* Polishing: Slightly larger badges */
            border-radius: 4px;
            font-weight: 600;
            line-height: 1.2;
            color: white;
        }

        .badge-success { background-color: var(--success-color); }
        .badge-warning { background-color: var(--warning-color); }
        .badge-danger { background-color: var(--error-color); }
        .badge-info { background-color: var(--primary-color); }
        .badge-secondary { background-color: var(--secondary-color); }
        
        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 1.4rem; /* Polishing: Slightly larger icons */
            margin-left: 0.75rem;
            transition: color 0.2s;
        }

        .icon-btn:hover {
            color: var(--primary-color);
        }

        /* [SHARED CSS BLOCK END] */

        /* ASSIGNMENTS SPECIFIC STYLES */
        .assignment-actions {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem; /* Polishing: Increased margin */
        }
        
        .action-cell .btn {
            margin-right: 0.5rem;
            padding: 0.5rem 1rem;
            font-size: 0.85rem;
        }

        /* Modal Styles */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6); /* Polishing: Darker overlay */
            display: none; 
            align-items: center;
            justify-content: center;
            z-index: 2000;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background-color: var(--card-bg);
            padding: 3rem; /* Polishing: Increased modal padding */
            border-radius: 10px;
            width: 90%;
            max-width: 700px; /* Polishing: Wider modal */
            box-shadow: var(--shadow);
            color: var(--text-color);
            max-height: 90vh; /* Polishing: Restrict height */
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 1rem; /* Polishing: Increased bottom padding */
        }
        
        .modal-header h3 {
            font-size: 1.5rem;
        }
        
        .form-control {
            padding: 0.5rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: var(--background-color);
            color: var(--text-color);
            transition: border-color 0.2s;
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
        }

    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section"><h2>Engg Portal</h2></div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="dashboard.html" id="nav-dashboard"><i class="fas fa-home"></i>Dashboard</a></li>
                <li class="nav-item"><a href="profile.html" id="nav-profile"><i class="fas fa-user-circle"></i>Profile</a></li>
                <li class="nav-item"><a href="classes.html" id="nav-classes"><i class="fas fa-chalkboard-teacher"></i>Classes</a></li>
                <li class="nav-item"><a href="assignments.html" id="nav-assignments" class="active"><i class="fas fa-tasks"></i>Assignments</a></li>
                <li class="nav-item"><a href="practicals.html" id="nav-practicals"><i class="fas fa-flask"></i>Practicals</a></li>
                <li class="nav-item"><a href="attendance.html" id="nav-attendance"><i class="fas fa-calendar-check"></i>Attendance</a></li>
                <li class="nav-item"><a href="reports.html" id="nav-reports"><i class="fas fa-chart-line"></i>Reports</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Assignments</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme"><i class="fas fa-sun"></i></button>
                    <button id="logoutBtn" class="icon-btn" title="Logout"><i class="fas fa-sign-out-alt"></i></button>
                </div>
            </div>
            
            <div class="assignment-actions">
                <h2>All Assignments</h2>
                <button id="createAssignmentBtn" class="btn btn-primary" style="display: none;"><i class="fas fa-plus-circle"></i> Create New Assignment</button>
            </div>
            
            <div class="card">
                <div class="table-responsive">
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th>Title</th>
                                <th>Subject</th>
                                <th>Due Date</th>
                                <th>Max Marks</th>
                                <th id="tableHeaderStatus">Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="assignmentsTableBody">
                            </tbody>
                    </table>
                </div>
            </div>

            <div id="markEntryModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3 id="modalAssignmentTitle">Mark Entries for Assignment Title</h3>
                        <button class="icon-btn" onclick="document.getElementById('markEntryModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    <form id="saveMarksForm">
                        <div class="table-responsive">
                            <table class="data-table">
                                <thead>
                                    <tr>
                                        <th>Student Name</th>
                                        <th>Roll No</th>
                                        <th>Marks Obtained</th>
                                    </tr>
                                </thead>
                                <tbody id="marksEntryList">
                                    </tbody>
                            </table>
                        </div>
                        <div style="text-align: right; margin-top: 2rem;"> <button type="submit" class="btn btn-success"><i class="fas fa-save"></i> Save Marks</button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Create Assignment Modal -->
            <div id="createAssignmentModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3>Create New Assignment</h3>
                        <button class="icon-btn" onclick="document.getElementById('createAssignmentModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    <form id="createAssignmentForm">
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="assignmentTitle">Title</label>
                            <input type="text" id="assignmentTitle" class="form-control" required style="width: 100%;">
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="assignmentDescription">Description</label>
                            <textarea id="assignmentDescription" class="form-control" rows="3" style="width: 100%;"></textarea>
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="assignmentClass">Class</label>
                            <select id="assignmentClass" class="form-control" required style="width: 100%;"></select>
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="assignmentDueDate">Due Date</label>
                            <input type="date" id="assignmentDueDate" class="form-control" required style="width: 100%;">
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="assignmentMaxMarks">Max Marks</label>
                            <input type="number" id="assignmentMaxMarks" class="form-control" required min="1" style="width: 100%;">
                        </div>
                        <div style="text-align: right; margin-top: 2rem;">
                            <button type="submit" class="btn btn-primary"><i class="fas fa-plus-circle"></i> Create Assignment</button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Submit Assignment Modal -->
            <div id="submitAssignmentModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3 id="submitAssignmentTitle">Submit Assignment</h3>
                        <button class="icon-btn" onclick="document.getElementById('submitAssignmentModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    <form id="submitAssignmentForm">
                        <p>You are submitting: <strong id="assignmentNameToSubmit"></strong></p>
                        <div class="form-group" style="margin-top: 1rem; margin-bottom: 1rem;">
                            <label for="submissionNotes">Submission Notes (Optional)</label>
                            <textarea id="submissionNotes" class="form-control" rows="4" style="width: 100%;"></textarea>
                        </div>
                        <div style="text-align: right; margin-top: 2rem;">
                            <button type="submit" class="btn btn-primary"><i class="fas fa-upload"></i> Submit</button>
                        </div>
                    </form>
                </div>
            </div>
        </main>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        // Database-connected functions
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function setupUserUI(user) {
            document.getElementById('userRoleBadge').textContent = user.role === 'teacher' ? 'Teacher' : 'Student';
        }
        
        function setActiveNavLink(page) {
            document.querySelectorAll('.nav-menu a').forEach(link => {
                link.classList.remove('active');
            });
            const activeLink = document.getElementById(`nav-${page}`);
            if (activeLink) {
                activeLink.classList.add('active');
            }
        }
        
        // Theme Toggle
        const themeToggle = document.getElementById('themeToggle');
        const appContainer = document.querySelector('.app-container');
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        appContainer.setAttribute('data-theme', currentTheme);
        themeToggle.querySelector('i').className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        themeToggle.addEventListener('click', () => {
            const newTheme = appContainer.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            appContainer.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            themeToggle.querySelector('i').className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        });

        // Logout Functionality
        document.getElementById('logoutBtn').addEventListener('click', () => {
            if (confirm('Are you sure you want to logout?')) {
                window.db.logout();
                window.location.href = 'main.html';
            }
        });
        /* [SHARED JAVASCRIPT BLOCK END] */

        // Database-connected data
        let currentAssignmentData = [];
        let currentAssignmentId = null; // Used by mark entry modal

        function loadAssignmentsFromDB(user) {
            if (!window.db || !window.db.data) return;

            if (user.role === 'teacher') {
                // Get assignments created by this teacher
                currentAssignmentData = window.db.getAssignments();
                currentAssignmentData = currentAssignmentData.filter(assignment => {
                    const assignmentClass = window.db.getClassById(assignment.classId);
                    return assignmentClass && assignmentClass.teacherId === user.id;
                });
            } else {
                // Get assignments for student's classes
                currentAssignmentData = window.db.getAssignments(null, user.id);
            }

            // Transform data to match expected format
            currentAssignmentData = currentAssignmentData.map(assignment => {
                const assignmentClass = window.db.getClassById(assignment.classId);
                const submissionCount = assignment.submissions ? assignment.submissions.length : 0;
                
                return {
                    id: assignment.id,
                    title: assignment.title,
                    subject: assignmentClass ? assignmentClass.name : 'Unknown',
                    dueDate: assignment.dueDate,
                    maxMarks: assignment.maxMarks,
                    status: assignment.status,
                    submissions: submissionCount,
                    submissionData: assignment.submissions || [],
                    classId: assignment.classId
                };
            });
        }

        // --- ASSIGNMENTS SPECIFIC FUNCTIONS ---

        function getStatusBadge(status) {
            let className;
            let icon;
            switch (status) {
                case 'graded': className = 'badge-success'; icon = 'fas fa-check-circle'; break;
                case 'pending': className = 'badge-warning'; icon = 'fas fa-hourglass-half'; break;
                case 'due soon': className = 'badge-danger'; icon = 'fas fa-exclamation-circle'; break;
                default: className = 'badge-secondary'; icon = 'fas fa-clock';
            }
            return `<span class="badge ${className}"><i class="${icon}"></i> ${status.toUpperCase()}</span>`;
        }
        
        function getActionButtons(userRole, assignment) {
            const user = getCurrentUser();
            if (userRole === 'teacher') {
                return `
                    <button class="btn btn-secondary" onclick="openMarkEntry(${assignment.id})"><i class="fas fa-marker"></i> Mark</button>
                    <button class="btn btn-secondary" onclick="editAssignment(${assignment.id})"><i class="fas fa-edit"></i> Edit</button>
                    <button class="btn btn-danger" onclick="deleteAssignment(${assignment.id})"><i class="fas fa-trash-alt"></i> Delete</button>
                `;
            } else {
                // Check if student has submitted
                const hasSubmission = assignment.submissionData.some(sub => sub.studentId === user.id);
                const submission = assignment.submissionData.find(sub => sub.studentId === user.id);
                
                if (hasSubmission && submission.marks !== null) {
                    return `
                        <button class="btn btn-success" onclick="viewFeedback(${assignment.id})"><i class="fas fa-eye"></i> View Grade (${submission.marks}/${assignment.maxMarks})</button>
                    `;
                } else if (hasSubmission) {
                    return `<span class="badge badge-info">Submitted - Pending Grade</span>`;
                } else if (new Date(assignment.dueDate) > new Date()) {
                    return `
                        <button class="btn btn-primary" onclick="submitAssignment(${assignment.id})"><i class="fas fa-upload"></i> Submit</button>
                    `;
                } else {
                    return `<span class="badge badge-danger">LATE</span>`;
                }
            }
        }
        
        function renderAssignments(user) {
            const tableBody = document.getElementById('assignmentsTableBody');
            tableBody.innerHTML = '';
            
            // Adjust Table Header for Role
            document.getElementById('tableHeaderStatus').textContent = user.role === 'teacher' ? 'Submissions' : 'Status / Grade';
            document.getElementById('createAssignmentBtn').style.display = user.role === 'teacher' ? 'inline-flex' : 'none'; /* Changed to inline-flex for button alignment */

            currentAssignmentData.forEach(assignment => {
                const row = document.createElement('tr');
                let statusCellContent;
                
                if (user.role === 'teacher') {
                    const assignmentClass = window.db.getClassById(assignment.classId);
                    const totalStudents = assignmentClass ? (assignmentClass.students ? assignmentClass.students.length : 0) : 0;
                    statusCellContent = `${assignment.submissions} / ${totalStudents}`;
                } else {
                    const submission = assignment.submissionData.find(sub => sub.studentId === user.id);
                    if (submission && submission.marks !== null) {
                        statusCellContent = `<span class="badge badge-info">Grade: ${submission.marks}/${assignment.maxMarks}</span>`;
                    } else if (submission) {
                        statusCellContent = `<span class="badge badge-warning">Submitted</span>`;
                    } else {
                        statusCellContent = getStatusBadge(assignment.status);
                    }
                }
                
                row.innerHTML = `
                    <td>${assignment.title}</td>
                    <td>${assignment.subject}</td>
                    <td>${assignment.dueDate}</td>
                    <td>${assignment.maxMarks}</td>
                    <td>${statusCellContent}</td>
                    <td class="action-cell">${getActionButtons(user.role, assignment)}</td>
                `;
                tableBody.appendChild(row);
            });
        }
        
        // Teacher Function: Open Modal
        function openMarkEntry(id) {
            const assignment = currentAssignmentData.find(a => a.id === id);
            currentAssignmentId = id;
            if (!assignment) return;
            
            document.getElementById('modalAssignmentTitle').textContent = `Mark Entries for: ${assignment.title} (Max: ${assignment.maxMarks})`;
            const marksEntryList = document.getElementById('marksEntryList');
            marksEntryList.innerHTML = '';
            
            // Get students enrolled in this assignment's class
            const assignmentClass = window.db.getClassById(assignment.classId);
            if (!assignmentClass || !assignmentClass.students) {
                alert('No students enrolled in this class.');
                return;
            }
            
            assignmentClass.students.forEach(studentId => {
                const student = window.db.getUserById(studentId);
                if (!student) return;
                
                const existingSubmission = assignment.submissionData.find(sub => sub.studentId === studentId);
                const existingMarks = existingSubmission ? existingSubmission.marks || '' : '';
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${student.name}</td>
                    <td>${student.rollNo}</td>
                    <td><input type="number" min="0" max="${assignment.maxMarks}" value="${existingMarks}" data-studentid="${studentId}" class="form-control" style="width: 80px; display: inline-block;"></td>
                `;
                marksEntryList.appendChild(row);
            });

            document.getElementById('markEntryModal').classList.add('active');
        }
        
        // Teacher Function: Save Marks from Modal
        document.getElementById('saveMarksForm').addEventListener('submit', (e) => {
            e.preventDefault();
            
            const markInputs = document.querySelectorAll('#marksEntryList input');
            let hasChanges = false;
            
            markInputs.forEach(input => {
                const studentId = parseInt(input.getAttribute('data-studentid'));
                const marks = input.value.trim();
                
                if (marks !== '') {
                    const marksNum = parseInt(marks);
                    const assignment = window.db.getAssignmentById(currentAssignmentId);
                    
                    if (marksNum >= 0 && marksNum <= assignment.maxMarks) {
                        // Grade the assignment in the database
                        window.db.gradeAssignment(currentAssignmentId, studentId, marksNum, 'Graded by teacher');
                        hasChanges = true;
                    }
                }
            });

            if (hasChanges) {
                alert('Marks saved successfully!');
                document.getElementById('markEntryModal').classList.remove('active');
                loadAssignmentsFromDB(getCurrentUser());
                renderAssignments(getCurrentUser());
            } else {
                alert('No valid marks entered.');
            }
        });
        
        // Student/Teacher Functions
        function submitAssignment(id) {
            const assignment = currentAssignmentData.find(a => a.id === id);
            if (!assignment) return;

            document.getElementById('assignmentNameToSubmit').textContent = assignment.title;
            document.getElementById('submitAssignmentModal').classList.add('active');
            
            // Store the assignment ID for the form handler
            document.getElementById('submitAssignmentForm').dataset.assignmentId = id;
        }

        document.getElementById('submitAssignmentForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const user = getCurrentUser();
            const assignmentId = parseInt(e.target.dataset.assignmentId);
            const submissionNote = document.getElementById('submissionNotes').value;
            const fileUrl = `/submissions/assignment${assignmentId}_${user.rollNo}_${Date.now()}.zip`;

            const success = window.db.submitAssignment(assignmentId, user.id, {
                fileUrl: fileUrl,
                submissionNote: submissionNote || 'No submission notes.'
            });

            if (success) {
                alert('Assignment submitted successfully!');
                document.getElementById('submitAssignmentModal').classList.remove('active');
                e.target.reset();
                loadAssignmentsFromDB(user);
                renderAssignments(user);
            } else {
                alert('Error submitting assignment. Please try again.');
            }
        });
        
        function viewFeedback(id) { 
            const user = getCurrentUser();
            const assignment = currentAssignmentData.find(a => a.id === id);
            const submission = assignment.submissionData.find(sub => sub.studentId === user.id);
            
            if (submission && submission.marks !== null) {
                alert(`Grade for ${assignment.title}:\nScore: ${submission.marks}/${assignment.maxMarks}\nFeedback: ${submission.feedback || 'No feedback provided'}`);
            } else {
                alert('No grade available yet.');
            }
        }
        
        function editAssignment(id) { alert(`Editing assignment ${id}... (Implementation needed)`); }

        function deleteAssignment(id) {
            const assignment = currentAssignmentData.find(a => a.id === id);
            if (!assignment) return;

            if (confirm(`Are you sure you want to delete the assignment "${assignment.title}"? This action is irreversible.`)) {
                const success = window.db.deleteAssignment(id);
                if (success) {
                    alert('Assignment deleted successfully.');
                    const user = getCurrentUser();
                    loadAssignmentsFromDB(user);
                    renderAssignments(user);
                } else {
                    alert('Error deleting assignment.');
                }
            }
        }
        
        // --- Create Assignment Modal Logic ---
        document.getElementById('createAssignmentBtn').addEventListener('click', () => {
            const user = getCurrentUser();
            const classSelect = document.getElementById('assignmentClass');
            classSelect.innerHTML = '';
            
            const teacherClasses = window.db.getClasses(user.id);
            teacherClasses.forEach(cls => {
                const option = document.createElement('option');
                option.value = cls.id;
                option.textContent = cls.name;
                classSelect.appendChild(option);
            });
            
            document.getElementById('createAssignmentModal').classList.add('active');
        });

        document.getElementById('createAssignmentForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const user = getCurrentUser();
            
            const newAssignment = {
                title: document.getElementById('assignmentTitle').value,
                description: document.getElementById('assignmentDescription').value,
                classId: parseInt(document.getElementById('assignmentClass').value),
                dueDate: document.getElementById('assignmentDueDate').value,
                maxMarks: parseInt(document.getElementById('assignmentMaxMarks').value),
                teacherId: user.id
            };

            const created = window.db.createAssignment(newAssignment);
            if (created) {
                alert('Assignment created successfully!');
                document.getElementById('createAssignmentModal').classList.remove('active');
                document.getElementById('createAssignmentForm').reset();
                loadAssignmentsFromDB(user);
                renderAssignments(user);
            } else {
                alert('Failed to create assignment.');
            }
        });

        // Initial render
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initAssignments = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initAssignments, 100);
                    return;
                }

                const user = getCurrentUser();
                if (!user) {
                    alert('Please log in to access the portal.');
                    window.location.href = 'main.html';
                    return;
                }
                
                loadAssignmentsFromDB(user);
                renderAssignments(user);
                setupUserUI(user);
                setActiveNavLink('assignments');
            };

            initAssignments();
        });
    </script>
</body>
</html>


Report Code:-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reports - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        /* [SHARED CSS BLOCK START] - POLISHED DEEP TEAL THEME */
        :root {
            /* Deep Teal & Soft Grey Theme */
            --primary-color: #00796B; 
            --secondary-color: #37474F; 
            --background-color: #F0F4F8; 
            --text-color: #263238; 
            --card-bg: #ffffff;
            --border-color: #CFD8DC; 
            --shadow: 0 6px 12px rgba(0,0,0,0.08); 
            --success-color: #4CAF50;
            --warning-color: #FF9800;
            --error-color: #F44336;
        }

        [data-theme="dark"] {
            --primary-color: #4DB6AC; 
            --secondary-color: #1A1E20; 
            --background-color: #263238; 
            --text-color: #CFD8DC; 
            --card-bg: #37474F; 
            --border-color: #546E7A; 
            --shadow: 0 6px 12px rgba(0,0,0,0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        /* --- Application Layout (Sidebar/Main Content) --- */
        .app-container {
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 250px;
            background-color: var(--secondary-color);
            color: white;
            padding: 1rem 0;
            box-shadow: 2px 0 10px rgba(0,0,0,0.15);
            flex-shrink: 0;
        }

        .logo-section {
            padding: 0 1.5rem 1rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 1rem;
        }

        .nav-menu {
            list-style: none;
        }

        .nav-item a {
            display: flex; 
            align-items: center;
            padding: 0.85rem 1.5rem; 
            color: white;
            text-decoration: none;
            transition: background-color 0.2s;
        }
        
        .nav-item a i {
            margin-right: 10px;
            font-size: 1.1rem;
        }

        .nav-item a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .nav-item .active {
            background-color: var(--primary-color);
            font-weight: bold;
        }

        .main-content {
            flex-grow: 1;
            padding: 2.5rem; 
            width: calc(100% - 250px);
        }

        /* --- Components & Utility Styles --- */
        .top-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1.25rem; 
            border-bottom: 1px solid var(--border-color);
        }

        .welcome-message {
            display: flex; 
            align-items: baseline;
            gap: 15px;
        }
        
        .welcome-message h1 {
            font-size: 2rem;
            font-weight: 300;
        }

        .role-badge {
            display: inline-block;
            padding: 0.3rem 1rem;
            background-color: var(--primary-color);
            color: white;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 2rem; 
            margin-bottom: 1.5rem;
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
        }

        .data-table th, .data-table td {
            padding: 1.1rem 1rem; 
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        .data-table th {
            background-color: var(--background-color);
            font-weight: 600;
        }
        
        .data-table tbody tr:hover {
            background-color: rgba(0, 121, 107, 0.05); 
        }

        .btn {
            color: white;
            border: none;
            padding: 0.6rem 1.2rem; 
            border-radius: 6px;
            cursor: pointer;
            text-decoration: none;
            display: inline-flex; 
            align-items: center;
            gap: 5px;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.1s;
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        .btn-primary { background-color: var(--primary-color); }
        .btn-secondary { background-color: var(--secondary-color); }
        .btn-success { background-color: var(--success-color); }
        .btn-danger { background-color: var(--error-color); }

        .badge {
            padding: 0.4em 0.8em; 
            border-radius: 4px;
            font-weight: 600;
            line-height: 1.2;
            color: white;
        }

        .badge-success { background-color: var(--success-color); }
        .badge-warning { background-color: var(--warning-color); }
        .badge-danger { background-color: var(--error-color); }
        .badge-info { background-color: var(--primary-color); }
        .badge-secondary { background-color: var(--secondary-color); }
        
        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 1.4rem; 
            margin-left: 0.75rem;
            transition: color 0.2s;
        }

        .icon-btn:hover {
            color: var(--primary-color);
        }
        
        .form-control {
            padding: 0.7rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: var(--background-color);
            color: var(--text-color);
            transition: border-color 0.2s;
            width: 100%;
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
        }
        /* [SHARED CSS BLOCK END] */

        /* REPORTS SPECIFIC STYLES */
        .report-filters {
            display: flex;
            gap: 15px;
            align-items: center;
            margin-bottom: 2rem;
        }
        
        .report-filters > label {
            white-space: nowrap;
        }
        
        .custom-date-range {
            display: flex;
            gap: 10px;
            align-items: center;
            display: none; /* Controlled by JS */
        }
        
        .export-actions {
            display: flex;
            gap: 10px;
            margin-top: 1.5rem;
        }
        
        #reportChart {
            border: 1px solid var(--border-color);
            border-radius: 8px;
            max-width: 100%;
            height: 300px;
        }
        
    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section"><h2>Engg Portal</h2></div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="dashboard.html" id="nav-dashboard"><i class="fas fa-home"></i>Dashboard</a></li>
                <li class="nav-item"><a href="profile.html" id="nav-profile"><i class="fas fa-user-circle"></i>Profile</a></li>
                <li class="nav-item"><a href="classes.html" id="nav-classes"><i class="fas fa-chalkboard-teacher"></i>Classes</a></li>
                <li class="nav-item"><a href="assignments.html" id="nav-assignments"><i class="fas fa-tasks"></i>Assignments</a></li>
                <li class="nav-item"><a href="practicals.html" id="nav-practicals"><i class="fas fa-flask"></i>Practicals</a></li>
                <li class="nav-item"><a href="attendance.html" id="nav-attendance"><i class="fas fa-calendar-check"></i>Attendance</a></li>
                <li class="nav-item"><a href="reports.html" id="nav-reports" class="active"><i class="fas fa-chart-line"></i>Reports</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Academic Reports</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme"><i class="fas fa-sun"></i></button>
                    <button id="logoutBtn" class="icon-btn" title="Logout"><i class="fas fa-sign-out-alt"></i></button>
                </div>
            </div>

            <div class="card">
                <div class="report-filters">
                    <label for="reportType">Report Type:</label>
                    <select id="reportType" class="form-control" style="max-width: 200px;">
                        <option value="gpa">GPA Trend</option>
                        <option value="attendance">Attendance Trend</option>
                        <option value="subject">Subject Grades</option>
                    </select>

                    <label for="timePeriod">Period:</label>
                    <select id="timePeriod" class="form-control" style="max-width: 150px;">
                        <option value="current">Current Semester</option>
                        <option value="annual">Last 1 Year</option>
                        <option value="custom">Custom Range</option>
                    </select>
                    
                    <div id="customDateRange" class="custom-date-range">
                        <input type="date" class="form-control">
                        <span>to</span>
                        <input type="date" class="form-control">
                    </div>
                </div>

                <div class="card-header" style="border-bottom: 1px solid var(--border-color); padding-bottom: 1rem;">
                    <h3>Performance Visualization</h3>
                    <button class="btn btn-primary" onclick="drawReportChart()"><i class="fas fa-chart-line"></i> Generate Chart</button>
                </div>
                
                <div style="margin-top: 2rem; text-align: center;">
                    <canvas id="reportChart" width="800" height="300"></canvas>
                </div>
            </div>
            
            <div class="card">
                <h2>Detailed Report Table</h2>
                <div class="table-responsive" style="margin-top: 1rem;">
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th id="tableHeader1">Parameter</th>
                                <th id="tableHeader2">Value</th>
                                <th id="tableHeader3">Details</th>
                            </tr>
                        </thead>
                        <tbody id="reportTableBody">
                            </tbody>
                    </table>
                </div>
                <div class="export-actions">
                    <button id="exportCsvBtn" class="btn btn-secondary"><i class="fas fa-file-csv"></i> Export CSV</button>
                    <button id="exportJsonBtn" class="btn btn-secondary"><i class="fas fa-file-code"></i> Export JSON</button>
                    <button id="printReportBtn" class="btn btn-secondary"><i class="fas fa-print"></i> Print Report</button>
                </div>
            </div>

        </main>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        /* [SHARED JAVASCRIPT BLOCK START] */
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function setupUserUI(user) {
            document.getElementById('userRoleBadge').textContent = user.role === 'teacher' ? 'Teacher' : 'Student';
            // Reports page usually looks the same for both roles, just the data changes
        }
        
        function setActiveNavLink(page) {
            document.querySelectorAll('.nav-menu a').forEach(link => {
                link.classList.remove('active');
            });
            const activeLink = document.getElementById(`nav-${page}`);
            if (activeLink) {
                activeLink.classList.add('active');
            }
        }
        
        // Theme Toggle
        const themeToggle = document.getElementById('themeToggle');
        const appContainer = document.querySelector('.app-container');
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        appContainer.setAttribute('data-theme', currentTheme);
        themeToggle.querySelector('i').className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        themeToggle.addEventListener('click', () => {
            const newTheme = appContainer.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            appContainer.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            themeToggle.querySelector('i').className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        });

        // Logout Functionality
        document.getElementById('logoutBtn').addEventListener('click', () => {
            if (confirm('Are you sure you want to logout?')) {
                window.db.logout();
                window.location.href = 'main.html';
            }
        });
        /* [SHARED JAVASCRIPT BLOCK END] */

        // DYNAMIC REPORT DATA
        let reportsData = {
            gpa: { labels: [], data: [], tables: [] },
            attendance: { labels: [], data: [], tables: [] },
            subject: { labels: [], data: [], tables: [] }
        };

        function generateReportsData(user) {
            if (!window.db || !window.db.data) return;

            if (user.role === 'student') {
                // GPA Report
                const grades = window.db.getGrades(user.id);
                const classes = window.db.getClasses(null, user.id);
                
                reportsData.gpa = {
                    labels: classes.map(c => c.code),
                    data: grades.map(g => g.gpa || 3.5), // Default if no GPA calculated
                    tables: [
                        { Parameter: 'Overall GPA', Value: '3.6', Details: 'Above average' },
                        { Parameter: 'Classes Enrolled', Value: classes.length.toString(), Details: 'Current semester' },
                        { Parameter: 'Credits Completed', Value: (classes.length * 3).toString(), Details: 'Total credits' }
                    ]
                };

                // Attendance Report
                const attendanceStats = window.db.getStudentAttendanceStats(user.id);
                const attendanceHistory = window.db.getAttendance();
                
                // Group by month
                const monthlyAttendance = {};
                attendanceHistory.forEach(att => {
                    const record = att.records.find(r => r.studentId === user.id);
                    if (record) {
                        const month = new Date(att.date).toLocaleDateString('en', {month: 'short'});
                        if (!monthlyAttendance[month]) {
                            monthlyAttendance[month] = { present: 0, total: 0 };
                        }
                        monthlyAttendance[month].total++;
                        if (record.status === 'present') {
                            monthlyAttendance[month].present++;
                        }
                    }
                });

                const months = Object.keys(monthlyAttendance);
                const monthlyPercentages = months.map(month => {
                    const data = monthlyAttendance[month];
                    return Math.round((data.present / data.total) * 100) || 0;
                });

                reportsData.attendance = {
                    labels: months,
                    data: monthlyPercentages,
                    tables: [
                        { Parameter: 'Overall Attendance', Value: `${attendanceStats.percentage}%`, Details: 'Current semester' },
                        { Parameter: 'Classes Attended', Value: attendanceStats.present.toString(), Details: 'Total present' },
                        { Parameter: 'Classes Missed', Value: attendanceStats.absent.toString(), Details: 'Total absent' }
                    ]
                };

                // Subject Grades Report
                const assignments = window.db.getAssignments(null, user.id);
                const subjectGrades = {};
                
                assignments.forEach(assignment => {
                    const classData = window.db.getClassById(assignment.classId);
                    const submission = assignment.submissions.find(s => s.studentId === user.id);
                    
                    if (classData && submission && submission.marks !== null) {
                        if (!subjectGrades[classData.code]) {
                            subjectGrades[classData.code] = { total: 0, count: 0, name: classData.name };
                        }
                        subjectGrades[classData.code].total += (submission.marks / assignment.maxMarks) * 100;
                        subjectGrades[classData.code].count++;
                    }
                });

                const subjects = Object.keys(subjectGrades);
                const subjectAvgs = subjects.map(code => {
                    const grade = subjectGrades[code];
                    return Math.round(grade.total / grade.count) || 0;
                });

                reportsData.subject = {
                    labels: subjects,
                    data: subjectAvgs,
                    tables: subjects.map(code => {
                        const avg = subjectAvgs[subjects.indexOf(code)];
                        const grade = avg >= 90 ? 'A' : avg >= 80 ? 'B' : avg >= 70 ? 'C' : avg >= 60 ? 'D' : 'F';
                        return {
                            Parameter: subjectGrades[code].name,
                            Value: grade,
                            Details: `Grade ${avg}/100`
                        };
                    })
                };
            } else {
                // Teacher view - show class statistics
                const teacherClasses = window.db.getClasses(user.id);
                const allAssignments = window.db.getAssignments();
                
                reportsData.gpa = {
                    labels: teacherClasses.map(c => c.code),
                    data: teacherClasses.map(() => Math.floor(Math.random() * 20) + 80), // Mock class averages
                    tables: [
                        { Parameter: 'Classes Teaching', Value: teacherClasses.length.toString(), Details: 'Current semester' },
                        { Parameter: 'Total Students', Value: teacherClasses.reduce((acc, c) => acc + (c.students ? c.students.length : 0), 0).toString(), Details: 'Across all classes' },
                        { Parameter: 'Assignments Created', Value: allAssignments.filter(a => teacherClasses.some(c => c.id === a.classId)).length.toString(), Details: 'Total assignments' }
                    ]
                };

                reportsData.attendance = reportsData.gpa; // Same for simplicity
                reportsData.subject = reportsData.gpa;
            }
        }

        // --- REPORTS SPECIFIC FUNCTIONS ---

        function drawReportChart() {
            const reportType = document.getElementById('reportType').value;
            const reportData = reportsData[reportType];
            
            if (!reportData) return;

            const canvas = document.getElementById('reportChart');
            const ctx = canvas.getContext('2d');
            const width = canvas.width;
            const height = canvas.height;
            const padding = 30;

            // Clear canvas
            ctx.clearRect(0, 0, width, height);

            // Get colors from CSS variables
            const primaryColor = getComputedStyle(document.documentElement).getPropertyValue('--primary-color');
            const secondaryColor = getComputedStyle(document.documentElement).getPropertyValue('--secondary-color');
            const textColor = getComputedStyle(document.documentElement).getPropertyValue('--text-color');
            
            ctx.fillStyle = primaryColor;
            ctx.strokeStyle = textColor;
            ctx.lineWidth = 1;
            ctx.font = '12px Arial';
            ctx.textAlign = 'center';

            const chartWidth = width - 2 * padding;
            const chartHeight = height - 2 * padding;
            const barWidth = 40;
            const spacing = (chartWidth - reportData.data.length * barWidth) / (reportData.data.length + 1);
            
            const maxValue = reportType === 'gpa' ? 4.0 : 100;
            
            // Draw axes
            ctx.beginPath();
            ctx.moveTo(padding, padding);
            ctx.lineTo(padding, height - padding);
            ctx.lineTo(width - padding, height - padding);
            ctx.stroke();

            // Draw bars
            reportData.data.forEach((value, i) => {
                // Normalize value for bar height
                const normalizedValue = reportType === 'gpa' ? (value / 4.0) : (value / 100);
                const barHeight = normalizedValue * (chartHeight - 10); // leave a small gap at top
                
                const x = padding + spacing + i * (barWidth + spacing);
                const y = height - padding - barHeight;
                
                ctx.fillStyle = primaryColor;
                ctx.fillRect(x, y, barWidth, barHeight);
                
                // Draw value label
                ctx.fillStyle = textColor;
                ctx.fillText(value.toFixed(reportType === 'gpa' ? 1 : 0), x + barWidth / 2, y - 5);
                
                // Draw label
                ctx.fillText(reportData.labels[i], x + barWidth / 2, height - padding + 15);
            });
            
            // Draw Y-axis labels (Mock)
            ctx.textAlign = 'right';
            ctx.fillText(maxValue, padding - 5, padding + 5);
            ctx.fillText(maxValue / 2, padding - 5, height - padding - chartHeight / 2);
            ctx.fillText(0, padding - 5, height - padding + 5);
            
            renderReportTable(reportData);
        }

        function renderReportTable(reportData) {
             const tableBody = document.getElementById('reportTableBody');
             tableBody.innerHTML = '';
             
             const type = document.getElementById('reportType').value;

             // Adjust table headers
             if (type === 'subject') {
                 document.getElementById('tableHeader1').textContent = 'Subject';
                 document.getElementById('tableHeader2').textContent = 'Final Grade';
                 document.getElementById('tableHeader3').textContent = 'Score Details';
             } else {
                 document.getElementById('tableHeader1').textContent = 'Parameter';
                 document.getElementById('tableHeader2').textContent = 'Value';
                 document.getElementById('tableHeader3').textContent = 'Details';
             }

             reportData.tables.forEach(row => {
                 const tr = document.createElement('tr');
                 // Use consistent object property names for table cells
                 tr.innerHTML = `
                     <td>${row.Parameter}</td>
                     <td>${row.Value}</td>
                     <td>${row.Details}</td>
                 `;
                 tableBody.appendChild(tr);
             });
        }

        // Export functionality
        document.getElementById('exportCsvBtn').addEventListener('click', () => {
            alert('Exporting report as CSV...');
        });

        document.getElementById('exportJsonBtn').addEventListener('click', () => {
            alert('Exporting report as JSON...');
        });

        document.getElementById('printReportBtn').addEventListener('click', () => {
            window.print();
        });

        // Show/hide custom date range
        document.getElementById('timePeriod').addEventListener('change', function() {
            const customRange = document.getElementById('customDateRange');
            if (this.value === 'custom') {
                customRange.style.display = 'flex';
            } else {
                customRange.style.display = 'none';
            }
        });
        
        // Change report type
        document.getElementById('reportType').addEventListener('change', function() {
            drawReportChart(); // Redraw chart and table for new report type
        });

        // Initial render
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initReports = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initReports, 100);
                    return;
                }

                const user = getCurrentUser();
                if (!user) {
                    alert('Please log in to access the portal.');
                    window.location.href = 'main.html';
                    return;
                }
                
                generateReportsData(user);
                setupUserUI(user);
                setActiveNavLink('reports');
                
                // Ensure chart is drawn on load
                drawReportChart();
            };

            initReports();
        });
    </script>
</body>
</html>


 Practical Code:-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Practicals - Engineering Student Portal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        /* [SHARED CSS BLOCK START] - POLISHED THEME AND SPACING */
        :root {
            /* New Deep Teal & Soft Grey Theme */
            --primary-color: #00796B; /* Deep Teal */
            --secondary-color: #37474F; /* Dark Slate */
            --background-color: #F0F4F8; /* Soft Light Grey/Blue */
            --text-color: #263238; /* Dark Text */
            --card-bg: #ffffff;
            --border-color: #CFD8DC; /* Light Border */
            --shadow: 0 6px 12px rgba(0,0,0,0.08); /* Softer Shadow */
            --success-color: #4CAF50;
            --warning-color: #FF9800;
            --error-color: #F44336;
        }

        [data-theme="dark"] {
            --primary-color: #4DB6AC; /* Lighter Teal */
            --secondary-color: #1A1E20; /* Very Dark Background */
            --background-color: #263238; /* Deep Slate Background */
            --text-color: #CFD8DC; /* Light Text */
            --card-bg: #37474F; /* Dark Card */
            --border-color: #546E7A; /* Dark Border */
            --shadow: 0 6px 12px rgba(0,0,0,0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        /* --- Application Layout (Sidebar/Main Content) --- */
        .app-container {
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 250px;
            background-color: var(--secondary-color);
            color: white;
            padding: 1rem 0;
            box-shadow: 2px 0 10px rgba(0,0,0,0.15);
            flex-shrink: 0;
        }

        .logo-section {
            padding: 0 1.5rem 1rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 1rem;
        }

        .nav-menu {
            list-style: none;
        }

        .nav-item a {
            display: flex; /* Polishing: use flex for icon alignment */
            align-items: center;
            padding: 0.85rem 1.5rem; /* Polishing: Slightly more vertical padding */
            color: white;
            text-decoration: none;
            transition: background-color 0.2s;
        }
        
        .nav-item a i {
            margin-right: 10px;
            font-size: 1.1rem;
        }

        .nav-item a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .nav-item .active {
            background-color: var(--primary-color);
            font-weight: bold;
        }

        .main-content {
            flex-grow: 1;
            padding: 2.5rem; /* Polishing: Increased main padding */
            width: calc(100% - 250px);
        }

        /* --- Components & Utility Styles --- */
        .top-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1.25rem; /* Polishing: Increased bottom padding */
            border-bottom: 1px solid var(--border-color);
        }

        .welcome-message {
            display: flex; /* Polishing: use flex to align H1 and Badge */
            align-items: baseline;
            gap: 15px;
        }
        
        .welcome-message h1 {
            font-size: 2rem;
            font-weight: 300;
        }

        .role-badge {
            display: inline-block;
            padding: 0.3rem 1rem;
            background-color: var(--primary-color);
            color: white;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 2rem; /* Polishing: Increased card padding for content area */
            margin-bottom: 1.5rem;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
        }

        .data-table th, .data-table td {
            padding: 1.1rem 1rem; /* Polishing: Slightly more vertical padding */
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        .data-table th {
            background-color: var(--background-color);
            font-weight: 600;
        }
        
        .data-table tbody tr:hover {
            background-color: rgba(0, 121, 107, 0.05); /* Hover based on primary color */
        }

        .btn {
            color: white;
            border: none;
            padding: 0.6rem 1.2rem; /* Polishing: Slightly larger buttons */
            border-radius: 6px;
            cursor: pointer;
            text-decoration: none;
            display: inline-flex; /* Polishing: Use flex for icon alignment */
            align-items: center;
            gap: 5px;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.1s;
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        .btn-primary { background-color: var(--primary-color); }
        .btn-secondary { background-color: var(--secondary-color); }
        .btn-success { background-color: var(--success-color); }
        .btn-danger { background-color: var(--error-color); }

        .badge {
            padding: 0.4em 0.8em; /* Polishing: Slightly larger badges */
            border-radius: 4px;
            font-weight: 600;
            line-height: 1.2;
            color: white;
        }

        .badge-success { background-color: var(--success-color); }
        .badge-warning { background-color: var(--warning-color); }
        .badge-danger { background-color: var(--error-color); }
        .badge-info { background-color: var(--primary-color); }
        .badge-secondary { background-color: var(--secondary-color); }
        
        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 1.4rem; /* Polishing: Slightly larger icons */
            margin-left: 0.75rem;
            transition: color 0.2s;
        }

        .icon-btn:hover {
            color: var(--primary-color);
        }

        /* [SHARED CSS BLOCK END] */

        /* PRACTICALS SPECIFIC STYLES */
        .practical-actions {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem; /* Polishing: Increased margin */
        }
        
        .action-cell .btn {
            margin-right: 0.5rem;
            padding: 0.5rem 1rem;
            font-size: 0.85rem;
        }

        /* Modal Styles */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6); /* Polishing: Darker overlay */
            display: none; 
            align-items: center;
            justify-content: center;
            z-index: 2000;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background-color: var(--card-bg);
            padding: 3rem; /* Polishing: Increased modal padding */
            border-radius: 10px;
            width: 90%;
            max-width: 700px; /* Polishing: Wider modal */
            box-shadow: var(--shadow);
            color: var(--text-color);
            max-height: 90vh; /* Polishing: Restrict height */
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 1rem; /* Polishing: Increased bottom padding */
        }
        
        .modal-header h3 {
            font-size: 1.5rem;
        }
        
        .form-control {
            padding: 0.5rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: var(--background-color);
            color: var(--text-color);
            transition: border-color 0.2s;
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
        }

    </style>
</head>
<body>
    <div class="app-container" data-theme="light">
        <aside class="sidebar">
            <div class="logo-section"><h2>Engg Portal</h2></div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="dashboard.html" id="nav-dashboard"><i class="fas fa-home"></i>Dashboard</a></li>
                <li class="nav-item"><a href="profile.html" id="nav-profile"><i class="fas fa-user-circle"></i>Profile</a></li>
                <li class="nav-item"><a href="classes.html" id="nav-classes"><i class="fas fa-chalkboard-teacher"></i>Classes</a></li>
                <li class="nav-item"><a href="assignments.html" id="nav-assignments"><i class="fas fa-tasks"></i>Assignments</a></li>
                <li class="nav-item"><a href="practicals.html" id="nav-practicals" class="active"><i class="fas fa-flask"></i>Practicals</a></li>
                <li class="nav-item"><a href="attendance.html" id="nav-attendance"><i class="fas fa-calendar-check"></i>Attendance</a></li>
                <li class="nav-item"><a href="reports.html" id="nav-reports"><i class="fas fa-chart-line"></i>Reports</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="top-navbar">
                <div class="welcome-message">
                    <h1>Practicals</h1>
                    <span id="userRoleBadge" class="role-badge">Role</span>
                </div>
                <div class="action-group">
                    <button id="themeToggle" class="icon-btn" title="Toggle Dark/Light Theme"><i class="fas fa-sun"></i></button>
                    <button id="logoutBtn" class="icon-btn" title="Logout"><i class="fas fa-sign-out-alt"></i></button>
                </div>
            </div>
            
            <div class="practical-actions">
                <h2>All Practicals</h2>
                <button id="createPracticalBtn" class="btn btn-primary" style="display: none;"><i class="fas fa-plus-circle"></i> Create New Practical</button>
            </div>
            
            <div class="card">
                <div class="table-responsive">
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th>Title</th>
                                <th>Subject</th>
                                <th>Due Date</th>
                                <th>Max Marks</th>
                                <th id="tableHeaderStatus">Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="practicalsTableBody">
                            </tbody>
                    </table>
                </div>
            </div>

            <div id="markEntryModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3 id="modalPracticalTitle">Mark Entries for Practical Title</h3>
                        <button class="icon-btn" onclick="document.getElementById('markEntryModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    <form id="saveMarksForm">
                        <div class="table-responsive">
                            <table class="data-table">
                                <thead>
                                    <tr>
                                        <th>Student Name</th>
                                        <th>Roll No</th>
                                        <th>Marks Obtained</th>
                                    </tr>
                                </thead>
                                <tbody id="marksEntryList">
                                    </tbody>
                            </table>
                        </div>
                        <div style="text-align: right; margin-top: 2rem;"> <button type="submit" class="btn btn-success"><i class="fas fa-save"></i> Save Marks</button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Create Practical Modal -->
            <div id="createPracticalModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3>Create New Practical</h3>
                        <button class="icon-btn" onclick="document.getElementById('createPracticalModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    <form id="createPracticalForm">
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="practicalTitle">Title</label>
                            <input type="text" id="practicalTitle" class="form-control" required style="width: 100%;">
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="practicalDescription">Description</label>
                            <textarea id="practicalDescription" class="form-control" rows="3" style="width: 100%;"></textarea>
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="practicalClass">Class</label>
                            <select id="practicalClass" class="form-control" required style="width: 100%;"></select>
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="practicalDueDate">Due Date</label>
                            <input type="date" id="practicalDueDate" class="form-control" required style="width: 100%;">
                        </div>
                        <div class="form-group" style="margin-bottom: 1rem;">
                            <label for="practicalMaxMarks">Max Marks</label>
                            <input type="number" id="practicalMaxMarks" class="form-control" required min="1" style="width: 100%;">
                        </div>
                        <div style="text-align: right; margin-top: 2rem;">
                            <button type="submit" class="btn btn-primary"><i class="fas fa-plus-circle"></i> Create Practical</button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Submit Practical Modal -->
            <div id="submitPracticalModal" class="modal">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3 id="submitPracticalTitle">Submit Practical</h3>
                        <button class="icon-btn" onclick="document.getElementById('submitPracticalModal').classList.remove('active')"><i class="fas fa-times"></i></button>
                    </div>
                    <form id="submitPracticalForm">
                        <p>You are submitting: <strong id="practicalNameToSubmit"></strong></p>
                        <div class="form-group" style="margin-top: 1rem; margin-bottom: 1rem;">
                            <label for="submissionNotes">Submission Notes (Optional)</label>
                            <textarea id="submissionNotes" class="form-control" rows="4" style="width: 100%;"></textarea>
                        </div>
                        <div style="text-align: right; margin-top: 2rem;">
                            <button type="submit" class="btn btn-primary"><i class="fas fa-upload"></i> Submit</button>
                        </div>
                    </form>
                </div>
            </div>
        </main>
    </div>

    <!-- Database Manager -->
    <script src="js/database.js"></script>
    
    <script>
        // Database-connected functions
        function getCurrentUser() {
            return window.db ? window.db.getCurrentUser() : null;
        }

        function setupUserUI(user) {
            document.getElementById('userRoleBadge').textContent = user.role === 'teacher' ? 'Teacher' : 'Student';
        }
        
        function setActiveNavLink(page) {
            document.querySelectorAll('.nav-menu a').forEach(link => {
                link.classList.remove('active');
            });
            const activeLink = document.getElementById(`nav-${page}`);
            if (activeLink) {
                activeLink.classList.add('active');
            }
        }
        
        // Theme Toggle
        const themeToggle = document.getElementById('themeToggle');
        const appContainer = document.querySelector('.app-container');
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        appContainer.setAttribute('data-theme', currentTheme);
        themeToggle.querySelector('i').className = currentTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        themeToggle.addEventListener('click', () => {
            const newTheme = appContainer.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            appContainer.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            themeToggle.querySelector('i').className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        });

        // Logout Functionality
        document.getElementById('logoutBtn').addEventListener('click', () => {
            if (confirm('Are you sure you want to logout?')) {
                window.db.logout();
                window.location.href = 'main.html';
            }
        });
        /* [SHARED JAVASCRIPT BLOCK END] */

        // Database-connected data
        let currentPracticalData = [];
        let currentPracticalId = null; // Used by mark entry modal

        function loadPracticalsFromDB(user) {
            if (!window.db || !window.db.data) return;

            if (user.role === 'teacher') {
                // Get practicals created by this teacher
                currentPracticalData = window.db.getPracticals();
                currentPracticalData = currentPracticalData.filter(practical => {
                    const practicalClass = window.db.getClassById(practical.classId);
                    return practicalClass && practicalClass.teacherId === user.id;
                });
            } else {
                // Get practicals for student's classes
                currentPracticalData = window.db.getPracticals(null, user.id);
            }

            // Transform data to match expected format
            currentPracticalData = currentPracticalData.map(practical => {
                const practicalClass = window.db.getClassById(practical.classId);
                const submissionCount = practical.submissions ? practical.submissions.length : 0;
                
                return {
                    id: practical.id,
                    title: practical.title,
                    subject: practicalClass ? practicalClass.name : 'Unknown',
                    dueDate: practical.dueDate,
                    maxMarks: practical.maxMarks,
                    status: practical.status,
                    submissions: submissionCount,
                    submissionData: practical.submissions || [],
                    classId: practical.classId
                };
            });
        }

        // --- PRACTICALS SPECIFIC FUNCTIONS ---

        function getStatusBadge(status) {
            let className;
            let icon;
            switch (status) {
                case 'graded': className = 'badge-success'; icon = 'fas fa-check-circle'; break;
                case 'pending': className = 'badge-warning'; icon = 'fas fa-hourglass-half'; break;
                case 'due soon': className = 'badge-danger'; icon = 'fas fa-exclamation-circle'; break;
                default: className = 'badge-secondary'; icon = 'fas fa-clock';
            }
            return `<span class="badge ${className}"><i class="${icon}"></i> ${status.toUpperCase()}</span>`;
        }
        
        function getActionButtons(userRole, practical) {
            const user = getCurrentUser();
            if (userRole === 'teacher') {
                return `
                    <button class="btn btn-secondary" onclick="openMarkEntry(${practical.id})"><i class="fas fa-marker"></i> Mark</button>
                    <button class="btn btn-secondary" onclick="editPractical(${practical.id})"><i class="fas fa-edit"></i> Edit</button>
                    <button class="btn btn-danger" onclick="deletePractical(${practical.id})"><i class="fas fa-trash-alt"></i> Delete</button>
                `;
            } else {
                // Check if student has submitted
                const hasSubmission = practical.submissionData.some(sub => sub.studentId === user.id);
                const submission = practical.submissionData.find(sub => sub.studentId === user.id);
                
                if (hasSubmission && submission.marks !== null) {
                    return `
                        <button class="btn btn-success" onclick="viewFeedback(${practical.id})"><i class="fas fa-eye"></i> View Grade (${submission.marks}/${practical.maxMarks})</button>
                    `;
                } else if (hasSubmission) {
                    return `<span class="badge badge-info">Submitted - Pending Grade</span>`;
                } else if (new Date(practical.dueDate) > new Date()) {
                    return `
                        <button class="btn btn-primary" onclick="submitPractical(${practical.id})"><i class="fas fa-upload"></i> Submit</button>
                    `;
                } else {
                    return `<span class="badge badge-danger">LATE</span>`;
                }
            }
        }
        
        function renderPracticals(user) {
            const tableBody = document.getElementById('practicalsTableBody');
            tableBody.innerHTML = '';
            
            // Adjust Table Header for Role
            document.getElementById('tableHeaderStatus').textContent = user.role === 'teacher' ? 'Submissions' : 'Status / Grade';
            document.getElementById('createPracticalBtn').style.display = user.role === 'teacher' ? 'inline-flex' : 'none'; /* Changed to inline-flex for button alignment */

            currentPracticalData.forEach(practical => {
                const row = document.createElement('tr');
                let statusCellContent;
                
                if (user.role === 'teacher') {
                    const practicalClass = window.db.getClassById(practical.classId);
                    const totalStudents = practicalClass ? (practicalClass.students ? practicalClass.students.length : 0) : 0;
                    statusCellContent = `${practical.submissions} / ${totalStudents}`;
                } else {
                    const submission = practical.submissionData.find(sub => sub.studentId === user.id);
                    if (submission && submission.marks !== null) {
                        statusCellContent = `<span class="badge badge-info">Grade: ${submission.marks}/${practical.maxMarks}</span>`;
                    } else if (submission) {
                        statusCellContent = `<span class="badge badge-warning">Submitted</span>`;
                    } else {
                        statusCellContent = getStatusBadge(practical.status);
                    }
                }
                
                row.innerHTML = `
                    <td>${practical.title}</td>
                    <td>${practical.subject}</td>
                    <td>${practical.dueDate}</td>
                    <td>${practical.maxMarks}</td>
                    <td>${statusCellContent}</td>
                    <td class="action-cell">${getActionButtons(user.role, practical)}</td>
                `;
                tableBody.appendChild(row);
            });
        }
        
        // Teacher Function: Open Modal
        function openMarkEntry(id) {
            const practical = currentPracticalData.find(a => a.id === id);
            currentPracticalId = id;
            if (!practical) return;
            
            document.getElementById('modalPracticalTitle').textContent = `Mark Entries for: ${practical.title} (Max: ${practical.maxMarks})`;
            const marksEntryList = document.getElementById('marksEntryList');
            marksEntryList.innerHTML = '';
            
            // Get students enrolled in this practical's class
            const practicalClass = window.db.getClassById(practical.classId);
            if (!practicalClass || !practicalClass.students) {
                alert('No students enrolled in this class.');
                return;
            }
            
            practicalClass.students.forEach(studentId => {
                const student = window.db.getUserById(studentId);
                if (!student) return;
                
                const existingSubmission = practical.submissionData.find(sub => sub.studentId === studentId);
                const existingMarks = existingSubmission ? existingSubmission.marks || '' : '';
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${student.name}</td>
                    <td>${student.rollNo}</td>
                    <td><input type="number" min="0" max="${practical.maxMarks}" value="${existingMarks}" data-studentid="${studentId}" class="form-control" style="width: 80px; display: inline-block;"></td>
                `;
                marksEntryList.appendChild(row);
            });

            document.getElementById('markEntryModal').classList.add('active');
        }
        
        // Teacher Function: Save Marks from Modal
        document.getElementById('saveMarksForm').addEventListener('submit', (e) => {
            e.preventDefault();
            
            const markInputs = document.querySelectorAll('#marksEntryList input');
            let hasChanges = false;
            
            markInputs.forEach(input => {
                const studentId = parseInt(input.getAttribute('data-studentid'));
                const marks = input.value.trim();
                
                if (marks !== '') {
                    const marksNum = parseInt(marks);
                    const practical = window.db.getPracticalById(currentPracticalId);
                    
                    if (marksNum >= 0 && marksNum <= practical.maxMarks) {
                        // Grade the practical in the database
                        window.db.gradePractical(currentPracticalId, studentId, marksNum, 'Graded by teacher');
                        hasChanges = true;
                    }
                }
            });

            if (hasChanges) {
                alert('Marks saved successfully!');
                document.getElementById('markEntryModal').classList.remove('active');
                loadPracticalsFromDB(getCurrentUser());
                renderPracticals(getCurrentUser());
            } else {
                alert('No valid marks entered.');
            }
        });
        
        // Student/Teacher Functions
        function submitPractical(id) {
            const practical = currentPracticalData.find(a => a.id === id);
            if (!practical) return;

            document.getElementById('practicalNameToSubmit').textContent = practical.title;
            document.getElementById('submitPracticalModal').classList.add('active');
            
            // Store the practical ID for the form handler
            document.getElementById('submitPracticalForm').dataset.practicalId = id;
        }

        document.getElementById('submitPracticalForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const user = getCurrentUser();
            const practicalId = parseInt(e.target.dataset.practicalId);
            const submissionNote = document.getElementById('submissionNotes').value;
            const fileUrl = `/submissions/practical${practicalId}_${user.rollNo}_${Date.now()}.zip`;

            const success = window.db.submitPractical(practicalId, user.id, {
                fileUrl: fileUrl,
                submissionNote: submissionNote || 'No submission notes.'
            });

            if (success) {
                alert('Practical submitted successfully!');
                document.getElementById('submitPracticalModal').classList.remove('active');
                e.target.reset();
                loadPracticalsFromDB(user);
                renderPracticals(user);
            } else {
                alert('Error submitting practical. Please try again.');
            }
        });
        
        function viewFeedback(id) { 
            const user = getCurrentUser();
            const practical = currentPracticalData.find(a => a.id === id);
            const submission = practical.submissionData.find(sub => sub.studentId === user.id);
            
            if (submission && submission.marks !== null) {
                alert(`Grade for ${practical.title}:\nScore: ${submission.marks}/${practical.maxMarks}\nFeedback: ${submission.feedback || 'No feedback provided'}`);
            } else {
                alert('No grade available yet.');
            }
        }
        
        function editPractical(id) { alert(`Editing practical ${id}... (Implementation needed)`); }

        function deletePractical(id) {
            const practical = currentPracticalData.find(a => a.id === id);
            if (!practical) return;

            if (confirm(`Are you sure you want to delete the practical "${practical.title}"? This action is irreversible.`)) {
                const success = window.db.deletePractical(id);
                if (success) {
                    alert('Practical deleted successfully.');
                    const user = getCurrentUser();
                    loadPracticalsFromDB(user);
                    renderPracticals(user);
                } else {
                    alert('Error deleting practical.');
                }
            }
        }
        
        // --- Create Practical Modal Logic ---
        document.getElementById('createPracticalBtn').addEventListener('click', () => {
            const user = getCurrentUser();
            const classSelect = document.getElementById('practicalClass');
            classSelect.innerHTML = '';
            
            const teacherClasses = window.db.getClasses(user.id);
            teacherClasses.forEach(cls => {
                const option = document.createElement('option');
                option.value = cls.id;
                option.textContent = cls.name;
                classSelect.appendChild(option);
            });
            
            document.getElementById('createPracticalModal').classList.add('active');
        });

        function validatePracticalData(practicalData) {
            if (!practicalData.title || practicalData.title.trim() === '') {
                alert('Title is required');
                return false;
            }
            if (!practicalData.classId || isNaN(practicalData.classId)) {
                alert('Valid class selection is required');
                return false;
            }
            if (!practicalData.dueDate) {
                alert('Due date is required');
                return false;
            }
            if (!practicalData.maxMarks || practicalData.maxMarks < 1) {
                alert('Valid max marks are required');
                return false;
            }
            return true;
        }

        document.getElementById('createPracticalForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const user = getCurrentUser();
            
            if (!user || user.role !== 'teacher') {
                alert('Only teachers can create practicals');
                return;
            }

            const newPractical = {
                title: document.getElementById('practicalTitle').value,
                description: document.getElementById('practicalDescription').value,
                classId: parseInt(document.getElementById('practicalClass').value),
                dueDate: document.getElementById('practicalDueDate').value,
                maxMarks: parseInt(document.getElementById('practicalMaxMarks').value),
                teacherId: user.id,
                status: 'pending',
                submissions: [],
                createdAt: new Date().toISOString()
            };

            if (!validatePracticalData(newPractical)) {
                return;
            }

            console.log('Attempting to create practical:', newPractical);
            const created = window.db.createPractical(newPractical);

            if (created) {
                alert('Practical created successfully!');
                document.getElementById('createPracticalModal').classList.remove('active');
                document.getElementById('createPracticalForm').reset();
                loadPracticalsFromDB(user);
                renderPracticals(user);
            } else {
                alert('Failed to create practical. Check console for details.');
            }
        });

        // Initial render
        document.addEventListener('DOMContentLoaded', () => {
            // Wait for database to load
            const initPracticals = () => {
                if (!window.db || !window.db.data) {
                    setTimeout(initPracticals, 100);
                    return;
                }

                const user = getCurrentUser();
                if (!user) {
                    alert('Please log in to access the portal.');
                    window.location.href = 'main.html';
                    return;
                }
                
                loadPracticalsFromDB(user);
                renderPracticals(user);
                setupUserUI(user);
                setActiveNavLink('practicals');
            };

            initPracticals();
        });
    </script>
</body>
</html>




Database Code:-
/**
 * Database Manager for Engineering Student Portal
 * Handles all CRUD operations with JSON database
 */

class DatabaseManager {
    constructor() {
        this.data = null;
        this.currentUser = null;
        this.loadCurrentUser();
    }

    async loadData() {
        try {
            const response = await fetch('./data.json');
            if (!response.ok) {
                throw new Error(`HTTP error! status: ${response.status}`);
            }
            this.data = await response.json();
            console.log('Database loaded successfully from JSON file');
            console.log('Loaded users:', this.data.users?.length || 0);
        } catch (error) {
            console.error('Error loading database from JSON file:', error);
            console.log('Initializing with default data...');
            
            // Initialize with default data if file doesn't exist or fails to load
            this.data = {
                users: [
                    {
                        id: 1,
                        name: "Sarthak Kumar",
                        email: "sarthak@engineering.edu",
                        password: "student123",
                        role: "student",
                        rollNo: "ENG001",
                        classId: 101,
                        address: "123 Main Street, City, State",
                        phone: "+1234567890",
                        dateOfBirth: "2002-05-15",
                        enrollmentYear: 2021,
                        department: "Computer Science",
                        createdAt: "2023-01-15T00:00:00Z",
                        lastLogin: new Date().toISOString()
                    },
                    {
                        id: 2,
                        name: "Dr. Priya Sharma",
                        email: "priya.sharma@engineering.edu",
                        password: "teacher123",
                        role: "teacher",
                        employeeId: "EMP001",
                        department: "Computer Science",
                        qualification: "PhD in Computer Science",
                        experience: 8,
                        address: "456 University Avenue, City, State",
                        phone: "+1234567891",
                        dateOfJoining: "2018-07-01",
                        createdAt: "2023-01-10T00:00:00Z",
                        lastLogin: new Date().toISOString()
                    }
                ],
                classes: [
                    {
                        id: 101,
                        name: "Data Structures and Algorithms",
                        code: "CS201",
                        department: "Computer Science",
                        teacherId: 2,
                        schedule: "Mon/Wed/Fri 10:00-11:00",
                        room: "CS-101",
                        semester: "Fall 2025",
                        credits: 4,
                        maxStudents: 60,
                        description: "Introduction to fundamental data structures and algorithms",
                        students: [1],
                        createdAt: "2025-08-01T00:00:00Z"
                    }
                ],
                assignments: [],
                practicals: [],
                attendance: [],
                grades: [],
                notifications: [],
                settings: {
                    academic_year: "2025-2026",
                    current_semester: "Fall 2025",
                    semester_start: "2025-08-01",
                    semester_end: "2025-12-15",
                    attendance_threshold: 75,
                    grading_scale: {
                        A: 90,
                        B: 80,
                        C: 70,
                        D: 60,
                        F: 0
                    }
                }
            };
            console.log('Default data initialized with users:', this.data.users.length);
        }
    }

    // Save data to localStorage (since we can't write to JSON file in browser)
    saveData() {
        try {
            localStorage.setItem('engineeringPortalData', JSON.stringify(this.data));
            console.log('Data saved successfully');
        } catch (error) {
            console.error('Error saving data:', error);
        }
    }

    // Load data from localStorage if available
    loadStoredData() {
        try {
            const storedData = localStorage.getItem('engineeringPortalData');
            if (storedData) {
                this.data = JSON.parse(storedData);
                console.log('Stored data loaded successfully');
                return true;
            }
            return false;
        } catch (error) {
            console.error('Error loading stored data:', error);
            return false;
        }
    }

    // Authentication Methods
    login(email, password) {
        if (!this.data || !this.data.users) {
            throw new Error('Database not loaded');
        }

        const user = this.data.users.find(u => 
            u.email.toLowerCase() === email.toLowerCase() && u.password === password
        );

        if (user) {
            // Update last login
            user.lastLogin = new Date().toISOString();
            this.currentUser = user;
            localStorage.setItem('currentUser', JSON.stringify(user));
            this.saveData();
            return user;
        }
        return null;
    }

    register(userData) {
        if (!this.data || !this.data.users) {
            throw new Error('Database not loaded');
        }

        // Check if email already exists
        const existingUser = this.data.users.find(u => 
            u.email.toLowerCase() === userData.email.toLowerCase()
        );

        if (existingUser) {
            throw new Error('Email already registered');
        }

        // Check if roll number already exists (for students)
        if (userData.role === 'student' && userData.rollNo) {
            const existingRoll = this.data.users.find(u => u.rollNo === userData.rollNo);
            if (existingRoll) {
                throw new Error('Roll number already registered');
            }
        }

        // Create new user
        const newUser = {
            id: this.generateId('users'),
            ...userData,
            createdAt: new Date().toISOString(),
            lastLogin: new Date().toISOString()
        };

        this.data.users.push(newUser);
        this.saveData();
        
        // Automatically log in the new user
        this.currentUser = newUser;
        localStorage.setItem('currentUser', JSON.stringify(newUser));
        
        return newUser;
    }

    logout() {
        this.currentUser = null;
        localStorage.removeItem('currentUser');
    }

    loadCurrentUser() {
        try {
            const userData = localStorage.getItem('currentUser');
            if (userData) {
                this.currentUser = JSON.parse(userData);
            }
        } catch (error) {
            console.error('Error loading current user:', error);
        }
    }

    getCurrentUser() {
        return this.currentUser;
    }

    // User Management
    getUsers(role = null) {
        if (!this.data || !this.data.users) return [];
        return role ? this.data.users.filter(u => u.role === role) : this.data.users;
    }

    getUserById(id) {
        if (!this.data || !this.data.users) return null;
        return this.data.users.find(u => u.id === id);
    }

    updateUser(userId, updates) {
        if (!this.data || !this.data.users) return false;
        const userIndex = this.data.users.findIndex(u => u.id === userId);
        if (userIndex !== -1) {
            this.data.users[userIndex] = { ...this.data.users[userIndex], ...updates };
            this.saveData();
            return true;
        }
        return false;
    }

    deleteUser(userId) {
        if (!this.data || !this.data.users) return false;
        const userIndex = this.data.users.findIndex(u => u.id === userId);
        if (userIndex !== -1) {
            this.data.users.splice(userIndex, 1);
            // Also remove user from any classes they are in
            if (this.data.classes) {
                this.data.classes.forEach(cls => {
                    if (cls.students) {
                        cls.students = cls.students.filter(studentId => studentId !== userId);
                    }
                });
            }
            this.saveData();
            return true;
        }
        return false;
    }

    // Class Management
    getClasses(teacherId = null, studentId = null) {
        if (!this.data || !this.data.classes) return [];
        let classes = this.data.classes;
        
        if (teacherId) {
            classes = classes.filter(c => c.teacherId === teacherId);
        }
        
        if (studentId) {
            classes = classes.filter(c => c.students && c.students.includes(studentId));
        }
        
        return classes;
    }

    getClassById(id) {
        if (!this.data || !this.data.classes) return null;
        return this.data.classes.find(c => c.id === id);
    }

    addStudentToClass(classId, studentId) {
        if (!this.data || !this.data.classes) return false;
        const classIndex = this.data.classes.findIndex(c => c.id === classId);
        if (classIndex !== -1) {
            if (!this.data.classes[classIndex].students) {
                this.data.classes[classIndex].students = [];
            }
            if (!this.data.classes[classIndex].students.includes(studentId)) {
                this.data.classes[classIndex].students.push(studentId);
                this.saveData();
                return true;
            }
        }
        return false;
    }

    removeStudentFromClass(classId, studentId) {
        if (!this.data || !this.data.classes) return false;
        const classIndex = this.data.classes.findIndex(c => c.id === classId);
        if (classIndex !== -1 && this.data.classes[classIndex].students) {
            this.data.classes[classIndex].students = this.data.classes[classIndex].students.filter(id => id !== studentId);
            this.saveData();
            return true;
        }
        return false;
    }

    addClass(classData) {
        if (!this.data || !this.data.classes) return false;
        const newClass = {
            id: this.generateId('classes'),
            ...classData,
            students: [],
            createdAt: new Date().toISOString()
        };
        this.data.classes.push(newClass);
        this.saveData();
        return true;
    }

    deleteClass(classId) {
        if (!this.data || !this.data.classes) return false;
        const classIndex = this.data.classes.findIndex(c => c.id === classId);
        if (classIndex !== -1) {
            this.data.classes.splice(classIndex, 1);
            // Also delete all assignments associated with this class
            if (this.data.assignments) {
                this.data.assignments = this.data.assignments.filter(a => a.classId !== classId);
            }
            this.saveData();
            return true;
        }
        return false;
    }

    // Assignment Management
    getAssignments(classId = null, studentId = null) {
        if (!this.data || !this.data.assignments) return [];
        let assignments = this.data.assignments;
        
        if (classId) {
            assignments = assignments.filter(a => a.classId === classId);
        }
        
        if (studentId) {
            // Get assignments for classes where student is enrolled
            const studentClasses = this.getClasses(null, studentId);
            const classIds = studentClasses.map(c => c.id);
            assignments = assignments.filter(a => classIds.includes(a.classId));
        }
        
        return assignments;
    }

    getAssignmentById(id) {
        if (!this.data || !this.data.assignments) return null;
        return this.data.assignments.find(a => a.id === id);
    }

    createAssignment(assignmentData) {
        if (!this.data || !this.data.assignments) return null;
        const newAssignment = {
            id: this.generateId('assignments'),
            ...assignmentData,
            submissions: [],
            createdDate: new Date().toISOString().split('T')[0],
            status: 'active'
        };
        this.data.assignments.push(newAssignment);
        this.saveData();
        return newAssignment;
    }

    submitAssignment(assignmentId, studentId, submissionData) {
        if (!this.data || !this.data.assignments) return false;
        const assignmentIndex = this.data.assignments.findIndex(a => a.id === assignmentId);
        if (assignmentIndex !== -1) {
            if (!this.data.assignments[assignmentIndex].submissions) {
                this.data.assignments[assignmentIndex].submissions = [];
            }
            
            // Remove existing submission if any
            this.data.assignments[assignmentIndex].submissions = 
                this.data.assignments[assignmentIndex].submissions.filter(s => s.studentId !== studentId);
            
            // Add new submission
            this.data.assignments[assignmentIndex].submissions.push({
                studentId,
                submittedAt: new Date().toISOString(),
                ...submissionData,
                marks: null,
                feedback: null,
                gradedAt: null,
                gradedBy: null
            });
            this.saveData();
            return true;
        }
        return false;
    }

    gradeAssignment(assignmentId, studentId, marks, feedback) {
        if (!this.data || !this.data.assignments) return false;
        const assignmentIndex = this.data.assignments.findIndex(a => a.id === assignmentId);
        if (assignmentIndex !== -1) {
            const submissionIndex = this.data.assignments[assignmentIndex].submissions
                .findIndex(s => s.studentId === studentId);
            if (submissionIndex !== -1) {
                this.data.assignments[assignmentIndex].submissions[submissionIndex].marks = marks;
                this.data.assignments[assignmentIndex].submissions[submissionIndex].feedback = feedback;
                this.data.assignments[assignmentIndex].submissions[submissionIndex].gradedAt = new Date().toISOString();
                this.data.assignments[assignmentIndex].submissions[submissionIndex].gradedBy = this.currentUser.id;
                this.saveData();
                return true;
            }
        }
        return false;
    }

    deleteAssignment(assignmentId) {
        if (!this.data || !this.data.assignments) return false;
        const assignmentIndex = this.data.assignments.findIndex(a => a.id === assignmentId);
        if (assignmentIndex !== -1) {
            this.data.assignments.splice(assignmentIndex, 1);
            this.saveData();
            return true;
        }
        return false;
    }

    // Practical Management
    getPracticals(classId = null, studentId = null) {
        if (!this.data || !this.data.practicals) return [];
        let practicals = this.data.practicals;
        
        if (classId) {
            practicals = practicals.filter(p => p.classId === classId);
        }
        
        if (studentId) {
            // Get practicals for classes where student is enrolled
            const studentClasses = this.getClasses(null, studentId);
            const classIds = studentClasses.map(c => c.id);
            practicals = practicals.filter(p => classIds.includes(p.classId));
        }
        
        return practicals;
    }

    getPracticalById(id) {
        if (!this.data || !this.data.practicals) return null;
        return this.data.practicals.find(p => p.id === id);
    }

    createPractical(practicalData) {
        try {
            if (!this.data.practicals) {
                this.data.practicals = [];
            }

            // Generate new ID
            const newId = this.data.practicals.length > 0 
                ? Math.max(...this.data.practicals.map(p => p.id)) + 1 
                : 1;

            // Create practical object
            const practical = {
                id: newId,
                ...practicalData,
                submissions: [],
                status: 'pending',
                createdAt: new Date().toISOString()
            };

            // Add to database
            this.data.practicals.push(practical);
            this.saveData();
            return true;
        } catch (error) {
            console.error('Error creating practical:', error);
            return false;
        }
    }

    submitPractical(practicalId, studentId, submissionData) {
        if (!this.data || !this.data.practicals) return false;
        const practicalIndex = this.data.practicals.findIndex(p => p.id === practicalId);
        if (practicalIndex !== -1) {
            if (!this.data.practicals[practicalIndex].submissions) {
                this.data.practicals[practicalIndex].submissions = [];
            }
            
            // Remove existing submission if any
            this.data.practicals[practicalIndex].submissions = 
                this.data.practicals[practicalIndex].submissions.filter(s => s.studentId !== studentId);
            
            // Add new submission
            this.data.practicals[practicalIndex].submissions.push({
                studentId,
                submittedAt: new Date().toISOString(),
                ...submissionData,
                marks: null,
                feedback: null,
                gradedAt: null,
                gradedBy: null
            });
            this.saveData();
            return true;
        }
        return false;
    }

    gradePractical(practicalId, studentId, marks, feedback) {
        if (!this.data || !this.data.practicals) return false;
        const practicalIndex = this.data.practicals.findIndex(p => p.id === practicalId);
        if (practicalIndex !== -1) {
            const submissionIndex = this.data.practicals[practicalIndex].submissions
                .findIndex(s => s.studentId === studentId);
            if (submissionIndex !== -1) {
                this.data.practicals[practicalIndex].submissions[submissionIndex].marks = marks;
                this.data.practicals[practicalIndex].submissions[submissionIndex].feedback = feedback;
                this.data.practicals[practicalIndex].submissions[submissionIndex].gradedAt = new Date().toISOString();
                this.data.practicals[practicalIndex].submissions[submissionIndex].gradedBy = this.currentUser.id;
                this.saveData();
                return true;
            }
        }
        return false;
    }

    deletePractical(practicalId) {
        if (!this.data || !this.data.practicals) return false;
        const practicalIndex = this.data.practicals.findIndex(p => p.id === practicalId);
        if (practicalIndex !== -1) {
            this.data.practicals.splice(practicalIndex, 1);
            this.saveData();
            return true;
        }
        return false;
    }

    // Attendance Management
    getAttendance(classId = null, studentId = null, date = null) {
        if (!this.data || !this.data.attendance) return [];
        let attendance = this.data.attendance;
        
        if (classId) {
            attendance = attendance.filter(a => a.classId === classId);
        }
        
        if (date) {
            attendance = attendance.filter(a => a.date === date);
        }
        
        if (studentId) {
            attendance = attendance.filter(a => 
                a.records && a.records.some(r => r.studentId === studentId)
            );
        }
        
        return attendance;
    }

    markAttendance(classId, date, records) {
        if (!this.data || !this.data.attendance) return false;
        
        // Remove existing attendance for the same class and date
        this.data.attendance = this.data.attendance.filter(a => 
            !(a.classId === classId && a.date === date)
        );
        
        // Add new attendance record
        const newAttendance = {
            id: this.generateId('attendance'),
            classId,
            date,
            records,
            markedBy: this.currentUser.id,
            markedAt: new Date().toISOString()
        };
        
        this.data.attendance.push(newAttendance);
        this.saveData();
        return true;
    }

    getStudentAttendanceStats(studentId) {
        if (!this.data || !this.data.attendance) return { total: 0, present: 0, absent: 0, percentage: 0 };
        
        let total = 0, present = 0;
        
        this.data.attendance.forEach(att => {
            const studentRecord = att.records.find(r => r.studentId === studentId);
            if (studentRecord) {
                total++;
                if (studentRecord.status === 'present') {
                    present++;
                }
            }
        });
        
        const absent = total - present;
        const percentage = total > 0 ? Math.round((present / total) * 100) : 0;
        
        return { total, present, absent, percentage };
    }

    // Grades Management
    getGrades(studentId = null, classId = null) {
        if (!this.data || !this.data.grades) return [];
        let grades = this.data.grades;
        
        if (studentId) {
            grades = grades.filter(g => g.studentId === studentId);
        }
        
        if (classId) {
            grades = grades.filter(g => g.classId === classId);
        }
        
        return grades;
    }

    // Notification Management
    getNotifications(userId = null) {
        if (!this.data || !this.data.notifications) return [];
        return userId ? 
            this.data.notifications.filter(n => n.userId === userId) : 
            this.data.notifications;
    }

    createNotification(userId, title, message, type = 'info') {
        if (!this.data || !this.data.notifications) return false;
        const notification = {
            id: this.generateId('notifications'),
            userId,
            title,
            message,
            type,
            read: false,
            createdAt: new Date().toISOString()
        };
        this.data.notifications.push(notification);
        this.saveData();
        return notification;
    }

    markNotificationAsRead(notificationId) {
        if (!this.data || !this.data.notifications) return false;
        const notificationIndex = this.data.notifications.findIndex(n => n.id === notificationId);
        if (notificationIndex !== -1) {
            this.data.notifications[notificationIndex].read = true;
            this.saveData();
            return true;
        }
        return false;
    }

    // Utility Methods
    generateId(collection) {
        if (!this.data || !this.data[collection]) return 1;
        const maxId = this.data[collection].length > 0 ? 
            Math.max(...this.data[collection].map(item => item.id)) : 0;
        return maxId + 1;
    }

    getSettings() {
        return this.data ? this.data.settings : {};
    }

    updateSettings(newSettings) {
        if (this.data) {
            this.data.settings = { ...this.data.settings, ...newSettings };
            this.saveData();
            return true;
        }
        return false;
    }
}

// Create global instance
window.db = new DatabaseManager();

// Initialize database
async function initializeDatabase() {
    try {
        // Try to load from localStorage first
        const hasStoredData = window.db.loadStoredData();
        
        // If no stored data or incomplete data, load from JSON file
        if (!hasStoredData || !window.db.data || !window.db.data.users || window.db.data.users.length === 0) {
            console.log('Loading fresh data from JSON file...');
            await window.db.loadData();
            window.db.saveData(); // Save to localStorage
        }
        
        console.log('Database initialized successfully');
        console.log('Users available:', window.db.data?.users?.length || 0);
    } catch (error) {
        console.error('Failed to initialize database:', error);
    }
}

// Initialize immediately
initializeDatabase();


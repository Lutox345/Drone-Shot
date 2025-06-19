<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drone-Shot Drone Services</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            padding: 0.5rem 1rem;
            border-radius: 25px;
        }

        .nav-links a:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .hero {
            text-align: center;
            padding: 4rem 0;
            color: white;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            animation: fadeInUp 1s ease;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .services {
            padding: 4rem 0;
        }

        .services h2 {
            text-align: center;
            color: white;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .service-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .service-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2.5rem;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .service-card:hover::before {
            left: 100%;
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 30px 60px rgba(0,0,0,0.2);
        }

        .service-card h3 {
            font-size: 1.8rem;
            color: #333;
            margin-bottom: 1rem;
            position: relative;
        }

        .price {
            font-size: 3rem;
            font-weight: bold;
            color: #667eea;
            margin-bottom: 1rem;
        }

        .service-card p {
            color: #666;
            margin-bottom: 2rem;
            font-size: 1.1rem;
        }

        .cta-button {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            position: relative;
            overflow: hidden;
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }

        .cta-button:active {
            transform: translateY(0);
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        .service-details {
            padding: 2rem 0;
        }

        .back-button {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid white;
            padding: 10px 20px;
            border-radius: 25px;
            text-decoration: none;
            display: inline-block;
            margin-bottom: 2rem;
            transition: all 0.3s ease;
        }

        .back-button:hover {
            background: white;
            color: #667eea;
        }

        .drone-options {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .drone-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            padding: 2rem;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .drone-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }

        .drone-card h4 {
            color: #667eea;
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .features {
            list-style: none;
            margin-bottom: 2rem;
        }

        .features li {
            padding: 0.5rem 0;
            color: #666;
            position: relative;
            padding-left: 1.5rem;
        }

        .features li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: #28a745;
            font-weight: bold;
        }

        .contact-info {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 2rem;
            border-radius: 15px;
            margin-top: 3rem;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .contact-info h3 {
            color: white;
            margin-bottom: 1rem;
            font-size: 1.8rem;
        }

        .contact-info p {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.1rem;
        }

        .email-link {
            color: #ffd700;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .email-link:hover {
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

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

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .service-grid {
                grid-template-columns: 1fr;
            }
            
            .drone-options {
                grid-template-columns: 1fr;
            }
            
            .nav-links {
                flex-direction: column;
                gap: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Homepage -->
    <div id="homepage" class="page active">
        <header>
            <nav class="container">
                <div class="logo">Drone-Shot</div>
                <ul class="nav-links">
                    <li><a href="#" onclick="showPage('homepage')">Home</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </header>

        <main class="container">
            <section class="hero">
                <h1>Professional Drone Services</h1>
                <p>Capture stunning aerial footage and photography with our premium drone services</p>
            </section>

            <section id="services" class="services">
                <h2>Our Service Packages</h2>
                <div class="service-grid">
                    <div class="service-card">
                        <h3>Normal</h3>
                        <div class="price">€50</div>
                        <p>High-quality aerial photography to capture your moments from above</p>
                        <button class="cta-button" onclick="showServiceDetails('normal')">Choose Normal</button>
                    </div>

                    <div class="service-card">
                        <h3>Plus</h3>
                        <div class="price">€80</div>
                        <p>Professional photography and videography package for comprehensive coverage</p>
                        <button class="cta-button" onclick="showServiceDetails('plus')">Choose Plus</button>
                    </div>

                    <div class="service-card">
                        <h3>Premium</h3>
                        <div class="price">€125</div>
                        <p>Complete package with professional editing and post-production for stunning results</p>
                        <button class="cta-button" onclick="showServiceDetails('premium')">Choose Premium</button>
                    </div>
                </div>
            </section>

            <section id="contact" class="contact-info">
                <h3>Ready to Get Started?</h3>
                <p>Contact us via email to book your drone service: <a href="mailto:drone-shot-lu@gmail.com" class="email-link">drone-shot-lu@gmail.com</a></p>
            </section>
        </main>
    </div>

    <!-- Service Details Pages -->
    <div id="normal-details" class="page">
        <header>
            <nav class="container">
                <div class="logo">Drone-Shot</div>
                <ul class="nav-links">
                    <li><a href="#" onclick="showPage('homepage')">Home</a></li>
                </ul>
            </nav>
        </header>

        <main class="container">
            <div class="service-details">
                <a href="#" class="back-button" onclick="showPage('homepage')">← Back to Services</a>
                
                <section class="hero">
                    <h1>Normal Package - €50</h1>
                    <p>Professional aerial photography services</p>
                </section>

                <div class="drone-options">
                    <div class="drone-card">
                        <h4>Normal Option - DJI Air 2S</h4>
                        <ul class="features">
                            <li>20MP professional aerial photography</li>
                            <li>High-resolution images in RAW format</li>
                            <li>Multiple angles and perspectives</li>
                            <li>1-hour shooting session</li>
                            <li>Basic color correction</li>
                            <li>Digital delivery within 48 hours</li>
                        </ul>
                        <p><strong>Perfect for:</strong> Real estate, events, landscapes, and personal projects</p>
                    </div>

                    <div class="drone-card">
                        <h4>FPV Option - DJI Avata</h4>
                        <ul class="features">
                            <li>Dynamic FPV aerial photography</li>
                            <li>Unique cinematic angles and movements</li>
                            <li>High-speed capturing capabilities</li>
                            <li>Creative perspective shots</li>
                            <li>1-hour FPV shooting session</li>
                            <li>Digital delivery within 48 hours</li>
                        </ul>
                        <p><strong>Perfect for:</strong> Action shots, creative content, and dynamic perspectives</p>
                    </div>
                </div>

                <div class="contact-info">
                    <h3>Book Your Normal Package</h3>
                    <p>Ready to capture stunning aerial photos? Contact us at: <a href="mailto:info@skycapture.com" class="email-link">info@skycapture.com</a></p>
                </div>
            </div>
        </main>
    </div>

    <div id="plus-details" class="page">
        <header>
            <nav class="container">
                <div class="logo">Drone-Shot</div>
                <ul class="nav-links">
                    <li><a href="#" onclick="showPage('homepage')">Home</a></li>
                </ul>
            </nav>
        </header>

        <main class="container">
            <div class="service-details">
                <a href="#" class="back-button" onclick="showPage('homepage')">← Back to Services</a>
                
                <section class="hero">
                    <h1>Plus Package - €80</h1>
                    <p>Complete photography and videography package</p>
                </section>

                <div class="drone-options">
                    <div class="drone-card">
                        <h4>Normal Option - DJI Air 2S</h4>
                        <ul class="features">
                            <li>20MP professional aerial photography</li>
                            <li>4K video recording at 60fps</li>
                            <li>Multiple photo angles and compositions</li>
                            <li>2-3 minute highlight video</li>
                            <li>2-hour shooting session</li>
                            <li>Basic editing and color grading</li>
                            <li>Digital delivery within 72 hours</li>
                        </ul>
                        <p><strong>Perfect for:</strong> Weddings, corporate events, property showcases</p>
                    </div>

                    <div class="drone-card">
                        <h4>FPV Option - DJI Avata</h4>
                        <ul class="features">
                            <li>Dynamic FPV photography and videography</li>
                            <li>Cinematic flight movements and transitions</li>
                            <li>High-speed action video recording</li>
                            <li>Creative perspective photography</li>
                            <li>2-hour FPV shooting session</li>
                            <li>Basic editing and stabilization</li>
                            <li>Digital delivery within 72 hours</li>
                        </ul>
                        <p><strong>Perfect for:</strong> Sports events, promotional content, adventure activities</p>
                    </div>
                </div>

                <div class="contact-info">
                    <h3>Book Your Plus Package</h3>
                    <p>Ready for comprehensive aerial coverage? Contact us at: <a href="mailto:info@skycapture.com" class="email-link">info@skycapture.com</a></p>
                </div>
            </div>
        </main>
    </div>

    <div id="premium-details" class="page">
        <header>
            <nav class="container">
                <div class="logo">Drone-Shot</div>
                <ul class="nav-links">
                    <li><a href="#" onclick="showPage('homepage')">Home</a></li>
                </ul>
            </nav>
        </header>

        <main class="container">
            <div class="service-details">
                <a href="#" class="back-button" onclick="showPage('homepage')">← Back to Services</a>
                
                <section class="hero">
                    <h1>Premium Package - €125</h1>
                    <p>Professional video production with full editing</p>
                </section>

                <div class="drone-options">
                    <div class="drone-card">
                        <h4>Normal Option - DJI Air 2S</h4>
                        <ul class="features">
                            <li>Professional 20MP aerial photography</li>
                            <li>4K cinematic video production</li>
                            <li>Professional video editing and post-production</li>
                            <li>Color grading and audio enhancement</li>
                            <li>5-8 minute final edited video</li>
                            <li>3-hour shooting session</li>
                            <li>Multiple delivery formats</li>
                            <li>Delivery within 5-7 business days</li>
                        </ul>
                        <p><strong>Perfect for:</strong> Commercial projects, marketing videos, documentaries</p>
                    </div>

                    <div class="drone-card">
                        <h4>FPV Option - DJI Avata</h4>
                        <ul class="features">
                            <li>Professional FPV cinematography</li>
                            <li>Advanced flight maneuvers and shots</li>
                            <li>Professional editing with effects</li>
                            <li>Smooth transitions and cinematic flow</li>
                            <li>Music and sound design</li>
                            <li>3-hour FPV shooting session</li>
                            <li>Custom graphics and titles</li>
                            <li>Delivery within 5-7 business days</li>
                        </ul>
                        <p><strong>Perfect for:</strong> Brand videos, social media content, artistic projects</p>
                    </div>
                </div>

                <div class="contact-info">
                    <h3>Book Your Premium Package</h3>
                    <p>Ready for professional video production? Contact us at: <a href="mailto:info@skycapture.com" class="email-link">info@skycapture.com</a></p>
                </div>
            </div>
        </main>
    </div>

    <script>
        function showPage(pageId) {
            // Hide all pages
            const pages = document.querySelectorAll('.page');
            pages.forEach(page => page.classList.remove('active'));
            
            // Show selected page
            document.getElementById(pageId).classList.add('active');
            
            // Scroll to top
            window.scrollTo(0, 0);
        }

        function showServiceDetails(service) {
            showPage(service + '-details');
        }

        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                if (this.getAttribute('href') !== '#') {
                    e.preventDefault();
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth'
                        });
                    }
                }
            });
        });
    </script>
</body>
</html>

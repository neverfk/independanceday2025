<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alok and Vikash Telecom</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/chart.js">
    <link rel="icon" href="logo (1).png" type="image/x-icon">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Comic Sans MS', cursive, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            min-height: 100vh;
            color: #333;
            overflow-x: hidden;
        }

        /* Header Styles */
        header {
            background: rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            padding: 20px 0;
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            animation: slideDown 0.8s ease-out;
        }

        @keyframes slideDown {
            from { transform: translateY(-100%); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .logo {
            text-align: center;
            margin-bottom: 20px;
        }

        .logo h1 {
            font-size: 2.8rem;
            background: linear-gradient(to right, #ff00cc 0%, #3333ff 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            display: inline-block;
            animation: bounce 2s infinite;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* Navigation */
        .nav-bar {
            display: flex;
            justify-content: center;
            gap: 15px;
            padding: 0 20px;
        }

        .nav-btn {
            background: rgba(255, 255, 255, 0.3);
            border: 2px solid rgba(255,255,255,0.5);
            padding: 12px 25px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: 600;
            color: #fff;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
        }

        .nav-btn:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
            color: white;
        }

        .nav-btn:nth-child(1):hover { background: rgba(255, 105, 180, 0.6); }
        .nav-btn:nth-child(2):hover { background: rgba(100, 200, 255, 0.6); }
        .nav-btn:nth-child(3):hover { background: rgba(255, 215, 0, 0.6); }
        .nav-btn:nth-child(4):hover { background: rgba(50, 205, 50, 0.6); }
        .nav-btn:nth-child(5):hover { background: rgba(138, 43, 226, 0.6); }

        /* Page Content */
        .page-content {
            display: none;
            margin-top: 180px;
            padding: 20px;
            animation: fadeIn 0.5s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .active-page {
            display: block;
        }

        /* Home Page */
        :root {
            --primary: #FF6B6B;
            --secondary: #4ECDC4;
            --accent: #FFE66D;
            --dark: #292F36;
            --light: #F7FFF7;
        }

        .home-page {
            padding: 0;
            margin-top: 180px;
        }

        .home-header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            padding: 1rem;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        .home-logo {
            font-size: 2.5rem;
            font-weight: bold;
            color: white;
            text-shadow: 3px 3px 0 var(--dark), 6px 6px 0 rgba(0,0,0,0.1);
            margin-bottom: 0.5rem;
        }

        .tagline {
            color: white;
            font-size: 1.2rem;
            margin-bottom: 1rem;
        }

        .hero {
            height: 60vh;
            background: url('https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80') center/cover;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .hero::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(255,107,107,0.7), rgba(78,205,196,0.7));
        }

        .hero-content {
            text-align: center;
            color: white;
            z-index: 1;
            padding: 2rem;
            max-width: 800px;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 0 var(--dark);
            animation: bounce 2s infinite;
        }

        .hero p {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        /* Services Page */
        .services-header {
            text-align: center;
            padding: 20px;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            border-radius: 20px;
            margin: 20px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.1);
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .services-header h2 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            animation: bounce 2s infinite;
        }

        .services-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            padding: 20px;
        }

        .service-card {
            background: rgba(255, 255, 255, 0.7);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
            border-top: 5px solid var(--card-color);
        }

        .service-card:hover {
            transform: translateY(-10px) scale(1.03);
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }

        .service-icon {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 15px;
        }

        .service-card h3 {
            color: #333;
            font-size: 1.5rem;
            margin-bottom: 15px;
            text-align: center;
        }

        .service-features {
            list-style-type: none;
            margin-bottom: 20px;
        }

        .service-features li {
            padding: 8px 0;
            border-bottom: 1px dashed rgba(0,0,0,0.1);
            position: relative;
            padding-left: 25px;
        }

        .service-features li:before {
            content: "✓";
            color: var(--card-color);
            font-weight: bold;
            position: absolute;
            left: 0;
        }

        .price-bubble {
            background: var(--card-color);
            color: white;
            padding: 8px 15px;
            border-radius: 50px;
            display: inline-block;
            font-weight: bold;
            position: absolute;
            bottom: -10px;
            right: 20px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            animation: floatUp 3s infinite ease-in-out;
        }

        @keyframes floatUp {
            0%, 100% { transform: translateY(0) rotate(-5deg); }
            50% { transform: translateY(-8px) rotate(5deg); }
        }

        /* Review Page */
        .review-container {
            max-width: 800px;
            margin: 20px auto;
            padding: 30px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .review-form {
            margin: 30px 0;
            padding: 20px;
            background: rgba(255,255,255,0.8);
            border-radius: 15px;
        }

        .rating-stars {
            margin: 15px 0;
            font-size: 2rem;
            cursor: pointer;
            display: flex;
            gap: 5px;
        }

        .rating-stars .star {
            color: #ddd;
            transition: all 0.3s;
        }

        .rating-stars .star.active,
        .rating-stars .star:hover {
            color: #FFD700;
            text-shadow: 0 0 10px rgba(255,215,0,0.5);
        }

        #rating-value {
            font-weight: bold;
            color: #FF6B6B;
            margin-left: 10px;
            font-size: 1.5rem;
        }

        .form-group {
            margin: 20px 0;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #333;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            transition: all 0.3s;
            background: rgba(255,255,255,0.8);
        }

        .review-btn {
            background: linear-gradient(135deg, #FF6B6B, #4ECDC4);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            display: block;
            margin: 0 auto;
        }

        .review-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }

        .reviews-list {
            margin-top: 40px;
        }

        .review-item {
            background: rgba(255,255,255,0.8);
            padding: 20px;
            margin: 15px 0;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .review-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .review-rating {
            color: #FFD700;
            font-size: 1.2rem;
        }

        .review-date {
            color: #777;
            font-size: 0.9rem;
        }

        /* About Page */
        .about-container {
            max-width: 1000px;
            margin: 20px auto;
            padding: 30px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .about-section {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin: 30px 0;
        }

        .about-card {
            flex: 1;
            min-width: 300px;
            background: rgba(255, 255, 255, 0.7);
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .about-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
        }

        .contact-section {
            margin: 40px 0;
            padding: 20px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 15px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            margin: 15px 0;
            font-size: 1.1rem;
        }

        .contact-icon {
            font-size: 1.5rem;
            margin-right: 15px;
            width: 30px;
            text-align: center;
        }

        .map-container {
            margin-top: 30px;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .timing-section {
            margin: 40px 0;
            padding: 20px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 15px;
        }

        /* Footer */
        footer {
            background: rgba(0, 0, 0, 0.6);
            color: white;
            text-align: center;
            padding: 30px 0;
            margin-top: 50px;
            border-top-left-radius: 20px;
            border-top-right-radius: 20px;
        }

        .social-icons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        .social-icons a {
            color: white;
            font-size: 1.8rem;
            transition: all 0.3s ease;
            background: rgba(255,255,255,0.2);
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
        }

        .social-icons a:hover {
            transform: translateY(-5px) scale(1.1);
            background: rgba(255,255,255,0.4);
        }

        .social-icons a:nth-child(1):hover { background: #25D366; }
        .social-icons a:nth-child(2):hover { background: #34B7F1; }
        .social-icons a:nth-child(3):hover { background: #D44638; }
        .social-icons a:nth-child(4):hover { background: #FFA500; }

        /* Admin Modal */
        .admin-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            z-index: 2000;
            animation: fadeIn 0.3s;
        }

        .admin-modal-content {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            margin: 5% auto;
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 5px 30px rgba(0,0,0,0.3);
            width: 90%;
            max-width: 1200px;
            position: relative;
            animation: slideUp 0.4s;
        }

        .close-admin {
            position: absolute;
            top: 15px;
            right: 25px;
            font-size: 2rem;
            color: #FF6B6B;
            cursor: pointer;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-bar {
                flex-wrap: wrap;
            }
            
            .nav-btn {
                padding: 10px 15px;
                font-size: 1rem;
            }
            
            .logo h1, .home-logo {
                font-size: 2rem;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .hero p {
                font-size: 1.2rem;
            }

            .services-header h2 {
                font-size: 2rem;
            }

            .review-container {
                padding: 20px;
            }
            
            .about-card {
                min-width: 100%;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">
            <h1>Alok and Vikash Telecom</h1>
        </div>
        <div class="nav-bar">
            <button class="nav-btn" onclick="showPage('home-page')">Home</button>
            <button class="nav-btn" onclick="showPage('services-page')">Services</button>
            <button class="nav-btn" onclick="showAdminModal()">Admin</button>
            <button class="nav-btn" onclick="showPage('review-page')">Review</button>
            <button class="nav-btn" onclick="showPage('about-page')">About</button>
        </div>
    </header>

    <!-- Home Page -->
    <div id="home-page" class="page-content home-page active-page">
        <div class="home-header">
            <h1 class="home-logo">Alok & Vikash Telecom</h1>
            <p class="tagline">Your One-Stop Solution for Mobile Accessories & Services</p>
        </div>
        
        <section class="hero">
            <div class="hero-content">
                <h1>Mobile Accessories & More!</h1>
                <p>We provide everything from mobile accessories to money transfer services, document services and much more!</p>
            </div>
            
            <div class="bubble" style="width: 50px; height: 50px; top: 20%; left: 10%;"></div>
            <div class="bubble" style="width: 30px; height: 30px; top: 70%; left: 80%;"></div>
            <div class="bubble" style="width: 40px; height: 40px; top: 40%; left: 70%;"></div>
            <div class="bubble" style="width: 60px; height: 60px; top: 80%; left: 20%;"></div>
        </section>
    </div>

    <!-- Services Page -->
    <div id="services-page" class="page-content">
        <div class="services-header">
            <h2>Our Awesome Services</h2>
            <p>One-stop solution for all your telecom and document needs!</p>
        </div>

        <div class="services-container">
            <!-- Mobile Services -->
            <div class="service-card" style="--card-color: #FF9AA2;">
                <div class="service-icon">📱</div>
                <h3>Mobile Services</h3>
                <ul class="service-features">
                    <li>Mobile Recharge (All Operators)</li>
                    <li>DTH Recharge</li>
                    <li>Mobile Unlocking</li>
                    <li>Aadhaar-Mobile Link</li>
                    <li>New SIM Activation</li>
                </ul>
                <div class="price-bubble">Instant</div>
            </div>

            <!-- Banking Services -->
            <div class="service-card" style="--card-color: #FFB7B2;">
                <div class="service-icon">🏦</div>
                <h3>Banking Services</h3>
                <ul class="service-features">
                    <li>Account Opening</li>
                    <li>AEPS Money Transfer</li>
                    <li>Mini Statement</li>
                    <li>Balance Inquiry</li>
                    <li>Cash Withdrawal</li>
                </ul>
                <div class="price-bubble">24/7</div>
            </div>

            <!-- Document Services -->
            <div class="service-card" style="--card-color: #FFDAC1;">
                <div class="service-icon">📄</div>
                <h3>Document Services</h3>
                <ul class="service-features">
                    <li>PAN Card (2 Hours)</li>
                    <li>Voter ID Card</li>
                    <li>Driving License</li>
                    <li>Aadhaar Services</li>
                    <li>EPFO Services</li>
                </ul>
                <div class="price-bubble">Fast</div>
            </div>

            <!-- Government Schemes -->
            <div class="service-card" style="--card-color: #E2F0CB;">
                <div class="service-icon">🪪</div>
                <h3>Government Schemes</h3>
                <ul class="service-features">
                    <li>Ayushman Bharat Card</li>
                    <li>e-Shram Card</li>
                    <li>PM Kisan Registration</li>
                    <li>Ration Card</li>
                    <li>Pension Services</li>
                </ul>
                <div class="price-bubble">Govt Approved</div>
            </div>

            <!-- Money Transfer -->
            <div class="service-card" style="--card-color: #B5EAD7;">
                <div class="service-icon">💸</div>
                <h3>Money Services</h3>
                <ul class="service-features">
                    <li>Domestic Money Transfer</li>
                    <li>Utility Bill Payments</li>
                    <li>Insurance Premium</li>
                    <li>Loan Repayment</li>
                    <li>Micro ATM Services</li>
                </ul>
                <div class="price-bubble">Secure</div>
            </div>

            <!-- Accessories & Repair -->
            <div class="service-card" style="--card-color: #C7CEEA;">
                <div class="service-icon">🔧</div>
                <h3>Mobile Care</h3>
                <ul class="service-features">
                    <li>Mobile Accessories</li>
                    <li>Screen Replacement</li>
                    <li>Battery Replacement</li>
                    <li>Software Repair</li>
                    <li>Water Damage Repair</li>
                </ul>
                <div class="price-bubble">Warranty</div>
            </div>

            <!-- Printing Services -->
            <div class="service-card" style="--card-color: #FFC8DD;">
                <div class="service-icon">🖨️</div>
                <h3>Printing Services</h3>
                <ul class="service-features">
                    <li>Photocopy & Printing</li>
                    <li>Passport Photos</li>
                    <li>Document Lamination</li>
                    <li>Form Filling</li>
                    <li>Online Application</li>
                </ul>
                <div class="price-bubble">₹5/page</div>
            </div>

            <!-- Special Services -->
            <div class="service-card" style="--card-color: #CDB4DB;">
                <div class="service-icon">✨</div>
                <h3>Special Services</h3>
                <ul class="service-features">
                    <li>Fast PAN Card in 2 Hours</li>
                    <li>Voter ID Correction</li>
                    <li>Driving License Renewal</li>
                    <li>e-Shram Card Registration</li>
                    <li>Ayushman Card Apply</li>
                </ul>
                <div class="price-bubble">Express</div>
            </div>
        </div>
    </div>

    <!-- Review Page -->
    <div id="review-page" class="page-content">
        <div class="review-container">
            <h2>Share Your Experience</h2>
            <p>We value your feedback! Please rate our services and leave a review.</p>
            
            <div class="review-form">
                <div class="rating-stars">
                    <span class="star" data-value="1">☆</span>
                    <span class="star" data-value="2">☆</span>
                    <span class="star" data-value="3">☆</span>
                    <span class="star" data-value="4">☆</span>
                    <span class="star" data-value="5">☆</span>
                    <span id="rating-value">0</span>/5
                </div>
                
                <div class="form-group">
                    <label for="reviewer-name">Your Name:</label>
                    <input type="text" id="reviewer-name" placeholder="Enter your name">
                </div>
                
                <div class="form-group">
                    <label for="review-text">Your Review:</label>
                    <textarea id="review-text" rows="5" placeholder="Share your experience..."></textarea>
                </div>
                
                <button id="submit-review" class="review-btn">Submit Review</button>
            </div>
            
            <div class="reviews-list">
                <h3>Customer Reviews</h3>
                <div id="live-reviews">
                    <!-- Reviews will appear here -->
                </div>
            </div>
        </div>
    </div>

    <!-- About Page -->
    <div id="about-page" class="page-content">
        <div class="about-container">
            <h2>About Alok and Vikash Telecom</h2>
            
            <div class="about-section">
                <div class="about-card">
                    <div class="about-icon">🏪</div>
                    <h3>Our Story</h3>
                    <p>Alok and Vikash Telecom has been serving the Kohara community since 2018, providing reliable telecom services and digital solutions.</p>
                </div>
                
                <div class="about-card">
                    <div class="about-icon">🎯</div>
                    <h3>Our Mission</h3>
                    <p>To provide fast, affordable, and reliable digital services to our community.</p>
                </div>
            </div>
            
            <div class="contact-section">
                <h3>📞 Contact Us</h3>
                <div class="contact-info">
                    <div class="contact-item">
                        <span class="contact-icon">📱</span>
                        <span>Alok: <a href="tel:8264161178">8264161178</a></span>
                    </div>
                    <div class="contact-item">
                        <span class="contact-icon">📱</span>
                        <span>Rahul: <a href="tel:8507712361">8507712361</a></span>
                    </div>
                    <div class="contact-item">
                        <span class="contact-icon">✉️</span>
                        <span>Email: <a href="mailto:alokvikascyberzone@gmail.com">alokvikascyberzone@gmail.com</a></span>
                    </div>
                    <div class="contact-item">
                        <span class="contact-icon">🏠</span>
                        <span>Address: Village Mehlon, Lakhowal Road, Kohara, Ludhiana, Punjab - 141112</span>
                    </div>
                </div>
                
                <div class="map-container">
                    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3416.789567832029!2d75.8765383151343!3d31.0664099814935!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x391a5a594d22b88d%3A0x4a2a5d5b5d5b5d5b!2sKohara%2C%20Ludhiana%2C%20Punjab%20141112!5e0!3m2!1sen!2sin!4v1620000000000!5m2!1sen!2sin" width="100%" height="300" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
                </div>
            </div>
            
            <div class="timing-section">
                <h3>⏰ Opening Hours</h3>
                <ul class="timing-list">
                    <li><strong>Monday - Saturday:</strong> 9:00 AM - 8:00 PM</li>
                    <li><strong>Sunday:</strong> 10:00 AM - 2:00 PM</li>
                    <li><strong>Public Holidays:</strong> Open with reduced hours</li>
                </ul>
            </div>
        </div>
    </div>

    <footer>
        <p>© 2018 Alok and Vikash Telecom. All rights reserved.</p>
        <p>Your trusted mobile connection</p>
        <div class="social-icons">
            <a href="https://wa.me/918507712361" target="_blank" title="WhatsApp">
                <i class="fab fa-whatsapp"></i>
            </a>
            <a href="tel:8264161178" title="Call">
                <i class="fas fa-phone-alt"></i>
            </a>
            <a href="mailto:alokvikascyberzone@gmail.com" title="Email">
                <i class="fas fa-envelope"></i>
            </a>
            <a href="#" title="Visit Shop">
                <i class="fas fa-store"></i>
            </a>
        </div>
    </footer>

    <!-- Admin Portal Modal -->
    <div id="adminModal" class="admin-modal">
        <div class="admin-modal-content">
            <span class="close-admin" onclick="closeAdminModal()">&times;</span>
            <div id="adminPortalContent"></div>
        </div>
    </div>

    <script>
        // Global variables
        let allReviews = [];
        let allRecords = [];
        let methodChart, dailyChart;

        // Page Navigation
        function showPage(pageId) {
            const pages = document.querySelectorAll('.page-content');
            pages.forEach(page => {
                page.classList.remove('active-page');
            });
            document.getElementById(pageId).classList.add('active-page');
            
            if (pageId === 'review-page') {
                displayLiveReviews();
            }
        }

        // Admin Modal Functions
        function showAdminModal() {
            document.getElementById('adminPortalContent').innerHTML = `
                <div class="admin-container">
                    <div id="admin-login" class="admin-login-form">
                        <h2>🔐 Admin Login</h2>
                        <form id="loginForm">
                            <div class="form-group">
                                <label for="username">Username (Mobile Number):</label>
                                <input type="text" id="username" name="username" required placeholder="Enter your mobile number">
                            </div>
                            <div class="form-group">
                                <label for="password">Password:</label>
                                <input type="password" id="password" name="password" required placeholder="Enter your password">
                            </div>
                            <button type="submit" class="admin-btn">🚀 Login</button>
                        </form>
                    </div>

                    <div id="admin-dashboard" class="admin-dashboard" style="display:none;">
                        <div class="admin-header">
                            <h2>🎛️ Admin Dashboard</h2>
                            <div class="admin-info">
                                <span id="logged-in-user"></span>
                                <button id="logout-btn" class="admin-btn logout-btn">👋 Logout</button>
                            </div>
                        </div>
                        
                        <div class="admin-tabs">
                            <button class="tab-btn active" onclick="openTab('reviews-tab')">🌟 Reviews</button>
                            <button class="tab-btn" onclick="openTab('record-tab')">💳 Records</button>
                            <button class="tab-btn" onclick="openTab('submitted-tab')">📋 Submissions</button>
                            <button class="tab-btn" onclick="openTab('stats-tab')">📊 Stats</button>
                        </div>
                        
                        <!-- Reviews Tab -->
                        <div id="reviews-tab" class="admin-tab-content active-tab">
                            <div class="admin-actions">
                                <button class="admin-btn" onclick="showPendingReviews()">⏳ Pending</button>
                                <button class="admin-btn" onclick="showApprovedReviews()">✅ Approved</button>
                            </div>
                            
                            <div id="reviews-list" class="reviews-container">
                                <!-- Reviews will be loaded here -->
                            </div>
                        </div>
                        
                        <!-- Record History Tab -->
                        <div id="record-tab" class="admin-tab-content">
                            <div class="payment-methods">
                                <h3>💸 Select Payment Method</h3>
                                <div class="method-options">
                                    <button class="method-btn" onclick="showRoinetForm()">🔄 Roinet</button>
                                    <button class="method-btn" onclick="showSpiceForm()">🌶️ Spice</button>
                                    <button class="method-btn" onclick="showPayNearbyForm()">🏪 PayNearby</button>
                                    <button class="method-btn" onclick="showATMCardForm()">💳 ATM Card</button>
                                    <button class="method-btn" onclick="showQRForm()">📱 QR Code</button>
                                    <button class="method-btn" onclick="showManualForm()">✍️ Manual</button>
                                </div>
                                
                                <!-- Digital Payment Form -->
                                <div id="digital-form" class="record-form" style="display:none;">
                                    <h4 id="digital-form-title">🔄 Digital Payment Form</h4>
                                    <form id="digitalPaymentForm">
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="customer-name">👤 Customer Name:</label>
                                                <input type="text" id="customer-name" required placeholder="Enter customer name">
                                            </div>
                                            <div class="form-group">
                                                <label for="aadhar-number">🆔 Aadhar Number:</label>
                                                <input type="text" id="aadhar-number" pattern="\\d{12}" required placeholder="12 digit Aadhar">
                                            </div>
                                        </div>
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="mobile-number">📱 Mobile Number:</label>
                                                <input type="tel" id="mobile-number" required placeholder="Customer mobile">
                                            </div>
                                            <div class="form-group">
                                                <label for="amount">💰 Amount (₹):</label>
                                                <input type="number" id="amount" required placeholder="Enter amount">
                                            </div>
                                        </div>
                                        <div class="form-group">
                                            <label for="bank-name">🏦 Bank Name:</label>
                                            <input type="text" id="bank-name" required placeholder="Bank name">
                                        </div>
                                        <div class="form-group">
                                            <label for="customer-address">🏠 Address:</label>
                                            <textarea id="customer-address" required placeholder="Customer address"></textarea>
                                        </div>
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="rrn-number">🔢 RRN Number:</label>
                                                <input type="text" id="rrn-number" placeholder="Transaction RRN">
                                            </div>
                                            <div class="form-group">
                                                <label for="signature">✍️ Signature:</label>
                                                <input type="text" id="signature" required placeholder="Customer signature">
                                            </div>
                                        </div>
                                        <div class="form-buttons">
                                            <button type="submit" class="admin-btn">📤 Submit</button>
                                            <button type="button" class="admin-btn cancel-btn" onclick="resetForms()">❌ Cancel</button>
                                        </div>
                                    </form>
                                </div>
                                
                                <!-- ATM Card Form -->
                                <div id="atm-form" class="record-form" style="display:none;">
                                    <h4>💳 ATM Card Payment</h4>
                                    <form id="atmPaymentForm">
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="card-number">💳 Card Number:</label>
                                                <input type="text" id="card-number" pattern="\\d{16}" required placeholder="16 digit card number">
                                            </div>
                                            <div class="form-group">
                                                <label for="expiry-date">📅 Expiry Date:</label>
                                                <input type="text" id="expiry-date" placeholder="MM/YY" required>
                                            </div>
                                        </div>
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="cvv">🔐 CVV:</label>
                                                <input type="text" id="cvv" pattern="\\d{3}" required placeholder="3 digit CVV">
                                            </div>
                                            <div class="form-group">
                                                <label for="atm-customer-name">👤 Customer Name:</label>
                                                <input type="text" id="atm-customer-name" required placeholder="Cardholder name">
                                            </div>
                                        </div>
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="atm-amount">💰 Amount (₹):</label>
                                                <input type="number" id="atm-amount" required placeholder="Enter amount">
                                            </div>
                                            <div class="form-group">
                                                <label for="atm-mobile">📱 Mobile Number:</label>
                                                <input type="tel" id="atm-mobile" required placeholder="Customer mobile">
                                            </div>
                                        </div>
                                        <div class="form-group">
                                            <label for="atm-address">🏠 Address:</label>
                                            <textarea id="atm-address" required placeholder="Customer address"></textarea>
                                        </div>
                                        <div class="form-group">
                                            <label for="atm-signature">✍️ Signature:</label>
                                            <input type="text" id="atm-signature" required placeholder="Customer signature">
                                        </div>
                                        <div class="form-buttons">
                                            <button type="submit" class="admin-btn">📤 Submit</button>
                                            <button type="button" class="admin-btn cancel-btn" onclick="resetForms()">❌ Cancel</button>
                                        </div>
                                    </form>
                                </div>
                                
                                <!-- QR Code Form -->
                                <div id="qr-form" class="record-form" style="display:none;">
                                    <h4>📱 QR Code Payment</h4>
                                    <form id="qrPaymentForm">
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="qr-customer-name">👤 Customer Name:</label>
                                                <input type="text" id="qr-customer-name" required placeholder="Enter customer name">
                                            </div>
                                            <div class="form-group">
                                                <label for="qr-mobile">📱 Mobile Number:</label>
                                                <input type="tel" id="qr-mobile" required placeholder="Customer mobile">
                                            </div>
                                        </div>
                                        <div class="form-row">
                                            <div class="form-group">
                                                <label for="qr-amount">💰 Amount (₹):</label>
                                                <input type="number" id="qr-amount" required placeholder="Enter amount">
                                            </div>
                                            <div class="form-group">
                                                <label for="qr-bank">🏦 Bank Name:</label>
                                                <input type="text" id="qr-bank" required placeholder="Bank name">
                                            </div>
                                        </div>
                                        <div class="form-group">
                                            <label for="qr-address">🏠 Address:</label>
                                            <textarea id="qr-address" required placeholder="Customer address"></textarea>
                                        </div>
                                        <div class="form-group">
                                            <label for="qr-signature">✍️ Signature:</label>
                                            <input type="text" id="qr-signature" required placeholder="Customer signature">
                                        </div>
                                        <div class="form-buttons">
                                            <button type="submit" class="admin-btn">📤 Submit</button>
                                            <button type="button" class="admin-btn cancel-btn" onclick="resetForms()">❌ Cancel</button>
                                        </div>
                                    </form>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Submitted Details Tab -->
                        <div id="submitted-tab" class="admin-tab-content">
                            <div class="search-filter">
                                <input type="text" id="search-records" placeholder="🔍 Search records...">
                                <select id="filter-method">
                                    <option value="all">All Methods</option>
                                    <option value="roinet">🔄 Roinet</option>
                                    <option value="spice">🌶️ Spice</option>
                                    <option value="paynearby">🏪 PayNearby</option>
                                    <option value="atm">💳 ATM Card</option>
                                    <option value="qr">📱 QR Code</option>
                                    <option value="manual">✍️ Manual</option>
                                </select>
                                <button class="admin-btn" onclick="filterRecords()">🔎 Filter</button>
                                <button class="admin-btn" onclick="exportToExcel()">📊 Export</button>
                            </div>
                            
                            <div id="submitted-records" class="records-container">
                                <!-- Submitted records will appear here -->
                            </div>
                        </div>
                        
                        <!-- Statistics Tab -->
                        <div id="stats-tab" class="admin-tab-content">
                            <div class="stats-container">
                                <div class="stat-card">
                                    <div class="stat-icon">💰</div>
                                    <div class="stat-value" id="total-transactions">0</div>
                                    <div class="stat-label">Total Transactions</div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon">💵</div>
                                    <div class="stat-value" id="total-amount">₹0</div>
                                    <div class="stat-label">Total Amount</div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon">👤</div>
                                    <div class="stat-value" id="total-customers">0</div>
                                    <div class="stat-label">Customers</div>
                                </div>
                            </div>
                            
                            <div class="chart-container">
                                <h3>📈 Transaction Methods</h3>
                                <canvas id="methodChart"></canvas>
                            </div>
                            
                            <div class="chart-container">
                                <h3>📅 Daily Transactions</h3>
                                <canvas id="dailyChart"></canvas>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            
            document.getElementById('adminModal').style.display = 'block';
            initAdminPortal();
        }

        function closeAdminModal() {
            document.getElementById('adminModal').style.display = 'none';
        }

        // Review System Functions
        function initReviewSystem() {
            const savedReviews = localStorage.getItem('telecomReviews');
            if (savedReviews) {
                allReviews = JSON.parse(savedReviews);
            }

            if (document.getElementById('review-page')) {
                const stars = document.querySelectorAll('.star');
                const ratingValue = document.getElementById('rating-value');
                let currentRating = 0;
                
                stars.forEach(star => {
                    star.addEventListener('click', function() {
                        currentRating = parseInt(this.getAttribute('data-value'));
                        ratingValue.textContent = currentRating;
                        
                        stars.forEach((s, index) => {
                            if (index < currentRating) {
                                s.classList.add('active');
                                s.textContent = '★';
                            } else {
                                s.classList.remove('active');
                                s.textContent = '☆';
                            }
                        });
                    });
                });
                
                document.getElementById('submit-review')?.addEventListener('click', function() {
                    const name = document.getElementById('reviewer-name').value.trim();
                    const text = document.getElementById('review-text').value.trim();
                    const currentRating = parseInt(document.getElementById('rating-value').textContent);
                    
                    if (!validateReview(currentRating, name, text)) return;
                    
                    const newReview = {
                        id: Date.now(),
                        name: name,
                        rating: currentRating,
                        text: text,
                        date: new Date().toLocaleDateString(),
                        status: 'approved'
                    };
                    
                    allReviews.push(newReview);
                    saveReviews();
                    displayLiveReviews();
                    resetReviewForm();
                    alert('Thank you for your review!');
                });
            }
        }

        function validateReview(rating, name, text) {
            if (rating === 0) {
                alert('Please select a rating!');
                return false;
            }
            
            if (name === '') {
                alert('Please enter your name!');
                return false;
            }
            
            if (text === '') {
                alert('Please write your review!');
                return false;
            }
            
            return true;
        }

        function displayLiveReviews() {
            const container = document.getElementById('live-reviews');
            if (!container) return;
            
            container.innerHTML = '';
            
            const approvedReviews = allReviews.filter(review => review.status === 'approved');
            
            if (approvedReviews.length === 0) {
                container.innerHTML = '<p>No reviews yet. Be the first to review!</p>';
                return;
            }
            
            approvedReviews.forEach(review => {
                const reviewItem = document.createElement('div');
                reviewItem.className = 'review-item';
                reviewItem.innerHTML = `
                    <div class="review-header">
                        <h4>${review.name}</h4>
                        <div class="review-rating">${'★'.repeat(review.rating)}${'☆'.repeat(5 - review.rating)}</div>
                    </div>
                    <p>"${review.text}"</p>
                    <div class="review-date">Posted: ${review.date}</div>
                `;
                container.appendChild(reviewItem);
            });
        }

        function saveReviews() {
            localStorage.setItem('telecomReviews', JSON.stringify(allReviews));
        }

        // Admin Portal Functions
        function initAdminPortal() {
            const adminCredentials = {
                "8507712361": "Rahul@123",
                "8264161178": "Alok@123",
                "9646721037": "Raman*123"
            };
            
            const adminNames = {
                "8507712361": "Rahul",
                "8264161178": "Alok",
                "9646721037": "Raman"
            };

            document.getElementById('loginForm')?.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const username = document.getElementById('username').value.trim();
                const password = document.getElementById('password').value;
                
                if(adminCredentials[username] && adminCredentials[username] === password) {
                    document.getElementById('admin-login').style.display = 'none';
                    document.getElementById('admin-dashboard').style.display = 'block';
                    document.getElementById('logged-in-user').textContent = `👤 ${adminNames[username]}`;
                    loadInitialData();
                } else {
                    alert('❌ Invalid credentials. Please try again.');
                }
            });

            document.getElementById('logout-btn')?.addEventListener('click', function() {
                document.getElementById('admin-dashboard').style.display = 'none';
                document.getElementById('admin-login').style.display = 'block';
                document.getElementById('loginForm').reset();
                
                if(methodChart) methodChart.destroy();
                if(dailyChart) dailyChart.destroy();
            });

            // Load initial data
            function loadInitialData() {
                const savedRecords = localStorage.getItem('telecomRecords');
                if (savedRecords) {
                    allRecords = JSON.parse(savedRecords);
                }
                
                showPendingReviews();
                displaySubmittedRecords();
                updateStats();
                openTab('reviews-tab');
                
                // Demo data if empty
                if(allReviews.length === 0) {
                    allReviews = [
                        {
                            id: 1,
                            name: "Rahul Sharma",
                            rating: 5,
                            text: "Excellent service! Got my PAN card in just 2 hours.",
                            date: "15 May 2023",
                            status: "approved"
                        }
                    ];
                    saveReviews();
                }
                
                if(allRecords.length === 0) {
                    const now = new Date();
                    allRecords = [
                        {
                            method: 'roinet',
                            customerName: 'Rahul Sharma',
                            aadharNumber: '123456789012',
                            mobileNumber: '9876543210',
                            amount: '1500',
                            bankName: 'SBI',
                            address: '123, Main Street, Delhi',
                            rrnNumber: 'ROI12345678',
                            signature: 'Rahul',
                            date: now.toLocaleString(),
                            recordedBy: 'Rahul'
                        }
                    ];
                    localStorage.setItem('telecomRecords', JSON.stringify(allRecords));
                }
            }
        }

        // Initialize when page loads
        document.addEventListener('DOMContentLoaded', function() {
            initReviewSystem();
            
            if (document.getElementById('review-page')) {
                displayLiveReviews();
            }
        });

        // Close modal when clicking outside
        window.onclick = function(event) {
            if (event.target == document.getElementById('adminModal')) {
                closeAdminModal();
            }
        }
    </script>
</body>
</html>

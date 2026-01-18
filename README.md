# Demo_site
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aurex Properties - Luxury Real Estate in Dubai</title>
    <style>
        /* Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Cinzel', serif; /* Luxury serif font for premium feel */
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
            color: #f5f5f5;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }
        .gold-accent {
            color: #d4af37;
        }
        .glassmorphism {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 15px;
        }

        /* Hero Section */
        #hero {
            height: 100vh;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }
        #hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://via.placeholder.com/1920x1080/000000/ffffff?text=Dubai+Skyline+3D') no-repeat center center/cover;
            z-index: -1;
            transform: translateZ(0); /* Parallax trigger */
        }
        .hero-content {
            text-align: center;
            z-index: 1;
            animation: fadeInUp 2s ease-out;
        }
        .hero-content h1 {
            font-size: 4rem;
            font-weight: bold;
            text-shadow: 0 0 20px rgba(212, 175, 55, 0.5);
        }
        .hero-content p {
            font-size: 1.5rem;
            margin: 20px 0;
        }
        .cta-button {
            background: linear-gradient(45deg, #d4af37, #ffd700);
            color: #000;
            padding: 15px 30px;
            border: none;
            border-radius: 25px;
            font-size: 1.2rem;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        .cta-button:hover {
            transform: scale(1.05);
        }

        /* Property Showcase */
        #properties {
            padding: 100px 20px;
            text-align: center;
        }
        .property-cards {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
        }
        .property-card {
            width: 300px;
            height: 400px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 15px;
            padding: 20px;
            transform: translateY(0);
            transition: transform 0.5s ease, box-shadow 0.5s ease;
            position: relative;
            overflow: hidden;
        }
        .property-card:hover {
            transform: translateY(-10px) rotateX(5deg);
            box-shadow: 0 20px 40px rgba(212, 175, 55, 0.3);
        }
        .property-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(212, 175, 55, 0.1) 0%, transparent 70%);
            animation: rotate 10s linear infinite;
        }

        /* Investment Benefits */
        #benefits {
            padding: 100px 20px;
            background: rgba(0, 0, 0, 0.5);
        }
        .benefit-icons {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }
        .benefit-icon {
            text-align: center;
            width: 200px;
            animation: float 3s ease-in-out infinite;
        }
        .benefit-icon:nth-child(2) { animation-delay: 1s; }
        .benefit-icon:nth-child(3) { animation-delay: 2s; }

        /* Testimonials */
        #testimonials {
            padding: 100px 20px;
        }
        .testimonial-cards {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
        }
        .testimonial-card {
            width: 300px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 15px;
            transform: translateY(0);
            transition: transform 0.5s ease;
            position: relative;
        }
        .testimonial-card:hover {
            transform: translateY(-5px);
        }
        .testimonial-card::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, #d4af37, #ffd700);
            transform: scaleX(0);
            transition: transform 0.5s ease;
        }
        .testimonial-card:hover::after {
            transform: scaleX(1);
        }

        /* Call to Action */
        #cta {
            padding: 100px 20px;
            text-align: center;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
        }
        .booking-form {
            max-width: 500px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 15px;
            padding: 30px;
            animation: slideIn 1s ease-out;
        }
        .booking-form input, .booking-form button {
            width: 100%;
            padding: 15px;
            margin: 10px 0;
            border: none;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: #f5f5f5;
        }
        .booking-form button {
            background: linear-gradient(45deg, #d4af37, #ffd700);
            color: #000;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        .booking-form button:hover {
            transform: scale(1.05);
        }

        /* Animations */
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(50px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(-50px); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* Parallax and Scroll Effects */
        .parallax {
            transform: translateZ(0);
        }
        /* Add scroll-triggered animations using Intersection Observer in JS */

        /* Responsive */
        @media (max-width: 768px) {
            .hero-content h1 { font-size: 2.5rem; }
            .property-cards { flex-direction: column; align-items: center; }
        }
    </style>
</head>
<body>
    <!-- Hero Section -->
    <section id="hero" class="parallax">
        <div class="hero-content">
            <h1 class="gold-accent">Aurex Properties</h1>
            <p>Experience the pinnacle of luxury living in Dubai's most exclusive estates.</p>
            <button class="cta-button">Explore Properties</button>
        </div>
    </section>

    <!-- Property Showcase -->
    <section id="properties">
        <h2 class="gold-accent">Luxury Property Showcase</h2>
        <div class="property-cards">
            <div class="property-card">
                <h3>Burj Khalifa Penthouse</h3>
                <p>Overlooking the iconic skyline, this penthouse offers unparalleled views and opulence.</p>
                <img src="https://via.placeholder.com/280x200/333333/ffffff?text=Penthouse" alt="Penthouse" style="width:100%; border-radius:10px;">
            </div>
            <div class="property-card">
                <h3>Palm Jumeirah Villa</h3>
                <p>A private oasis on the Palm, blending modern luxury with waterfront serenity.</p>
                <img src="https://via.placeholder.com/280x200/333333/ffffff?text=Villa" alt="Villa" style="width:100%; border-radius:10px;">
            </div>
            <div class="property-card">
                <h3>Downtown Dubai Apartment</h3>
                <p>Urban sophistication in the heart of Dubai, with world-class amenities.</p>
                <img src="https://via.placeholder.com/280x200/333333/ffffff?text=Apartment" alt="Apartment" style="width:100%; border-radius:10px;">
            </div>
        </div>
    </section>

    <!-- Investment Benefits -->
    <section id="benefits">
        <h2 class="gold-accent">Investment Benefits</h2>
        <div class="benefit-icons">
            <div class="benefit-icon">
                <img src="https://via.placeholder.com/100x100/d4af37/000000?text=ROI" alt="High ROI" style="width:100px; height:100px;">
                <p>High Returns on Investment</p>
            </div>
            <div class="benefit-icon">
                <img src="https://via.placeholder.com/100x100/d4af37/000000?text=Security" alt="Security" style="width:100px; height:100px;">
                <p>Secure & Stable Market</p>
            </div>
            <div class="benefit-icon">
                <img src="https://via.placeholder.com/100x100/d4af37/000000?text=Luxury" alt="Luxury" style="width:100px; height:100px;">
                <p>Luxury Lifestyle Perks</p>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section id="testimonials">
        <h2 class="gold-accent">Client Testimonials</h2>
        <div class="testimonial-cards">
            <div class="testimonial-card">
                <p>"Aurex Properties transformed my investment into a dream home. Pure elegance."</p>
                <cite>- Sheikh Ahmed</cite>
            </div>
            <div class="testimonial-card">
                <p>"The attention to detail and futuristic design are unmatched. Highly recommend."</p>
                <cite>- Ms. Fatima Al-Zahra</cite>
            </div>
            <div class="testimonial-card">
                <p>"Investing with Aurex felt like stepping into the billionaire lifestyle."</p>
                <cite>- Mr. Rajan Kumar</cite>
            </div>
        </div>
    </section>

    <!-- Call to Action -->
    <section id="cta">
        <h2 class="gold-accent">Book Your Exclusive Viewing</h2>
        <form class="booking-form">
            <input type="text" placeholder="Your Name" required>
            <input type="email" placeholder="Your Email" required>
            <input type="tel" placeholder="Your Phone" required>
            <button type="submit">Schedule Viewing</button>
        </form>
    </section>

    <script>
        // Simple Parallax Effect
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const rate = scrolled * -0.5;
            document.querySelector('#hero::before').style.transform = `translateY(${rate}px)`;
        });

        // Intersection Observer for Scroll Animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        });

        document.querySelectorAll('.property-card, .testimonial-card').forEach(card => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(50px)';
            card.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
            observer.observe(card);
        });

        // Floating Elements (Subtle)
        setInterval(() => {
            document.querySelectorAll('.benefit-icon').forEach(icon => {
                icon.style.transform = `translateY(${Math.sin(Date.now() / 1000) * 5}px)`;
            });
        }, 100);
    </script>
</body>
</html>

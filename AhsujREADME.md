<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple King</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f0f23 100%);
            color: #f4f4f4;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .crown-pattern {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.05;
            z-index: -1;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 100 100'%3E%3Cpath d='M50 10 L60 30 L80 25 L65 45 L85 60 L60 55 L50 75 L40 55 L15 60 L35 45 L20 25 L40 30 Z' fill='%23ffd700' opacity='0.3'/%3E%3C/svg%3E");
            background-repeat: repeat;
            background-size: 200px 200px;
        }

        header {
            text-align: center;
            padding: 4rem 2rem;
            position: relative;
        }

        .crown {
            font-size: 4rem;
            color: #ffd700;
            margin-bottom: 1rem;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 0 20px rgba(255, 215, 0, 0.5); }
            to { text-shadow: 0 0 30px rgba(255, 215, 0, 0.8), 0 0 40px rgba(255, 215, 0, 0.3); }
        }

        h1 {
            font-size: 3.5rem;
            font-weight: bold;
            color: #ffd700;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
            margin-bottom: 0.5rem;
            letter-spacing: 2px;
        }

        .subtitle {
            font-size: 1.2rem;
            color: #c9c9c9;
            font-style: italic;
            margin-bottom: 2rem;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section {
            margin: 4rem 0;
            padding: 3rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 215, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .section:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(255, 215, 0, 0.1);
        }

        .section h2 {
            font-size: 2.2rem;
            color: #ffd700;
            margin-bottom: 1.5rem;
            text-align: center;
            border-bottom: 2px solid #ffd700;
            padding-bottom: 0.5rem;
        }

        .section p {
            font-size: 1.1rem;
            line-height: 1.8;
            text-align: center;
            color: #e0e0e0;
        }

        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.08);
            padding: 2rem;
            border-radius: 12px;
            border: 1px solid rgba(255, 215, 0, 0.15);
            text-align: center;
            transition: all 0.3s ease;
        }

        .feature-card:hover {
            background: rgba(255, 215, 0, 0.1);
            transform: scale(1.02);
        }

        .feature-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #ffd700;
        }

        .feature-card h3 {
            color: #ffd700;
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        .quote {
            font-size: 1.4rem;
            font-style: italic;
            text-align: center;
            color: #ffd700;
            margin: 3rem 0;
            padding: 2rem;
            border-left: 4px solid #ffd700;
            background: rgba(255, 215, 0, 0.05);
            border-radius: 0 12px 12px 0;
        }

        footer {
            text-align: center;
            padding: 3rem 2rem;
            margin-top: 4rem;
            border-top: 1px solid rgba(255, 215, 0, 0.3);
            background: rgba(0, 0, 0, 0.2);
        }

        .royal-separator {
            text-align: center;
            margin: 3rem 0;
            font-size: 2rem;
            color: #ffd700;
        }

        .visitor-stats {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #ffd700;
            border-radius: 10px;
            padding: 1rem;
            z-index: 1000;
            min-width: 200px;
            backdrop-filter: blur(10px);
        }

        .visitor-stats h3 {
            color: #ffd700;
            font-size: 1rem;
            margin-bottom: 0.5rem;
            text-align: center;
        }

        .stat-item {
            display: flex;
            justify-content: space-between;
            margin: 0.3rem 0;
            font-size: 0.9rem;
            color: #e0e0e0;
        }

        .visitor-log {
            max-height: 200px;
            overflow-y: auto;
            margin-top: 1rem;
            padding-top: 0.5rem;
            border-top: 1px solid #ffd700;
        }

        .visitor-entry {
            font-size: 0.8rem;
            color: #c0c0c0;
            margin: 0.2rem 0;
            padding: 0.2rem;
            background: rgba(255, 215, 0, 0.1);
            border-radius: 3px;
        }

        .toggle-stats {
            position: fixed;
            top: 20px;
            right: 240px;
            background: #ffd700;
            color: #000;
            border: none;
            border-radius: 50px;
            padding: 10px 15px;
            cursor: pointer;
            font-weight: bold;
            z-index: 1001;
        }

        @media (max-width: 768px) {
            .visitor-stats {
                position: relative;
                top: auto;
                right: auto;
                margin: 1rem;
                width: calc(100% - 2rem);
            }
            .toggle-stats {
                position: relative;
                top: auto;
                right: auto;
                margin: 1rem;
                display: block;
            }
        }

        @media (max-width: 768px) {
            h1 { font-size: 2.5rem; }
            .crown { font-size: 3rem; }
            .section { padding: 2rem; margin: 2rem 0; }
            .features { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div class="crown-pattern"></div>
    
    <button class="toggle-stats" onclick="toggleStats()">👁️ Royal Intel</button>
    
    <div class="visitor-stats" id="visitorStats">
        <h3>👑 Royal Visitors</h3>
        <div class="stat-item">
            <span>Total Visits:</span>
            <span id="totalVisits">0</span>
        </div>
        <div class="stat-item">
            <span>Today:</span>
            <span id="todayVisits">0</span>
        </div>
        <div class="stat-item">
            <span>Online Now:</span>
            <span id="currentVisitors">1</span>
        </div>
        <div class="stat-item">
            <span>Your IP:</span>
            <span id="userIP">Loading...</span>
        </div>
        <div class="stat-item">
            <span>Location:</span>
            <span id="userLocation">Loading...</span>
        </div>
        <div class="stat-item">
            <span>Browser:</span>
            <span id="userBrowser">Loading...</span>
        </div>
        
        <div class="visitor-log" id="visitorLog">
            <div style="color: #ffd700; font-size: 0.9rem; margin-bottom: 0.5rem;">Recent Royal Visits:</div>
        </div>
    </div>
    
    <header>
        <div class="crown">👑</div>
        <h1>Simple King</h1>
        <p class="subtitle">Where Simplicity Reigns Supreme</p>
    </header>

    <div class="container">
        <section class="section">
            <h2>Welcome to Your Royal Domain</h2>
            <p>
                In a world of complexity and chaos, you have chosen the path of elegant simplicity. 
                This is your digital kingdom where less is more, and clarity rules over confusion. 
                Here, every element serves a purpose, and every choice reflects the wisdom of restraint.
            </p>
        </section>

        <div class="royal-separator">⚜️ ⚜️ ⚜️</div>

        <section class="section">
            <h2>Royal Principles</h2>
            <div class="features">
                <div class="feature-card">
                    <div class="feature-icon">🎯</div>
                    <h3>Purposeful Design</h3>
                    <p>Every element serves a clear purpose, nothing is superfluous in this royal court.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">✨</div>
                    <h3>Elegant Simplicity</h3>
                    <p>True luxury lies in the refinement of the essential, not the accumulation of excess.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🏰</div>
                    <h3>Timeless Quality</h3>
                    <p>Built to last, designed to endure, crafted with the patience of royalty.</p>
                </div>
            </div>
        </section>

        <div class="quote">
            "Simplicity is the ultimate sophistication. A true king needs not elaborate displays, 
            for his presence alone commands respect."
        </div>

        <section class="section">
            <h2>Your Royal Decree</h2>
            <p>
                As the Simple King, you understand that true power comes not from complexity, 
                but from the mastery of fundamentals. Your reign is built on clear communication, 
                thoughtful decisions, and the courage to say no to the unnecessary. 
                This website stands as a testament to your philosophy: that in simplicity, 
                we find both beauty and strength.
            </p>
        </section>

        <div class="royal-separator">⚜️ ⚜️ ⚜️</div>

        <section class="section">
            <h2>The Simple Manifesto</h2>
            <p>
                Choose quality over quantity. Embrace clarity over confusion. 
                Value purpose over decoration. Lead with intention, not impulse. 
                Remember that the most profound truths are often the simplest ones, 
                and the greatest leaders are those who can make the complex feel effortless.
            </p>
        </section>
    </div>

    <footer>
        <p>&copy; 2025 Simple King | Where Less Becomes More</p>
        <div style="margin-top: 1rem; font-size: 1.5rem;">👑</div>
    </footer>

    <script>
        // Visitor tracking and analytics
        let visitorData = {
            totalVisits: 0,
            todayVisits: 0,
            visitors: [],
            lastVisitDate: null
        };

        // Load existing data from localStorage
        function loadVisitorData() {
            const saved = localStorage.getItem('simpleKingVisitors');
            if (saved) {
                visitorData = JSON.parse(saved);
            }
        }

        // Save data to localStorage
        function saveVisitorData() {
            localStorage.setItem('simpleKingVisitors', JSON.stringify(visitorData));
        }

        // Get visitor information
        async function getVisitorInfo() {
            const userAgent = navigator.userAgent;
            const browser = getBrowserName(userAgent);
            const currentTime = new Date();
            
            // Check if it's a new day
            const today = currentTime.toDateString();
            if (visitorData.lastVisitDate !== today) {
                visitorData.todayVisits = 0;
                visitorData.lastVisitDate = today;
            }
            
            // Increment visits
            visitorData.totalVisits++;
            visitorData.todayVisits++;
            
            // Try to get IP and location (mock data for demo)
            let ipInfo = {
                ip: 'Hidden for privacy',
                city: 'Royal Palace',
                country: 'Kingdom'
            };
            
            // In a real scenario, you'd use a service like ipapi.co
            try {
                // This is a mock - in reality you'd need a proper IP service
                ipInfo.ip = 'Your IP (Protected)';
            } catch (error) {
                console.log('IP service unavailable');
            }
            
            // Add visitor entry
            const visitor = {
                timestamp: currentTime.toLocaleString(),
                browser: browser,
                ip: ipInfo.ip,
                location: `${ipInfo.city}, ${ipInfo.country}`,
                userAgent: userAgent.substring(0, 50) + '...'
            };
            
            visitorData.visitors.unshift(visitor);
            if (visitorData.visitors.length > 10) {
                visitorData.visitors = visitorData.visitors.slice(0, 10);
            }
            
            return { visitor, ipInfo };
        }

        // Get browser name from user agent
        function getBrowserName(userAgent) {
            if (userAgent.includes('Chrome') && !userAgent.includes('Edg')) return 'Chrome';
            if (userAgent.includes('Firefox')) return 'Firefox';
            if (userAgent.includes('Safari') && !userAgent.includes('Chrome')) return 'Safari';
            if (userAgent.includes('Edg')) return 'Edge';
            if (userAgent.includes('Opera')) return 'Opera';
            return 'Unknown';
        }

        // Update the visitor stats display
        function updateStatsDisplay(visitorInfo) {
            document.getElementById('totalVisits').textContent = visitorData.totalVisits;
            document.getElementById('todayVisits').textContent = visitorData.todayVisits;
            document.getElementById('currentVisitors').textContent = Math.floor(Math.random() * 5) + 1;
            document.getElementById('userIP').textContent = visitorInfo.visitor.ip;
            document.getElementById('userLocation').textContent = visitorInfo.visitor.location;
            document.getElementById('userBrowser').textContent = visitorInfo.visitor.browser;
            
            // Update visitor log
            const visitorLog = document.getElementById('visitorLog');
            const logEntries = visitorLog.querySelectorAll('.visitor-entry');
            logEntries.forEach(entry => entry.remove());
            
            visitorData.visitors.forEach(visitor => {
                const entry = document.createElement('div');
                entry.className = 'visitor-entry';
                entry.innerHTML = `
                    <div><strong>${visitor.timestamp}</strong></div>
                    <div>${visitor.browser} | ${visitor.location}</div>
                `;
                visitorLog.appendChild(entry);
            });
        }

        // Toggle stats visibility
        function toggleStats() {
            const stats = document.getElementById('visitorStats');
            if (stats.style.display === 'none') {
                stats.style.display = 'block';
            } else {
                stats.style.display = 'none';
            }
        }

        // Initialize visitor tracking
        async function initVisitorTracking() {
            loadVisitorData();
            const visitorInfo = await getVisitorInfo();
            updateStatsDisplay(visitorInfo);
            saveVisitorData();
        }

        // Add some subtle interactive effects
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize visitor tracking
            initVisitorTracking();
            
            const sections = document.querySelectorAll('.section');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, { threshold: 0.1 });

            sections.forEach(section => {
                section.style.opacity = '0';
                section.style.transform = 'translateY(20px)';
                section.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
                observer.observe(section);
            });

            // Add crown rotation on scroll
            const crown = document.querySelector('.crown');
            let lastScrollY = window.scrollY;
            
            window.addEventListener('scroll', () => {
                const scrollY = window.scrollY;
                const rotation = scrollY * 0.1;
                crown.style.transform = `rotate(${rotation}deg)`;
                lastScrollY = scrollY;
            });

            // Update visitor count periodically
            setInterval(() => {
                document.getElementById('currentVisitors').textContent = Math.floor(Math.random() * 5) + 1;
            }, 30000); // Update every 30 seconds
        });
    </script>
</body>
</html>

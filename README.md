4.
a) Design an HTML webpage that demonstrates the use of tables, lists, images, and
forms to create a simple college information portal.
b) Design an AJAX-based webpage for an online feedback system that submits and
displays user feedback dynamically without reloading the page

A.ans

college.html


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>College Information Portal</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 900px; margin: 0 auto; padding: 20px; }
    h1 { background: #1a237e; color: white; padding: 20px; text-align: center; border-radius: 8px; }
    h2 { color: #1a237e; border-left: 4px solid #1a237e; padding-left: 10px; margin-top: 30px; }
    table { width: 100%; border-collapse: collapse; margin: 15px 0; }
    th { background: #1a237e; color: white; padding: 10px; text-align: left; }
    td { padding: 10px; border: 1px solid #ddd; }
    tr:nth-child(even) { background: #f5f5f5; }
    ul { line-height: 2; }
    img { width: 100%; max-height: 220px; object-fit: cover; border-radius: 8px; margin: 10px 0; }
    form { background: #f9f9f9; padding: 20px; border-radius: 8px; }
    label { display: block; margin-bottom: 5px; font-weight: bold; }
    input, textarea, select { width: 100%; padding: 10px; margin-bottom: 15px;
      border: 1px solid #ddd; border-radius: 4px; }
    button { background: #1a237e; color: white; padding: 10px 24px;
      border: none; border-radius: 4px; cursor: pointer; }
  </style>
</head>
<body>
  <h1>🏫 ABC College of Engineering</h1>

  <h2>About Us</h2>
  <img src="https://via.placeholder.com/900x220?text=College+Campus" alt="Campus">
  <p>Founded in 1998, ABC College is a premier engineering institution with over 5000 students
  and 200 faculty members dedicated to excellence in technical education.</p>

  <h2>Departments</h2>
  <ul>
    <li>Computer Science & Engineering</li>
    <li>Electronics & Communication Engineering</li>
    <li>Mechanical Engineering</li>
    <li>Civil Engineering</li>
    <li>Information Technology</li>
  </ul>

  <h2>Academic Calendar</h2>
  <table>
    <tr><th>Event</th><th>Date</th><th>Department</th></tr>
    <tr><td>Semester Start</td><td>01 July 2024</td><td>All</td></tr>
    <tr><td>Mid Semester Exam</td><td>15 Sep 2024</td><td>All</td></tr>
    <tr><td>Tech Fest</td><td>10 Oct 2024</td><td>CSE, IT</td></tr>
    <tr><td>End Semester Exam</td><td>25 Nov 2024</td><td>All</td></tr>
  </table>

  <h2>Facilities</h2>
  <table>
    <tr><th>Facility</th><th>Capacity</th><th>Location</th></tr>
    <tr><td>Central Library</td><td>500 Students</td><td>Block A</td></tr>
    <tr><td>Computer Lab</td><td>120 Workstations</td><td>Block B</td></tr>
    <tr><td>Sports Complex</td><td>1000 People</td><td>Block D</td></tr>
  </table>

  <h2>Admissions 2024</h2>
  <form onsubmit="handleApply(event)">
    <label>Full Name</label>
    <input type="text" id="appName" placeholder="Your full name" required>
    <label>Email</label>
    <input type="email" id="appEmail" placeholder="your@email.com" required>
    <label>Department of Interest</label>
    <select id="appDept">
      <option>Computer Science</option>
      <option>Electronics</option>
      <option>Mechanical</option>
      <option>Civil</option>
    </select>
    <label>Message</label>
    <textarea id="appMsg" rows="4" placeholder="Any queries..."></textarea>
    <button type="submit">Submit Application</button>
  </form>
  <p id="appResult" style="color:green;font-weight:bold;margin-top:10px"></p>

  <script>
    function handleApply(e) {
      e.preventDefault();
      document.getElementById('appResult').textContent =
        '✅ Application submitted for ' + document.getElementById('appName').value;
      e.target.reset();
    }
  </script>
</body>
</html>


B.ans

feedback.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Online Feedback System</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 700px; margin: 40px auto; padding: 20px; }
    h1 { color: #2563eb; }
    .form-box { background: #f0f4ff; padding: 24px; border-radius: 10px; margin-bottom: 24px; }
    input, textarea, select { width: 100%; padding: 10px; margin: 8px 0 14px;
      border: 1px solid #ccc; border-radius: 5px; font-size: 14px; }
    button { background: #2563eb; color: white; border: none; padding: 10px 28px;
      border-radius: 5px; cursor: pointer; font-size: 15px; }
    button:hover { background: #1d4ed8; }
    #feedbackList { display: flex; flex-direction: column; gap: 12px; }
    .feedback-card { background: white; border: 1px solid #e0e0e0; border-radius: 8px;
      padding: 14px; animation: slideIn 0.3s ease; box-shadow: 0 2px 6px rgba(0,0,0,0.07); }
    .feedback-card .meta { font-size: 12px; color: #888; margin-bottom: 6px; }
    .stars { color: #f59e0b; }
    @keyframes slideIn { from { opacity:0; transform:translateY(-10px); } to { opacity:1; transform:none; } }
    #counter { font-size: 13px; color: #555; margin-bottom: 12px; }
  </style>
</head>
<body>
  <h1>📝 Feedback System</h1>

  <div class="form-box">
    <input type="text" id="fbName" placeholder="Your Name" required>
    <input type="email" id="fbEmail" placeholder="Your Email" required>
    <select id="fbRating">
      <option value="5">⭐⭐⭐⭐⭐ Excellent</option>
      <option value="4">⭐⭐⭐⭐ Good</option>
      <option value="3">⭐⭐⭐ Average</option>
      <option value="2">⭐⭐ Poor</option>
      <option value="1">⭐ Very Poor</option>
    </select>
    <textarea id="fbMsg" rows="3" placeholder="Write your feedback here..."></textarea>
    <button onclick="submitFeedback()">Submit Feedback</button>
  </div>

  <div id="counter">0 feedback(s) submitted</div>
  <div id="feedbackList"></div>

  <script>
    let feedbacks = [];

    function submitFeedback() {
      const name    = document.getElementById('fbName').value.trim();
      const email   = document.getElementById('fbEmail').value.trim();
      const rating  = document.getElementById('fbRating').value;
      const message = document.getElementById('fbMsg').value.trim();

      if (!name || !email || !message) {
        alert('Please fill all fields'); return;
      }

      // Simulate async AJAX call
      setTimeout(() => {
        feedbacks.unshift({ name, email, rating, message,
          time: new Date().toLocaleTimeString() });
        renderFeedbacks();
        document.getElementById('fbName').value = '';
        document.getElementById('fbEmail').value = '';
        document.getElementById('fbMsg').value = '';
      }, 300);
    }

    function renderFeedbacks() {
      document.getElementById('counter').textContent =
        feedbacks.length + ' feedback(s) submitted';
      document.getElementById('feedbackList').innerHTML = feedbacks.map(f => `
        <div class="feedback-card">
          <div class="meta">${f.name} (${f.email}) · ${f.time}</div>
          <div class="stars">${'⭐'.repeat(parseInt(f.rating))}</div>
          <p style="margin-top:6px">${f.message}</p>
        </div>`).join('');
    }
  </script>
</body>
</html>


5.
a) Create a webpage displaying three images side by side using HTML and Boostrap.
b) Design an HTML structure for an online news article page (title, author, article
body, published date).

A.ans

images.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Three Images Side by Side</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
  <style>
    .img-card img { width: 100%; height: 220px; object-fit: cover; border-radius: 8px; }
    .img-card { text-align: center; }
  </style>
</head>
<body class="bg-light">
  <div class="container py-5">
    <h2 class="text-center mb-4">Our Gallery</h2>
    <div class="row g-4">
      <div class="col-md-4 img-card">
        <img src="https://picsum.photos/seed/nature/400/220" alt="Nature">
        <p class="mt-2 fw-semibold">Nature</p>
      </div>
      <div class="col-md-4 img-card">
        <img src="https://picsum.photos/seed/city/400/220" alt="City">
        <p class="mt-2 fw-semibold">City</p>
      </div>
      <div class="col-md-4 img-card">
        <img src="https://picsum.photos/seed/tech/400/220" alt="Technology">
        <p class="mt-2 fw-semibold">Technology</p>
      </div>
    </div>
  </div>
</body>
</html>


B.ans 

news-article.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>News Article</title>
  <style>
    body { font-family: Georgia, serif; max-width: 720px; margin: 40px auto; padding: 20px; color: #222; }
    .category { background: #e63946; color: white; font-size: 12px;
      padding: 4px 10px; border-radius: 4px; font-family: Arial, sans-serif; }
    h1 { font-size: 2rem; margin: 16px 0 8px; line-height: 1.3; }
    .meta { display: flex; gap: 16px; align-items: center; font-size: 14px;
      color: #666; margin-bottom: 20px; font-family: Arial, sans-serif; border-bottom: 1px solid #ddd; padding-bottom: 16px; }
    .author-img { width: 36px; height: 36px; border-radius: 50%; object-fit: cover; }
    .hero-img { width: 100%; height: 360px; object-fit: cover;
      border-radius: 8px; margin-bottom: 24px; }
    .article-body p { font-size: 1.05rem; line-height: 1.85; margin-bottom: 18px; }
    blockquote { border-left: 4px solid #e63946; margin: 24px 0;
      padding: 12px 20px; font-style: italic; color: #444; background: #f9f9f9; }
    .tags { margin-top: 24px; display: flex; gap: 8px; flex-wrap: wrap; }
    .tag { background: #f0f0f0; padding: 4px 12px; border-radius: 20px; font-size: 13px; font-family: Arial,sans-serif; }
  </style>
</head>
<body>
  <span class="category">TECHNOLOGY</span>
  <h1>How Artificial Intelligence is Transforming Modern Education</h1>

  <div class="meta">
    <img src="https://i.pravatar.cc/36?img=5" alt="Author" class="author-img">
    <span>By <strong>Ananya Krishnan</strong></span>
    <span>📅 Published: June 15, 2024</span>
    <span>⏱ 5 min read</span>
  </div>

  <img src="https://picsum.photos/seed/education/720/360" alt="AI Education" class="hero-img">

  <div class="article-body">
    <p>Artificial Intelligence is no longer a concept confined to science fiction. Today, it is reshaping
    the way students learn, teachers teach, and institutions operate across the globe.</p>

    <p>From personalized learning paths powered by machine learning algorithms to AI tutors
    available 24/7, the education sector is witnessing a paradigm shift that promises to make
    quality education accessible to all.</p>

    <blockquote>"AI will not replace teachers, but teachers who use AI will replace those who don't."
    — Dr. Rajesh Mehta, IIT Bombay</blockquote>

    <p>Platforms like Khan Academy and Coursera have already integrated AI to recommend courses
    based on learning history, while adaptive assessment tools adjust question difficulty in real time
    based on student performance.</p>

    <p>The road ahead is promising. With continued investment and thoughtful implementation, AI has
    the potential to democratize education and bridge the gap between urban and rural learning
    opportunities in India and beyond.</p>
  </div>

  <div class="tags">
    <span class="tag">#ArtificialIntelligence</span>
    <span class="tag">#EdTech</span>
    <span class="tag">#Education</span>
    <span class="tag">#Technology</span>
  </div>
</body>
</html>


6.
a) Create an HTML form to collect feedback from users with fields like name, email,
comments, and a submit button.
b) Write CSS code to create a navigation bar with horizontal links that change color
on hover.

A.ans

feedback-form.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Feedback Form</title>
  <style>
    * { box-sizing: border-box; }
    body { background: #f0f2f5; display: flex; justify-content: center;
      align-items: center; min-height: 100vh; margin: 0; font-family: Arial, sans-serif; }
    .form-container { background: white; padding: 2rem; border-radius: 12px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.1); width: 480px; }
    h2 { color: #1a237e; margin-bottom: 1.5rem; text-align: center; }
    label { display: block; font-size: 14px; font-weight: bold;
      color: #333; margin-bottom: 5px; }
    input, textarea, select { width: 100%; padding: 10px 14px; border: 1px solid #ddd;
      border-radius: 6px; font-size: 14px; outline: none; transition: border-color 0.2s; }
    input:focus, textarea:focus { border-color: #1a237e; }
    .field { margin-bottom: 16px; }
    .radio-group { display: flex; gap: 16px; }
    .radio-group label { font-weight: normal; display: flex; align-items: center; gap: 6px; }
    button { width: 100%; padding: 12px; background: #1a237e; color: white;
      border: none; border-radius: 6px; font-size: 16px; cursor: pointer; }
    button:hover { background: #283593; }
    .success { display: none; text-align: center; color: green;
      font-weight: bold; margin-top: 12px; font-size: 15px; }
  </style>
</head>
<body>
  <div class="form-container">
    <h2>📋 Feedback Form</h2>
    <div class="field"><label>Full Name</label>
      <input type="text" id="fname" placeholder="Enter your name"></div>
    <div class="field"><label>Email Address</label>
      <input type="email" id="femail" placeholder="your@email.com"></div>
    <div class="field"><label>Phone (Optional)</label>
      <input type="tel" id="fphone" placeholder="+91 XXXXXXXXXX"></div>
    <div class="field"><label>Category</label>
      <select id="fcat">
        <option>General Feedback</option>
        <option>Course Content</option>
        <option>Faculty</option>
        <option>Infrastructure</option>
      </select></div>
    <div class="field"><label>Overall Rating</label>
      <div class="radio-group">
        <label><input type="radio" name="rating" value="5"> Excellent</label>
        <label><input type="radio" name="rating" value="4"> Good</label>
        <label><input type="radio" name="rating" value="3"> Average</label>
        <label><input type="radio" name="rating" value="2"> Poor</label>
      </div></div>
    <div class="field"><label>Comments</label>
      <textarea id="fcomments" rows="4" placeholder="Share your thoughts..."></textarea></div>
    <button onclick="submitForm()">Submit Feedback</button>
    <p class="success" id="successMsg">✅ Thank you! Your feedback has been submitted.</p>
  </div>
  <script>
    function submitForm() {
      const name = document.getElementById('fname').value;
      const email = document.getElementById('femail').value;
      if (!name || !email) { alert('Name and Email are required!'); return; }
      if (!/\S+@\S+\.\S+/.test(email)) { alert('Enter a valid email!'); return; }
      document.getElementById('successMsg').style.display = 'block';
    }
  </script>
</body>
</html>

B.ans

navbar.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Navigation Bar</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: Arial, sans-serif; }

    /* Navigation Bar */
    nav { background: #1a237e; padding: 0 30px; }
    nav ul { list-style: none; display: flex; align-items: center; gap: 0; }
    nav ul .brand { margin-right: auto; }
    nav ul .brand a { font-size: 1.3rem; font-weight: bold; color: #FFD700; }
    nav ul li a {
      display: block;
      color: white;
      text-decoration: none;
      padding: 18px 20px;
      transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover {
      background: #FFD700;
      color: #1a237e;
    }
    nav ul li a.active {
      background: rgba(255,255,255,0.15);
      border-bottom: 3px solid #FFD700;
    }

    /* Hero Section */
    .hero { background: linear-gradient(135deg, #1a237e 0%, #3949ab 100%);
      color: white; text-align: center; padding: 80px 20px; }
    .hero h1 { font-size: 2.5rem; margin-bottom: 12px; }
    .hero p { font-size: 1.1rem; opacity: 0.85; }
  </style>
</head>
<body>
  <nav>
    <ul>
      <li class="brand"><a href="#">MyWebsite</a></li>
      <li><a href="#" class="active">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Portfolio</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>
  <div class="hero">
    <h1>Welcome to MyWebsite</h1>
    <p>Hover over the navigation links to see the color change effect.</p>
  </div>
</body>
</html>

8.
a) Write CSS to design a responsive navigation menu that changes into a mobile-
friendly hamburger menu on smaller screens.
b) Style a login form using CSS and JavaScript with a centered layout, colored input
fields, rounded corners, and validation effects for incorrect entries.

A.ans

hamburger-nav.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Responsive Hamburger Menu</title>
  <style>
    * { margin:0; padding:0; box-sizing:border-box; }
    body { font-family: Arial, sans-serif; }
    nav { background: #1a237e; padding: 0 24px; display: flex;
      justify-content: space-between; align-items: center; height: 60px; }
    .logo { color: #FFD700; font-size: 1.3rem; font-weight: bold; }
    .nav-links { display: flex; list-style: none; gap: 0; }
    .nav-links a { color: white; text-decoration: none; padding: 18px 18px;
      display: block; transition: background 0.2s; }
    .nav-links a:hover { background: rgba(255,255,255,0.15); }

    /* Hamburger button — hidden on desktop */
    .hamburger { display: none; flex-direction: column; cursor: pointer; gap: 5px; }
    .hamburger span { width: 25px; height: 3px; background: white;
      border-radius: 3px; transition: all 0.3s; }
    .hamburger.open span:nth-child(1) { transform: translateY(8px) rotate(45deg); }
    .hamburger.open span:nth-child(2) { opacity: 0; }
    .hamburger.open span:nth-child(3) { transform: translateY(-8px) rotate(-45deg); }

    /* Mobile styles */
    @media (max-width: 768px) {
      .hamburger { display: flex; }
      .nav-links { display: none; flex-direction: column; position: absolute;
        top: 60px; left: 0; right: 0; background: #1a237e; padding: 8px 0; }
      .nav-links.open { display: flex; }
      .nav-links li a { padding: 14px 24px; border-bottom: 1px solid rgba(255,255,255,0.1); }
    }

    .page { padding: 60px 24px; text-align: center; }
    .page h1 { font-size: 2rem; color: #1a237e; }
    .page p { color: #555; margin-top: 12px; }
  </style>
</head>
<body>
  <nav>
    <div class="logo">MyApp</div>
    <div class="hamburger" id="hamburger" onclick="toggleMenu()">
      <span></span><span></span><span></span>
    </div>
    <ul class="nav-links" id="navLinks">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Portfolio</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>
  <div class="page">
    <h1>Responsive Navigation</h1>
    <p>Resize the browser window below 768px to see the hamburger menu appear.</p>
  </div>
  <script>
    function toggleMenu() {
      document.getElementById('hamburger').classList.toggle('open');
      document.getElementById('navLinks').classList.toggle('open');
    }
  </script>
</body>
</html>

B.ans

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Login Form with Validation</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { background: linear-gradient(135deg, #1a237e 0%, #3949ab 100%);
      min-height: 100vh; display: flex; align-items: center; justify-content: center; }
    .box { background: white; padding: 2.5rem; border-radius: 16px;
      width: 400px; box-shadow: 0 8px 32px rgba(0,0,0,0.2); }
    h2 { text-align: center; color: #1a237e; margin-bottom: 0.25rem; }
    .subtitle { text-align: center; color: #888; font-size: 14px; margin-bottom: 1.5rem; }
    .field { margin-bottom: 1rem; }
    label { display: block; font-size: 13px; font-weight: bold; color: #444; margin-bottom: 5px; }
    input { width: 100%; padding: 12px 14px; border: 2px solid #e0e0e0; border-radius: 8px;
      font-size: 15px; outline: none; transition: border-color 0.2s, background 0.2s; }
    input:focus { border-color: #3949ab; background: #f0f4ff; }
    input.error { border-color: #e63946; background: #fff5f5; animation: shake 0.3s; }
    input.success { border-color: #2d6a4f; background: #f0fff4; }
    @keyframes shake {
      0%,100% { transform: translateX(0); }
      20%,60% { transform: translateX(-6px); }
      40%,80% { transform: translateX(6px); }
    }
    .err-msg { font-size: 12px; color: #e63946; margin-top: 4px; display: none; }
    .err-msg.show { display: block; }
    button { width: 100%; padding: 13px; background: #1a237e; color: white;
      border: none; border-radius: 8px; font-size: 15px; cursor: pointer;
      margin-top: 0.5rem; transition: background 0.2s; }
    button:hover { background: #283593; }
    .forgot { text-align: center; font-size: 13px; color: #3949ab;
      cursor: pointer; margin-top: 12px; }
    .success-banner { display: none; background: #e8f5e9; border: 1px solid #a5d6a7;
      color: #2d6a4f; padding: 12px; border-radius: 8px; text-align: center;
      margin-top: 12px; font-size: 14px; }
  </style>
</head>
<body>
  <div class="box">
    <h2>Welcome Back</h2>
    <p class="subtitle">Please login to your account</p>
    <div class="field">
      <label>Email Address</label>
      <input type="email" id="email" placeholder="you@example.com"
        oninput="validate('email')" onfocus="clearErr('email')">
      <div class="err-msg" id="email-err">Please enter a valid email address.</div>
    </div>
    <div class="field">
      <label>Password</label>
      <input type="password" id="password" placeholder="Min. 6 characters"
        oninput="validate('password')" onfocus="clearErr('password')">
      <div class="err-msg" id="password-err">Password must be at least 6 characters.</div>
    </div>
    <button onclick="submitLogin()">Login</button>
    <p class="forgot">Forgot password?</p>
    <div class="success-banner" id="successBanner">
      ✅ Login successful! Redirecting...
    </div>
  </div>
  <script>
    function validate(field) {
      const el = document.getElementById(field);
      const err = document.getElementById(field+'-err');
      let valid = false;
      if (field === 'email') valid = /\S+@\S+\.\S+/.test(el.value);
      if (field === 'password') valid = el.value.length >= 6;
      el.className = el.value ? (valid ? 'success' : 'error') : '';
      err.className = 'err-msg' + (el.value && !valid ? ' show' : '');
      return valid;
    }
    function clearErr(field) {
      document.getElementById(field).className = '';
      document.getElementById(field+'-err').className = 'err-msg';
    }
    function submitLogin() {
      const ev = validate('email'), pv = validate('password');
      if (ev && pv) {
        document.getElementById('successBanner').style.display = 'block';
      }
    }
  </script>
</body>
</html>


9.
a) Create a webpage using javascript for counting the number of users logged in a
session.
b) Write CSS to animate a box to move from left to right across the screen.

A.ans

session-counter.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Session User Counter</title>
  <style>
    body { font-family: Arial, sans-serif; display: flex; flex-direction: column;
      align-items: center; justify-content: center; min-height: 100vh;
      background: #0d1117; color: white; gap: 20px; }
    .counter-box { background: #161b22; border: 1px solid #30363d;
      border-radius: 16px; padding: 40px 60px; text-align: center; }
    .counter-box h1 { font-size: 4rem; font-weight: bold; color: #58a6ff; }
    .counter-box p { color: #8b949e; margin-top: 8px; }
    .live-dot { display: inline-block; width: 10px; height: 10px;
      background: #3fb950; border-radius: 50%; margin-right: 6px;
      animation: pulse 1.5s ease-in-out infinite; }
    @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.5;transform:scale(1.3)} }
    .user-list { background: #161b22; border: 1px solid #30363d;
      border-radius: 12px; padding: 20px; width: 340px; }
    .user-list h3 { color: #8b949e; font-size: 13px; text-transform: uppercase;
      margin-bottom: 12px; }
    .user-item { display: flex; align-items: center; gap: 10px;
      padding: 8px 0; border-bottom: 1px solid #21262d; }
    .user-item:last-child { border: none; }
    .avatar { width: 32px; height: 32px; border-radius: 50%; background: #21262d;
      display: flex; align-items: center; justify-content: center;
      font-size: 14px; font-weight: bold; color: #58a6ff; }
    .user-info p { margin: 0; font-size: 14px; }
    .user-info small { color: #8b949e; font-size: 12px; }
    .btn { padding: 10px 24px; background: #238636; color: white; border: none;
      border-radius: 6px; cursor: pointer; font-size: 14px; }
    .btn.leave { background: #b62324; }
  </style>
</head>
<body>
  <div class="counter-box">
    <p style="font-size:14px;color:#8b949e"><span class="live-dot"></span>Live Session</p>
    <h1 id="count">1</h1>
    <p>User(s) currently online</p>
  </div>
  <div style="display:flex;gap:12px">
    <button class="btn" onclick="addUser()">+ Simulate Login</button>
    <button class="btn leave" onclick="removeUser()">− Simulate Logout</button>
  </div>
  <div class="user-list">
    <h3>Active Sessions</h3>
    <div id="userList"></div>
  </div>

  <script>
    const names = ['Alice','Bob','Charlie','David','Eva','Frank','Grace','Heidi'];
    let users = [{ id:1, name: 'You (Current)', time: new Date() }];
    sessionStorage.setItem('sessionId', 'user_' + Date.now());

    function render() {
      document.getElementById('count').textContent = users.length;
      document.getElementById('userList').innerHTML = users.map(u => `
        <div class="user-item">
          <div class="avatar">${u.name[0]}</div>
          <div class="user-info">
            <p>${u.name}</p>
            <small>Joined: ${u.time.toLocaleTimeString()}</small>
          </div>
        </div>`).join('');
    }

    function addUser() {
      const name = names[Math.floor(Math.random() * names.length)];
      users.push({ id: Date.now(), name, time: new Date() });
      render();
    }

    function removeUser() {
      if (users.length > 1) users.pop();
      render();
    }

    render();
  </script>
</body>
</html>


B.ans

box-animation.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>CSS Box Animation</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f0f2f5;
      display: flex; flex-direction: column; align-items: center;
      justify-content: center; min-height: 100vh; gap: 32px; }
    h2 { color: #333; }
    .track { width: 90vw; max-width: 800px; height: 80px; background: white;
      border-radius: 12px; position: relative; overflow: hidden;
      border: 1px solid #ddd; box-shadow: 0 2px 12px rgba(0,0,0,0.08); }
    .box {
      width: 70px; height: 70px; position: absolute; top: 5px; left: -80px;
      border-radius: 10px; display: flex; align-items: center;
      justify-content: center; font-size: 1.8rem;
      animation: moveRight 3s linear infinite;
    }
    .box1 { background: linear-gradient(135deg,#e63946,#ff758f); animation-delay:0s; }
    .box2 { background: linear-gradient(135deg,#3a86ff,#56cfff); animation-delay:1s; }
    .box3 { background: linear-gradient(135deg,#2d6a4f,#74c69d); animation-delay:2s; }

    @keyframes moveRight {
      0%   { left: -80px; opacity: 1; }
      85%  { opacity: 1; }
      100% { left: calc(100% + 10px); opacity: 0; }
    }

    .controls { display: flex; gap: 12px; }
    .ctrl-btn { padding: 9px 22px; border: 2px solid #333; background: transparent;
      border-radius: 6px; cursor: pointer; font-size: 14px; transition: all 0.2s; }
    .ctrl-btn:hover { background: #333; color: white; }
    #status { font-size: 14px; color: #666; }
  </style>
</head>
<body>
  <h2>CSS Box Animations</h2>
  <div class="track" id="track">
    <div class="box box1">🎯</div>
    <div class="box box2">⚡</div>
    <div class="box box3">🚀</div>
  </div>
  <div class="controls">
    <button class="ctrl-btn" onclick="setSpeed(2)">Slow</button>
    <button class="ctrl-btn" onclick="setSpeed(1)">Normal</button>
    <button class="ctrl-btn" onclick="setSpeed(0.4)">Fast</button>
    <button class="ctrl-btn" onclick="togglePause()">⏸ Pause/Resume</button>
  </div>
  <p id="status">Animation running</p>
  <script>
    let paused = false;
    function setSpeed(s) {
      document.querySelectorAll('.box').forEach(b => b.style.animationDuration = s+'s');
    }
    function togglePause() {
      paused = !paused;
      document.querySelectorAll('.box').forEach(b =>
        b.style.animationPlayState = paused ? 'paused' : 'running');
      document.getElementById('status').textContent =
        paused ? 'Animation paused' : 'Animation running';
    }
  </script>
</body>
</html>


7.
a) Create a react page for the student result management system.
b) Design a &quot;card&quot; layout using CSS and flexbox with a border, shadow, padding, and
centered text.

A.ans

Step 1 — Create the React project
Open your terminal and run:
npx create-react-app student-results
cd student-results
npm start
Your browser will open at http://localhost:3000 automatically.

Step 2 — File structure
You only need to touch two files:
src/
  App.js        ← replace this entirely
  Results.js    ← create this new file
  index.css     ← optional styling

Step 3 — Create src/Results.js
Create a new file src/Results.js and paste the full code from the guide (Exp 7a tab).
Results.js:
import React, { useState } from 'react';

const initialStudents = [
  { id:1, name:'Rahul Sharma', roll:'CS101', subjects:{ Maths:85, Physics:72, Chemistry:78, English:90, CS:95 } },
  { id:2, name:'Priya Singh', roll:'CS102', subjects:{ Maths:92, Physics:88, Chemistry:84, English:76, CS:98 } },
  { id:3, name:'Aakash Patel', roll:'CS103', subjects:{ Maths:55, Physics:48, Chemistry:62, English:70, CS:65 } },
];

function getGrade(pct) {
  if (pct >= 90) return { grade:'O', color:'#2d6a4f' };
  if (pct >= 75) return { grade:'A', color:'#1d6fa4' };
  if (pct >= 60) return { grade:'B', color:'#5c3d99' };
  if (pct >= 50) return { grade:'C', color:'#d97706' };
  if (pct >= 40) return { grade:'D', color:'#d45c00' };
  return { grade:'F', color:'#e63946' };
}

export default function Results() {
  const [search, setSearch] = useState('');
  const [selected, setSelected] = useState(null);

  const filtered = initialStudents.filter(s =>
    s.name.toLowerCase().includes(search.toLowerCase()) ||
    s.roll.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div style={{fontFamily:'Arial,sans-serif',maxWidth:900,margin:'0 auto',padding:'2rem'}}>
      <h1 style={{color:'#1a237e',marginBottom:'0.5rem'}}>📊 Student Result Management</h1>
      <input
        style={{width:'100%',padding:'10px 14px',border:'1px solid #ddd',borderRadius:24,fontSize:15,marginBottom:'1.5rem'}}
        placeholder="🔍 Search by name or roll number..."
        value={search} onChange={e=>setSearch(e.target.value)}
      />

      <div style={{display:'grid',gridTemplateColumns:'repeat(auto-fill,minmax(260px,1fr))',gap:'1rem'}}>
        {filtered.map(student => {
          const marks = Object.values(student.subjects);
          const total = marks.reduce((a,b)=>a+b,0);
          const pct = (total/(marks.length*100)*100).toFixed(1);
          const { grade, color } = getGrade(pct);
          return (
            <div key={student.id}
              style={{background:'white',border:'1px solid #e0e0e0',borderRadius:12,padding:'1.2rem',
                cursor:'pointer',boxShadow:'0 2px 8px rgba(0,0,0,0.07)',
                borderTop:`4px solid ${color}`}}
              onClick={()=>setSelected(student)}>
              <div style={{display:'flex',justifyContent:'space-between',alignItems:'flex-start'}}>
                <div>
                  <h3 style={{margin:'0 0 4px',color:'#1a237e'}}>{student.name}</h3>
                  <p style={{fontSize:13,color:'#666',margin:0}}>Roll: {student.roll}</p>
                </div>
                <div style={{background:color,color:'white',borderRadius:8,padding:'6px 14px',
                  fontWeight:'bold',fontSize:'1.1rem'}}>{grade}</div>
              </div>
              <div style={{marginTop:'0.75rem',display:'flex',justifyContent:'space-between',
                fontSize:14,color:'#444'}}>
                <span>Total: {total}/{marks.length*100}</span>
                <span style={{color,fontWeight:'bold'}}>{pct}%</span>
              </div>
              <p style={{fontSize:12,color:'#888',margin:'8px 0 0',textAlign:'center'}}>
                Click for detailed view
              </p>
            </div>
          );
        })}
      </div>

      {/* Detail modal */}
      {selected && (
        <div style={{position:'fixed',inset:0,background:'rgba(0,0,0,0.5)',
          display:'flex',alignItems:'center',justifyContent:'center',zIndex:999}}
          onClick={()=>setSelected(null)}>
          <div style={{background:'white',borderRadius:16,padding:'2rem',width:480,
            maxWidth:'95vw'}} onClick={e=>e.stopPropagation()}>
            <h2 style={{color:'#1a237e',marginBottom:'0.25rem'}}>{selected.name}</h2>
            <p style={{color:'#666',marginBottom:'1.5rem',fontSize:14}}>Roll: {selected.roll}</p>
            {Object.entries(selected.subjects).map(([subj, marks]) => {
              const pct = marks;
              const { grade, color } = getGrade(pct);
              return (
                <div key={subj} style={{display:'flex',alignItems:'center',gap:'10px',marginBottom:10}}>
                  <span style={{width:100,fontSize:14}}>{subj}</span>
                  <div style={{flex:1,background:'#f0f0f0',borderRadius:10,height:16,overflow:'hidden'}}>
                    <div style={{width:`${pct}%`,height:'100%',background:color,transition:'width 0.6s'}}/>
                  </div>
                  <span style={{fontSize:14,fontWeight:'bold',color,width:30}}>{marks}</span>
                  <span style={{fontSize:12,background:color,color:'white',padding:'1px 6px',borderRadius:4}}>{grade}</span>
                </div>
              );
            })}
            <button style={{marginTop:'1rem',padding:'8px 20px',background:'#1a237e',color:'white',
              border:'none',borderRadius:6,cursor:'pointer'}} onClick={()=>setSelected(null)}>
              Close
            </button>
          </div>
        </div>
      )}
    </div>
  );
}

Step 4:
App.js(delete whatever was into app.js and write ):
import React from 'react';
import Results from './Results';

export default function App() {
  return <Results />;
}

Step 5 : npm start


B.ans

card-layout.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>CSS Flexbox Card Layout</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { background: #f0f2f5; font-family: Arial, sans-serif; padding: 40px 20px; }
    h1 { text-align: center; margin-bottom: 32px; color: #333; }

    .cards-container {
      display: flex;
      flex-wrap: wrap;
      gap: 24px;
      justify-content: center;
      max-width: 1000px;
      margin: 0 auto;
    }

    .card {
      background: white;
      border: 1px solid #e0e0e0;
      border-radius: 12px;
      padding: 28px 24px;
      width: 280px;
      text-align: center;
      box-shadow: 0 4px 16px rgba(0,0,0,0.08);
      transition: transform 0.2s, box-shadow 0.2s;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 12px;
    }
    .card:hover { transform: translateY(-5px); box-shadow: 0 8px 24px rgba(0,0,0,0.14); }
    .card .icon { font-size: 2.5rem; }
    .card h3 { font-size: 1.1rem; color: #222; }
    .card p { font-size: 14px; color: #666; line-height: 1.6; }
    .card .badge { background: #e8f0fe; color: #1a237e;
      font-size: 12px; padding: 4px 14px; border-radius: 20px; }
    .card .btn { padding: 8px 22px; border: 2px solid #1a237e; color: #1a237e;
      border-radius: 6px; cursor: pointer; background: transparent;
      font-size: 14px; transition: all 0.2s; }
    .card .btn:hover { background: #1a237e; color: white; }
  </style>
</head>
<body>
  <h1>Our Services</h1>
  <div class="cards-container">
    <div class="card">
      <div class="icon">💻</div>
      <h3>Web Development</h3>
      <p>Build modern, responsive websites using the latest technologies and frameworks.</p>
      <span class="badge">Popular</span>
      <button class="btn">Learn More</button>
    </div>
    <div class="card">
      <div class="icon">📱</div>
      <h3>Mobile Apps</h3>
      <p>Create cross-platform mobile applications for Android and iOS platforms.</p>
      <span class="badge">Trending</span>
      <button class="btn">Learn More</button>
    </div>
    <div class="card">
      <div class="icon">🤖</div>
      <h3>AI Solutions</h3>
      <p>Integrate artificial intelligence and machine learning into your business workflows.</p>
      <span class="badge">New</span>
      <button class="btn">Learn More</button>
    </div>
  </div>
</body>
</html>


10.
a) Design a webpage in React for managing student course registrations with features
to add, view, and update course details dynamically.
b) Create a JavaScript function that changes the background color of a webpage
dynamically when a button is clicked and displays a confirmation message using
animations and DOM manipulation.


A.ans

Step 1 — Create the React project
npx create-react-app course-manager
cd course-manager
npm start

Step 2 — File structure
src/
  App.js             ← replace this
  CourseManager.js   ← create this new file

Step 3 — Create src/CourseManager.js
Paste the full code from the Exp 10a tab.

CourseManager.js:

import React, { useState } from 'react';

const initialCourses = [
  { id:1, name:'Web Technologies', code:'CS301', credits:4, instructor:'Prof. Sharma', status:'Active' },
  { id:2, name:'Database Management', code:'CS302', credits:3, instructor:'Prof. Verma', status:'Active' },
  { id:3, name:'Operating Systems', code:'CS303', credits:4, instructor:'Prof. Patel', status:'Inactive' },
];

export default function CourseManager() {
  const [courses, setCourses] = useState(initialCourses);
  const [form, setForm] = useState({ name:'', code:'', credits:'', instructor:'', status:'Active' });
  const [editing, setEditing] = useState(null);
  const [search, setSearch] = useState('');
  const [showForm, setShowForm] = useState(false);

  const filtered = courses.filter(c =>
    c.name.toLowerCase().includes(search.toLowerCase()) ||
    c.code.toLowerCase().includes(search.toLowerCase())
  );

  const handleSubmit = () => {
    if (!form.name || !form.code) { alert('Name and Code required'); return; }
    if (editing !== null) {
      setCourses(courses.map(c => c.id === editing ? { ...form, id: editing } : c));
      setEditing(null);
    } else {
      setCourses([...courses, { ...form, id: Date.now(), credits: parseInt(form.credits)||3 }]);
    }
    setForm({ name:'', code:'', credits:'', instructor:'', status:'Active' });
    setShowForm(false);
  };

  const startEdit = (course) => {
    setForm(course);
    setEditing(course.id);
    setShowForm(true);
  };

  const deleteCourse = (id) => {
    if (window.confirm('Delete this course?')) setCourses(courses.filter(c => c.id !== id));
  };

  const s = { inp:{width:'100%',padding:'9px 12px',border:'1px solid #ddd',
    borderRadius:6,fontSize:14,marginBottom:10},
    btn:{padding:'8px 18px',border:'none',borderRadius:6,cursor:'pointer',fontSize:14} };

  return (
    <div style={{fontFamily:'Arial,sans-serif',maxWidth:900,margin:'0 auto',padding:'2rem'}}>
      <div style={{display:'flex',justifyContent:'space-between',alignItems:'center',marginBottom:'1.5rem'}}>
        <h1 style={{color:'#1a237e'}}>📚 Course Registration Manager</h1>
        <button style={{...s.btn,background:'#1a237e',color:'white',padding:'10px 20px'}}
          onClick={()=>{setShowForm(!showForm);setEditing(null);setForm({name:'',code:'',credits:'',instructor:'',status:'Active'})}}>
          {showForm ? '✕ Cancel' : '+ Add Course'}
        </button>
      </div>

      {showForm && (
        <div style={{background:'#f0f4ff',border:'1px solid #c5cae9',borderRadius:12,padding:'1.5rem',marginBottom:'1.5rem'}}>
          <h3 style={{marginBottom:'1rem',color:'#1a237e'}}>{editing ? 'Edit Course' : 'New Course'}</h3>
          <div style={{display:'grid',gridTemplateColumns:'1fr 1fr',gap:'0 16px'}}>
            <div><label style={{fontSize:13,fontWeight:'bold'}}>Course Name</label>
              <input style={s.inp} value={form.name} onChange={e=>setForm({...form,name:e.target.value})}/></div>
            <div><label style={{fontSize:13,fontWeight:'bold'}}>Course Code</label>
              <input style={s.inp} value={form.code} onChange={e=>setForm({...form,code:e.target.value})}/></div>
            <div><label style={{fontSize:13,fontWeight:'bold'}}>Credits</label>
              <input style={s.inp} type="number" value={form.credits} onChange={e=>setForm({...form,credits:e.target.value})}/></div>
            <div><label style={{fontSize:13,fontWeight:'bold'}}>Instructor</label>
              <input style={s.inp} value={form.instructor} onChange={e=>setForm({...form,instructor:e.target.value})}/></div>
            <div><label style={{fontSize:13,fontWeight:'bold'}}>Status</label>
              <select style={s.inp} value={form.status} onChange={e=>setForm({...form,status:e.target.value})}>
                <option>Active</option><option>Inactive</option>
              </select></div>
          </div>
          <button style={{...s.btn,background:'#1a237e',color:'white'}} onClick={handleSubmit}>
            {editing ? 'Update Course' : 'Add Course'}
          </button>
        </div>
      )}

      <input style={{...s.inp,borderRadius:24,paddingLeft:16}} placeholder="🔍 Search courses..."
        value={search} onChange={e=>setSearch(e.target.value)}/>

      <p style={{fontSize:13,color:'#666',margin:'0 0 12px'}}>
        Showing {filtered.length} of {courses.length} courses
      </p>

      <table style={{width:'100%',borderCollapse:'collapse',background:'white',
        borderRadius:12,overflow:'hidden',boxShadow:'0 2px 8px rgba(0,0,0,0.08)'}}>
        <thead><tr style={{background:'#1a237e',color:'white'}}>
          {['Course Name','Code','Credits','Instructor','Status','Actions'].map(h=><th key={h}
            style={{padding:'12px 16px',textAlign:'left',fontWeight:'normal',fontSize:14}}>{h}</th>)}
        </tr></thead>
        <tbody>{filtered.map((c,i)=><tr key={c.id} style={{background:i%2===0?'white':'#fafafa'}}>
          <td style={{padding:'12px 16px',fontWeight:'bold',fontSize:14}}>{c.name}</td>
          <td style={{padding:'12px 16px',fontSize:13,color:'#555'}}>{c.code}</td>
          <td style={{padding:'12px 16px',textAlign:'center'}}>{c.credits}</td>
          <td style={{padding:'12px 16px',fontSize:14}}>{c.instructor}</td>
          <td style={{padding:'12px 16px'}}>
            <span style={{background:c.status==='Active'?'#e8f5e9':'#fff3e0',
              color:c.status==='Active'?'#2d6a4f':'#e65100',
              padding:'3px 10px',borderRadius:20,fontSize:12}}>{c.status}</span>
          </td>
          <td style={{padding:'12px 16px'}}>
            <button style={{...s.btn,background:'#e8f0fe',color:'#1a237e',marginRight:6,padding:'5px 12px'}}
              onClick={()=>startEdit(c)}>Edit</button>
            <button style={{...s.btn,background:'#fce4ec',color:'#b71c1c',padding:'5px 12px'}}
              onClick={()=>deleteCourse(c.id)}>Delete</button>
          </td>
        </tr>)}</tbody>
      </table>
    </div>
  );
}

Step 4: App.js(replace with this one):

import React from 'react';
import CourseManager from './CourseManager';

export default function App() {
  return <CourseManager />;
}

Step 5:
npm start


B.ans

bg-changer.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Background Color Changer</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: Arial, sans-serif; min-height: 100vh; display: flex;
      flex-direction: column; align-items: center; justify-content: center;
      transition: background-color 0.6s ease; background: #ffffff; gap: 20px; }
    #colorDisplay { font-size: 1.4rem; font-weight: bold; padding: 16px 40px;
      border-radius: 12px; background: rgba(255,255,255,0.8); backdrop-filter: blur(4px);
      box-shadow: 0 2px 12px rgba(0,0,0,0.1); }
    .buttons { display: flex; flex-wrap: wrap; gap: 12px; justify-content: center; }
    .btn { padding: 12px 28px; border: 2px solid rgba(255,255,255,0.4); border-radius: 50px;
      cursor: pointer; font-size: 15px; font-weight: bold; color: white;
      transition: transform 0.15s, box-shadow 0.15s; }
    .btn:hover { transform: scale(1.05); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
    .btn:active { transform: scale(0.97); }
    #message { font-size: 1.1rem; font-weight: bold; opacity: 0;
      transition: opacity 0.4s; background: rgba(255,255,255,0.85);
      padding: 10px 24px; border-radius: 50px; }
    #message.visible { opacity: 1; }
  </style>
</head>
<body>
  <h2 id="colorDisplay">Current: #ffffff</h2>
  <div class="buttons">
    <button class="btn" style="background:#e63946" onclick="changeBg('#e63946','Crimson Red')">🔴 Red</button>
    <button class="btn" style="background:#3a86ff" onclick="changeBg('#3a86ff','Ocean Blue')">🔵 Blue</button>
    <button class="btn" style="background:#2d6a4f" onclick="changeBg('#2d6a4f','Forest Green')">🟢 Green</button>
    <button class="btn" style="background:#e9c46a;color:#333" onclick="changeBg('#e9c46a','Sunny Yellow')">🟡 Yellow</button>
    <button class="btn" style="background:#7209b7" onclick="changeBg('#7209b7','Deep Purple')">🟣 Purple</button>
    <button class="btn" style="background:#f4845f" onclick="changeBg('#f4845f','Sunset Orange')">🟠 Orange</button>
    <button class="btn" style="background:#023e8a" onclick="changeBg('#023e8a','Midnight Blue')">🌙 Midnight</button>
    <button class="btn" style="background:#555;color:#fff" onclick="changeBg('#ffffff','Clean White')">⬜ Reset</button>
    <button class="btn" style="background:#444" onclick="randomColor()">🎲 Random</button>
  </div>
  <p id="message"></p>

  <script>
    function changeBg(color, name) {
      document.body.style.backgroundColor = color;
      document.getElementById('colorDisplay').textContent = 'Current: ' + color;
      showMsg('✅ Changed to ' + name + '!');
    }

    function randomColor() {
      const hex = '#' + Math.floor(Math.random() * 0xffffff).toString(16).padStart(6,'0');
      document.body.style.backgroundColor = hex;
      document.getElementById('colorDisplay').textContent = 'Current: ' + hex;
      showMsg('🎲 Random color: ' + hex);
    }

    function showMsg(text) {
      const m = document.getElementById('message');
      m.textContent = text;
      m.classList.add('visible');
      setTimeout(() => m.classList.remove('visible'), 2000);
    }
  </script>
</body>
</html>



3.Design and develop a full-stack Online Examination System where students can
register, log in, and attend exams online.Design the frontend design for exam
interfaces, backend processing for evaluation, and secure storage of student responses
and results.Include features such as authentication, timer-based exams, result
generation, and responsive design.


ANS
same as exp1 and exp2 
Frontend(src/Exam.js):

import React, { useState, useEffect, useCallback } from 'react';

const questions = [
  { id:1, q:'What does HTML stand for?',
    options:['HyperText Markup Language','High Text Machine Language','HyperTool Markup Link','None'],
    answer:0 },
  { id:2, q:'Which tag is used to create a hyperlink?',
    options:['<link>','<a>','<href>','<url>'], answer:1 },
  { id:3, q:'CSS stands for:',
    options:['Computer Style Sheets','Creative Style Sheets','Cascading Style Sheets','Colorful Style Sheets'],
    answer:2 },
  { id:4, q:'Which is a JavaScript framework?',
    options:['Django','Spring','React','Laravel'], answer:2 },
  { id:5, q:'HTTP status code for "Not Found" is:',
    options:['200','301','404','500'], answer:2 },
];

export default function Exam() {
  const [started, setStarted] = useState(false);
  const [current, setCurrent] = useState(0);
  const [answers, setAnswers] = useState({});
  const [timeLeft, setTimeLeft] = useState(300); // 5 min
  const [submitted, setSubmitted] = useState(false);
  const [result, setResult] = useState(null);
  const [name, setName] = useState('');

  const submit = useCallback(() => {
    let score = 0;
    questions.forEach(q => { if (answers[q.id] === q.answer) score++; });
    setResult({ score, total: questions.length, percent: (score/questions.length*100).toFixed(1) });
    setSubmitted(true);
  }, [answers]);

  useEffect(() => {
    if (!started || submitted) return;
    if (timeLeft === 0) { submit(); return; }
    const t = setTimeout(() => setTimeLeft(t => t-1), 1000);
    return () => clearTimeout(t);
  }, [started, submitted, timeLeft, submit]);

  const mins = String(Math.floor(timeLeft/60)).padStart(2,'0');
  const secs = String(timeLeft%60).padStart(2,'0');

  if (!started) return (
    <div style={centerBox}>
      <h2>Online Examination</h2>
      <p style={{margin:'12px 0',color:'#555'}}>5 Questions · 5 Minutes · Auto-Submit</p>
      <input style={inp} placeholder="Enter your name" value={name}
        onChange={e=>setName(e.target.value)}/>
      <button style={btn} onClick={()=>name && setStarted(true)} disabled={!name}>
        Start Exam
      </button>
    </div>
  );

  if (submitted) return (
    <div style={centerBox}>
      <h2>Exam Completed!</h2>
      <div style={{fontSize:'4rem',margin:'1rem 0'}}>
        {result.percent >= 60 ? '🎉' : '📚'}
      </div>
      <p style={{fontSize:'1.4rem',fontWeight:'bold'}}>
        {result.score} / {result.total}
      </p>
      <p style={{color: result.percent >= 60 ? 'green' : 'red', fontSize:'1.1rem'}}>
        {result.percent}% — {result.percent >= 60 ? 'PASS' : 'FAIL'}
      </p>
      <h3 style={{marginTop:'1.5rem',marginBottom:'0.75rem'}}>Review</h3>
      {questions.map(q=><div key={q.id} style={{textAlign:'left',marginBottom:12,
        background: answers[q.id]===q.answer ? '#e8f5e9':'#ffebee',
        padding:'10px',borderRadius:6}}>
        <p style={{fontWeight:'bold',fontSize:14}}>{q.q}</p>
        <p style={{fontSize:13,color:'green'}}>Correct: {q.options[q.answer]}</p>
        {answers[q.id] !== q.answer &&
          <p style={{fontSize:13,color:'red'}}>Your answer: {q.options[answers[q.id]] || 'Not answered'}</p>}
      </div>)}
      <button style={btn} onClick={()=>{setStarted(false);setSubmitted(false);setAnswers({});
        setTimeLeft(300);setCurrent(0);}}>Retake Exam</button>
    </div>
  );

  const q = questions[current];
  return (
    <div style={{maxWidth:640,margin:'40px auto',fontFamily:'Arial,sans-serif',padding:'1rem'}}>
      <div style={{display:'flex',justifyContent:'space-between',alignItems:'center',marginBottom:'1.5rem'}}>
        <span style={{fontWeight:'bold'}}>{name}'s Exam</span>
        <span style={{background: timeLeft < 60 ? '#e63946':'#3a86ff',color:'white',
          padding:'6px 16px',borderRadius:20,fontFamily:'monospace',fontSize:'1.1rem'}}>
          {mins}:{secs}
        </span>
        <span style={{color:'#666'}}>Q {current+1}/{questions.length}</span>
      </div>

      <div style={{background:'white',borderRadius:12,padding:'1.5rem',
        boxShadow:'0 2px 12px rgba(0,0,0,0.1)',marginBottom:'1.5rem'}}>
        <p style={{fontSize:'1.1rem',fontWeight:'bold',marginBottom:'1rem'}}>{q.q}</p>
        {q.options.map((opt,i)=><div key={i}
          style={{padding:'10px 14px',marginBottom:8,borderRadius:6,cursor:'pointer',
            border:`2px solid ${answers[q.id]===i ? '#3a86ff':'#ddd'}`,
            background: answers[q.id]===i ? '#e8f0fe':'white'}}
          onClick={()=>setAnswers({...answers,[q.id]:i})}>
          {String.fromCharCode(65+i)}. {opt}
        </div>)}
      </div>

      <div style={{display:'flex',justifyContent:'space-between'}}>
        <button style={{...btn,background:'#888'}} onClick={()=>setCurrent(c=>c-1)} disabled={current===0}>
          Previous
        </button>
        {current < questions.length-1
          ? <button style={btn} onClick={()=>setCurrent(c=>c+1)}>Next</button>
          : <button style={{...btn,background:'#2d6a4f'}} onClick={submit}>Submit Exam</button>}
      </div>
    </div>
  );
}

const centerBox = {maxWidth:480,margin:'60px auto',background:'white',
  padding:'2rem',borderRadius:12,boxShadow:'0 2px 12px rgba(0,0,0,0.1)',textAlign:'center',fontFamily:'Arial,sans-serif'};
const inp = {display:'block',width:'100%',padding:'10px 14px',border:'1px solid #ddd',borderRadius:6,marginBottom:12,fontSize:15};
const btn = {padding:'10px 24px',background:'#3a86ff',color:'white',border:'none',borderRadius:6,cursor:'pointer',fontSize:15};


Backend (same as EXP1 )
do everytrhigs same as exp 1 and 2




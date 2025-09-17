<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Authorization Page</title>
  <style>
    :root {
      --border-color: rgba(255,255,255,0.12);
      --input-bg: rgba(255,255,255,0.04);
      --accent-shadow: rgba(74,172,254,0.12);
    }

    * { box-sizing: border-box; }

    body{
      margin:0;
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
      color: #fff;
      background: linear-gradient(#0c0c0c);
      padding: 24px;
    }

    /* Single thin bordered group around all items */
    .container {
      width:100%;
      max-width:420px;
      border-radius:12px;
      padding:20px;
      border: 1px solid var(--border-color); /* thin border */
      background:  #fff(255,255,255,0.02); /* very subtle tint so the border shows on all screens */
      backdrop-filter: blur(4px);
    }

    .container h2{
      margin:0 0 16px 0;
      text-align:center;
      font-size:20px;
      font-weight:600;
      color: #fff;
    }

    form { width:100%; }

    .input-group {
      position: relative;
      margin-bottom:14px;
    }

    .input-group input,
    .input-group select {
      width:100%;
      padding: 12px 40px 12px 12px;
      border-radius:8px;
      border: 1px solid rgba(255,255,255,0.06);
      background: var(--input-bg);
      color: #fff;
      outline: none;
      transition: border-color .18s ease, box-shadow .18s ease, transform .12s ease;
      font-size:14px;
    }

    .input-group select {
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
      background-image: none;
    }

    .input-group input::placeholder,
    .input-group select::placeholder {
      color: rgba(255,255,255,0.8);
    }

    .input-group input:focus,
    .input-group select:focus {
      border-color: #fff(218, 209, 209, 0.22);
      box-shadow: 0 0 0 6px var(--accent-shadow);
      transform: translateY(-1px);
    }

    .input-group i {
      position:absolute;
      right:12px;
      top:50%;
      transform:translateY(-50%);
      pointer-events:none;
      color:#141313;
      font-style: normal; /* emojis look fine */
      opacity:0.95;
    }

    button {
      width:100%;
      padding:12px;
      border-radius:8px;
      border:none;
      background: linear-gradient(135deg, #4facfe, #43e97b);
      color:#fff;
      font-weight:600;
      font-size:15px;
      cursor:pointer;
      transition: transform .14s ease, box-shadow .14s ease;
    }

    button:hover {
      transform: translateY(-3px);
      box-shadow: 0 6px 18px  #fff(248, 246, 246, 0.15);
    }

    @media (max-width:480px){
      .container { padding:16px; }
      .input-group input, .input-group select { font-size:15px; }
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Authorization Form</h2>
    <form id="authForm" novalidate>
      <div class="input-group">
        <input type="text" id="fullname" placeholder="Full Name" required />
        <i>👤</i>
      </div>

      <div class="input-group">
        <input type="email" id="email" placeholder="Email" required />
        <i>📧</i>
      </div>

      <div class="input-group">
        <input type="password" id="password" placeholder="Password" required />
        <i>🔒</i>
      </div>

      <div class="input-group">
        <input type="text" id="projectName" placeholder="Project Name" required />
        <i>📂</i>
      </div>

     <!-------- <div class="input-group">
        <select id="projectSize" required>
          <option value="">Select Project Size</option>
          <option value="Small">Small</option>
          <option value="Medium">Medium</option>
          <option value="Large">Large</option>
        </select>
        <i>📏</i>
      </div>---->

      <div class="input-group">
        <input type="text" id="contact" placeholder="Contact Number (10 digits)" required />
        <i>📱</i>
      </div>

      <button type="submit">Submit</button>
    </form>
  </div>

  <script>
    const form = document.getElementById('authForm');

    form.addEventListener('submit', function(e){
      e.preventDefault();

      const fullname = document.getElementById('fullname').value.trim();
      const email = document.getElementById('email').value.trim();
      const password = document.getElementById('password').value.trim();
      const projectName = document.getElementById('projectName').value.trim();
     // const projectSize = document.getElementById('projectSize').value;//
      const contact = document.getElementById('contact').value.trim();

      // Simple validations
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!fullname) { alert("Please enter your full name."); return; }
      if (!emailPattern.test(email)) { alert("Please enter a valid email address."); return; }
      if (password.length < 6) { alert("Password must be at least 6 characters."); return; }
      if (!projectName) { alert("Please enter project name."); return; }
    //  if (!projectSize) { alert("Please select project size."); return; }//
      if (!/^\d{10}$/.test(contact)) { alert("Contact number must be exactly 10 digits."); return; }

      // Success
      alert("Form submitted successfully!");
      form.reset();
    });
  </script>
</body>
</html>

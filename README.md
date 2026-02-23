<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>CIU · Mobile Money</title>
  <!-- Font Awesome 6 (free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 16px;
    }

    /* Clean phone frame - perfect size */
    .phone {
      max-width: 380px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 36px;
      box-shadow: 0 20px 40px rgba(0, 20, 30, 0.1);
      overflow: hidden;
      padding: 30px 24px 20px 24px;
    }

    /* Logo Area */
    .logo-area {
      text-align: left;
      margin-bottom: 30px;
    }

    .logo-icon {
      width: 60px;
      height: 60px;
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 12px;
      color: white;
      font-size: 2rem;
    }

    .logo-area h1 {
      color: #003d4d;
      font-size: 2.2rem;
      font-weight: 700;
      line-height: 1;
      margin-bottom: 4px;
    }

    .logo-area p {
      color: #597e89;
      font-size: 0.9rem;
    }

    /* Auth Tabs */
    .auth-tabs {
      display: flex;
      gap: 20px;
      margin-bottom: 30px;
    }

    .auth-tab {
      font-size: 1.2rem;
      font-weight: 600;
      color: #999;
      cursor: pointer;
      padding-bottom: 8px;
    }

    .auth-tab.active {
      color: #006a7a;
      border-bottom: 3px solid #006a7a;
    }

    /* Forms */
    .auth-form {
      display: none;
    }

    .auth-form.active {
      display: block;
    }

    .form-group {
      margin-bottom: 20px;
    }

    .form-group label {
      display: block;
      color: #333;
      font-weight: 500;
      margin-bottom: 8px;
      font-size: 0.95rem;
    }

    .input-icon {
      position: relative;
    }

    .input-icon i {
      position: absolute;
      left: 16px;
      top: 50%;
      transform: translateY(-50%);
      color: #00acc1;
      font-size: 1.1rem;
    }

    .input-icon input {
      width: 100%;
      padding: 16px 16px 16px 50px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      background: #fafafa;
    }

    .input-icon input:focus {
      border-color: #00bcd4;
      background: white;
    }

    .auth-btn {
      background: #006a7a;
      color: white;
      border: none;
      width: 100%;
      padding: 16px;
      border-radius: 30px;
      font-size: 1.1rem;
      font-weight: 600;
      margin: 20px 0 15px;
      cursor: pointer;
      transition: background 0.2s;
    }

    .auth-btn:hover {
      background: #00838f;
    }

    .auth-footer {
      text-align: center;
      color: #597e89;
      font-size: 0.95rem;
    }

    .auth-footer a {
      color: #006a7a;
      font-weight: 600;
      text-decoration: none;
    }

    /* Success Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 12px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      border: 2px solid #c3e6cb;
      display: none;
    }

    /* Main Dashboard */
    #mainDashboard, #profilePage, #levelPage {
      display: none;
    }

    .welcome-title {
      font-size: 2rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 0.9rem;
      color: #333;
      margin-bottom: 15px;
    }

    .balance-container {
      background: #f9f9f9;
      border-radius: 20px;
      padding: 15px;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid #eaeaea;
    }

    .balance-label {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .balance-label i {
      font-size: 1.5rem;
      color: #333;
    }

    .balance-info h4 {
      color: #666;
      font-size: 0.8rem;
    }

    .balance-info .amount {
      font-size: 1.4rem;
      font-weight: 700;
      color: #000;
    }

    .task-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 15px;
    }

    .task-header h3 {
      font-size: 1.4rem;
      color: #000;
    }

    .teaser-badge {
      background: #333;
      color: white;
      padding: 4px 12px;
      border-radius: 30px;
      font-size: 0.75rem;
    }

    .reward-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 0;
      border-bottom: 1px solid #f0f0f0;
    }

    .card-title {
      font-weight: 600;
      color: #000;
    }

    .card-value {
      font-weight: 700;
      color: #000;
    }

    .action-row {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin: 20px 0;
    }

    .action-item {
      display: flex;
      align-items: center;
      gap: 8px;
      color: #000;
      font-weight: 500;
      cursor: pointer;
    }

    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }

    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
    }

    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      padding: 15px 0 5px 0;
      border-top: 1px solid #f0f0f0;
      margin-top: 15px;
    }

    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #999;
      font-size: 0.7rem;
      gap: 4px;
      cursor: pointer;
    }

    .nav-item i {
      font-size: 1.2rem;
      color: #999;
    }

    .nav-item.active {
      color: #006a7a;
    }

    .nav-item.active i {
      color: #006a7a;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      color: #333;
      padding: 8px 20px;
      border-radius: 30px;
      cursor: pointer;
      margin: 15px 0;
    }

    /* Level Page */
    .level-title {
      color: #ff0000;
      font-size: 1.8rem;
      font-weight: 800;
      text-transform: uppercase;
      text-align: center;
      margin: 40px 0;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- AUTHENTICATION SECTION -->
    <div id="authContainer">
      <!-- Logo -->
      <div class="logo-area">
        <div class="logo-icon">
          <i class="fas fa-hand-holding-heart"></i>
        </div>
        <h1>CIU</h1>
        <p>Mobile Money · Earn</p>
      </div>

      <!-- Success Message -->
      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

      <!-- Auth Tabs - Simple as image -->
      <div class="auth-tabs">
        <div class="auth-tab active" onclick="switchAuthTab('login')" id="loginTab">Login</div>
        <div class="auth-tab" onclick="switchAuthTab('register')" id="registerTab">Register</div>
      </div>

      <!-- LOGIN FORM - Exactly as your image -->
      <div id="loginForm" class="auth-form active">
        <form onsubmit="handleLogin(event)">
          <div class="form-group">
            <label>Enter your phone number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="loginPhone" placeholder="0756 673 144" required>
            </div>
          </div>

          <div class="form-group">
            <label>Enter your password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="loginPassword" placeholder="••••••••" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">Log in</button>

          <div class="auth-footer">
            Don't have an account? <a href="#" onclick="switchAuthTab('register'); return false;">Register</a>
          </div>
        </form>
      </div>

      <!-- REGISTRATION FORM -->
      <div id="registerForm" class="auth-form">
        <form onsubmit="handleRegister(event)">
          <div class="form-group">
            <label>Full names</label>
            <div class="input-icon">
              <i class="fas fa-user"></i>
              <input type="text" id="regFullName" placeholder="Enter your full names" required>
            </div>
          </div>

          <div class="form-group">
            <label>Phone number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="regPhone" placeholder="Enter your phone number" required>
            </div>
          </div>

          <div class="form-group">
            <label>Country</label>
            <div class="input-icon">
              <i class="fas fa-globe-africa"></i>
              <select id="regCountry" style="padding: 16px 16px 16px 50px; width:100%; border:2px solid #e0f0f3; border-radius:30px; background:#fafafa;" required>
                <option value="">Select country</option>
                <option value="Uganda">Uganda 🇺🇬</option>
                <option value="Kenya">Kenya 🇰🇪</option>
                <option value="Tanzania">Tanzania 🇹🇿</option>
              </select>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regPassword" placeholder="Create a password" required>
            </div>
          </div>

          <div class="form-group">
            <label>Confirm password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regConfirmPassword" placeholder="Confirm your password" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">Register</button>

          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchAuthTab('login'); return false;">Log in</a>
          </div>
        </form>
      </div>
    </div>

    <!-- MAIN DASHBOARD (Home) -->
    <div id="mainDashboard">
      <div class="welcome-title">WELCOME</div>
      <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES</div>
      
      <div class="balance-container">
        <div class="balance-label">
          <i class="fas fa-wallet"></i>
          <div class="balance-info">
            <h4>Available Balance</h4>
            <div class="amount" id="balanceAmount">12,500 <small>UGX</small></div>
          </div>
        </div>
        <button class="history-btn" onclick="showHistory()">History</button>
      </div>

      <div class="task-header">
        <h3>Task Hall</h3>
        <span class="teaser-badge">TEASER</span>
      </div>

      <div class="card-grid">
        <div class="reward-card">
          <span class="card-title">TEASER</span>
          <span class="card-value">+1200.00 <small>UGX</small></span>
        </div>
        <div class="reward-card">
          <span class="card-title">VAF</span>
          <span class="card-value">+1200.00 <small>UGX</small></span>
        </div>
        <div class="reward-card">
          <span class="card-title">Out of Ideas</span>
          <span class="card-value">+1200.00 <small>UGX</small></span>
        </div>
      </div>

      <div class="action-row">
        <div class="action-item" onclick="openDepositModal()"><span>Recharge</span></div>
        <div class="action-item" onclick="alert('Coming soon')"><span>Withdraw</span></div>
        <div class="action-item" onclick="alert('Company profile')"><span>Company Profile</span></div>
      </div>

      <div class="company-line">
        <span>Company Profile</span>
        <i class="fas fa-chevron-right"></i>
      </div>

      <div class="bottom-nav">
        <div class="nav-item active" onclick="showHomePage()"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showLevelPage()"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showProfilePage()"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- LEVEL PAGE -->
    <div id="levelPage">
      <div style="height: 200px; display: flex; align-items: center; justify-content: center;">
        <div class="level-title">LEVEL PRICE AND INCOME</div>
      </div>
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item active" onclick="showLevelPage()"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showProfilePage()"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- PROFILE PAGE -->
    <div id="profilePage">
      <div style="padding: 20px 0">
        <div style="display: flex; justify-content: space-between;">
          <span id="currentTime">9:24 PM</span>
          <span><i class="fas fa-user"></i> User</span>
        </div>
        <h3 id="profileName" style="margin:20px 0">Regular Employee</h3>
        
        <div style="display: flex; gap: 10px; margin:20px 0">
          <div style="flex:1; background:#f9f9f9; padding:15px; border-radius:15px;">
            <div style="color:#666; font-size:0.8rem;">Main wallet</div>
            <div id="mainWallet" style="font-weight:700;">0.00 UGX</div>
          </div>
          <div style="flex:1; background:#f9f9f9; padding:15px; border-radius:15px;">
            <div style="color:#666; font-size:0.8rem;">Commission</div>
            <div style="font-weight:700;">387,566.50 UGX</div>
          </div>
        </div>

        <button class="logout-btn" onclick="logout()" style="width:100%;">Logout</button>
      </div>
      
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showLevelPage()"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item active" onclick="showProfilePage()"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL -->
  <div class="modal-overlay" id="depositModal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); justify-content:center; align-items:center;">
    <div style="background:white; max-width:350px; width:90%; border-radius:30px; padding:20px;">
      <h3 style="margin-bottom:15px;">Mobile Money</h3>
      <div style="background:#f0f0f0; padding:15px; border-radius:15px; text-align:center; margin-bottom:15px;">
        <div style="font-size:1.3rem; font-weight:700;">0756 673 144</div>
        <div>NAMUHANGA VERONIC</div>
      </div>
      <input type="number" id="customAmount" placeholder="Enter amount" style="width:100%; padding:15px; border:1px solid #ddd; border-radius:15px; margin-bottom:10px;">
      <button onclick="processDeposit()" style="background:#000; color:white; width:100%; padding:15px; border:none; border-radius:30px;">Pay</button>
      <button onclick="closeDepositModal()" style="margin-top:10px; width:100%; padding:10px; border:none; background:none;">Close</button>
    </div>
  </div>

  <script>
    let users = JSON.parse(localStorage.getItem('cueUsers')) || {};
    let currentUser = localStorage.getItem('currentUser');

    // Show message
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      document.getElementById('messageText').textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      setTimeout(() => msgBox.style.display = 'none', 3000);
    }

    // Switch tabs
    function switchAuthTab(tab) {
      document.getElementById('loginForm').classList.toggle('active', tab === 'login');
      document.getElementById('registerForm').classList.toggle('active', tab === 'register');
      document.getElementById('loginTab').classList.toggle('active', tab === 'login');
      document.getElementById('registerTab').classList.toggle('active', tab === 'register');
    }

    // Handle Login
    function handleLogin(e) {
      e.preventDefault();
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;
      
      users = JSON.parse(localStorage.getItem('cueUsers')) || {};
      
      if (users[phone] && users[phone].password === password) {
        localStorage.setItem('currentUser', phone);
        currentUser = phone;
        showMessage('Login successful!');
        setTimeout(() => showDashboard(), 500);
      } else {
        showMessage('Invalid phone or password', false);
      }
    }

    // Handle Register
    function handleRegister(e) {
      e.preventDefault();
      
      const fullName = document.getElementById('regFullName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;
      const confirmPass = document.getElementById('regConfirmPassword').value;
      
      if (!fullName || !phone || !country || !password) {
        showMessage('Please fill all fields', false);
        return;
      }
      
      if (password.length < 6) {
        showMessage('Password too short', false);
        return;
      }
      
      if (password !== confirmPass) {
        showMessage('Passwords do not match', false);
        return;
      }
      
      users = JSON.parse(localStorage.getItem('cueUsers')) || {};
      
      if (users[phone]) {
        showMessage('Phone already registered', false);
        switchAuthTab('login');
        return;
      }
      
      users[phone] = {
        fullName, phone, country, password,
        balance: 12500,
        registeredDate: new Date().toLocaleString()
      };
      
      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      currentUser = phone;
      
      showMessage('Registration successful!');
      setTimeout(() => showDashboard(), 500);
    }

    // Show dashboard
    function showDashboard() {
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'block';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      
      const user = users[currentUser];
      if (user) {
        document.getElementById('balanceAmount').innerHTML = `${user.balance.toLocaleString()} <small>UGX</small>`;
        document.getElementById('mainWallet').innerHTML = `${user.balance.toFixed(2)} UGX`;
        document.getElementById('profileName').textContent = user.fullName || 'Regular Employee';
      }
      updateTime();
    }

    function showHomePage() {
      document.getElementById('mainDashboard').style.display = 'block';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
    }

    function showProfilePage() {
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'block';
      document.getElementById('levelPage').style.display = 'none';
    }

    function showLevelPage() {
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'block';
    }

    function logout() {
      localStorage.removeItem('currentUser');
      currentUser = null;
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      switchAuthTab('login');
    }

    function updateTime() {
      const now = new Date();
      let hours = now.getHours();
      const minutes = now.getMinutes().toString().padStart(2, '0');
      const ampm = hours >= 12 ? 'PM' : 'AM';
      hours = hours % 12 || 12;
      document.getElementById('currentTime').textContent = `${hours}:${minutes} ${ampm}`;
    }

    // Deposit functions
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
    }
    
    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }
    
    function processDeposit() {
      const amount = parseInt(document.getElementById('customAmount').value);
      if (!amount || amount < 1000) {
        alert('Enter valid amount (min 1000 UGX)');
        return;
      }
      
      alert(`Dial *165*1*0756673144*${amount}# to complete payment`);
      
      if (currentUser && users[currentUser]) {
        users[currentUser].balance += amount;
        localStorage.setItem('cueUsers', JSON.stringify(users));
        document.getElementById('balanceAmount').innerHTML = `${users[currentUser].balance.toLocaleString()} <small>UGX</small>`;
      }
      
      closeDepositModal();
    }

    function showHistory() {
      alert('Transaction history coming soon');
    }

    // Check if user is logged in
    window.onload = function() {
      if (currentUser && users[currentUser]) {
        showDashboard();
      }
      
      // Create demo account if none
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'Demo User',
          phone: '0756673144',
          country: 'Uganda',
          password: '123456',
          balance: 12500,
          registeredDate: new Date().toLocaleString()
        };
        localStorage.setItem('cueUsers', JSON.stringify(users));
      }
      
      setInterval(updateTime, 60000);
    };
  </script>
</body>
</html>

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
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: #f5f5f5;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 12px;
    }

    /* Phone frame */
    .phone {
      max-width: 360px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 36px;
      box-shadow: 0 15px 30px rgba(0,0,0,0.1);
      overflow: hidden;
      padding: 24px 20px;
    }

    /* ===== AUTH PAGES ===== */
    .auth-container {
      display: block;
    }

    .logo-area {
      margin-bottom: 30px;
    }

    .logo-icon {
      width: 48px;
      height: 48px;
      background: #00b8a9;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.5rem;
      margin-bottom: 15px;
    }

    .logo-area h1 {
      font-size: 2.2rem;
      font-weight: 600;
      color: #000;
      line-height: 1.1;
    }

    .logo-area p {
      color: #666;
      font-size: 0.9rem;
      margin-top: 5px;
    }

    .tabs {
      display: flex;
      gap: 30px;
      margin-bottom: 30px;
      border-bottom: 1px solid #f0f0f0;
    }

    .tab {
      font-size: 1.1rem;
      font-weight: 500;
      color: #999;
      padding-bottom: 10px;
      cursor: pointer;
    }

    .tab.active {
      color: #00b8a9;
      border-bottom: 2px solid #00b8a9;
    }

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
    }

    .input-wrapper {
      position: relative;
    }

    .input-wrapper i {
      position: absolute;
      left: 15px;
      top: 50%;
      transform: translateY(-50%);
      color: #00b8a9;
    }

    .input-wrapper input, .input-wrapper select {
      width: 100%;
      padding: 14px 14px 14px 45px;
      border: 1px solid #e0e0e0;
      border-radius: 30px;
      font-size: 0.95rem;
      outline: none;
      background: #fafafa;
    }

    .auth-btn {
      width: 100%;
      padding: 14px;
      background: #00b8a9;
      color: white;
      border: none;
      border-radius: 30px;
      font-size: 1rem;
      font-weight: 600;
      margin: 20px 0 15px;
      cursor: pointer;
    }

    .auth-footer {
      text-align: center;
      color: #666;
      font-size: 0.9rem;
    }

    .auth-footer a {
      color: #00b8a9;
      text-decoration: none;
      font-weight: 500;
    }

    /* ===== HOME PAGE (matches first image) ===== */
    #homePage, #profilePage, #levelPage {
      display: none;
    }

    .welcome-title {
      font-size: 2rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 0.85rem;
      color: #333;
      line-height: 1.4;
      margin-bottom: 15px;
    }

    .divider {
      width: 100%;
      height: 1px;
      background-color: #e0e0e0;
      margin: 15px 0;
    }

    .collab-text {
      font-size: 1rem;
      font-weight: 500;
      color: #000;
      margin-bottom: 20px;
    }

    .task-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 15px;
    }

    .task-header h3 {
      font-size: 1.4rem;
      font-weight: 600;
      color: #000;
    }

    .teaser-badge {
      background: #333;
      color: white;
      padding: 4px 12px;
      border-radius: 30px;
      font-size: 0.75rem;
      font-weight: 500;
    }

    .task-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 0;
      border-bottom: 1px solid #f0f0f0;
    }

    .task-name {
      font-weight: 500;
      color: #000;
    }

    .task-value {
      font-weight: 600;
      color: #000;
    }

    .task-value small {
      font-size: 0.7rem;
      color: #666;
      font-weight: 400;
    }

    .action-list {
      margin: 20px 0;
    }

    .action-item {
      display: flex;
      align-items: center;
      gap: 8px;
      color: #000;
      font-weight: 500;
      margin-bottom: 8px;
      cursor: pointer;
    }

    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }

    .company-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
      margin-bottom: 15px;
    }

    .company-row span {
      font-weight: 500;
      color: #000;
    }

    /* Bottom Navigation */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      padding: 15px 0 5px 0;
      border-top: 1px solid #f0f0f0;
      margin-top: 10px;
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
      color: #00b8a9;
    }

    .nav-item.active i {
      color: #00b8a9;
    }

    /* ===== PROFILE PAGE (matches second image) ===== */
    .profile-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      color: #333;
      font-size: 0.9rem;
    }

    .profile-name-large {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .profile-role {
      color: #666;
      font-size: 0.9rem;
      margin-bottom: 25px;
    }

    .wallet-grid {
      display: flex;
      gap: 12px;
      margin-bottom: 25px;
    }

    .wallet-card {
      flex: 1;
      background: #f9f9f9;
      border-radius: 16px;
      padding: 15px;
    }

    .wallet-label {
      color: #666;
      font-size: 0.8rem;
      margin-bottom: 5px;
    }

    .wallet-amount {
      font-weight: 700;
      color: #000;
    }

    .wallet-amount small {
      font-size: 0.7rem;
      color: #999;
      font-weight: 400;
    }

    .profile-actions {
      display: flex;
      gap: 25px;
      margin-bottom: 25px;
    }

    .profile-action-btn {
      display: flex;
      align-items: center;
      gap: 8px;
      background: none;
      border: none;
      font-size: 0.95rem;
      font-weight: 500;
      color: #000;
      cursor: pointer;
    }

    .income-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      margin-bottom: 20px;
    }

    .income-item {
      border-bottom: 1px solid #f0f0f0;
      padding-bottom: 8px;
    }

    .income-label {
      color: #666;
      font-size: 0.8rem;
      margin-bottom: 3px;
    }

    .income-value {
      font-weight: 700;
      color: #000;
    }

    .income-value small {
      font-size: 0.7rem;
      color: #999;
      font-weight: 400;
    }

    .commission-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 0;
      border-top: 1px solid #eaeaea;
      border-bottom: 1px solid #eaeaea;
      margin-bottom: 20px;
    }

    .commission-label {
      color: #000;
      font-size: 0.9rem;
    }

    .commission-value {
      font-weight: 700;
      color: #000;
    }

    .commission-value small {
      font-size: 0.7rem;
      color: #999;
      font-weight: 400;
    }

    .menu-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
      margin-bottom: 30px;
    }

    .menu-item {
      display: flex;
      align-items: center;
      gap: 10px;
      color: #000;
      font-size: 0.9rem;
    }

    .menu-item i {
      color: #666;
      width: 20px;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      color: #333;
      padding: 10px 20px;
      border-radius: 30px;
      cursor: pointer;
      width: 100%;
      margin: 15px 0;
    }

    /* ===== LEVEL PAGE ===== */
    .level-header {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 200px;
    }

    .level-title {
      color: #ff0000;
      font-size: 1.8rem;
      font-weight: 800;
      text-transform: uppercase;
      text-align: center;
      line-height: 1.3;
    }

    /* Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 12px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      display: none;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- ===== AUTHENTICATION SECTION ===== -->
    <div id="authContainer" class="auth-container">
      <div class="logo-area">
        <div class="logo-icon">
          <i class="fas fa-hand-holding-heart"></i>
        </div>
        <h1>CIU</h1>
        <p>Mobile Money · Earn</p>
      </div>

      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

      <div class="tabs">
        <div class="tab active" onclick="switchTab('login')" id="loginTab">Login</div>
        <div class="tab" onclick="switchTab('register')" id="registerTab">Register</div>
      </div>

      <!-- LOGIN FORM -->
      <div id="loginForm" class="auth-form active">
        <form onsubmit="handleLogin(event)">
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-wrapper">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="loginPhone" placeholder="Enter phone number" required>
            </div>
          </div>
          <div class="form-group">
            <label>Password</label>
            <div class="input-wrapper">
              <i class="fas fa-lock"></i>
              <input type="password" id="loginPassword" placeholder="Enter password" required>
            </div>
          </div>
          <button type="submit" class="auth-btn">Log in</button>
          <div class="auth-footer">
            Don't have an account? <a href="#" onclick="switchTab('register'); return false;">Register</a>
          </div>
        </form>
      </div>

      <!-- REGISTER FORM -->
      <div id="registerForm" class="auth-form">
        <form onsubmit="handleRegister(event)">
          <div class="form-group">
            <label>Full Name</label>
            <div class="input-wrapper">
              <i class="fas fa-user"></i>
              <input type="text" id="regName" placeholder="Enter full name" required>
            </div>
          </div>
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-wrapper">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="regPhone" placeholder="Enter phone number" required>
            </div>
          </div>
          <div class="form-group">
            <label>Country</label>
            <div class="input-wrapper">
              <i class="fas fa-globe-africa"></i>
              <select id="regCountry" required>
                <option value="">Select country</option>
                <option value="Uganda">Uganda</option>
                <option value="Kenya">Kenya</option>
                <option value="Tanzania">Tanzania</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Password</label>
            <div class="input-wrapper">
              <i class="fas fa-lock"></i>
              <input type="password" id="regPassword" placeholder="Create password" required>
            </div>
          </div>
          <button type="submit" class="auth-btn">Register</button>
          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchTab('login'); return false;">Log in</a>
          </div>
        </form>
      </div>
    </div>

    <!-- ===== HOME PAGE (matches first image) ===== -->
    <div id="homePage">
      <div class="welcome-title">WELCOME</div>
      <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES WORK TOGETHER TO CREATE A BETTER FUTURE</div>
      <div class="divider"></div>

      <div class="collab-text">Collaboration. We Believe That Every Employee Can:</div>

      <div class="task-header">
        <h3>Task Hall</h3>
        <span class="teaser-badge">TEASER</span>
      </div>

      <div class="task-card">
        <span class="task-name">TEASER</span>
        <span class="task-value">+1200.00 <small>UGX</small></span>
      </div>
      <div class="task-card">
        <span class="task-name">VAF</span>
        <span class="task-value">+1200.00 <small>UGX</small></span>
      </div>
      <div class="task-card">
        <span class="task-name">Out of Ideas</span>
        <span class="task-value">+1200.00 <small>UGX</small></span>
      </div>

      <div class="action-list">
        <div class="action-item" onclick="alert('Recharge coming soon')"><span>Recharge</span></div>
        <div class="action-item" onclick="alert('Withdraw coming soon')"><span>Withdraw</span></div>
        <div class="action-item" onclick="alert('Company Profile')"><span>Company Profile</span></div>
      </div>

      <div class="company-row">
        <span>Company Profile</span>
        <i class="fas fa-chevron-right"></i>
      </div>

      <div class="bottom-nav">
        <div class="nav-item active" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task page coming soon')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income page coming soon')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- ===== PROFILE PAGE (matches second image) ===== -->
    <div id="profilePage">
      <div class="profile-header">
        <span id="currentTime"></span>
        <span><i class="fas fa-user"></i> <span id="profileDisplayName">User</span></span>
      </div>

      <div class="profile-name-large" id="profileFullName">Mindy official</div>
      <div class="profile-role">M3 Regular Employee</div>

      <div class="wallet-grid">
        <div class="wallet-card">
          <div class="wallet-label">Main wallet</div>
          <div class="wallet-amount" id="mainWallet">0.00 <small>UGX</small></div>
        </div>
        <div class="wallet-card">
          <div class="wallet-label">Commission wallet</div>
          <div class="wallet-amount" id="commissionWallet">387,566.50 <small>UGX</small></div>
        </div>
      </div>

      <div class="profile-actions">
        <button class="profile-action-btn" onclick="alert('Recharge feature coming soon')">
          <i class="fas fa-lock"></i> Recharge
        </button>
        <button class="profile-action-btn" onclick="alert('Withdraw feature coming soon')">
          <i class="fas fa-folder"></i> Withdraw
        </button>
      </div>

      <div class="income-grid">
        <div class="income-item">
          <div class="income-label">yesterday's income</div>
          <div class="income-value">565.00 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">today's income</div>
          <div class="income-value">72,340.00 <small>UGX</small></div>
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
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: #f5f5f5;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 12px;
    }

    /* Phone frame */
    .phone {
      max-width: 360px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 36px;
      box-shadow: 0 15px 30px rgba(0,0,0,0.1);
      overflow: hidden;
      padding: 24px 20px;
    }

    /* ===== AUTH PAGES ===== */
    .auth-container {
      display: block;
    }

    .logo-area {
      margin-bottom: 30px;
    }

    .logo-icon {
      width: 48px;
      height: 48px;
      background: #00b8a9;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.5rem;
      margin-bottom: 15px;
    }

    .logo-area h1 {
      font-size: 2.2rem;
      font-weight: 600;
      color: #000;
      line-height: 1.1;
    }

    .logo-area p {
      color: #666;
      font-size: 0.9rem;
      margin-top: 5px;
    }

    .tabs {
      display: flex;
      gap: 30px;
      margin-bottom: 30px;
      border-bottom: 1px solid #f0f0f0;
    }

    .tab {
      font-size: 1.1rem;
      font-weight: 500;
      color: #999;
      padding-bottom: 10px;
      cursor: pointer;
    }

    .tab.active {
      color: #00b8a9;
      border-bottom: 2px solid #00b8a9;
    }

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
    }

    .input-wrapper {
      position: relative;
    }

    .input-wrapper i {
      position: absolute;
      left: 15px;
      top: 50%;
      transform: translateY(-50%);
      color: #00b8a9;
    }

    .input-wrapper input, .input-wrapper select {
      width: 100%;
      padding: 14px 14px 14px 45px;
      border: 1px solid #e0e0e0;
      border-radius: 30px;
      font-size: 0.95rem;
      outline: none;
      background: #fafafa;
    }

    .auth-btn {
      width: 100%;
      padding: 14px;
      background: #00b8a9;
      color: white;
      border: none;
      border-radius: 30px;
      font-size: 1rem;
      font-weight: 600;
      margin: 20px 0 15px;
      cursor: pointer;
    }

    .auth-footer {
      text-align: center;
      color: #666;
      font-size: 0.9rem;
    }

    .auth-footer a {
      color: #00b8a9;
      text-decoration: none;
      font-weight: 500;
    }

    /* ===== HOME PAGE (matches first image) ===== */
    #homePage, #profilePage, #levelPage {
      display: none;
    }

    .welcome-title {
      font-size: 2rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 0.85rem;
      color: #333;
      line-height: 1.4;
      margin-bottom: 15px;
    }

    .divider {
      width: 100%;
      height: 1px;
      background-color: #e0e0e0;
      margin: 15px 0;
    }

    .collab-text {
      font-size: 1rem;
      font-weight: 500;
      color: #000;
      margin-bottom: 20px;
    }

    .task-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 15px;
    }

    .task-header h3 {
      font-size: 1.4rem;
      font-weight: 600;
      color: #000;
    }

    .teaser-badge {
      background: #333;
      color: white;
      padding: 4px 12px;
      border-radius: 30px;
      font-size: 0.75rem;
      font-weight: 500;
    }

    .task-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 0;
      border-bottom: 1px solid #f0f0f0;
    }

    .task-name {
      font-weight: 500;
      color: #000;
    }

    .task-value {
      font-weight: 600;
      color: #000;
    }

    .task-value small {
      font-size: 0.7rem;
      color: #666;
      font-weight: 400;
    }

    .action-list {
      margin: 20px 0;
    }

    .action-item {
      display: flex;
      align-items: center;
      gap: 8px;
      color: #000;
      font-weight: 500;
      margin-bottom: 8px;
      cursor: pointer;
    }

    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }

    .company-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
      margin-bottom: 15px;
    }

    .company-row span {
      font-weight: 500;
      color: #000;
    }

    /* Bottom Navigation */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      padding: 15px 0 5px 0;
      border-top: 1px solid #f0f0f0;
      margin-top: 10px;
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
      color: #00b8a9;
    }

    .nav-item.active i {
      color: #00b8a9;
    }

    /* ===== PROFILE PAGE (matches second image) ===== */
    .profile-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      color: #333;
      font-size: 0.9rem;
    }

    .profile-name-large {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .profile-role {
      color: #666;
      font-size: 0.9rem;
      margin-bottom: 25px;
    }

    .wallet-grid {
      display: flex;
      gap: 12px;
      margin-bottom: 25px;
    }

    .wallet-card {
      flex: 1;
      background: #f9f9f9;
      border-radius: 16px;
      padding: 15px;
    }

    .wallet-label {
      color: #666;
      font-size: 0.8rem;
      margin-bottom: 5px;
    }

    .wallet-amount {
      font-weight: 700;
      color: #000;
    }

    .wallet-amount small {
      font-size: 0.7rem;
      color: #999;
      font-weight: 400;
    }

    .profile-actions {
      display: flex;
      gap: 25px;
      margin-bottom: 25px;
    }

    .profile-action-btn {
      display: flex;
      align-items: center;
      gap: 8px;
      background: none;
      border: none;
      font-size: 0.95rem;
      font-weight: 500;
      color: #000;
      cursor: pointer;
    }

    .income-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      margin-bottom: 20px;
    }

    .income-item {
      border-bottom: 1px solid #f0f0f0;
      padding-bottom: 8px;
    }

    .income-label {
      color: #666;
      font-size: 0.8rem;
      margin-bottom: 3px;
    }

    .income-value {
      font-weight: 700;
      color: #000;
    }

    .income-value small {
      font-size: 0.7rem;
      color: #999;
      font-weight: 400;
    }

    .commission-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 0;
      border-top: 1px solid #eaeaea;
      border-bottom: 1px solid #eaeaea;
      margin-bottom: 20px;
    }

    .commission-label {
      color: #000;
      font-size: 0.9rem;
    }

    .commission-value {
      font-weight: 700;
      color: #000;
    }

    .commission-value small {
      font-size: 0.7rem;
      color: #999;
      font-weight: 400;
    }

    .menu-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
      margin-bottom: 30px;
    }

    .menu-item {
      display: flex;
      align-items: center;
      gap: 10px;
      color: #000;
      font-size: 0.9rem;
    }

    .menu-item i {
      color: #666;
      width: 20px;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      color: #333;
      padding: 10px 20px;
      border-radius: 30px;
      cursor: pointer;
      width: 100%;
      margin: 15px 0;
    }

    /* ===== LEVEL PAGE ===== */
    .level-header {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 200px;
    }

    .level-title {
      color: #ff0000;
      font-size: 1.8rem;
      font-weight: 800;
      text-transform: uppercase;
      text-align: center;
      line-height: 1.3;
    }

    /* Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 12px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      display: none;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- ===== AUTHENTICATION SECTION ===== -->
    <div id="authContainer" class="auth-container">
      <div class="logo-area">
        <div class="logo-icon">
          <i class="fas fa-hand-holding-heart"></i>
        </div>
        <h1>CIU</h1>
        <p>Mobile Money · Earn</p>
      </div>

      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

      <div class="tabs">
        <div class="tab active" onclick="switchTab('login')" id="loginTab">Login</div>
        <div class="tab" onclick="switchTab('register')" id="registerTab">Register</div>
      </div>

      <!-- LOGIN FORM -->
      <div id="loginForm" class="auth-form active">
        <form onsubmit="handleLogin(event)">
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-wrapper">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="loginPhone" placeholder="Enter phone number" required>
            </div>
          </div>
          <div class="form-group">
            <label>Password</label>
            <div class="input-wrapper">
              <i class="fas fa-lock"></i>
              <input type="password" id="loginPassword" placeholder="Enter password" required>
            </div>
          </div>
          <button type="submit" class="auth-btn">Log in</button>
          <div class="auth-footer">
            Don't have an account? <a href="#" onclick="switchTab('register'); return false;">Register</a>
          </div>
        </form>
      </div>

      <!-- REGISTER FORM -->
      <div id="registerForm" class="auth-form">
        <form onsubmit="handleRegister(event)">
          <div class="form-group">
            <label>Full Name</label>
            <div class="input-wrapper">
              <i class="fas fa-user"></i>
              <input type="text" id="regName" placeholder="Enter full name" required>
            </div>
          </div>
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-wrapper">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="regPhone" placeholder="Enter phone number" required>
            </div>
          </div>
          <div class="form-group">
            <label>Country</label>
            <div class="input-wrapper">
              <i class="fas fa-globe-africa"></i>
              <select id="regCountry" required>
                <option value="">Select country</option>
                <option value="Uganda">Uganda</option>
                <option value="Kenya">Kenya</option>
                <option value="Tanzania">Tanzania</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Password</label>
            <div class="input-wrapper">
              <i class="fas fa-lock"></i>
              <input type="password" id="regPassword" placeholder="Create password" required>
            </div>
          </div>
          <button type="submit" class="auth-btn">Register</button>
          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchTab('login'); return false;">Log in</a>
          </div>
        </form>
      </div>
    </div>

    <!-- ===== HOME PAGE (matches first image) ===== -->
    <div id="homePage">
      <div class="welcome-title">WELCOME</div>
      <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES WORK TOGETHER TO CREATE A BETTER FUTURE</div>
      <div class="divider"></div>

      <div class="collab-text">Collaboration. We Believe That Every Employee Can:</div>

      <div class="task-header">
        <h3>Task Hall</h3>
        <span class="teaser-badge">TEASER</span>
      </div>

      <div class="task-card">
        <span class="task-name">TEASER</span>
        <span class="task-value">+1200.00 <small>UGX</small></span>
      </div>
      <div class="task-card">
        <span class="task-name">VAF</span>
        <span class="task-value">+1200.00 <small>UGX</small></span>
      </div>
      <div class="task-card">
        <span class="task-name">Out of Ideas</span>
        <span class="task-value">+1200.00 <small>UGX</small></span>
      </div>

      <div class="action-list">
        <div class="action-item" onclick="alert('Recharge coming soon')"><span>Recharge</span></div>
        <div class="action-item" onclick="alert('Withdraw coming soon')"><span>Withdraw</span></div>
        <div class="action-item" onclick="alert('Company Profile')"><span>Company Profile</span></div>
      </div>

      <div class="company-row">
        <span>Company Profile</span>
        <i class="fas fa-chevron-right"></i>
      </div>

      <div class="bottom-nav">
        <div class="nav-item active" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task page coming soon')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income page coming soon')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- ===== PROFILE PAGE (matches second image) ===== -->
    <div id="profilePage">
      <div class="profile-header">
        <span id="currentTime"></span>
        <span><i class="fas fa-user"></i> <span id="profileDisplayName">User</span></span>
      </div>

      <div class="profile-name-large" id="profileFullName">Mindy official</div>
      <div class="profile-role">M3 Regular Employee</div>

      <div class="wallet-grid">
        <div class="wallet-card">
          <div class="wallet-label">Main wallet</div>
          <div class="wallet-amount" id="mainWallet">0.00 <small>UGX</small></div>
        </div>
        <div class="wallet-card">
          <div class="wallet-label">Commission wallet</div>
          <div class="wallet-amount" id="commissionWallet">387,566.50 <small>UGX</small></div>
        </div>
      </div>

      <div class="profile-actions">
        <button class="profile-action-btn" onclick="alert('Recharge feature coming soon')">
          <i class="fas fa-lock"></i> Recharge
        </button>
        <button class="profile-action-btn" onclick="alert('Withdraw feature coming soon')">
          <i class="fas fa-folder"></i> Withdraw
        </button>
      </div>

      <div class="income-grid">
        <div class="income-item">
          <div class="income-label">yesterday's income</div>
          <div class="income-value">565.00 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">today's income</div>
          <div class="income-value">72,340.00 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">total income</div>
          <div class="income-value">713,066.50 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">this week's income</div>
          <div class="income-value">72,340.00 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">this month's income</div>
          <div class="income-value">387,461.50 <small>UGX</small></div>
        </div>
      </div>

      <div class="commission-row">
        <span class="commission-label">Commission from subordinate tasks</span>
        <span class="commission-value">1,096.50 <small>UGX</small></span>
      </div>

      <div class="menu-grid">
        <div class="menu-item"><i class="fas fa-clipboard-list"></i> task record</div>
        <div class="menu-item"><i class="fas fa-users"></i> team report</div>
        <div class="menu-item"><i class="fas fa-calendar-alt"></i> daily report</div>
        <div class="menu-item"><i class="fas fa-file-invoice"></i> bill record</div>
        <div class="menu-item"><i class="fas fa-chart-line"></i> Position Salary</div>
        <div class="menu-item"><i class="fas fa-download"></i> APP download</div>
      </div>

      <button class="logout-btn" onclick="logout()"><i class="fas fa-sign-out-alt"></i> Logout</button>

      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task page coming soon')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income page coming soon')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item active" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- ===== LEVEL PAGE (with red text) ===== -->
    <div id="levelPage">
      <div class="level-header">
        <div class="level-title">LEVELS PRICE AND SALARIES</div>
      </div>

      <div style="text-align: center; color: #666; margin-top: 50px;">
        <p>Level details coming soon...</p>
      </div>

      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task page coming soon')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item active" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income page coming soon')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>
  </div>

  <script>
    // ===== DATA =====
    let users = JSON.parse(localStorage.getItem('ciuUsers')) || {};
    let currentUser = localStorage.getItem('currentUser');

    // ===== UI FUNCTIONS =====
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      document.getElementById('messageText').textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      setTimeout(() => msgBox.style.display = 'none', 3000);
    }

    function switchTab(tab) {
      document.getElementById('loginForm').classList.toggle('active', tab === 'login');
      document.getElementById('registerForm').classList.toggle('active', tab === 'register');
      document.getElementById('loginTab').classList.toggle('active', tab === 'login');
      document.getElementById('registerTab').classList.toggle('active', tab === 'register');
    }

    function showPage(page) {
      document.getElementById('homePage').style.display = page === 'home' ? 'block' : 'none';
      document.getElementById('profilePage').style.display = page === 'profile' ? 'block' : 'none';
      document.getElementById('levelPage').style.display = page === 'level' ? 'block' : 'none';
      document.getElementById('authContainer').style.display = 'none';
    }

    // ===== AUTH FUNCTIONS =====
    function handleLogin(e) {
      e.preventDefault();
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;

      users = JSON.parse(localStorage.getItem('ciuUsers')) || {};

      if (users[phone] && users[phone].password === password) {
        localStorage.setItem('currentUser', phone);
        currentUser = phone;
        showMessage('Login successful!');
        setTimeout(() => {
          loadUserData();
          showPage('home');
        }, 500);
      } else {
        showMessage('Invalid phone or password', false);
      }
    }

    function handleRegister(e) {
      e.preventDefault();
      const name = document.getElementById('regName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;

      if (!name || !phone || !country || !password) {
        showMessage('Please fill all fields', false);
        return;
      }

      users = JSON.parse(localStorage.getItem('ciuUsers')) || {};

      if (users[phone]) {
        showMessage('Phone already registered', false);
        switchTab('login');
        return;
      }

      users[phone] = {
        fullName: name,
        phone: phone,
        country: country,
        password: password,
        balance: 12500,
        registeredDate: new Date().toLocaleString()
      };

      localStorage.setItem('ciuUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      currentUser = phone;

      showMessage('Registration successful!');
      setTimeout(() => {
        loadUserData();
        showPage('home');
      }, 500);
    }

    function loadUserData() {
      if (!currentUser) return;
      const user = users[currentUser];
      if (!user) return;

      document.getElementById('profileFullName').textContent = user.fullName || 'Mindy official';
      document.getElementById('profileDisplayName').textContent = user.fullName?.split(' ')[0] || 'User';
      document.getElementById('mainWallet').innerHTML = `${(user.balance || 0).toFixed(2)} <small>UGX</small>`;
    }

    function logout() {
      localStorage.removeItem('currentUser');
      currentUser = null;
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('homePage').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      switchTab('login');
    }

    // ===== TIME FUNCTION =====
    function updateTime() {
      const now = new Date();
      let hours = now.getHours();
      const minutes = now.getMinutes().toString().padStart(2, '0');
      const ampm = hours >= 12 ? 'PM' : 'AM';
      hours = hours % 12 || 12;
      document.getElementById('currentTime').textContent = `${hours}:${minutes} ${ampm}`;
    }

    // ===== INIT =====
    window.onload = function() {
      // Create demo account if none exists
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'Mindy official',
          phone: '0756673144',
          country: 'Uganda',
          password: '123456',
          balance: 12500,
          registeredDate: new Date().toLocaleString()
        };
        localStorage.setItem('ciuUsers', JSON.stringify(users));
      }

      if (currentUser && users[currentUser]) {
        loadUserData();
        showPage('home');
      }

      updateTime();
      setInterval(updateTime, 60000);
    };
  </script>
</body>
</html>￼Enter        </div>
        <div class="income-item">
          <div class="income-label">total income</div>
          <div class="income-value">713,066.50 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">this week's income</div>
          <div class="income-value">72,340.00 <small>UGX</small></div>
        </div>
        <div class="income-item">
          <div class="income-label">this month's income</div>
          <div class="income-value">387,461.50 <small>UGX</small></div>
        </div>
      </div>

      <div class="commission-row">
        <span class="commission-label">Commission from subordinate tasks</span>
        <span class="commission-value">1,096.50 <small>UGX</small></span>
      </div>

      <div class="menu-grid">
        <div class="menu-item"><i class="fas fa-clipboard-list"></i> task record</div>
        <div class="menu-item"><i class="fas fa-users"></i> team report</div>
        <div class="menu-item"><i class="fas fa-calendar-alt"></i> daily report</div>
        <div class="menu-item"><i class="fas fa-file-invoice"></i> bill record</div>
        <div class="menu-item"><i class="fas fa-chart-line"></i> Position Salary</div>
        <div class="menu-item"><i class="fas fa-download"></i> APP download</div>
      </div>

      <button class="logout-btn" onclick="logout()"><i class="fas fa-sign-out-alt"></i> Logout</button>

      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task page coming soon')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
  <div class="nav-item" onclick="alert('Income page coming soon')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item active" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- ===== LEVEL PAGE (with red text) ===== -->
    <div id="levelPage">
      <div class="level-header">
        <div class="level-title">LEVELS PRICE AND SALARIES</div>
      </div>

      <div style="text-align: center; color: #666; margin-top: 50px;">
        <p>Level details coming soon...</p>
      </div>

      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="alert('Task page coming soon')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item active" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="alert('Income page coming soon')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>
  </div>

  <script>
    // ===== DATA =====
    let users = JSON.parse(localStorage.getItem('ciuUsers')) || {};
    let currentUser = localStorage.getItem('currentUser');

    // ===== UI FUNCTIONS =====
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      document.getElementById('messageText').textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      setTimeout(() => msgBox.style.display = 'none', 3000);
    }

    function switchTab(tab) {
      document.getElementById('loginForm').classList.toggle('active', tab === 'login');
      document.getElementById('registerForm').classList.toggle('active', tab === 'register');
      document.getElementById('loginTab').classList.toggle('active', tab === 'login');
      document.getElementById('registerTab').classList.toggle('active', tab === 'register');
    }

    function showPage(page) {
      document.getElementById('homePage').style.display = page === 'home' ? 'block' : 'none';
      document.getElementById('profilePage').style.display = page === 'profile' ? 'block' : 'none';
      document.getElementById('levelPage').style.display = page === 'level' ? 'block' : 'none';
      document.getElementById('authContainer').style.display = 'none';
    }

    // ===== AUTH FUNCTIONS =====
    function handleLogin(e) {
      e.preventDefault();
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;

      users = JSON.parse(localStorage.getItem('ciuUsers')) || {};

      if (users[phone] && users[phone].password === password) {
        localStorage.setItem('currentUser', phone);
        currentUser = phone;
        showMessage('Login successful!');
        setTimeout(() => {
          loadUserData();
          showPage('home');

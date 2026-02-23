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

    /* phone frame */
    .phone {
      max-width: 390px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 40px;
      box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      height: 700px;
    }

    /* Scrollable content area */
    .scroll-content {
      flex: 1;
      overflow-y: auto;
      padding: 20px 20px 10px 20px;
    }

    /* Bottom Navigation */
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
      background: white;
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

    /* Success Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 15px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      display: none;
    }

    /* Main Dashboard Pages */
    #mainDashboard, #profilePage, #levelPage, #taskPage, #incomePage, #taskRecordPage, #teamReportPage {
      display: none;
      flex-direction: column;
      height: 100%;
    }

    /* Welcome Section */
    .welcome-title {
      font-size: 2.2rem;
      font-weight: 700;
      color: #000000;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 0.9rem;
      color: #333333;
      margin-bottom: 15px;
    }

    .divider-line {
      height: 1px;
      background-color: #e0e0e0;
      margin: 15px 0;
    }

    /* Member Card */
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

    /* Upgrade Section */
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
    }

    .upgrade-btn {
      background: #ff9800;
      color: white;
      border: none;
      padding: 14px;
      border-radius: 30px;
      width: 100%;
      font-weight: 600;
      cursor: pointer;
    }

    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
    }

    /* Wallets */
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
    }

    .wallet-box.main {
      border-left: 3px solid #006a7a;
    }

    .wallet-box.commission {
      border-left: 3px solid #ff9800;
    }

    /* Profile Page */
    .profile-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 20px;
    }

    .employee-name {
      font-size: 1.3rem;
      font-weight: 700;
      margin-bottom: 5px;
    }

    .employee-role {
      color: #666;
      margin-bottom: 20px;
    }

    /* Income Grid - CLEAN */
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
      color: #666;
      font-size: 0.8rem;
      margin-bottom: 3px;
    }

    .income-value {
      font-weight: 700;
      color: #000;
    }

    /* Commission Row */
    .commission-row {
      display: flex;
      justify-content: space-between;
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
      cursor: pointer;
    }

    .menu-item i {
      color: #666;
      width: 20px;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      padding: 12px;
      border-radius: 30px;
      width: 100%;
      cursor: pointer;
    }

    /* Level Page - COMPACT STYLES */
    .level-page-title {
      font-size: 1.8rem;
      font-weight: 700;
      color: #ff0000;
      text-align: center;
      margin: 15px 0;
      text-transform: uppercase;
    }

    .level-card-compact {
      margin-bottom: 10px;
      line-height: 1.2;
    }

    .level-name-compact {
      font-size: 1.3rem;
      font-weight: 700;
      color: #006a7a;
      margin-bottom: 3px;
    }

    .level-detail-compact {
      font-size: 0.95rem;
      margin-bottom: 2px;
      color: #333;
    }

    .click-to-join-compact {
      color: #006a7a;
      font-weight: 600;
      margin-top: 3px;
      margin-bottom: 5px;
      cursor: pointer;
      text-decoration: underline;
      font-size: 0.95rem;
    }

    .click-to-join-compact:hover {
      color: #ff0000;
    }

    .level-separator-compact {
      width: 100%;
      height: 1px;
      background: #ddd;
      margin: 8px 0 12px 0;
    }

    /* Wallet Displays */
    .main-wallet-display {
      background: #e6f3ff;
      border-radius: 15px;
      padding: 12px;
      margin-bottom: 8px;
      text-align: center;
      font-size: 1.1rem;
      font-weight: 700;
      color: #0066cc;
      border: 2px solid #0099ff;
    }

    .commission-wallet-display {
      background: #fff3cd;
      border-radius: 15px;
      padding: 12px;
      margin-bottom: 15px;
      text-align: center;
      font-size: 1.1rem;
      font-weight: 700;
      color: #856404;
      border: 2px solid #ffc107;
    }

    /* Task Record Page Styles */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-bottom: 25px;
    }

    .stat-card {
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      text-align: center;
      border: 1px solid #eaeaea;
    }

    .stat-card .stat-value {
      font-size: 1.5rem;
      font-weight: 700;
      color: #006a7a;
    }

    .stat-card .stat-label {
      font-size: 0.75rem;
      color: #666;
      margin-top: 5px;
    }

    .task-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 10px;
    }

    .task-table th {
      background: #f0f0f0;
      color: #333;
      font-weight: 600;
      font-size: 0.8rem;
      padding: 10px;
      text-align: left;
    }

    .task-table td {
      padding: 12px 10px;
      border-bottom: 1px solid #f0f0f0;
      font-size: 0.85rem;
    }

    .status-badge {
      padding: 4px 8px;
      border-radius: 20px;
      font-size: 0.7rem;
      font-weight: 600;
    }

    .status-complete {
      background: #d4edda;
      color: #155724;
    }

    .status-pending {
      background: #fff3cd;
      color: #856404;
    }

    .section-title {
      font-size: 1.1rem;
      font-weight: 600;
      margin: 20px 0 10px 0;
    }

    .back-btn {
      background: none;
      border: none;
      color: #006a7a;
      font-size: 0.9rem;
      cursor: pointer;
      margin-bottom: 15px;
    }

    /* Team Report Page Styles */
    .team-section {
      margin-bottom: 25px;
    }

    .team-letter {
      font-size: 1.5rem;
      font-weight: 700;
      color: #006a7a;
      margin-bottom: 10px;
    }

    .team-member {
      padding: 8px 0 8px 20px;
      border-bottom: 1px solid #f0f0f0;
      font-size: 0.95rem;
    }

    .member-phone {
      font-weight: 600;
    }

    .member-level {
      color: #666;
      margin-left: 5px;
    }

    .member-deposit {
      color: #ff0000;
      font-weight: 600;
      margin-left: 5px;
    }

    .member-tasks {
      color: #006a7a;
      margin-left: 5px;
    }

    .section-total {
      margin-top: 10px;
      padding: 10px 0 10px 20px;
      background: #f9f9f9;
      border-radius: 10px;
      font-weight: 600;
    }

    .total-deposit {
      color: #ff0000;
    }

    .total-tasks {
      color: #006a7a;
      margin-left: 10px;
    }

    .empty-section {
      padding: 8px 0 8px 20px;
      color: #999;
      font-style: italic;
      border-bottom: 1px solid #f0f0f0;
    }

    .team-stats {
      background: #f0f8ff;
      border-radius: 15px;
      padding: 15px;
      margin-top: 20px;
    }

    .team-stats div {
      display: flex;
      justify-content: space-between;
      margin-bottom: 8px;
    }

    /* Modals */
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
    }

    .recipient-card {
      background: #f9f9f9;
      border-radius: 15px;
      padding: 16px;
      text-align: center;
      margin-bottom: 20px;
    }

    .recipient-card .number {
      font-size: 1.3rem;
      font-weight: 700;
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

      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

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
          <button type="submit" class="auth-btn">Login</button>
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
              <select id="regCountry" required>
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
          </div>
          <button type="submit" class="auth-btn">Register</button>
          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchAuthTab('login'); return false;">Login here</a>
          </div>
        </form>
      </div>
    </div>

    <!-- MAIN DASHBOARD (Home Page) -->
    <div id="mainDashboard">
      <div class="scroll-content">
        <div class="welcome-title">WELCOME</div>
        <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES WORK TOGETHER TO CREATE A BETTER FUTURE</div>
        <div class="divider-line"></div>

        <!-- Member Card -->
        <div class="member-card" id="memberCard">
          <div class="member-type" id="memberTypeDisplay">INTERN MEMBER</div>
          <div class="member-days" id="memberDaysDisplay">4 days remaining</div>
          <div class="progress-bar">
            <div class="progress-fill" id="memberProgress" style="width: 100%;"></div>
          </div>
        </div>

        <!-- Wallets -->
        <div class="wallets-container">
          <div class="wallet-box main">
            <div class="label">💰 MAIN WALLET</div>
            <div class="amount" id="mainWalletAmount">0 UGX</div>
          </div>
          <div class="wallet-box commission">
            <div class="label">💰 COMMISSION</div>
            <div class="amount" id="commissionWalletAmount">0 UGX</div>
          </div>
        </div>

        <!-- Daily Counter -->
        <div style="background:#f0f8ff; padding:12px; border-radius:15px; margin-bottom:15px; display:flex; justify-content:space-between;">
          <span>📚 Today: <span id="booksReadToday">0</span>/<span id="dailyBookLimit">1</span></span>
          <span>💰 Earned: <span id="dailyEarnings">0</span> UGX</span>
        </div>

        <!-- Books -->
        <div class="book-grid" id="bookGrid"></div>

        <!-- Actions -->
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

        <!-- Upgrade Section -->
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
            <button class="upgrade-btn" onclick="openDepositModal()">DEPOSIT & UPGRADE NOW</button>
          </div>
        </div>

        <!-- Company Profile -->
        <div class="company-line">
          <span>Company Profile</span>
          <i class="fas fa-chevron-right"></i>
        </div>
      </div>

      <!-- Bottom Nav -->
      <div class="bottom-nav">
        <div class="nav-item active" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- PROFILE PAGE (ME) -->
    <div id="profilePage">
      <div class="scroll-content">
        <div class="profile-header">
          <span class="time" id="currentTime"></span>
          <span><i class="fas fa-user"></i> <span id="profileDisplayName">User</span></span>
        </div>

        <div class="employee-name" id="profileFullName">User Name</div>
        <div class="employee-role" id="profileMemberType">INTERN MEMBER</div>

        <!-- Wallets -->
        <div class="wallets-container">
          <div class="wallet-box main">
            <div class="label">💰 MAIN WALLET</div>
            <div class="amount" id="profileMainWallet">0 UGX</div>
          </div>
          <div class="wallet-box commission">
            <div class="label">💰 COMMISSION</div>
            <div class="amount" id="profileCommissionWallet">0 UGX</div>
          </div>
        </div>

        <!-- Member Stats -->
        <div style="background:#f0f8ff; border-radius:15px; padding:15px; margin-bottom:20px;">
          <div style="display:flex; justify-content:space-between;">
            <span>Days Left: <span id="profileDaysLeft">4</span></span>
            <span>Books Today: <span id="profileBooksToday">0/1</span></span>
          </div>
        </div>

        <!-- INCOME GRID - CLEAN -->
        <div class="income-grid">
          <div class="income-item">
            <div class="income-label">today's income</div>
            <div class="income-value" id="todayIncomeValue">0.00 UGX</div>
          </div>
          <div class="income-item">
            <div class="income-label">total income</div>
            <div class="income-value" id="totalIncomeValue">0.00 UGX</div>
          </div>
          <div class="income-item">
            <div class="income-label">month's income</div>
            <div class="income-value" id="monthIncomeValue">0.00 UGX</div>
          </div>
        </div>

        <!-- Commission Row -->
        <div class="commission-row">
          <span class="commission-label">Commission from subordinate tasks</span>
          <span class="commission-value" id="subordinateCommission">0.00 UGX</span>
        </div>

        <!-- Menu Grid - Clickable -->
        <div class="menu-grid">
          <div class="menu-item" onclick="showTaskRecord()"><i class="fas fa-clipboard-list"></i> task record</div>
          <div class="menu-item" onclick="showTeamReport()"><i class="fas fa-users"></i> team report</div>
          <div class="menu-item" onclick="alert('daily report coming soon')"><i class="fas fa-calendar-alt"></i> daily report</div>
          <div class="menu-item" onclick="alert('bill record coming soon')"><i class="fas fa-file-invoice"></i> bill record</div>
          <div class="menu-item" onclick="alert('Position Salary coming soon')"><i class="fas fa-chart-line"></i> Position Salary</div>
          <div class="menu-item" onclick="alert('APP download coming soon')"><i class="fas fa-download"></i> APP download</div>
        </div>

        <!-- Logout -->
        <button class="logout-btn" onclick="logout()"><i class="fas fa-sign-out-alt"></i> Logout</button>
      </div>

      <!-- Bottom Nav -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item active" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- TASK RECORD PAGE -->
    <div id="taskRecordPage">
      <div class="scroll-content">
        <!-- Back Button -->
        <button class="back-btn" onclick="showPage('profile')"><i class="fas fa-arrow-left"></i> Back to Profile</button>

        <h3 style="margin-bottom:20px;">📋 Task Record</h3>

        <!-- Stats Cards -->
        <div class="stats-grid">
          <div class="stat-card">
            <div class="stat-value" id="totalReadBooks">0</div>
            <div class="stat-label">Read Books</div>
          </div>
          <div class="stat-card">
            <div class="stat-value" id="completeBooks">0</div>
            <div class="stat-label">Complete Books</div>
          </div>
          <div class="stat-card">
            <div class="stat-value" id="pendingBooks">0</div>
            <div class="stat-label">Pending Books</div>
          </div>
        </div>

        <!-- Task History Table -->
        <div class="section-title">📚 Book History</div>
        <table class="task-table" id="taskHistoryTable">
          <thead>
            <tr>
              <th>Date</th>
              <th>Book</th>
              <th>Status</th>
              <th>Reward</th>
            </tr>
          </thead>
          <tbody id="taskHistoryBody">
            <!-- Filled by JavaScript -->
          </tbody>
        </table>
      </div>

      <!-- Bottom Nav -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- TEAM REPORT PAGE -->
    <div id="teamReportPage">
      <div class="scroll-content">
        <!-- Back Button -->
        <button class="back-btn" onclick="showPage('profile')"><i class="fas fa-arrow-left"></i> Back to Profile</button>

        <h3 style="margin-bottom:20px;">👥 Team Report</h3>

        <!-- A Section -->
        <div class="team-section">
          <div class="team-letter">A</div>
          <div id="teamASection">
            <!-- Filled by JavaScript -->
          </div>
        </div>

        <!-- B Section -->
        <div class="team-section">
          <div class="team-letter">B</div>
          <div id="teamBSection">
            <!-- Filled by JavaScript -->
          </div>
        </div>

        <!-- C Section -->
        <div class="team-section">
          <div class="team-letter">C</div>
          <div id="teamCSection">
            <!-- Filled by JavaScript -->
          </div>
        </div>

        <!-- Team Stats -->
        <div class="team-stats">
          <div><span>Total Team Members:</span> <span id="totalTeamMembers">0</span></div>
          <div><span>Active Today:</span> <span id="activeTeamMembers">0</span></div>
        </div>
      </div>

      <!-- Bottom Nav -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- LEVEL PAGE - COMPACT VERSION -->
    <div id="levelPage">
      <div class="scroll-content">
        <div class="level-page-title">LEVELS PRICE AND SALARIES</div>

        <!-- Wallet Displays -->
        <div class="main-wallet-display" id="levelMainWallet">
          Main Wallet: 0 UGX
        </div>

        <div class="commission-wallet-display" id="levelCommissionWallet">
          Commission Wallet: 0 UGX
        </div>

        <!-- D1 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D1</div>
          <div class="level-detail-compact">UGX 63000. 2 tasks</div>
          <div class="level-detail-compact">UGX 1125 per task</div>
          <div class="level-detail-compact">UGX 2250 daily</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(1, 63000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D2 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D2</div>
          <div class="level-detail-compact">UGX 200000. 4 tasks</div>
          <div class="level-detail-compact">UGX 1775 per task</div>
          <div class="level-detail-compact">UGX 7100 daily</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(2, 200000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D3 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D3</div>
          <div class="level-detail-compact">UGX 532000. 12 tasks</div>
          <div class="level-detail-compact">UGX 1584 per task</div>
          <div class="level-detail-compact">UGX 19008 daily</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(3, 532000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D4 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D4</div>
          <div class="level-detail-compact">UGX 1450000 16 tasks</div>
          <div class="level-detail-compact">UGX 3238 per task</div>
          <div class="level-detail-compact">UGX 51808 per day</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(4, 1450000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D5 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D5</div>
          <div class="level-detail-compact">UGX 3920000 24 tasks</div>
          <div class="level-detail-compact">UGX 6050 per task</div>
          <div class="level-detail-compact">UGX 145200 per day</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(5, 3920000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D6 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D6</div>
          <div class="level-detail-compact">UGX 10640000 24 tasks</div>
          <div class="level-detail-compact">UGX 11875 per task</div>
          <div class="level-detail-compact">UGX 38000 per day</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(6, 10640000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D7 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D7</div>
          <div class="level-detail-compact">UGX 40040000 52 tasks</div>
          <div class="level-detail-compact">UGX 27500 per task</div>
          <div class="level-detail-compact">UGX 1430000 per day</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(7, 40040000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D8 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D8</div>
          <div class="level-detail-compact">UGX 57120000 64 tasks</div>
          <div class="level-detail-compact">UGX 31875 per task</div>
          <div class="level-detail-compact">UGX 2040000 per day</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(8, 57120000)">Click to join</div>
        </div>
        <div class="level-separator-compact"></div>

        <!-- D9 - COMPACT -->
        <div class="level-card-compact">
          <div class="level-name-compact">D9</div>
          <div class="level-detail-compact">UGX 84000000 74 tasks</div>
          <div class="level-detail-compact">UGX 40000 per task</div>
          <div class="level-detail-compact">UGX 3000000 per day</div>
          <div class="click-to-join-compact" onclick="purchaseLevel(9, 84000000)">Click to join</div>
        </div>
      </div>

      <!-- Bottom Nav -->
      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item active" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- TASK PAGE -->
    <div id="taskPage">
      <div class="scroll-content">
        <h3 style="margin-bottom:20px;">Book Library</h3>
        <div class="book-grid" id="taskBookGrid"></div>
      </div>
      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item active" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>

    <!-- INCOME PAGE -->
    <div id="incomePage">
      <div class="scroll-content">
        <h3 style="margin:20px 0;">Income History</h3>
        <p style="color:#666; text-align:center;">Coming soon...</p>
      </div>
      <div class="bottom-nav">
        <div class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i><span>Home</span></div>
        <div class="nav-item" onclick="showPage('task')"><i class="fas fa-tasks"></i><span>Task</span></div>
        <div class="nav-item" onclick="showPage('level')"><i class="fas fa-chart-simple"></i><span>Level</span></div>
        <div class="nav-item active" onclick="showPage('income')"><i class="fas fa-coins"></i><span>Income</span></div>
        <div class="nav-item" onclick="showPage('profile')"><i class="fas fa-user"></i><span>Me</span></div>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL -->
  <div class="modal-overlay" id="depositModal">
    <div class="modal-content">
      <div class="modal-header" style="display:flex; justify-content:space-between; margin-bottom:20px;">
        <h2>Deposit</h2>
        <button class="close-btn" onclick="closeDepositModal()" style="font-size:1.8rem; background:none; border:none;">&times;</button>
      </div>
      <div class="recipient-card">
        <div class="number">0756 673 144</div>
        <div class="name">NAMUHANGA VERONIC</div>
      </div>
      <div class="custom-amount">
        <input type="number" id="depositAmount" placeholder="Enter amount" style="width:100%; padding:15px; border:1px solid #ddd; border-radius:15px;">
      </div>
      <button class="deposit-btn" onclick="submitDeposit()" style="background:#000; color:white; width:100%; padding:15px; border:none; border-radius:30px; margin-top:15px;">Send Money</button>
    </div>
  </div>

  <!-- WITHDRAW MODAL -->
  <div class="modal-overlay" id="withdrawModal">
    <div class="modal-content">
      <div class="modal-header" style="display:flex; justify-content:space-between; margin-bottom:20px;">
        <h2>Withdraw</h2>
        <button class="close-btn" onclick="closeWithdrawModal()" style="font-size:1.8rem; background:none; border:none;">&times;</button>
      </div>
      <div class="wallet-selector" style="display:flex; gap:10px; margin:15px 0;">
        <div class="wallet-option" id="walletMainOption" onclick="selectWallet('main')" style="flex:1; background:#f9f9f9; border:2px solid #ddd; border-radius:15px; padding:15px; text-align:center; cursor:pointer;">
          <div class="wallet-name" style="font-weight:600;">MAIN</div>
          <div class="wallet-balance" id="withdrawMainBalance">0 UGX</div>
        </div>
        <div class="wallet-option" id="walletCommissionOption" onclick="selectWallet('commission')" style="flex:1; background:#f9f9f9; border:2px solid #ddd; border-radius:15px; padding:15px; text-align:center; cursor:pointer;">
          <div class="wallet-name" style="font-weight:600;">COMMISSION</div>
          <div class="wallet-balance" id="withdrawCommissionBalance">0 UGX</div>
        </div>
      </div>
      <input type="number" id="withdrawAmount" placeholder="Amount" style="width:100%; padding:15px; border:1px solid #ddd; border-radius:15px; margin-bottom:10px;">
      <input type="tel" id="withdrawPhone" placeholder="Mobile number" style="width:100%; padding:15px; border:1px solid #ddd; border-radius:15px; margin-bottom:10px;">
      <button onclick="submitWithdraw()" style="background:#000; color:white; width:100%; padding:15px; border:none; border-radius:30px;">Withdraw</button>
    </div>
  </div>

  <script>
    // ========== DATA ==========
    let users = JSON.parse(localStorage.getItem('cueUsers')) || {};
    let currentUser = localStorage.getItem('currentUser');
    let pendingDeposits = JSON.parse(localStorage.getItem('pendingDeposits')) || [];
    let pendingWithdrawals = JSON.parse(localStorage.getItem('pendingWithdrawals')) || [];
    let selectedWallet = 'main';
    let books = [
      { id: 1, title: "Financial Literacy", desc: "Learn about money management" },
      { id: 2, title: "Think and Grow Rich", desc: "Napoleon Hill's classic" },
      { id: 3, title: "Rich Dad Poor Dad", desc: "Robert Kiyosaki's bestseller" }
    ];

    // Level definitions with exact numbers from image
    const levels = {
      0: { name: "Intern", dailyBooks: 1, reward: 1500, duration: 4, canWithdraw: false, hasReferral: false },
      1: { name: "D1", dailyBooks: 2, reward: 1125, deposit: 63000, duration: 365, canWithdraw: true, hasReferral: true },
      2: { name: "D2", dailyBooks: 4, reward: 1775, deposit: 200000, duration: 365, canWithdraw: true, hasReferral: true },
      3: { name: "D3", dailyBooks: 12, reward: 1584, deposit: 532000, duration: 365, canWithdraw: true, hasReferral: true },
      4: { name: "D4", dailyBooks: 16, reward: 3238, deposit: 1450000, duration: 365, canWithdraw: true, hasReferral: true },
      5: { name: "D5", dailyBooks: 24, reward: 6050, deposit: 3920000, duration: 365, canWithdraw: true, hasReferral: true },
      6: { name: "D6", dailyBooks: 24, reward: 11875, deposit: 10640000, duration: 365, canWithdraw: true, hasReferral: true },
      7: { name: "D7", dailyBooks: 52, reward: 27500, deposit: 40040000, duration: 365, canWithdraw: true, hasReferral: true },
      8: { name: "D8", dailyBooks: 64, reward: 31875, deposit: 57120000, duration: 365, canWithdraw: true, hasReferral: true },
      9: { name: "D9", dailyBooks: 74, reward: 40000, deposit: 84000000, duration: 365, canWithdraw: true, hasReferral: true }
    };

    // ========== AUTH ==========
    function switchAuthTab(tab) {
      document.getElementById('loginForm').classList.toggle('active', tab === 'login');
      document.getElementById('registerForm').classList.toggle('active', tab === 'register');
      document.getElementById('loginTab').classList.toggle('active', tab === 'login');
      document.getElementById('registerTab').classList.toggle('active', tab === 'register');
    }

    function handleRegister(e) {
      e.preventDefault();
      const fullName = document.getElementById('regFullName').value;
      const phone = document.getElementById('regPhone').value;
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;

      if (!fullName || !phone || !country || !password) {
        alert('Please fill all fields');
        return;
      }

      if (users[phone]) {
        alert('Phone already registered');
        switchAuthTab('login');
        return;
      }

      const now = new Date();
      const expiry = new Date(now);
      expiry.setDate(expiry.getDate() + 4);

      users[phone] = {
        fullName, phone, country, password,
        memberLevel: 0,
        memberExpiry: expiry.toISOString(),
        mainWallet: 0,
        commissionWallet: 0,
        booksReadToday: 0,
        lastReadDate: now.toDateString(),
        totalEarned: 0,
        taskHistory: [],
        referredBy: null,
        referrals: [],
        registeredDate: now.toISOString()
      };

      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      currentUser = phone;
      alert('Registration successful!');
      loadUserData();
      showPage('home');
    }

    function handleLogin(e) {
      e.preventDefault();
      const phone = document.getElementById('loginPhone').value;
      const password = document.getElementById('loginPassword').value;

      if (users[phone] && users[phone].password === password) {
        localStorage.setItem('currentUser', phone);
        currentUser = phone;
        alert('Login successful!');
        loadUserData();
        showPage('home');
      } else {
        alert('Invalid phone or password');
      }
    }

    // ========== PAGE NAVIGATION ==========
    function showPage(page) {
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = page === 'home' ? 'flex' : 'none';
      document.getElementById('profilePage').style.display = page === 'profile' ? 'flex' : 'none';
      document.getElementById('levelPage').style.display = page === 'level' ? 'flex' : 'none';
      document.getElementById('taskPage').style.display = page === 'task' ? 'flex' : 'none';
      document.getElementById('incomePage').style.display = page === 'income' ? 'flex' : 'none';
      document.getElementById('taskRecordPage').style.display = page === 'taskRecord' ? 'flex' : 'none';
      document.getElementById('teamReportPage').style.display = page === 'teamReport' ? 'flex' : 'none';

      // Update active nav
      document.querySelectorAll('.bottom-nav').forEach(nav => {
        const items = nav.querySelectorAll('.nav-item');
        items.forEach(item => item.classList.remove('active'));
        if (page === 'home') items[0]?.classList.add('active');
        else if (page === 'task') items[1]?.classList.add('active');
        else if (page === 'level') items[2]?.classList.add('active');
        else if (page === 'income') items[3]?.classList.add('active');
        else if (page === 'profile') items[4]?.classList.add('active');
      });

      if (page === 'task') loadTaskBooks();
      if (page === 'home') loadHomeBooks();
      if (page === 'taskRecord') loadTaskRecord();
      if (page === 'teamReport') loadTeamReport();
      if (page === 'level') updateLevelWalletDisplay();
    }

    function showTaskRecord() {
      showPage('taskRecord');
    }

    function showTeamReport() {
      showPage('teamReport');
    }

    // ========== LEVEL PURCHASE ==========
    function purchaseLevel(level, cost) {
      const user = users[currentUser];
      if (!user) {
        alert('Please login first');
        return;
      }

      // Check if already at this level or higher
      if (user.memberLevel >= level) {
        alert(`You are already at ${levels[level].name} or higher!`);
        return;
      }

      // INTERN MEMBER (level 0) - Main Wallet only
      if (user.memberLevel === 0) {
        if (user.mainWallet < cost) {
          alert(`❌ Insufficient balance! Need ${cost.toLocaleString()} UGX in Main Wallet`);
          return;
        }
        
        // Deduct from main wallet only
        if (confirm(`Upgrade to ${levels[level].name} for ${cost.toLocaleString()} UGX?`)) {
          user.mainWallet -= cost;
          upgradeUser(user, level, cost);
        }
      } 
      // EXISTING MEMBER (level 1-8) - Can use both wallets
      else {
        const totalBalance = (user.mainWallet || 0) + (user.commissionWallet || 0);
        
        if (totalBalance < cost) {
          alert(`❌ Insufficient balance! Need ${cost.toLocaleString()} UGX total in both wallets`);
          return;
        }

        if (confirm(`Upgrade to ${levels[level].name} for ${cost.toLocaleString()} UGX? This will use funds from your wallets.`)) {
          // Deduct from main wallet first, then commission if needed
          let remaining = cost;
          
          // Take from main wallet first
          if (user.mainWallet > 0) {
            const fromMain = Math.min(user.mainWallet, remaining);
            user.mainWallet -= fromMain;
            remaining -= fromMain;
          }
          
          // Take from commission wallet if still needed
          if (remaining > 0 && user.commissionWallet > 0) {
            const fromCommission = Math.min(user.commissionWallet, remaining);
            user.commissionWallet -= fromCommission;
            remaining -= fromCommission;
          }
          
          upgradeUser(user, level, cost);
        }
      }
    }

    function upgradeUser(user, level, cost) {
      // Upgrade member level
      user.memberLevel = level;
      
      // Set expiry to 365 days from now
      const expiry = new Date();
      expiry.setDate(expiry.getDate() + 365);
      user.memberExpiry = expiry.toISOString();

      // Add transaction record
      if (!user.transactions) user.transactions = [];
      user.transactions.unshift({
        type: 'level_upgrade',
        level: level,
        amount: cost,
        date: new Date().toLocaleString()
      });

      localStorage.setItem('cueUsers', JSON.stringify(users));
      
      alert(`✅ Congratulations! You are now ${levels[level].name} member!`);
      loadUserData();
      updateLevelWalletDisplay();
    }

    function updateLevelWalletDisplay() {
      const user = users[currentUser];
      if (user) {
        document.getElementById('levelMainWallet').innerHTML = `Main Wallet: ${(user.mainWallet || 0).toLocaleString()} UGX`;
        document.getElementById('levelCommissionWallet').innerHTML = `Commission Wallet: ${(user.commissionWallet || 0).toLocaleString()} UGX`;
      }
    }

    // ========== LOAD USER DATA ==========
    function loadUserData() {
      if (!currentUser) return;
      const user = users[currentUser];
      if (!user) return;

      // Check daily reset
      const today = new Date().toDateString();
      if (user.lastReadDate !== today) {
        user.booksReadToday = 0;
        user.lastReadDate = today;
        localStorage.setItem('cueUsers', JSON.stringify(users));
      }

      const level = user.memberLevel || 0;
      const levelData = levels[level];

      // Update home page
      document.getElementById('mainWalletAmount').innerHTML = `${(user.mainWallet || 0).toLocaleString()} UGX`;
      document.getElementById('commissionWalletAmount').innerHTML = `${(user.commissionWallet || 0).toLocaleString()} UGX`;
      document.getElementById('memberTypeDisplay').textContent = levelData.name;
      
      const daysLeft = Math.ceil((new Date(user.memberExpiry) - new Date()) / (1000*60*60*24));
      document.getElementById('memberDaysDisplay').textContent = `${daysLeft} days remaining`;
      document.getElementById('booksReadToday').textContent = user.booksReadToday || 0;
      document.getElementById('dailyBookLimit').textContent = levelData.dailyBooks;
      document.getElementById('dailyEarnings').textContent = user.commissionWallet || 0;

      // Update profile page
      document.getElementById('profileFullName').textContent = user.fullName;
      document.getElementById('profileDisplayName').textContent = user.fullName.split(' ')[0];
      document.getElementById('profileMemberType').textContent = levelData.name;
      document.getElementById('profileMainWallet').innerHTML = `${(user.mainWallet || 0).toLocaleString()} UGX`;
      document.getElementById('profileCommissionWallet').innerHTML = `${(user.commissionWallet || 0).toLocaleString()} UGX`;
      document.getElementById('profileDaysLeft').textContent = daysLeft;
      document.getElementById('profileBooksToday').textContent = `${user.booksReadToday || 0}/${levelData.dailyBooks}`;
      
      // Update income values
      document.getElementById('todayIncomeValue').innerHTML = `${(user.commissionWallet || 0).toFixed(2)} UGX`;
      document.getElementById('totalIncomeValue').innerHTML = `${(user.commissionWallet || 0).toFixed(2)} UGX`;
      document.getElementById('monthIncomeValue').innerHTML = `0.00 UGX`;
      document.getElementById('subordinateCommission').innerHTML = `0.00 UGX`;
      
      // Update withdraw modal balances
      document.getElementById('withdrawMainBalance').innerHTML = (user.mainWallet || 0).toLocaleString() + ' UGX';
      document.getElementById('withdrawCommissionBalance').innerHTML = (user.commissionWallet || 0).toLocaleString() + ' UGX';

      // Update level page wallet
      updateLevelWalletDisplay();

      updateTime();
    }

    // ========== TEAM REPORT ==========
    function maskPhone(phone) {
      if (!phone || phone.length < 7) return phone;
      return phone.substring(0, 4) + '***' + phone.substring(phone.length - 3);
    }

    function countCompletedTasks(user) {
      if (!user.taskHistory) return 0;
      return user.taskHistory.filter(task => task.status === 'complete').length;
    }

    function loadTeamReport() {
      const user = users[currentUser];
      if (!user) return;

      // Find A members (direct referrals)
      const aMembers = Object.values(users).filter(u => u.referredBy === currentUser);
      
      // Find B members (referrals of A members)
      const aPhones = aMembers.map(m => m.phone);
      const bMembers = Object.values(users).filter(u => aPhones.includes(u.referredBy));
      
      // Find C members (referrals of B members)
      const bPhones = bMembers.map(m => m.phone);
      const cMembers = Object.values(users).filter(u => bPhones.includes(u.referredBy));

      // Display A section
      const aSection = document.getElementById('teamASection');
      if (aMembers.length === 0) {
        aSection.innerHTML = '<div class="empty-section">(empty)</div>';
      } else {
        let html = '';
        let aTotalDeposit = 0;
        let aTotalTasks = 0;
        
        aMembers.forEach(member => {
          const levelText = member.memberLevel === 0 ? 'intern' : `D${member.memberLevel}`;
          const maskedPhone = maskPhone(member.phone);
          const deposit = member.mainWallet || 0;
          aTotalDeposit += deposit;
          
          if (member.memberLevel > 0) {
            const tasks = countCompletedTasks(member);
            aTotalTasks += tasks;
            html += `<div class="team-member"><span class="member-phone">${maskedPhone}</span> <span class="member-level">${levelText}</span> | <span class="member-deposit">💰 ${deposit.toLocaleString()} UGX</span> | <span class="member-tasks">📚 ${tasks} tasks</span></div>`;
          } else {
            html += `<div class="team-member"><span class="member-phone">${maskedPhone}</span> <span class="member-level">${levelText}</span> | <span class="member-deposit">💰 ${deposit.toLocaleString()} UGX</span></div>`;
          }
        });
        
        html += `<div class="section-total"><span class="total-deposit">🔴 A Total: ${aTotalDeposit.toLocaleString()} UGX</span> | <span class="total-tasks">📚 Active Tasks: ${aTotalTasks}</span></div>`;
        aSection.innerHTML = html;
      }

      // Display B section
      const bSection = document.getElementById('teamBSection');
      if (bMembers.length === 0) {
        bSection.innerHTML = '<div class="empty-section">(empty)</div>';
      } else {
        let html = '';
        let bTotalDeposit = 0;
        let bTotalTasks = 0;
        
        bMembers.forEach(member => {
          const levelText = member.memberLevel === 0 ? 'intern' : `D${member.memberLevel}`;
          const maskedPhone = maskPhone(member.phone);
          const deposit = member.mainWallet || 0;
          bTotalDeposit += deposit;
          
          if (member.memberLevel > 0) {
            const tasks = countCompletedTasks(member);
            bTotalTasks += tasks;
            html += `<div class="team-member"><span class="member-phone">${maskedPhone}</span> <span class="member-level">${levelText}</span> | <span class="member-deposit">💰 ${deposit.toLocaleString()} UGX</span> | <span class="member-tasks">📚 ${tasks} tasks</span></div>`;
          } else {
            html += `<div class="team-member"><span class="member-phone">${maskedPhone}</span> <span class="member-level">${levelText}</span> | <span class="member-deposit">💰 ${deposit.toLocaleString()} UGX</span></div>`;
          }
        });
        
        html += `<div class="section-total"><span class="total-deposit">🔴 B Total: ${bTotalDeposit.toLocaleString()} UGX</span> | <span class="total-tasks">📚 Active Tasks: ${bTotalTasks}</span></div>`;
        bSection.innerHTML = html;
      }

      // Display C section
      const cSection = document.getElementById('teamCSection');
      if (cMembers.length === 0) {
        cSection.innerHTML = '<div class="empty-section">(empty)</div>';
      } else {
        let html = '';
        let cTotalDeposit = 0;
        let cTotalTasks = 0;
        
        cMembers.forEach(member => {
          const levelText = member.memberLevel === 0 ? 'intern' : `D${member.memberLevel}`;
          const maskedPhone = maskPhone(member.phone);
          const deposit = member.mainWallet || 0;
          cTotalDeposit += deposit;
          
          if (member.memberLevel > 0) {
            const tasks = countCompletedTasks(member);
            cTotalTasks += tasks;
            html += `<div class="team-member"><span class="member-phone">${maskedPhone}</span> <span class="member-level">${levelText}</span> | <span class="member-deposit">💰 ${deposit.toLocaleString()} UGX</span> | <span class="member-tasks">📚 ${tasks} tasks</span></div>`;
          } else {
            html += `<div class="team-member"><span class="member-phone">${maskedPhone}</span> <span class="member-level">${levelText}</span> | <span class="member-deposit">💰 ${deposit.toLocaleString()} UGX</span></div>`;
          }
        });
        
        html += `<div class="section-total"><span class="total-deposit">🔴 C Total: ${cTotalDeposit.toLocaleString()} UGX</span> | <span class="total-tasks">📚 Active Tasks: ${cTotalTasks}</span></div>`;
        cSection.innerHTML = html;
      }

      // Update stats
      const total = aMembers.length + bMembers.length + cMembers.length;
      document.getElementById('totalTeamMembers').textContent = total;

      // Count active today
      const today = new Date().toDateString();
      const activeCount = [aMembers, bMembers, cMembers].flat().filter(m => m.lastReadDate === today).length;
      document.getElementById('activeTeamMembers').textContent = activeCount;
    }

    // ========== TASK RECORD ==========
    function loadTaskRecord() {
      const user = users[currentUser];
      if (!user) return;

      // Calculate stats
      const history = user.taskHistory || [];
      const completed = history.filter(task => task.status === 'complete');
      const pending = history.filter(task => task.status === 'pending');
      
      document.getElementById('totalReadBooks').textContent = history.length;
      document.getElementById('completeBooks').textContent = completed.length;
      document.getElementById('pendingBooks').textContent = pending.length;

      // Load table
      const tbody = document.getElementById('taskHistoryBody');
      if (history.length === 0) {
        tbody.innerHTML = '<tr><td colspan="4" style="text-align:center; padding:30px;">No task history yet</td></tr>';
        return;
      }

      let html = '';
      history.slice().reverse().forEach(task => {
        const statusClass = task.status === 'complete' ? 'status-complete' : 'status-pending';
        const statusText = task.status === 'complete' ? '✅ Complete' : '⏳ Pending';
        const rewardDisplay = task.status === 'complete' ? `+${task.reward} UGX` : '-';
        
        html += `
          <tr>
            <td>${task.date}</td>
            <td>${task.book}</td>
            <td><span class="status-badge ${statusClass}">${statusText}</span></td>
            <td>${rewardDisplay}</td>
          </tr>
        `;
      });
      tbody.innerHTML = html;
    }

    // ========== BOOKS ==========
    function loadHomeBooks() {
      const grid = document.getElementById('bookGrid');
      let html = '';
      books.slice(0, 2).forEach(book => {
        html += `
          <div class="book-card">
            <div class="book-title">📖 ${book.title}</div>
            <div class="book-desc">${book.desc}</div>
            <button class="read-btn" onclick="startReading(${book.id})" id="home-book-${book.id}">READ</button>
            <div id="home-timer-${book.id}" class="timer-display" style="display:none;">10s</div>
          </div>
        `;
      });
      grid.innerHTML = html;
    }

    function loadTaskBooks() {
      const grid = document.getElementById('taskBookGrid');
      let html = '';
      books.forEach(book => {
        html += `
          <div class="book-card">
            <div class="book-title">📖 ${book.title}</div>
            <div class="book-desc">${book.desc}</div>
            <button class="read-btn" onclick="startReading(${book.id})" id="task-book-${book.id}">READ</button>
            <div id="task-timer-${book.id}" class="timer-display" style="display:none;">10s</div>
          </div>
        `;
      });
      grid.innerHTML = html;
    }

    function startReading(bookId) {
      const user = users[currentUser];
      if (!user) return;

      const level = user.memberLevel || 0;
      const levelData = levels[level];
      const book = books.find(b => b.id === bookId);

      if (user.booksReadToday >= levelData.dailyBooks) {
        alert(`Daily limit of ${levelData.dailyBooks} books reached`);
        return;
      }

      // Add to task history as pending
      if (!user.taskHistory) user.taskHistory = [];
      user.taskHistory.push({
        date: new Date().toLocaleDateString(),
        book: book.title,
        status: 'pending',
        reward: 0
      });
      localStorage.setItem('cueUsers', JSON.stringify(users));

      // Hide button, show timer
      const homeBtn = document.getElementById(`home-book-${bookId}`);
      const taskBtn = document.getElementById(`task-book-${bookId}`);
      const homeTimer = document.getElementById(`home-timer-${bookId}`);
      const taskTimer = document.getElementById(`task-timer-${bookId}`);

      if (homeBtn) { homeBtn.style.display = 'none'; homeTimer.style.display = 'block'; }
      if (taskBtn) { taskBtn.style.display = 'none'; taskTimer.style.display = 'block'; }

      let seconds = 10;
      const timer = setInterval(() => {
        seconds--;
        if (homeTimer) homeTimer.textContent = seconds + 's';
        if (taskTimer) taskTimer.textContent = seconds + 's';

        if (seconds <= 0) {
          clearInterval(timer);
          
          // Show harvest button
          if (homeBtn) {
            homeTimer.style.display = 'none';
            homeBtn.style.display = 'block';
            homeBtn.textContent = '🌾 HARVEST';
            homeBtn.classList.add('harvest-ready');
            homeBtn.onclick = () => harvestReward(bookId);
          }
          if (taskBtn) {
            taskTimer.style.display = 'none';
            taskBtn.style.display = 'block';
            taskBtn.textContent = '🌾 HARVEST';
            taskBtn.classList.add('harvest-ready');
            taskBtn.onclick = () => harvestReward(bookId);
          }
        }
      }, 1000);
    }

    function harvestReward(bookId) {
      const user = users[currentUser];
      if (!user) return;

      const level = user.memberLevel || 0;
      const levelData = levels[level];
      const reward = levelData.reward;
      const book = books.find(b => b.id === bookId);

      // Add to COMMISSION WALLET
      user.commissionWallet = (user.commissionWallet || 0) + reward;
      user.booksReadToday = (user.booksReadToday || 0) + 1;
      user.lastReadDate = new Date().toDateString();

      // Update task history - find most recent pending entry for this book
      if (user.taskHistory) {
        const pendingTask = user.taskHistory
          .slice()
          .reverse()
          .find(t => t.book === book.title && t.status === 'pending');
        if (pendingTask) {
          pendingTask.status = 'complete';
          pendingTask.reward = reward;
        }
      }

      localStorage.setItem('cueUsers', JSON.stringify(users));

      // Update buttons
      const homeBtn = document.getElementById(`home-book-${bookId}`);
      const taskBtn = document.getElementById(`task-book-${bookId}`);
      
      if (homeBtn) {
        homeBtn.textContent = '✅ DONE';
        homeBtn.classList.remove('harvest-ready');
        homeBtn.disabled = true;
      }
      if (taskBtn) {
        taskBtn.textContent = '✅ DONE';
        taskBtn.classList.remove('harvest-ready');
        taskBtn.disabled = true;
      }

      alert(`+${reward} UGX added to Commission Wallet!`);
      loadUserData();
    }

    // ========== DEPOSIT ==========
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
    }

    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }

    function submitDeposit() {
      const amount = parseInt(document.getElementById('depositAmount').value);
      if (!amount || amount < 1000) {
        alert('Enter valid amount (min 1000)');
        return;
      }

      pendingDeposits.push({
        id: Date.now(),
        userId: currentUser,
        phone: users[currentUser]?.phone,
        amount: amount,
        timestamp: new Date().toISOString()
      });
      localStorage.setItem('pendingDeposits', JSON.stringify(pendingDeposits));
      
      alert('Deposit request sent! Admin will verify.');
      closeDepositModal();
    }

    // ========== WITHDRAW ==========
    function selectWallet(wallet) {
      selectedWallet = wallet;
      document.getElementById('walletMainOption').classList.toggle('selected', wallet === 'main');
      document.getElementById('walletCommissionOption').classList.toggle('selected', wallet === 'commission');
    }

    function openWithdrawModal() {
      loadUserData();
      document.getElementById('withdrawModal').style.display = 'flex';
    }

    function closeWithdrawModal() {
      document.getElementById('withdrawModal').style.display = 'none';
    }

    function submitWithdraw() {
      const amount = parseInt(document.getElementById('withdrawAmount').value);
      const phone = document.getElementById('withdrawPhone').value;
      const user = users[currentUser];

      if (!amount || amount < 1000) {
        alert('Enter valid amount');
        return;
      }

      const balance = selectedWallet === 'main' ? user.mainWallet : user.commissionWallet;
      if (amount > balance) {
        alert('Insufficient balance');
        return;
      }

      if (selectedWallet === 'main') {
        user.mainWallet -= amount;
      } else {
        if (amount < 10000) {
          alert('Commission wallet minimum withdrawal is 10,000 UGX');
          return;
        }
        user.commissionWallet -= amount;
      }

      pendingWithdrawals.push({
        id: Date.now(),
        userId: currentUser,
        amount: amount,
        wallet: selectedWallet,
        mobileNumber: phone,
        timestamp: new Date().toISOString()
      });

      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('pendingWithdrawals', JSON.stringify(pendingWithdrawals));

      alert('Withdrawal request submitted!');
      closeWithdrawModal();
      loadUserData();
    }

    // ========== UTILITY ==========
    function updateTime() {
      const now = new Date();
      let hours = now.getHours();
      const mins = now.getMinutes().toString().padStart(2, '0');
      const ampm = hours >= 12 ? 'PM' : 'AM';
      hours = hours % 12 || 12;
      document.getElementById('currentTime').textContent = `${hours}:${mins} ${ampm}`;
    }

    function logout() {
      localStorage.removeItem('currentUser');
      currentUser = null;
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('mainDashboard').style.display = 'none';
      document.getElementById('profilePage').style.display = 'none';
      document.getElementById('levelPage').style.display = 'none';
      document.getElementById('taskPage').style.display = 'none';
      document.getElementById('incomePage').style.display = 'none';
      document.getElementById('taskRecordPage').style.display = 'none';
      document.getElementById('teamReportPage').style.display = 'none';
    }

    // ========== INIT ==========
    window.onload = function() {
      // Create demo accounts if empty
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'Admin User',
          phone: '0756673144',
          country: 'Uganda',
          password: 'admin123',
          memberLevel: 9,
          memberExpiry: new Date(Date.now() + 365*24*60*60*1000).toISOString(),
          mainWallet: 1000000,
          commissionWallet: 500000,
          booksReadToday: 0,
          lastReadDate: new Date().toDateString(),
          totalEarned: 0,
          taskHistory: [],
          referredBy: null,
          referrals: []
        };
        
        // Demo intern user
        users['0777123456'] = {
          fullName: 'Intern User',
          phone: '0777123456',
          country: 'Uganda',
          password: '123456',
          memberLevel: 0,
          memberExpiry: new Date(Date.now() + 4*24*60*60*1000).toISOString(),
          mainWallet: 100000,
          commissionWallet: 1500,
          booksReadToday: 1,
          lastReadDate: new Date().toDateString(),
          totalEarned: 1500,
          taskHistory: [
            { date: '2/23/2026', book: 'Financial Literacy', status: 'complete', reward: 1500 },
            { date: '2/23/2026', book: 'Think and Grow Rich', status: 'pending', reward: 0 },
            { date: '2/22/2026', book: 'Rich Dad Poor Dad', status: 'complete', reward: 1500 }
          ],
          referredBy: null,
          referrals: []
        };

        // Demo D1 member
        users['0788123456'] = {
          fullName: 'John D1',
          phone: '0788123456',
          country: 'Uganda',
          password: '123456',
          memberLevel: 1,
          memberExpiry: new Date(Date.now() + 365*24*60*60*1000).toISOString(),
          mainWallet: 150000,
          commissionWallet: 30000,
          booksReadToday: 2,
          lastReadDate: new Date().toDateString(),
          totalEarned: 3000,
          taskHistory: [
            { date: '2/23/2026', book: 'Financial Literacy', status: 'complete', reward: 1125 },
            { date: '2/23/2026', book: 'Think and Grow Rich', status: 'complete', reward: 1125 }
          ],
          referredBy: null,
          referrals: []
        };

        localStorage.setItem('cueUsers', JSON.stringify(users));
      }

      if (currentUser && users[currentUser]) {
        loadUserData();
        showPage('home');
      }

      setInterval(updateTime, 60000);
      updateTime();
    };
  </script>
</body>
</html>

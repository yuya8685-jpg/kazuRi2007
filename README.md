<!DOCTYPE html>
<html lang="my">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Boost Service</title>
  <style>
    /* Modern Color Scheme */
    :root {
      --primary: #6366f1;
      --primary-dark: #4f46e5;
      --secondary: #10b981;
      --secondary-dark: #059669;
      --danger: #ef4444;
      --danger-dark: #dc2626;
      --warning: #f59e0b;
      --info: #06b6d4;
      --dark: #1f2937;
      --light: #f8fafc;
      --gray: #6b7280;
      --border: #e5e7eb;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body { 
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
      padding: 20px;
      color: var(--dark);
    }
    
    .app-container {
      max-width: 480px;
      margin: 0 auto;
    }
    
    .container { 
      background: white; 
      padding: 24px; 
      border-radius: 16px; 
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
      margin-bottom: 20px;
      border: 1px solid var(--border);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
    
    .container:hover {
      transform: translateY(-5px);
      box-shadow: 0 15px 30px rgba(0,0,0,0.15);
    }
    
    h2 { 
      text-align: center; 
      color: var(--primary); 
      margin-bottom: 16px;
      font-weight: 700;
      font-size: 1.75rem;
    }
    
    h3 {
      color: var(--dark);
      margin: 20px 0 12px;
      font-weight: 600;
      font-size: 1.25rem;
    }
    
    h4 {
      color: var(--dark);
      margin: 16px 0 8px;
      font-weight: 600;
    }
    
    input, select, button, textarea { 
      width: 100%; 
      padding: 12px 16px; 
      margin: 8px 0; 
      border-radius: 10px; 
      border: 1px solid var(--border); 
      font-size: 16px; 
      transition: all 0.3s ease;
    }
    
    input:focus, select:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
    }
    
    button { 
      background: var(--primary); 
      color: white; 
      cursor: pointer; 
      border: none; 
      font-weight: 600;
      transition: all 0.3s ease;
      position: relative;
      overflow: hidden;
    }
    
    button:hover:not(:disabled) { 
      background: var(--primary-dark); 
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }
    
    button:disabled {
      background: var(--gray);
      cursor: not-allowed;
      transform: none;
      box-shadow: none;
    }
    
    .admin-btn { 
      background: var(--secondary); 
    }
    
    .admin-btn:hover { 
      background: var(--secondary-dark); 
    }
    
    .payment-box { 
      background: linear-gradient(135deg, #d1fae5, #a7f3d0);
      border: 1px solid var(--secondary); 
      border-radius: 10px; 
      padding: 14px; 
      text-align: center; 
      cursor: pointer; 
      user-select: all; 
      margin: 8px 0;
      font-weight: 600;
      transition: all 0.3s ease;
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 80px;
    }
    
    .payment-box:hover {
      transform: scale(1.02);
    }
    
    .copied { 
      background: #dbeafe !important; 
      border-color: var(--primary) !important; 
    }
    
    .payment-number {
      font-size: 1.2rem;
      font-weight: bold;
      margin: 5px 0;
      color: var(--dark);
    }
    
    .payment-name {
      font-size: 0.9rem;
      color: var(--gray);
      margin-bottom: 8px;
    }
    
    .copy-indicator {
      position: absolute;
      top: 5px;
      right: 10px;
      font-size: 0.8rem;
      color: var(--primary);
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    
    .payment-box.copied .copy-indicator {
      opacity: 1;
    }
    
    .balance-box { 
      text-align: center; 
      background: linear-gradient(135deg, #fef3c7, #fde68a);
      border: 1px solid var(--warning); 
      padding: 16px; 
      border-radius: 12px; 
      margin-bottom: 16px; 
      font-weight: bold;
      font-size: 1.1rem;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    }
    
    .error { 
      color: var(--danger); 
      font-weight: 600; 
      background: #fef2f2;
      padding: 12px;
      border-radius: 8px;
      border-left: 4px solid var(--danger);
    }
    
    .success { 
      color: var(--secondary-dark); 
      font-weight: 600; 
      background: #f0fdf4;
      padding: 12px;
      border-radius: 8px;
      border-left: 4px solid var(--secondary);
    }
    
    table { 
      width: 100%; 
      border-collapse: collapse; 
      margin-top: 12px; 
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    }
    
    th, td { 
      border: 1px solid var(--border); 
      padding: 12px; 
      text-align: center; 
    }
    
    th { 
      background: var(--primary); 
      color: white; 
      font-weight: 600;
    }
    
    .small-btn { 
      padding: 8px 12px; 
      font-size: 14px; 
      border-radius: 8px; 
      cursor: pointer; 
      margin: 2px; 
      border: none; 
      width: auto;
      display: inline-block;
    }
    
    .note { 
      font-size: 14px; 
      color: var(--gray); 
      margin-top: 8px; 
      line-height: 1.5;
    }
    
    .deduct-note { 
      font-size: 14px; 
      color: var(--danger); 
      margin-top: 8px; 
      text-align: center; 
      font-weight: 600; 
      background: #fef2f2;
      padding: 10px;
      border-radius: 8px;
    } 
    
    #orderMessage, #topupMessage { 
      margin-top: 12px; 
      padding: 12px; 
      border-radius: 8px; 
      text-align: center; 
    } 
    
    .signup-note { 
      font-size: 14px; 
      color: var(--primary); 
      text-align: center; 
      margin-bottom: 12px;
      background: #f0f9ff;
      padding: 10px;
      border-radius: 8px;
    } 
    
    .service-table th { 
      background: var(--dark); 
    }
    
    .service-delete { 
      background: var(--danger); 
      color: white; 
    }
    
    .service-delete:hover {
      background: var(--danger-dark);
    }
    
    .service-save { 
      background: var(--primary); 
      color: white; 
    }
    
    .telegram-btn { 
      background: linear-gradient(135deg, #08aeea, #2af598);
      color: white; 
      border: none; 
      padding: 14px; 
      margin: 10px 0; 
      border-radius: 10px; 
      cursor: pointer; 
      font-weight: 600;
      transition: all 0.3s ease;
    }
    
    .telegram-btn:hover:not(:disabled) { 
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }
    
    .telegram-btn:disabled {
      background: var(--gray);
      cursor: not-allowed;
      transform: none;
      box-shadow: none;
    }
    
    .price-input-small { 
      width: 90px; 
      padding: 8px; 
      margin: 0; 
      display: inline-block; 
      text-align: center;
    }
    
    .login-tabs { 
      display: flex; 
      margin-bottom: 20px; 
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    }
    
    .login-tab { 
      flex: 1; 
      padding: 14px; 
      text-align: center; 
      background: #f8fafc; 
      border: 1px solid var(--border); 
      cursor: pointer; 
      font-weight: 600;
      transition: all 0.3s ease;
    }
    
    .login-tab.active { 
      background: var(--primary); 
      color: white; 
    }
    
    .login-form { 
      display: none; 
    }
    
    .login-form.active { 
      display: block; 
    }
    
    .vpn-warning { 
      background: #fffbeb; 
      border: 1px solid #fcd34d; 
      border-radius: 10px; 
      padding: 14px; 
      margin: 12px 0; 
      font-size: 14px; 
      color: #92400e;
      text-align: center;
      line-height: 1.5;
    }
    
    .topup-form { 
      background: #f8fafc; 
      border-radius: 12px; 
      padding: 20px; 
      margin: 20px 0;
      border: 1px solid var(--border);
    }
    
    .file-input { 
      background: white; 
      border: 2px dashed var(--primary); 
      padding: 20px; 
      text-align: center; 
      cursor: pointer;
      margin: 12px 0;
      border-radius: 10px;
      transition: all 0.3s ease;
    }
    
    .file-input:hover { 
      background: #f0f9ff; 
      transform: scale(1.01);
    }
    
    .user-management { 
      margin-top: 20px; 
    }
    
    .confirm-btn { 
      background: var(--secondary); 
    }
    
    .confirm-btn:hover {
      background: var(--secondary-dark);
    }
    
    .channel-promo {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      padding: 20px;
      border-radius: 12px;
      text-align: center;
      margin: 20px 0;
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }
    
    .channel-promo a {
      color: #ffeb3b;
      text-decoration: none;
      font-weight: bold;
      display: inline-block;
      margin-top: 8px;
      padding: 8px 16px;
      background: rgba(255,255,255,0.2);
      border-radius: 8px;
      transition: all 0.3s ease;
    }
    
    .channel-promo a:hover {
      background: rgba(255,255,255,0.3);
      transform: translateY(-2px);
    }
    
    .settings-btn {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: var(--primary);
      color: white;
      border: none;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      font-size: 24px;
      cursor: pointer;
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
      z-index: 1000;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .settings-btn:hover {
      background: var(--primary-dark);
      transform: translateY(-3px) rotate(15deg);
      box-shadow: 0 10px 20px rgba(0,0,0,0.25);
    }
    
    .home-btn {
      position: fixed;
      bottom: 90px;
      right: 20px;
      background: var(--secondary);
      color: white;
      border: none;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      font-size: 24px;
      cursor: pointer;
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
      z-index: 1000;
      transition: all 0.3s ease;
      display: none;
      align-items: center;
      justify-content: center;
    }
    
    .home-btn:hover {
      background: var(--secondary-dark);
      transform: translateY(-3px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.25);
    }
    
    .username-copy {
      background: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 12px;
      margin: 8px 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    
    .copy-btn {
      width: auto;
      padding: 8px 16px;
      background: var(--info);
      margin: 0;
      border-radius: 8px;
    }
    
    .copy-btn:hover {
      background: #0891b2;
      transform: none;
    }
    
    .info-note {
      background: #ecfeff;
      border: 1px solid #a5f3fc;
      border-radius: 10px;
      padding: 14px;
      margin: 12px 0;
      font-size: 14px;
      color: #0e7490;
      line-height: 1.5;
    }
    
    .notification {
      position: fixed;
      top: 20px;
      right: 20px;
      background: var(--secondary);
      color: white;
      padding: 16px 20px;
      border-radius: 12px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
      z-index: 1001;
      max-width: 320px;
      animation: slideIn 0.4s ease-out;
      font-weight: 600;
    }
    
    @keyframes slideIn {
      from { transform: translateX(100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
    
    .deduct-btn {
      background: var(--danger);
      color: white;
    }
    
    .deduct-btn:hover {
      background: var(--danger-dark);
    }
    
    .tg-ch-box {
      background: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 16px;
      margin: 12px 0;
      font-size: 14px;
      text-align: center;
    }
    
    .cost-display {
      background: linear-gradient(135deg, #e0f2fe, #bae6fd);
      border-radius: 10px;
      padding: 12px;
      margin: 12px 0;
      text-align: center;
      font-weight: 600;
      font-size: 1.1rem;
      color: var(--primary-dark);
    }
    
    .deduction-confirmation {
      background: #fef3c7;
      border: 1px solid #f59e0b;
      border-radius: 10px;
      padding: 14px;
      margin: 12px 0;
      text-align: center;
      display: none;
    }
    
    hr {
      margin: 20px 0;
      border: none;
      border-top: 1px dashed var(--border);
    }
    
    .logo {
      text-align: center;
      margin-bottom: 20px;
    }
    
    .logo h1 {
      color: white;
      font-size: 2.5rem;
      font-weight: 800;
      text-shadow: 0 2px 10px rgba(0,0,0,0.2);
      margin-bottom: 8px;
    }
    
    .logo p {
      color: rgba(255,255,255,0.8);
      font-size: 1rem;
    }
    
    .service-card {
      background: white;
      border-radius: 12px;
      padding: 16px;
      margin: 12px 0;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
      border: 1px solid var(--border);
      transition: all 0.3s ease;
    }
    
    .service-card:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 15px rgba(0,0,0,0.1);
    }
    
    /* Platform Selection Buttons */
    .platform-tabs {
      display: flex;
      margin-bottom: 20px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    }
    
    .platform-tab {
      flex: 1;
      padding: 12px;
      text-align: center;
      background: #f8fafc;
      border: 1px solid var(--border);
      cursor: pointer;
      font-weight: 600;
      transition: all 0.3s ease;
      font-size: 14px;
    }
    
    .platform-tab.active {
      background: var(--primary);
      color: white;
    }
    
    .platform-tab.tiktok.active {
      background: #000000;
    }
    
    .platform-tab.facebook.active {
      background: #1877F2;
    }
    
    .platform-tab.telegram.active {
      background: #0088cc;
    }
    
    .platform-tab.youtube.active {
      background: #FF0000;
    }
    
    /* Navigation Tabs */
    .nav-tabs {
      display: flex;
      margin-bottom: 20px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    }
    
    .nav-tab {
      flex: 1;
      padding: 14px;
      text-align: center;
      background: #f8fafc;
      border: 1px solid var(--border);
      cursor: pointer;
      font-weight: 600;
      transition: all 0.3s ease;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 5px;
    }
    
    .nav-tab.active {
      background: var(--primary);
      color: white;
    }
    
    .nav-tab i {
      font-size: 1.2rem;
    }
    
    .nav-content {
      display: none;
    }
    
    .nav-content.active {
      display: block;
    }
    
    /* History Styles */
    .history-item {
      background: white;
      border-radius: 10px;
      padding: 16px;
      margin: 12px 0;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
      border: 1px solid var(--border);
    }
    
    .history-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 8px;
    }
    
    .history-status {
      padding: 4px 12px;
      border-radius: 20px;
      font-size: 0.8rem;
      font-weight: 600;
    }
    
    .status-pending {
      background: #fef3c7;
      color: #92400e;
    }
    
    .status-completed {
      background: #d1fae5;
      color: #065f46;
    }
    
    .status-rejected {
      background: #fef2f2;
      color: #991b1b;
    }
    
    /* Admin Navigation */
    .admin-nav-tabs {
      display: flex;
      margin-bottom: 20px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    }
    
    .admin-nav-tab {
      flex: 1;
      padding: 14px;
      text-align: center;
      background: #f8fafc;
      border: 1px solid var(--border);
      cursor: pointer;
      font-weight: 600;
      transition: all 0.3s ease;
    }
    
    .admin-nav-tab.active {
      background: var(--primary);
      color: white;
    }
    
    .admin-nav-content {
      display: none;
    }
    
    .admin-nav-content.active {
      display: block;
    }
    
    /* Button Timer */
    .button-timer {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.7);
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: bold;
      border-radius: 10px;
    }
    
    /* Responsive Design */
    @media (max-width: 480px) {
      body {
        padding: 10px;
      }
      
      .container {
        padding: 16px;
      }
      
      h2 {
        font-size: 1.5rem;
      }
      
      .settings-btn, .home-btn {
        width: 50px;
        height: 50px;
        font-size: 20px;
      }
      
      .home-btn {
        bottom: 80px;
      }
      
      .platform-tab {
        padding: 10px;
        font-size: 12px;
      }
      
      .nav-tab {
        padding: 10px;
        font-size: 12px;
      }
      
      .nav-tab i {
        font-size: 1rem;
      }
      
      .admin-nav-tab {
        padding: 10px;
        font-size: 12px;
      }
    }
  </style>
</head>
<body>
  <div class="app-container">
    <div class="logo">
      <h1>Boost Service</h1>
      <p>Your Social Media Growth Partner</p>
    </div>

    <div id="notification" class="notification" style="display: none;"></div>

    <button class="settings-btn" onclick="goToSettings()">⚙️</button>
    
    <button class="home-btn" onclick="goBackToOrder()">🏠</button>

    <div class="container" id="authSection">
      <h2>Login / Sign Up</h2>
      
      <div class="login-tabs">
        <div class="login-tab active" onclick="switchLoginTab('email')">Email Login</div>
        <div class="login-tab" onclick="switchLoginTab('username')">Username Login</div>
      </div>
      
      <div class="login-form active" id="emailLoginForm">
        <input type="email" id="email" placeholder="Email">
        <input type="password" id="password" placeholder="Password">
        <p class="signup-note">Email တစ်ခုလျှင် တစ်ကောင့်သာ အသုံးပြုနိုင်သည်</p> 
        <button type="button" onclick="loginWithEmail()">Login</button>
        <button type="button" onclick="signupWithEmail()">Sign Up</button>
      </div>
      
      <div class="login-form" id="usernameLoginForm">
        <input type="text" id="username" placeholder="Username">
        <input type="password" id="usernamePassword" placeholder="Password">
        <p class="signup-note">Username တစ်ခုလျှင် တစ်ကောင့်သာ အသုံးပြုနိုင်သည်</p> 
        <button type="button" onclick="loginWithUsername()">Login</button>
        <button type="button" onclick="signupWithUsername()">Sign Up</button>
      </div>
      
      <button class="admin-btn" type="button" onclick="showAdminLogin()">👑 Admin Login</button>
      <p id="authMessage"></p>
    </div>

    <div class="container" id="adminLoginSection" style="display:none;">
      <h2>👑 Admin Login</h2>
      <input type="email" id="adminEmail" placeholder="Admin Email">
      <input type="password" id="adminPassword" placeholder="Admin Password">
      <button type="button" onclick="adminLogin()">Login as Admin</button>
      <button type="button" onclick="cancelAdminLogin()">Cancel</button>
      <p id="adminLoginMsg"></p>
    </div>

    <div class="container" id="adminPanel" style="display:none;">
      <h2>Admin Dashboard</h2>
      
      <!-- Admin Navigation Tabs -->
      <div class="admin-nav-tabs">
        <div class="admin-nav-tab active" onclick="switchAdminTab('services')">Services</div>
        <div class="admin-nav-tab" onclick="switchAdminTab('users')">Users</div>
        <div class="admin-nav-tab" onclick="switchAdminTab('topupRequests')">Top Up Requests</div>
        <div class="admin-nav-tab" onclick="switchAdminTab('orderRequests')">Order Requests</div>
        <div class="admin-nav-tab" onclick="switchAdminTab('accounts')">Accounts</div>
      </div>

      <!-- Services Management -->
      <div class="admin-nav-content active" id="servicesContent">
        <h3>🛠️ Service Management</h3>
        
        <div class="platform-tabs">
          <div class="platform-tab tiktok active" onclick="switchPlatform('tiktok', this)">TikTok</div>
          <div class="platform-tab facebook" onclick="switchPlatform('facebook', this)">Facebook</div>
          <div class="platform-tab telegram" onclick="switchPlatform('telegram', this)">Telegram</div>
          <div class="platform-tab youtube" onclick="switchPlatform('youtube', this)">YouTube</div>
        </div>

        <h4>📉 Current Service Prices (Per 1000)</h4>
        <table id="serviceTable" class="service-table">
            <thead><tr><th>Service Name (ID)</th><th>Price (MMK)</th><th>Action</th></tr></thead>
            <tbody></tbody>
        </table>
        <p id="priceMessage" class="note" style="text-align:center;"></p>

        <h4>➕ Add New Service</h4>
        <input type="text" id="newServiceId" placeholder="Service ID (e.g., 'comment')" style="margin-bottom: 5px;">
        <input type="text" id="newServiceName" placeholder="Service Name (e.g., 'TikTok Comments')" style="margin-bottom: 5px;">
        <input type="number" id="newServicePrice" placeholder="Price (MMK per 1000, e.g., 5000)" min="1">
        <button type="button" onclick="addService()" style="background:var(--info); color:white; margin-bottom: 15px;">Add Service</button>
      </div>

      <!-- User Management -->
      <div class="admin-nav-content" id="usersContent">
        <h3>👥 User Balance Control</h3>
        <input type="text" id="adminSearchInput" onkeyup="renderUserList()" placeholder="Email/Username ဖြင့် ရှာဖွေပါ..." style="margin-bottom: 15px;"> 
        <table id="userTable" aria-live="polite">
          <thead><tr><th>Email/Username</th><th>Balance (MMK)</th><th>Action</th></tr></thead>
          <tbody></tbody>
        </table>
        <p class="note">Tip: type an amount and click Add/Deduct to modify user's balance.</p>
      </div>

      <!-- Top Up Requests -->
      <div class="admin-nav-content" id="topupRequestsContent">
        <h3>💰 Top Up Requests</h3>
        <div id="pendingTopups">
          <p class="note">No pending top up requests</p>
        </div>
      </div>

      <!-- Order Requests -->
      <div class="admin-nav-content" id="orderRequestsContent">
        <h3>🛒 Order Requests</h3>
        <div id="pendingOrders">
          <p class="note">No pending order requests</p>
        </div>
      </div>

      <!-- User Account Management -->
      <div class="admin-nav-content" id="accountsContent">
        <h3>🔐 User Account Management</h3>
        <div class="user-management">
          <table id="userAccountTable">
            <thead>
              <tr>
                <th>Username</th>
                <th>Email</th>
                <th>Password</th>
                <th>Login Type</th>
                <th>Balance</th>
              </tr>
            </thead>
            <tbody></tbody>
          </table>
        </div>
      </div>

      <button type="button" onclick="adminLogout()" style="background:var(--danger);margin-top:10px;">Logout Admin</button>
    </div>
    
    <div class="container" id="orderSection" style="display:none;">
      <h2>Boost Service</h2>

      <div class="balance-box">💰 လက်ရှိငွေလက်ကျန်: <span id="userBalance">0</span> MMK</div>

      <div class="channel-promo">
        <h3>🚀 အထူးလျှော့ဈေးများ ရရှိနိုင်ပါသည်!</h3>
        <p>လျှော့ဈေးများနှင့် Promotion များအတွက် ကျွန်ုပ်တို့၏ Telegram Channel ကို Join ပါ!</p>
        <a href="https://t.me/KazuRi_boost" target="_blank">👉 @KazuRi_boost Channel ကို Join ပါ 👈</a>
      </div>

      <!-- Navigation Tabs -->
      <div class="nav-tabs">
        <div class="nav-tab active" onclick="switchNavTab('order')">
          <i>🛒</i>
          <span>Order</span>
        </div>
        <div class="nav-tab" onclick="switchNavTab('topup')">
          <i>💰</i>
          <span>Top Up</span>
        </div>
        <div class="nav-tab" onclick="switchNavTab('orderHistory')">
          <i>📋</i>
          <span>Order History</span>
        </div>
        <div class="nav-tab" onclick="switchNavTab('topupHistory')">
          <i>📊</i>
          <span>Top Up History</span>
        </div>
      </div>

      <!-- Order Content -->
      <div class="nav-content active" id="orderContent">
        <div class="platform-tabs">
          <div class="platform-tab tiktok active" onclick="switchPlatform('tiktok', this)">TikTok</div>
          <div class="platform-tab facebook" onclick="switchPlatform('facebook', this)">Facebook</div>
          <div class="platform-tab telegram" onclick="switchPlatform('telegram', this)">Telegram</div>
          <div class="platform-tab youtube" onclick="switchPlatform('youtube', this)">YouTube</div>
        </div>

        <label>ဝန်ဆောင်မှုရွေးချယ်ပါ:</label>
        <select id="serviceSelect" onchange="calculateCost()"></select> 
        <input type="text" id="tiktokLink" placeholder="TikTok လင့်ခ်">
        <input type="number" id="amount" placeholder="အရေအတွက် (ဥပမာ 1000)" oninput="calculateCost()" min="1">
        
        <div class="cost-display" id="costDisplay">ကုန်ကျငွေ: 0 MMK</div>
        
        <div id="deductionConfirmation" class="deduction-confirmation">
          <p><strong>သတိပေးချက်:</strong> Order တင်ပါက <span id="deductionAmount">0</span> MMK ဖြတ်တောက်သွားမည်ဖြစ်ပါသည်။</p>
        </div>

        <button type="button" id="orderSubmitBtn" onclick="submitOrder()">
          Order တင်ရန်
        </button>
        <p id="orderMessage"></p>
        <p class="deduct-note">မှတ်ချက်။ ။ Order တင်ပြီးပါက သင်၏လက်ကျန်ငွေမှ အော်တိုဖြတ်တောက်သွားပါမည်။</p>
      </div>

      <!-- Top Up Content -->
      <div class="nav-content" id="topupContent">
        <h3>💰 ငွေဖြည့်ရန် (Top Up)</h3>
        
        <!-- Improved Payment Boxes -->
        <div class="payment-box" id="waveBox">
          <span class="copy-indicator">✓ Copied!</span>
          <div class="payment-name">Wave Money</div>
          <div class="payment-number">09781487575</div>
          <div class="payment-name">Tin Tin Khaing</div>
          <div class="note" style="margin-top: 5px; font-size: 0.8rem;">Click to copy number</div>
        </div>
        
        <div class="payment-box" id="kpayBox">
          <span class="copy-indicator">✓ Copied!</span>
          <div class="payment-name">KPay</div>
          <div class="payment-number">09450337600</div>
          <div class="payment-name">Lin Khant Zaw</div>
          <div class="note" style="margin-top: 5px; font-size: 0.8rem;">Click to copy number</div>
        </div>

        <div class="topup-form">
          <h3>📤 ငွေဖြည့်ရန် တောင်းဆိုချက်ပုံစံ</h3>
          
          <div class="info-note">
            <strong>⚠️ သတိပြုရန်:</strong> မှားယွင်းမှုမရှိစေရန် သင့် Username/Email ကို အောက်တွင် ပြထားပါသည်။
          </div>
          
          <div class="username-copy">
            <span id="topupUserIdentifier">-</span>
            <button class="copy-btn" onclick="copyTopupIdentifier()">Copy</button>
          </div>
          
          <input type="number" id="topupAmount" placeholder="ဖြည့်မည့် ပမာဏ (MMK)">
          
          <div class="file-input" onclick="document.getElementById('proofImage').click()">
            <p>📎 ငွေပေးချေမှု ပြေစာပုံတင်ရန် ကလစ်နှိပ်ပါ</p>
            <input type="file" id="proofImage" accept="image/*" style="display: none;" onchange="previewImage()">
            <img id="imagePreview" style="max-width: 100%; max-height: 200px; display: none; margin-top: 10px; border-radius: 8px;">
          </div>
          
          <div class="vpn-warning">
            ⚠️ <strong>သတိပြုရန်:</strong> ပြေစာပုံပို့ရာတွင် Telegram ပို့လို့မရပါက <strong>VPN အသုံးပြုပေးပါ</strong>။ 
            ပြေစာပုံနှင့်အတူ <strong>Email or Username</strong> ကိုလည်း မဖြစ်မနေတွဲပို့ပေးပါ။
          </div>
          
          <button class="telegram-btn" type="button" id="telegramSendBtn" onclick="sendTopupToTelegram()">
            ✉️ Telegram သို့ ပြေစာပုံပို့ရန်
          </button>
        </div>

        <p id="topupMessage"></p>
      </div>

      <!-- Order History Content -->
      <div class="nav-content" id="orderHistoryContent">
        <h3>📋 Order History</h3>
        <div id="orderHistoryList">
          <p class="note">No order history found</p>
        </div>
      </div>

      <!-- Top Up History Content -->
      <div class="nav-content" id="topupHistoryContent">
        <h3>📊 Top Up History</h3>
        <div id="topupHistoryList">
          <p class="note">No top up history found</p>
        </div>
      </div>
      
      <button id="logoutBtn" type="button" onclick="logout()" style="background:var(--gray);">Logout</button>
    </div>

    <div class="container" id="settingsSection" style="display:none;">
      <h2>👤 User Settings</h2>
      
      <div style="margin-bottom: 20px;">
        <button type="button" onclick="goBackToOrder()" style="background:var(--gray); width: auto; padding: 10px 16px; border-radius: 8px;">← Back to Order</button>
      </div>
      
      <div id="userInfo">
        <p><strong>Username:</strong></p>
        <div class="username-copy">
          <span id="displayUsername">-</span>
          <button class="copy-btn" onclick="copyUsername()">Copy</button>
        </div>
        <p><strong>Email:</strong> <span id="displayEmail">-</span></p>
        <p><strong>Balance:</strong> <span id="displayBalance">0</span> MMK</p>
      </div>
      
      <hr>
      
      <h3>Change Username</h3>
      <input type="text" id="newUsername" placeholder="New Username">
      <button type="button" onclick="changeUsername()" style="background:var(--info);">Change Username</button>
      <p id="usernameMessage"></p>
      
      <hr>
      
      <h3>Change Password</h3>
      <input type="password" id="currentPassword" placeholder="Current Password">
      <input type="password" id="newPassword" placeholder="New Password">
      <input type="password" id="confirmPassword" placeholder="Confirm New Password">
      <button type="button" onclick="changePassword()" style="background:var(--info);">Change Password</button>
      <p id="passwordMessage"></p>
      
      <div class="info-note">
        <strong>⚠️ သတိပြုရန်:</strong> စကားဝှက်မေ့သွားပါက Admin ဆီသို့ ဆက်သွယ်ပါ။<br>
        Telegram: <a href="https://t.me/Sir_KazuRi2007" target="_blank" style="color: #0e7490;">@Sir_KazuRi2007</a>
      </div>
      
      <hr>
      
      <h3>Contact Admin</h3>
      <p>အကူအညီလိုအပ်ပါက Admin ဆီသို့ ဆက်သွယ်ပါ:</p>
      
      <div class="tg-ch-box">
        <p><strong>Telegram:</strong> @Sir_KazuRi2007</p>
        <button class="telegram-btn" type="button" onclick="contactAdmin()">
          📞 Admin နှင့် ဆက်သွယ်ရန်
        </button>
      </div>
      
      <button id="logoutBtnSettings" type="button" onclick="logout()" style="background:var(--danger); margin-top: 20px;">Logout</button>
    </div>
  </div>

  <script>
    /* ---------------------------
      CONFIG & INITIALIZATION
    ----------------------------*/
    const adminCred = { email: "kazuri8890@gmail.com", password: "KazuRi1230k" }; 
    const botToken = "8344338458:AAEnjsYlIb5F2i8uNBGnbnPdb2rPsCD5Fo0";
    const chatId = "8169482948"; 
    const TELEGRAM_URL = `https://api.telegram.org/bot${botToken}/`;
    const TELEGRAM_USERNAME = "Sir_KazuRi2007";
    const TELEGRAM_CHANNEL = "https://t.me/KazuRi_boost";
    
    // Service data structure
    let services = {
      tiktok: [
        { id: "followers", name: "TikTok Followers", price: 5000 },
        { id: "likes", name: "TikTok Likes", price: 3000 },
        { id: "views", name: "TikTok Views", price: 2000 },
        { id: "comments", name: "TikTok Comments", price: 4000 }
      ],
      facebook: [
        { id: "followers", name: "Facebook Followers", price: 6000 },
        { id: "likes", name: "Facebook Likes", price: 3500 },
        { id: "page_likes", name: "Facebook Page Likes", price: 4500 },
        { id: "shares", name: "Facebook Shares", price: 5000 }
      ],
      telegram: [
        { id: "members", name: "Telegram Members", price: 7000 },
        { id: "reactions", name: "Telegram Reactions", price: 4000 },
        { id: "views", name: "Telegram Views", price: 2500 },
        { id: "comments", name: "Telegram Comments", price: 5500 }
      ],
      youtube: [
        { id: "subscribers", name: "YouTube Subscribers", price: 8000 },
        { id: "likes", name: "YouTube Likes", price: 4000 },
        { id: "views", name: "YouTube Views", price: 3000 },
        { id: "comments", name: "YouTube Comments", price: 6000 }
      ]
    };
    
    // Current user data
    let currentUser = null;
    let currentPlatform = 'tiktok';
    let userAccounts = JSON.parse(localStorage.getItem('userAccounts')) || [];
    let pendingTopups = JSON.parse(localStorage.getItem('pendingTopups')) || [];
    let pendingOrders = JSON.parse(localStorage.getItem('pendingOrders')) || [];
    let orderHistory = JSON.parse(localStorage.getItem('orderHistory')) || [];
    let topupHistory = JSON.parse(localStorage.getItem('topupHistory')) || [];
    let serviceData = JSON.parse(localStorage.getItem('serviceData')) || services;
    
    // Button timer states
    let orderButtonTimer = 0;
    let topupButtonTimer = 0;
    
    // Initialize the app
    document.addEventListener('DOMContentLoaded', function() {
      // Load service data from localStorage
      if (localStorage.getItem('serviceData')) {
        serviceData = JSON.parse(localStorage.getItem('serviceData'));
      } else {
        localStorage.setItem('serviceData', JSON.stringify(services));
      }
      
      // Check if user is already logged in
      const savedUser = localStorage.getItem('currentUser');
      if (savedUser) {
        currentUser = JSON.parse(savedUser);
        showOrderSection();
      }
      
      // Initialize platform tabs
      switchPlatform('tiktok', document.querySelector('.platform-tab.tiktok'));
      
      // Initialize payment box copy functionality
      document.getElementById('waveBox').addEventListener('click', function() {
        copyPaymentNumber('09781487575', this);
      });
      
      document.getElementById('kpayBox').addEventListener('click', function() {
        copyPaymentNumber('09450337600', this);
      });
      
      // Start button timer checks
      setInterval(updateButtonTimers, 1000);
    });
    
    /* ---------------------------
      BUTTON TIMER FUNCTIONS
    ----------------------------*/
    function updateButtonTimers() {
      // Update order button timer
      if (orderButtonTimer > 0) {
        orderButtonTimer--;
        const orderBtn = document.getElementById('orderSubmitBtn');
        orderBtn.disabled = true;
        orderBtn.innerHTML = `Please wait... (${orderButtonTimer}s)`;
        
        if (orderButtonTimer === 0) {
          orderBtn.disabled = false;
          orderBtn.innerHTML = 'Order တင်ရန်';
        }
      }
      
      // Update topup button timer
      if (topupButtonTimer > 0) {
        topupButtonTimer--;
        const topupBtn = document.getElementById('telegramSendBtn');
        topupBtn.disabled = true;
        topupBtn.innerHTML = `Please wait... (${topupButtonTimer}s)`;
        
        if (topupButtonTimer === 0) {
          topupBtn.disabled = false;
          topupBtn.innerHTML = '✉️ Telegram သို့ ပြေစာပုံပို့ရန်';
        }
      }
    }
    
    function startOrderButtonTimer() {
      orderButtonTimer = 60; // 60 seconds
    }
    
    function startTopupButtonTimer() {
      topupButtonTimer = 60; // 60 seconds
    }
    
    /* ---------------------------
      ADMIN NAVIGATION FUNCTIONS
    ----------------------------*/
    function switchAdminTab(tab) {
      document.querySelectorAll('.admin-nav-tab').forEach(t => t.classList.remove('active'));
      document.querySelectorAll('.admin-nav-content').forEach(c => c.classList.remove('active'));
      
      if (tab === 'services') {
        document.querySelector('.admin-nav-tab:nth-child(1)').classList.add('active');
        document.getElementById('servicesContent').classList.add('active');
      } else if (tab === 'users') {
        document.querySelector('.admin-nav-tab:nth-child(2)').classList.add('active');
        document.getElementById('usersContent').classList.add('active');
        renderUserList();
      } else if (tab === 'topupRequests') {
        document.querySelector('.admin-nav-tab:nth-child(3)').classList.add('active');
        document.getElementById('topupRequestsContent').classList.add('active');
        renderPendingTopups();
      } else if (tab === 'orderRequests') {
        document.querySelector('.admin-nav-tab:nth-child(4)').classList.add('active');
        document.getElementById('orderRequestsContent').classList.add('active');
        renderPendingOrders();
      } else if (tab === 'accounts') {
        document.querySelector('.admin-nav-tab:nth-child(5)').classList.add('active');
        document.getElementById('accountsContent').classList.add('active');
        renderUserAccountTable();
      }
    }
    
    /* ---------------------------
      NAVIGATION FUNCTIONS
    ----------------------------*/
    function switchNavTab(tab) {
      document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
      document.querySelectorAll('.nav-content').forEach(c => c.classList.remove('active'));
      
      if (tab === 'order') {
        document.querySelector('.nav-tab:nth-child(1)').classList.add('active');
        document.getElementById('orderContent').classList.add('active');
      } else if (tab === 'topup') {
        document.querySelector('.nav-tab:nth-child(2)').classList.add('active');
        document.getElementById('topupContent').classList.add('active');
        
        // Update topup user identifier
        if (currentUser) {
          document.getElementById('topupUserIdentifier').textContent = currentUser.email || currentUser.username;
        }
      } else if (tab === 'orderHistory') {
        document.querySelector('.nav-tab:nth-child(3)').classList.add('active');
        document.getElementById('orderHistoryContent').classList.add('active');
        renderOrderHistory();
      } else if (tab === 'topupHistory') {
        document.querySelector('.nav-tab:nth-child(4)').classList.add('active');
        document.getElementById('topupHistoryContent').classList.add('active');
        renderTopupHistory();
      }
    }
    
    /* ---------------------------
      AUTHENTICATION FUNCTIONS
    ----------------------------*/
    function switchLoginTab(tab) {
      document.querySelectorAll('.login-tab').forEach(t => t.classList.remove('active'));
      document.querySelectorAll('.login-form').forEach(f => f.classList.remove('active'));
      
      if (tab === 'email') {
        document.querySelector('.login-tab:nth-child(1)').classList.add('active');
        document.getElementById('emailLoginForm').classList.add('active');
      } else {
        document.querySelector('.login-tab:nth-child(2)').classList.add('active');
        document.getElementById('usernameLoginForm').classList.add('active');
      }
    }
    
    function loginWithEmail() {
      const email = document.getElementById('email').value.trim();
      const password = document.getElementById('password').value;
      
      if (!email || !password) {
        showNotification('Email နှင့် Password ထည့်ပေးပါ', 'error');
        return;
      }
      
      const user = userAccounts.find(u => u.email === email && u.password === password);
      if (user) {
        currentUser = user;
        localStorage.setItem('currentUser', JSON.stringify(currentUser));
        showOrderSection();
        showNotification('Login အောင်မြင်ပါသည်', 'success');
      } else {
        showNotification('Email သို့မဟုတ် Password မှားနေပါသည်', 'error');
      }
    }
    
    function signupWithEmail() {
      const email = document.getElementById('email').value.trim();
      const password = document.getElementById('password').value;
      
      if (!email || !password) {
        showNotification('Email နှင့် Password ထည့်ပေးပါ', 'error');
        return;
      }
      
      if (userAccounts.find(u => u.email === email)) {
        showNotification('ဤ Email ဖြင့် Account ရှိပြီးသားဖြစ်သည်', 'error');
        return;
      }
      
      const username = email.split('@')[0] + Math.floor(Math.random() * 1000);
      const newUser = {
        email: email,
        username: username,
        password: password,
        balance: 0,
        loginType: 'email'
      };
      
      userAccounts.push(newUser);
      localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
      currentUser = newUser;
      localStorage.setItem('currentUser', JSON.stringify(currentUser));
      showOrderSection();
      showNotification('Account အောင်မြင်စွာ ဖန်တီးပြီးပါပြီ', 'success');
    }
    
    function loginWithUsername() {
      const username = document.getElementById('username').value.trim();
      const password = document.getElementById('usernamePassword').value;
      
      if (!username || !password) {
        showNotification('Username နှင့် Password ထည့်ပေးပါ', 'error');
        return;
      }
      
      const user = userAccounts.find(u => u.username === username && u.password === password);
      if (user) {
        currentUser = user;
        localStorage.setItem('currentUser', JSON.stringify(currentUser));
        showOrderSection();
        showNotification('Login အောင်မြင်ပါသည်', 'success');
      } else {
        showNotification('Username သို့မဟုတ် Password မှားနေပါသည်', 'error');
      }
    }
    
    function signupWithUsername() {
      const username = document.getElementById('username').value.trim();
      const password = document.getElementById('usernamePassword').value;
      
      if (!username || !password) {
        showNotification('Username နှင့် Password ထည့်ပေးပါ', 'error');
        return;
      }
      
      if (userAccounts.find(u => u.username === username)) {
        showNotification('ဤ Username ဖြင့် Account ရှိပြီးသားဖြစ်သည်', 'error');
        return;
      }
      
      const newUser = {
        email: '',
        username: username,
        password: password,
        balance: 0,
        loginType: 'username'
      };
      
      userAccounts.push(newUser);
      localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
      currentUser = newUser;
      localStorage.setItem('currentUser', JSON.stringify(currentUser));
      showOrderSection();
      showNotification('Account အောင်မြင်စွာ ဖန်တီးပြီးပါပြီ', 'success');
    }
    
    function logout() {
      currentUser = null;
      localStorage.removeItem('currentUser');
      document.getElementById('authSection').style.display = 'block';
      document.getElementById('orderSection').style.display = 'none';
      document.getElementById('settingsSection').style.display = 'none';
      document.getElementById('adminPanel').style.display = 'none';
      document.getElementById('adminLoginSection').style.display = 'none';
      document.querySelector('.home-btn').style.display = 'none';
      
      // Reset form fields
      document.getElementById('email').value = '';
      document.getElementById('password').value = '';
      document.getElementById('username').value = '';
      document.getElementById('usernamePassword').value = '';
      
      showNotification('Logout လုပ်ပြီးပါပြီ', 'success');
    }
    
    /* ---------------------------
      ADMIN FUNCTIONS
    ----------------------------*/
    function showAdminLogin() {
      document.getElementById('authSection').style.display = 'none';
      document.getElementById('adminLoginSection').style.display = 'block';
    }
    
    function cancelAdminLogin() {
      document.getElementById('adminLoginSection').style.display = 'none';
      document.getElementById('authSection').style.display = 'block';
    }
    
    function adminLogin() {
      const email = document.getElementById('adminEmail').value.trim();
      const password = document.getElementById('adminPassword').value;
      
      if (email === adminCred.email && password === adminCred.password) {
        document.getElementById('adminLoginSection').style.display = 'none';
        document.getElementById('adminPanel').style.display = 'block';
        document.getElementById('authSection').style.display = 'none';
        document.getElementById('orderSection').style.display = 'none';
        document.getElementById('settingsSection').style.display = 'none';
        document.querySelector('.home-btn').style.display = 'none';
        
        renderServiceTable();
        renderUserList();
        renderPendingTopups();
        renderPendingOrders();
        renderUserAccountTable();
        
        showNotification('Admin Login အောင်မြင်ပါသည်', 'success');
      } else {
        showNotification('Admin Email သို့မဟုတ် Password မှားနေပါသည်', 'error');
      }
    }
    
    function adminLogout() {
      document.getElementById('adminPanel').style.display = 'none';
      document.getElementById('authSection').style.display = 'block';
      document.querySelector('.home-btn').style.display = 'none';
      showNotification('Admin Logout လုပ်ပြီးပါပြီ', 'success');
    }
    
    function renderServiceTable() {
      const tbody = document.querySelector('#serviceTable tbody');
      tbody.innerHTML = '';
      
      serviceData[currentPlatform].forEach(service => {
        const tr = document.createElement('tr');
        tr.innerHTML = `
          <td>${service.name} (${service.id})</td>
          <td><input type="number" class="price-input-small" value="${service.price}" data-id="${service.id}"></td>
          <td>
            <button class="small-btn service-save" onclick="updateServicePrice('${service.id}')">Save</button>
            <button class="small-btn service-delete" onclick="deleteService('${service.id}')">Delete</button>
          </td>
        `;
        tbody.appendChild(tr);
      });
    }
    
    function updateServicePrice(serviceId) {
      const input = document.querySelector(`.price-input-small[data-id="${serviceId}"]`);
      const newPrice = parseInt(input.value);
      
      if (isNaN(newPrice) || newPrice < 1) {
        showNotification('ဈေးနှုန်းထည့်ပေးပါ', 'error');
        return;
      }
      
      const serviceIndex = serviceData[currentPlatform].findIndex(s => s.id === serviceId);
      if (serviceIndex !== -1) {
        serviceData[currentPlatform][serviceIndex].price = newPrice;
        localStorage.setItem('serviceData', JSON.stringify(serviceData));
        showNotification('Service ဈေးနှုန်းပြင်ဆင်ပြီးပါပြီ', 'success');
      }
    }
    
    function deleteService(serviceId) {
      if (confirm('ဤ Service ကို ဖျက်မည်မှာ သေချာပါသလား?')) {
        serviceData[currentPlatform] = serviceData[currentPlatform].filter(s => s.id !== serviceId);
        localStorage.setItem('serviceData', JSON.stringify(serviceData));
        renderServiceTable();
        showNotification('Service ဖျက်ပြီးပါပြီ', 'success');
      }
    }
    
    function addService() {
      const serviceId = document.getElementById('newServiceId').value.trim();
      const serviceName = document.getElementById('newServiceName').value.trim();
      const servicePrice = parseInt(document.getElementById('newServicePrice').value);
      
      if (!serviceId || !serviceName || isNaN(servicePrice) || servicePrice < 1) {
        showNotification('Service ID, Name နှင့် Price အားလုံးထည့်ပေးပါ', 'error');
        return;
      }
      
      if (serviceData[currentPlatform].find(s => s.id === serviceId)) {
        showNotification('ဤ Service ID ရှိပြီးသားဖြစ်သည်', 'error');
        return;
      }
      
      serviceData[currentPlatform].push({
        id: serviceId,
        name: serviceName,
        price: servicePrice
      });
      
      localStorage.setItem('serviceData', JSON.stringify(serviceData));
      renderServiceTable();
      
      // Clear form
      document.getElementById('newServiceId').value = '';
      document.getElementById('newServiceName').value = '';
      document.getElementById('newServicePrice').value = '';
      
      showNotification('Service အသစ်ထည့်ပြီးပါပြီ', 'success');
    }
    
    function renderUserList() {
      const tbody = document.querySelector('#userTable tbody');
      const searchInput = document.getElementById('adminSearchInput').value.toLowerCase();
      tbody.innerHTML = '';
      
      const filteredUsers = userAccounts.filter(user => 
        user.email.toLowerCase().includes(searchInput) || 
        user.username.toLowerCase().includes(searchInput)
      );
      
      filteredUsers.forEach(user => {
        const tr = document.createElement('tr');
        tr.innerHTML = `
          <td>${user.email || user.username}</td>
          <td>${user.balance}</td>
          <td>
            <input type="number" id="amount-${user.email || user.username}" placeholder="Amount" style="width: 80px; display: inline-block; padding: 5px;">
            <button class="small-btn" style="background:var(--secondary);" onclick="addBalance('${user.email || user.username}')">Add</button>
            <button class="small-btn deduct-btn" onclick="deductBalance('${user.email || user.username}')">Deduct</button>
          </td>
        `;
        tbody.appendChild(tr);
      });
    }
    
    function addBalance(userIdentifier) {
      const amountInput = document.getElementById(`amount-${userIdentifier}`);
      const amount = parseInt(amountInput.value);
      
      if (isNaN(amount) || amount < 1) {
        showNotification('ငွေပမာဏထည့်ပေးပါ', 'error');
        return;
      }
      
      const userIndex = userAccounts.findIndex(u => u.email === userIdentifier || u.username === userIdentifier);
      if (userIndex !== -1) {
        userAccounts[userIndex].balance += amount;
        localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
        
        // Update current user if they are the one being modified
        if (currentUser && (currentUser.email === userIdentifier || currentUser.username === userIdentifier)) {
          currentUser.balance = userAccounts[userIndex].balance;
          localStorage.setItem('currentUser', JSON.stringify(currentUser));
          updateBalanceDisplay();
        }
        
        renderUserList();
        amountInput.value = '';
        showNotification(`User ${userIdentifier} အား ${amount} MMK ထည့်ပြီးပါပြီ`, 'success');
      }
    }
    
    function deductBalance(userIdentifier) {
      const amountInput = document.getElementById(`amount-${userIdentifier}`);
      const amount = parseInt(amountInput.value);
      
      if (isNaN(amount) || amount < 1) {
        showNotification('ငွေပမာဏထည့်ပေးပါ', 'error');
        return;
      }
      
      const userIndex = userAccounts.findIndex(u => u.email === userIdentifier || u.username === userIdentifier);
      if (userIndex !== -1) {
        if (userAccounts[userIndex].balance < amount) {
          showNotification('User ၏ လက်ကျန်ငွေ မလုံလောက်ပါ', 'error');
          return;
        }
        
        userAccounts[userIndex].balance -= amount;
        localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
        
        // Update current user if they are the one being modified
        if (currentUser && (currentUser.email === userIdentifier || currentUser.username === userIdentifier)) {
          currentUser.balance = userAccounts[userIndex].balance;
          localStorage.setItem('currentUser', JSON.stringify(currentUser));
          updateBalanceDisplay();
        }
        
        renderUserList();
        amountInput.value = '';
        showNotification(`User ${userIdentifier} မှ ${amount} MMK ဖြတ်တောက်ပြီးပါပြီ`, 'success');
      }
    }
    
    function renderPendingTopups() {
      const container = document.getElementById('pendingTopups');
      
      if (pendingTopups.length === 0) {
        container.innerHTML = '<p class="note">No pending top up requests</p>';
        return;
      }
      
      // Sort by date (newest first)
      const sortedTopups = [...pendingTopups].sort((a, b) => new Date(b.date) - new Date(a.date));
      
      container.innerHTML = '';
      sortedTopups.forEach((request, index) => {
        const div = document.createElement('div');
        div.className = 'topup-form';
        div.innerHTML = `
          <p><strong>User:</strong> ${request.username}</p>
          <p><strong>Amount:</strong> ${request.amount} MMK</p>
          <p><strong>Date:</strong> ${request.date}</p>
          <button class="small-btn confirm-btn" onclick="confirmTopup(${pendingTopups.indexOf(request)})">Confirm</button>
          <button class="small-btn deduct-btn" onclick="rejectTopup(${pendingTopups.indexOf(request)})">Reject</button>
        `;
        container.appendChild(div);
      });
    }
    
    function renderPendingOrders() {
      const container = document.getElementById('pendingOrders');
      
      if (pendingOrders.length === 0) {
        container.innerHTML = '<p class="note">No pending order requests</p>';
        return;
      }
      
      // Sort by date (newest first)
      const sortedOrders = [...pendingOrders].sort((a, b) => new Date(b.date) - new Date(a.date));
      
      container.innerHTML = '';
      sortedOrders.forEach((order, index) => {
        const div = document.createElement('div');
        div.className = 'topup-form';
        div.innerHTML = `
          <p><strong>User:</strong> ${order.username}</p>
          <p><strong>Platform:</strong> ${order.platform}</p>
          <p><strong>Service:</strong> ${order.service}</p>
          <p><strong>Link:</strong> ${order.link}</p>
          <p><strong>Amount:</strong> ${order.amount}</p>
          <p><strong>Cost:</strong> ${order.cost} MMK</p>
          <p><strong>Date:</strong> ${order.date}</p>
          <button class="small-btn confirm-btn" onclick="confirmOrder(${pendingOrders.indexOf(order)})">Confirm</button>
          <button class="small-btn deduct-btn" onclick="rejectOrder(${pendingOrders.indexOf(order)})">Reject</button>
        `;
        container.appendChild(div);
      });
    }
    
    function confirmTopup(index) {
      const request = pendingTopups[index];
      const userIndex = userAccounts.findIndex(u => 
        u.username === request.username || u.email === request.username
      );
      
      if (userIndex !== -1) {
        userAccounts[userIndex].balance += request.amount;
        localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
        
        // Update current user if they are the one being topped up
        if (currentUser && (currentUser.username === request.username || currentUser.email === request.username)) {
          currentUser.balance = userAccounts[userIndex].balance;
          localStorage.setItem('currentUser', JSON.stringify(currentUser));
          updateBalanceDisplay();
        }
        
        // Update topup history status
        const topupIndex = topupHistory.findIndex(t => 
          t.username === request.username && t.amount === request.amount && t.date === request.date
        );
        if (topupIndex !== -1) {
          topupHistory[topupIndex].status = 'completed';
          topupHistory[topupIndex].processedDate = new Date().toLocaleString();
          localStorage.setItem('topupHistory', JSON.stringify(topupHistory));
        }
        
        pendingTopups.splice(index, 1);
        localStorage.setItem('pendingTopups', JSON.stringify(pendingTopups));
        renderPendingTopups();
        renderUserList();
        showNotification('Top up အောင်မြင်စွာ အတည်ပြုပြီးပါပြီ', 'success');
      }
    }
    
    function rejectTopup(index) {
      const request = pendingTopups[index];
      
      // Update topup history status
      const topupIndex = topupHistory.findIndex(t => 
        t.username === request.username && t.amount === request.amount && t.date === request.date
      );
      if (topupIndex !== -1) {
        topupHistory[topupIndex].status = 'rejected';
        topupHistory[topupIndex].processedDate = new Date().toLocaleString();
        localStorage.setItem('topupHistory', JSON.stringify(topupHistory));
      }
      
      pendingTopups.splice(index, 1);
      localStorage.setItem('pendingTopups', JSON.stringify(pendingTopups));
      renderPendingTopups();
      showNotification('Top up request ကို ပယ်ဖျက်လိုက်ပါပြီ', 'success');
    }
    
    function confirmOrder(index) {
      const order = pendingOrders[index];
      
      // Update order history status
      const orderIndex = orderHistory.findIndex(o => 
        o.username === order.username && o.platform === order.platform && 
        o.service === order.service && o.date === order.date
      );
      if (orderIndex !== -1) {
        orderHistory[orderIndex].status = 'completed';
        orderHistory[orderIndex].processedDate = new Date().toLocaleString();
        localStorage.setItem('orderHistory', JSON.stringify(orderHistory));
      }
      
      pendingOrders.splice(index, 1);
      localStorage.setItem('pendingOrders', JSON.stringify(pendingOrders));
      renderPendingOrders();
      showNotification('Order အောင်မြင်စွာ အတည်ပြုပြီးပါပြီ', 'success');
    }
    
    function rejectOrder(index) {
      const order = pendingOrders[index];
      
      // Update order history status
      const orderIndex = orderHistory.findIndex(o => 
        o.username === order.username && o.platform === order.platform && 
        o.service === order.service && o.date === order.date
      );
      if (orderIndex !== -1) {
        orderHistory[orderIndex].status = 'rejected';
        orderHistory[orderIndex].processedDate = new Date().toLocaleString();
        localStorage.setItem('orderHistory', JSON.stringify(orderHistory));
      }
      
      pendingOrders.splice(index, 1);
      localStorage.setItem('pendingOrders', JSON.stringify(pendingOrders));
      renderPendingOrders();
      showNotification('Order request ကို ပယ်ဖျက်လိုက်ပါပြီ', 'success');
    }
    
    function renderUserAccountTable() {
      const tbody = document.querySelector('#userAccountTable tbody');
      tbody.innerHTML = '';
      
      userAccounts.forEach(user => {
        const tr = document.createElement('tr');
        tr.innerHTML = `
          <td>${user.username}</td>
          <td>${user.email || '-'}</td>
          <td>${user.password}</td>
          <td>${user.loginType}</td>
          <td>${user.balance}</td>
        `;
        tbody.appendChild(tr);
      });
    }
    
    /* ---------------------------
      ORDER & PLATFORM FUNCTIONS
    ----------------------------*/
    function switchPlatform(platform, element) {
      // Update active platform tab
      document.querySelectorAll('.platform-tab').forEach(tab => {
        tab.classList.remove('active');
      });
      element.classList.add('active');
      
      currentPlatform = platform;
      
      // Update service dropdown
      const serviceSelect = document.getElementById('serviceSelect');
      serviceSelect.innerHTML = '';
      
      serviceData[platform].forEach(service => {
        const option = document.createElement('option');
        option.value = service.id;
        option.textContent = `${service.name} - ${service.price} MMK/1000`;
        serviceSelect.appendChild(option);
      });
      
      // Update placeholder based on platform
      const linkInput = document.getElementById('tiktokLink');
      switch(platform) {
        case 'tiktok':
          linkInput.placeholder = 'TikTok လင့်ခ်';
          break;
        case 'facebook':
          linkInput.placeholder = 'Facebook လင့်ခ်';
          break;
        case 'telegram':
          linkInput.placeholder = 'Telegram လင့်ခ်';
          break;
        case 'youtube':
          linkInput.placeholder = 'YouTube လင့်ခ်';
          break;
      }
      
      // Reset cost calculation
      calculateCost();
      
      // If in admin panel, update service table
      if (document.getElementById('adminPanel').style.display === 'block') {
        renderServiceTable();
      }
    }
    
    function calculateCost() {
      const serviceSelect = document.getElementById('serviceSelect');
      const amountInput = document.getElementById('amount');
      const costDisplay = document.getElementById('costDisplay');
      const deductionConfirmation = document.getElementById('deductionConfirmation');
      const deductionAmount = document.getElementById('deductionAmount');
      
      const selectedServiceId = serviceSelect.value;
      const amount = parseInt(amountInput.value) || 0;
      
      if (selectedServiceId && amount > 0) {
        const service = serviceData[currentPlatform].find(s => s.id === selectedServiceId);
        if (service) {
          const cost = Math.ceil((service.price * amount) / 1000);
          costDisplay.textContent = `ကုန်ကျငွေ: ${cost} MMK`;
          
          // Show deduction confirmation
          deductionConfirmation.style.display = 'block';
          deductionAmount.textContent = cost;
        }
      } else {
        costDisplay.textContent = 'ကုန်ကျငွေ: 0 MMK';
        deductionConfirmation.style.display = 'none';
      }
    }
    
    function submitOrder() {
      // Check if button is in cooldown
      if (orderButtonTimer > 0) {
        showNotification('Please wait before submitting another order', 'error');
        return;
      }
      
      const serviceSelect = document.getElementById('serviceSelect');
      const linkInput = document.getElementById('tiktokLink');
      const amountInput = document.getElementById('amount');
      
      const selectedServiceId = serviceSelect.value;
      const link = linkInput.value.trim();
      const amount = parseInt(amountInput.value);
      
      if (!selectedServiceId || !link || !amount || amount < 1) {
        showNotification('ဝန်ဆောင်မှု၊ လင့်ခ်နှင့် အရေအတွက် အားလုံးထည့်ပေးပါ', 'error');
        return;
      }
      
      const service = serviceData[currentPlatform].find(s => s.id === selectedServiceId);
      const cost = Math.ceil((service.price * amount) / 1000);
      
      if (currentUser.balance < cost) {
        showNotification('လက်ကျန်ငွေ မလုံလောက်ပါ။ ငွေဖြည့်ပါ', 'error');
        return;
      }
      
      // Deduct balance
      currentUser.balance -= cost;
      const userIndex = userAccounts.findIndex(u => 
        (u.email && u.email === currentUser.email) || 
        (u.username && u.username === currentUser.username)
      );
      
      if (userIndex !== -1) {
        userAccounts[userIndex].balance = currentUser.balance;
        localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
        localStorage.setItem('currentUser', JSON.stringify(currentUser));
        updateBalanceDisplay();
      }
      
      // Create order object
      const platformNames = {
        tiktok: 'TikTok',
        facebook: 'Facebook',
        telegram: 'Telegram',
        youtube: 'YouTube'
      };
      
      const order = {
        username: currentUser.email || currentUser.username,
        platform: platformNames[currentPlatform],
        service: service.name,
        link: link,
        amount: amount,
        cost: cost,
        date: new Date().toLocaleString(),
        status: 'pending'
      };
      
      // Add to pending orders
      pendingOrders.push(order);
      localStorage.setItem('pendingOrders', JSON.stringify(pendingOrders));
      
      // Add to order history
      orderHistory.push(order);
      localStorage.setItem('orderHistory', JSON.stringify(orderHistory));
      
      // Send order to Telegram
      const message = `
🛒 **New Order Received**
━━━━━━━━━━━━━━━━━━
👤 **User:** ${currentUser.email || currentUser.username}
📱 **Platform:** ${platformNames[currentPlatform]}
🛍️ **Service:** ${service.name}
🔗 **Link:** ${link}
📊 **Amount:** ${amount}
💰 **Cost:** ${cost} MMK
💳 **Remaining Balance:** ${currentUser.balance} MMK
      `;
      
      sendToTelegram(message);
      
      // Start button timer
      startOrderButtonTimer();
      
      // Reset form
      linkInput.value = '';
      amountInput.value = '';
      calculateCost();
      
      showNotification('Order အောင်မြင်စွာတင်ပြီးပါပြီ', 'success');
    }
    
    /* ---------------------------
      HISTORY FUNCTIONS
    ----------------------------*/
    function renderOrderHistory() {
      const container = document.getElementById('orderHistoryList');
      const userOrders = orderHistory.filter(order => 
        order.username === (currentUser.email || currentUser.username)
      );
      
      // Sort by date (newest first)
      userOrders.sort((a, b) => new Date(b.date) - new Date(a.date));
      
      if (userOrders.length === 0) {
        container.innerHTML = '<p class="note">No order history found</p>';
        return;
      }
      
      container.innerHTML = '';
      userOrders.forEach((order, index) => {
        const statusClass = order.status === 'completed' ? 'status-completed' : 
                           order.status === 'rejected' ? 'status-rejected' : 'status-pending';
        
        const div = document.createElement('div');
        div.className = 'history-item';
        div.innerHTML = `
          <div class="history-header">
            <strong>${order.platform} - ${order.service}</strong>
            <span class="history-status ${statusClass}">${order.status.toUpperCase()}</span>
          </div>
          <p><strong>Link:</strong> ${order.link}</p>
          <p><strong>Amount:</strong> ${order.amount}</p>
          <p><strong>Cost:</strong> ${order.cost} MMK</p>
          <p><strong>Date:</strong> ${order.date}</p>
          ${order.processedDate ? `<p><strong>Processed:</strong> ${order.processedDate}</p>` : ''}
        `;
        container.appendChild(div);
      });
    }
    
    function renderTopupHistory() {
      const container = document.getElementById('topupHistoryList');
      const userTopups = topupHistory.filter(topup => 
        topup.username === (currentUser.email || currentUser.username)
      );
      
      // Sort by date (newest first)
      userTopups.sort((a, b) => new Date(b.date) - new Date(a.date));
      
      if (userTopups.length === 0) {
        container.innerHTML = '<p class="note">No top up history found</p>';
        return;
      }
      
      container.innerHTML = '';
      userTopups.forEach((topup, index) => {
        const statusClass = topup.status === 'completed' ? 'status-completed' : 
                           topup.status === 'rejected' ? 'status-rejected' : 'status-pending';
        
        const div = document.createElement('div');
        div.className = 'history-item';
        div.innerHTML = `
          <div class="history-header">
            <strong>Top Up Request</strong>
            <span class="history-status ${statusClass}">${topup.status.toUpperCase()}</span>
          </div>
          <p><strong>Amount:</strong> ${topup.amount} MMK</p>
          <p><strong>Date:</strong> ${topup.date}</p>
          ${topup.processedDate ? `<p><strong>Processed:</strong> ${topup.processedDate}</p>` : ''}
        `;
        container.appendChild(div);
      });
    }
    
    /* ---------------------------
      TOP UP FUNCTIONS
    ----------------------------*/
    function previewImage() {
      const fileInput = document.getElementById('proofImage');
      const preview = document.getElementById('imagePreview');
      
      if (fileInput.files && fileInput.files[0]) {
        const reader = new FileReader();
        
        reader.onload = function(e) {
          preview.src = e.target.result;
          preview.style.display = 'block';
        }
        
        reader.readAsDataURL(fileInput.files[0]);
      }
    }
    
    function copyTopupIdentifier() {
      if (currentUser) {
        const identifier = currentUser.email || currentUser.username;
        copyToClipboard(identifier, document.getElementById('topupUserIdentifier'));
        showNotification('Username/Email copied to clipboard!', 'success');
      }
    }
    
    function sendTopupToTelegram() {
      // Check if button is in cooldown
      if (topupButtonTimer > 0) {
        showNotification('Please wait before sending another top up request', 'error');
        return;
      }
      
      const amount = parseInt(document.getElementById('topupAmount').value);
      const proofImage = document.getElementById('proofImage').files[0];
      
      if (!amount || amount < 1 || !proofImage) {
        showNotification('ငွေပမာဏနှင့် ပြေစာပုံ အားလုံးထည့်ပေးပါ', 'error');
        return;
      }
      
      const username = currentUser.email || currentUser.username;
      
      // Create topup request
      const topupRequest = {
        username: username,
        amount: amount,
        date: new Date().toLocaleString(),
        status: 'pending'
      };
      
      // Add to pending topups
      pendingTopups.push(topupRequest);
      localStorage.setItem('pendingTopups', JSON.stringify(pendingTopups));
      
      // Add to topup history
      topupHistory.push(topupRequest);
      localStorage.setItem('topupHistory', JSON.stringify(topupHistory));
      
      // Start button timer
      startTopupButtonTimer();
      
      // Send to Telegram (simulated)
      const formData = new FormData();
      formData.append('chat_id', chatId);
      formData.append('caption', `💳 Top Up Request\nUser: ${username}\nAmount: ${amount} MMK`);
      formData.append('photo', proofImage);
      
      fetch(TELEGRAM_URL + 'sendPhoto', {
        method: 'POST',
        body: formData
      })
      .then(response => response.json())
      .then(data => {
        if (data.ok) {
          // Reset form
          document.getElementById('topupAmount').value = '';
          document.getElementById('proofImage').value = '';
          document.getElementById('imagePreview').style.display = 'none';
          
          showNotification('ပြေစာပုံအား Telegram သို့ပို့ပြီးပါပြီ။ Admin မှအတည်ပြုပါက ငွေဖြည့်ပေးပါမည်', 'success');
        } else {
          showNotification('ပြေစာပုံပို့ရာတွင် အမှားတစ်ခုရှိသည်။ VPN ဖွင့်ပြီး ထပ်ကြိုးစားကြည့်ပါ', 'error');
        }
      })
      .catch(error => {
        console.error('Error:', error);
        showNotification('ပြေစာပုံပို့ရာတွင် အမှားတစ်ခုရှိသည်။ VPN ဖွင့်ပြီး ထပ်ကြိုးစားကြည့်ပါ', 'error');
      });
    }
    
    /* ---------------------------
      SETTINGS FUNCTIONS
    ----------------------------*/
    function goToSettings() {
      document.getElementById('authSection').style.display = 'none';
      document.getElementById('orderSection').style.display = 'none';
      document.getElementById('adminPanel').style.display = 'none';
      document.getElementById('adminLoginSection').style.display = 'none';
      document.getElementById('settingsSection').style.display = 'block';
      document.querySelector('.home-btn').style.display = 'flex';
      
      // Update user info
      document.getElementById('displayUsername').textContent = currentUser.username;
      document.getElementById('displayEmail').textContent = currentUser.email || '-';
      document.getElementById('displayBalance').textContent = currentUser.balance;
    }
    
    function goBackToOrder() {
      document.getElementById('settingsSection').style.display = 'none';
      document.getElementById('adminPanel').style.display = 'none';
      document.getElementById('adminLoginSection').style.display = 'none';
      document.getElementById('orderSection').style.display = 'block';
      document.querySelector('.home-btn').style.display = 'none';
    }
    
    function copyUsername() {
      copyToClipboard(currentUser.username, document.getElementById('displayUsername'));
      showNotification('Username ကို Copy ယူပြီးပါပြီ', 'success');
    }
    
    function changeUsername() {
      const newUsername = document.getElementById('newUsername').value.trim();
      
      if (!newUsername) {
        showNotification('New Username ထည့်ပေးပါ', 'error');
        return;
      }
      
      if (userAccounts.find(u => u.username === newUsername && u !== currentUser)) {
        showNotification('ဤ Username ကို အခြားသူသုံးထားပြီးဖြစ်သည်', 'error');
        return;
      }
      
      // Update in userAccounts
      const userIndex = userAccounts.findIndex(u => 
        (u.email && u.email === currentUser.email) || 
        (u.username && u.username === currentUser.username)
      );
      
      if (userIndex !== -1) {
        userAccounts[userIndex].username = newUsername;
        localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
      }
      
      // Update currentUser
      currentUser.username = newUsername;
      localStorage.setItem('currentUser', JSON.stringify(currentUser));
      
      // Update display
      document.getElementById('displayUsername').textContent = newUsername;
      document.getElementById('newUsername').value = '';
      
      showNotification('Username အောင်မြင်စွာပြောင်းပြီးပါပြီ', 'success');
    }
    
    function changePassword() {
      const currentPassword = document.getElementById('currentPassword').value;
      const newPassword = document.getElementById('newPassword').value;
      const confirmPassword = document.getElementById('confirmPassword').value;
      
      if (!currentPassword || !newPassword || !confirmPassword) {
        showNotification('Password အားလုံးထည့်ပေးပါ', 'error');
        return;
      }
      
      if (currentPassword !== currentUser.password) {
        showNotification('လက်ရှိ Password မှားနေပါသည်', 'error');
        return;
      }
      
      if (newPassword !== confirmPassword) {
        showNotification('New Password နှင့် Confirm Password တူညီရပါမည်', 'error');
        return;
      }
      
      // Update in userAccounts
      const userIndex = userAccounts.findIndex(u => 
        (u.email && u.email === currentUser.email) || 
        (u.username && u.username === currentUser.username)
      );
      
      if (userIndex !== -1) {
        userAccounts[userIndex].password = newPassword;
        localStorage.setItem('userAccounts', JSON.stringify(userAccounts));
      }
      
      // Update currentUser
      currentUser.password = newPassword;
      localStorage.setItem('currentUser', JSON.stringify(currentUser));
      
      // Reset form
      document.getElementById('currentPassword').value = '';
      document.getElementById('newPassword').value = '';
      document.getElementById('confirmPassword').value = '';
      
      showNotification('Password အောင်မြင်စွာပြောင်းပြီးပါပြီ', 'success');
    }
    
    function contactAdmin() {
      window.open(`https://t.me/${TELEGRAM_USERNAME}`, '_blank');
    }
    
    /* ---------------------------
      UTILITY FUNCTIONS
    ----------------------------*/
    function showOrderSection() {
      document.getElementById('authSection').style.display = 'none';
      document.getElementById('orderSection').style.display = 'block';
      document.getElementById('settingsSection').style.display = 'none';
      document.getElementById('adminPanel').style.display = 'none';
      document.getElementById('adminLoginSection').style.display = 'none';
      document.querySelector('.home-btn').style.display = 'none';
      
      updateBalanceDisplay();
      switchPlatform('tiktok', document.querySelector('.platform-tab.tiktok'));
      
      // Update topup user identifier
      if (currentUser) {
        document.getElementById('topupUserIdentifier').textContent = currentUser.email || currentUser.username;
      }
    }
    
    function updateBalanceDisplay() {
      if (currentUser) {
        document.getElementById('userBalance').textContent = currentUser.balance;
      }
    }
    
    function copyToClipboard(text, element) {
      navigator.clipboard.writeText(text).then(() => {
        if (element) {
          element.classList.add('copied');
          setTimeout(() => {
            element.classList.remove('copied');
          }, 2000);
        }
      });
    }
    
    function copyPaymentNumber(number, element) {
      copyToClipboard(number, element);
      showNotification(`Payment number ${number} copied to clipboard!`, 'success');
    }
    
    function sendToTelegram(message) {
      const url = `${TELEGRAM_URL}sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}&parse_mode=Markdown`;
      
      fetch(url)
        .then(response => response.json())
        .then(data => {
          if (!data.ok) {
            console.error('Telegram error:', data);
          }
        })
        .catch(error => console.error('Error sending to Telegram:', error));
    }
    
    function showNotification(message, type) {
      const notification = document.getElementById('notification');
      notification.textContent = message;
      notification.style.display = 'block';
      notification.style.background = type === 'error' ? 'var(--danger)' : 'var(--secondary)';
      
      setTimeout(() => {
        notification.style.display = 'none';
      }, 4000);
    }
  </script>
</body>
</html>

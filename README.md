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
        <div class="admin-

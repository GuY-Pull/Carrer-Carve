<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>CareerCarve Home Screen – Professional UI</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" xintegrity="sha512-DTOQO9RWCH3ppGqcWaEA1BIZOC6xxalwEsw9c2QQeAIftl+Vegovlnee1c9QX4TctnWMn13TZye+giMm8e2LwA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <style>
      :root {
          --radius: 16px;
          --shadow: 0 24px 60px -15px rgba(31, 41, 55, 0.08);
          --bg: #F7F7F8;
          --card-bg: #ffffff;
          --primary: #4F46E5; /* Indigo */
          --secondary: #D946EF; /* Fuchsia */
          --accent: #F59E0B; /* Amber for stars */
          --text: #1F2937;
          --muted: #6B7280;
          --transition: .2s ease;
          font-family: "Inter", system-ui,-apple-system,BlinkMacSystemFont,sans-serif;
      }

      .dark-theme {
          --shadow: 0 24px 60px -15px rgba(0,0,0,0.2);
          --bg: #191C32;
          --card-bg: rgba(255, 255, 255, 0.05);
          --primary: #00E5FF; /* Cyan */
          --secondary: #FFD700; /* Gold */
          --accent: #FFD700;
          --text: #E0E0E0;
          --muted: #A0A0A0;
      }

      * {box-sizing:border-box;}
      body {
          margin:0;
          background: var(--bg);
          color: var(--text);
          -webkit-font-smoothing: antialiased;
          padding-bottom: 90px;
          transition: background-color var(--transition), color var(--transition);
      }
      a {
        text-decoration: none;
        color: inherit;
      }
      .container {
          max-width: 480px;
          margin: 0 auto;
          padding: 0 16px;
      }
      .header {
          padding: 14px 4px 8px;
          display:flex;
          justify-content: space-between;
          align-items: center;
      }
      .greeting {
          display:flex;
          gap:12px;
          align-items:center;
      }
      .avatar {
          width:44px;
          height:44px;
          border-radius:50%;
          background: linear-gradient(135deg,var(--primary),var(--secondary));
          padding:2px;
          display:flex;
          align-items:center;
          justify-content:center;
      }
      .avatar-inner {
          width:100%;
          height:100%;
          border-radius:50%;
          background: var(--bg);
          display:flex;
          align-items:center;
          justify-content:center;
          font-weight:700;
          color: var(--text);
          font-size:16px;
          transition: background-color var(--transition);
      }
      .header-text {
          display:flex;
          flex-direction: column;
      }
      .header-text .hi {
          font-size: 1rem;
          font-weight:600;
          margin:0;
      }
      .sub {
          font-size: 0.75rem;
          color: var(--muted);
          margin:2px 0 0;
      }
      .icon-btns {
          display:flex;
          gap:14px;
          align-items:center;
      }
      .icon-circle {
          width:38px;
          height:38px;
          border-radius:50%;
          background:var(--card-bg);
          border: 1px solid rgba(0,0,0,0.05);
          display:flex;
          align-items:center;
          justify-content:center;
          box-shadow:0 10px 25px -10px rgba(0,0,0,0.07);
          cursor:pointer;
          font-size:16px;
          color: var(--primary);
          transition: all var(--transition);
      }
      .dark-theme .icon-circle {
        border-color: rgba(255,255,255,0.1);
      }
      .icon-circle:hover { transform: translateY(-2px); }
      .card {
          background: var(--card-bg);
          border-radius: var(--radius);
          padding: 16px 20px;
          margin: 14px 0;
          box-shadow: var(--shadow);
          transition: transform var(--transition), box-shadow var(--transition), background-color var(--transition), border-color var(--transition);
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          border: 1px solid transparent;
      }
      .dark-theme .card {
        border-color: rgba(255,255,255,0.1);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
      }
      .card:hover { transform: translateY(-2px); box-shadow: 0 28px 65px -15px rgba(31, 41, 55, 0.15); }
      .dark-theme .card:hover { box-shadow: 0 28px 65px -15px rgba(0,0,0,0.25); }
      .resume-card {
          display:flex;
          align-items:center;
          gap:16px;
      }
      .circle {
          position: relative;
          width:80px;
          height:80px;
          flex-shrink:0;
      }
      .circle svg { transform: rotate(-90deg); }
      .circle .inner {
          position:absolute;
          top:0;
          left:0;
          width:100%;
          height:100%;
          display:flex;
          flex-direction: column;
          align-items:center;
          justify-content:center;
          font-size:20px;
          font-weight:700;
          color: var(--primary);
      }
      .circle .inner-subtext {
          font-size: 10px;
          font-weight: 500;
          color: var(--muted);
          margin-top: -2px;
      }
      .resume-info { flex:1; }
      .resume-info h3 { margin:0; font-size:1rem; }
      .resume-info p { margin:4px 0; font-size:0.75rem; color: var(--muted); }
      .gamification-details {
          font-size: 11px;
          margin: 8px 0;
          line-height: 1.5;
      }
      .gamification-details .streak { color: #D97706; font-weight: 600; }
      .dark-theme .gamification-details .streak { color: var(--accent); }
      .gamification-details .improvement { color: #38A169; font-weight: 600; }
      .btn {
          padding:10px 18px;
          border:none;
          border-radius:999px;
          cursor:pointer;
          font-weight:600;
          font-size:0.8rem;
          display:inline-flex;
          align-items:center;
          gap:6px;
          transition: all var(--transition);
      }
      .btn-primary {
          background: var(--primary);
          color:#fff;
          box-shadow: 0 16px 50px -10px rgba(79, 70, 229, 0.4);
      }
      .dark-theme .btn-primary {
        color: #000;
        box-shadow: 0 16px 50px -10px rgba(0, 229, 255, 0.3);
      }
      .btn-primary:hover { transform: translateY(-1px); filter: brightness(1.05); }
      .btn-secondary {
          background: #EDF2F7;
          color: var(--text);
      }
      .dark-theme .btn-secondary {
        background: rgba(255,255,255,0.1);
        color: var(--text);
      }
      .btn-secondary:hover { background: #E2E8F0; }
      .dark-theme .btn-secondary:hover { background: rgba(255,255,255,0.2); }
      
      .section-title {
          display:flex;
          justify-content: space-between;
          align-items:center;
          margin:24px 0 8px;
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          animation-delay: .1s;
      }
      .section-title h2 {
          font-size:1rem;
          margin:0;
          font-weight:700;
          color: var(--text);
          display: flex;
          align-items: center;
          gap: 8px;
      }
      .section-title h2 i { color: var(--primary); }
      .see-all {
          font-size:0.8rem;
          color: var(--primary);
          cursor:pointer;
          font-weight:500;
      }
      .quick-actions {
          display:grid;
          grid-template-columns: repeat(3,1fr);
          gap:12px;
          margin: 6px 0 8px;
      }
      .action-tile {
          background:var(--card-bg);
          border-radius:14px;
          padding: 12px;
          display:flex;
          flex-direction: column;
          align-items:center;
          justify-content: center;
          text-align:center;
          gap: 8px;
          box-shadow: var(--shadow);
          font-size:12px;
          font-weight: 600;
          cursor:pointer;
          transition: transform var(--transition), box-shadow var(--transition), background-color var(--transition), border-color var(--transition);
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          border: 1px solid transparent;
      }
      .dark-theme .action-tile {
        border-color: rgba(255,255,255,0.1);
      }
      .action-tile:hover { transform: translateY(-4px); box-shadow: 0 20px 40px -15px rgba(31, 41, 55, 0.2); }
      .dark-theme .action-tile:hover { box-shadow: 0 20px 40px -15px rgba(0,0,0,0.25); }
      .action-tile i { font-size: 18px; color: var(--primary); transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
      .action-tile:hover i { transform: scale(1.2) rotate(-10deg); }

      .list-card {
          background: var(--card-bg);
          padding: 14px;
          border-radius: 14px;
          box-shadow: var(--shadow);
          margin-bottom: 12px;
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          cursor: pointer;
          position: relative;
          border: 1px solid transparent;
          transition: transform var(--transition), box-shadow var(--transition), background-color var(--transition), border-color var(--transition);
      }
      .dark-theme .list-card {
        border-color: rgba(255,255,255,0.1);
      }
      .list-card .arrow-icon {
        position: absolute;
        right: 16px;
        top: 50%;
        transform: translateY(-50%);
        color: var(--muted);
        opacity: 0;
        transition: opacity var(--transition), right var(--transition);
      }
      .list-card:hover .arrow-icon {
        opacity: 1;
        right: 12px;
      }

      .mentor-card-vertical {
          display: flex;
          align-items: center;
          gap: 14px;
      }
      .mentor-photo {
          width:48px;
          height:48px;
          border-radius:50%;
          flex-shrink: 0;
          background: var(--secondary);
          color: var(--text);
          font-weight: 700;
          font-size: 14px;
          display: flex;
          align-items: center;
          justify-content: center;
      }
      .mentor-info { flex:1; }
      .mentor-info h4 { margin:0; font-size:0.9rem; }
      .mentor-info p { margin:4px 0 2px; font-size:0.7rem; color:var(--muted); }
      .mentor-info .availability { font-size: 0.7rem; color: #38A169; font-weight: 500; }
      .star-rating { color: var(--accent); font-size: 10px; }
      
      .concept-grid {
          display: grid;
          grid-template-columns: 1fr 1fr;
          gap: 12px;
      }
      .concept-card-new {
          background: var(--card-bg);
          border-radius: 14px;
          padding: 16px;
          box-shadow: var(--shadow);
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          cursor: pointer;
          transition: transform var(--transition), box-shadow var(--transition), background-color var(--transition), border-color var(--transition);
          position: relative;
          overflow: hidden;
          border: 1px solid transparent;
      }
      .dark-theme .concept-card-new {
        border-color: rgba(255,255,255,0.1);
      }
      .concept-card-new:hover {
          transform: translateY(-4px);
          box-shadow: 0 20px 40px -15px rgba(31, 41, 55, 0.2);
      }
      .dark-theme .concept-card-new:hover {
        box-shadow: 0 20px 40px -15px rgba(0,0,0,0.25);
      }
      .concept-card-new .icon {
          font-size: 24px;
          color: var(--primary);
          margin-bottom: 8px;
      }
      .concept-card-new h4 {
          margin: 0 0 4px;
          font-size: 1rem;
      }
      .concept-card-new p {
          font-size: 0.75rem;
          color: var(--muted);
          margin: 0;
          line-height: 1.4;
      }
      .concept-card-new .read-now {
          position: absolute;
          bottom: -40px;
          left: 16px;
          right: 16px;
          text-align: center;
          background: var(--primary);
          color: #fff;
          padding: 8px;
          border-radius: 8px;
          font-size: 12px;
          font-weight: 600;
          transition: bottom .3s ease;
      }
      .dark-theme .concept-card-new .read-now {
        color: #000;
      }
      .concept-card-new:hover .read-now {
          bottom: 16px;
      }

      .podcast-scroller {
          display: flex;
          gap: 12px;
          overflow-x: auto;
          padding-bottom: 16px;
          scroll-snap-type: x mandatory;
          -ms-overflow-style: none;
          scrollbar-width: none;
          scroll-behavior: smooth;
      }
      .podcast-scroller::-webkit-scrollbar {
          display: none;
      }
      .podcast-tile {
          flex: 0 0 70%;
          max-width: 70%;
          background: var(--card-bg);
          border-radius: 14px;
          padding: 16px;
          box-shadow: var(--shadow);
          scroll-snap-align: start;
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          cursor: pointer;
          border: 1px solid transparent;
          transition: transform var(--transition), box-shadow var(--transition), background-color var(--transition), border-color var(--transition);
      }
      .dark-theme .podcast-tile {
        border-color: rgba(255,255,255,0.1);
      }
      .podcast-item {
          display: flex;
          align-items: center;
          gap: 14px;
      }
      .podcast-item i {
          font-size: 20px;
          color: var(--primary);
      }
      .podcast-info h4 {
          margin: 0;
          font-size: 0.9rem;
      }
      .podcast-info p {
          margin: 4px 0 0;
          font-size: 0.75rem;
          color: var(--muted);
      }
      .scroll-dots {
          display: flex;
          justify-content: center;
          gap: 6px;
          margin-top: -4px;
      }
      .dot {
          width: 6px;
          height: 6px;
          border-radius: 50%;
          background: #d1d5db;
          transition: all var(--transition);
      }
      .dark-theme .dot {
        background: rgba(255,255,255,0.2);
      }
      .dot.active {
          background: var(--primary);
          transform: scale(1.2);
      }
      
      .story-scroller {
          display: flex;
          gap: 12px;
          overflow-x: auto;
          padding-bottom: 16px;
          scroll-snap-type: x mandatory;
          -ms-overflow-style: none;
          scrollbar-width: none;
      }
      .story-scroller::-webkit-scrollbar { display: none; }
      .story-tile {
          flex: 0 0 80%;
          max-width: 80%;
          background: var(--card-bg);
          border-radius: 14px;
          box-shadow: var(--shadow);
          scroll-snap-align: start;
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          cursor: pointer;
          padding: 16px;
          display: flex;
          flex-direction: column;
          align-items: center;
          text-align: center;
          border: 1px solid transparent;
          transition: transform var(--transition), box-shadow var(--transition), background-color var(--transition), border-color var(--transition);
      }
      .dark-theme .story-tile {
        border-color: rgba(255,255,255,0.1);
      }
      .story-photo {
          width: 60px;
          height: 60px;
          border-radius: 50%;
          margin-bottom: 12px;
          border: 3px solid var(--secondary);
      }
      .story-tile h4 {
          margin: 0 0 4px;
          font-size: 0.9rem;
      }
      .story-tile .placement {
          font-size: 0.75rem;
          font-weight: 600;
          color: var(--primary);
          margin-bottom: 8px;
      }
      .story-tile .quote {
          font-size: 0.75rem;
          color: var(--muted);
          font-style: italic;
      }

      .premium-scroller {
        display: flex;
        gap: 12px;
        overflow-x: auto;
        padding-bottom: 16px;
        scroll-snap-type: x mandatory;
        -ms-overflow-style: none;
        scrollbar-width: none;
      }
      .premium-scroller::-webkit-scrollbar { display: none; }
      .premium-tile {
          flex: 0 0 75%;
          max-width: 75%;
          background: linear-gradient(135deg, var(--primary), var(--secondary));
          color: #fff;
          border-radius: 14px;
          padding: 16px;
          box-shadow: 0 20px 50px -15px rgba(79, 70, 229, 0.4);
          scroll-snap-align: start;
          animation: fadeInUp .5s ease forwards;
          opacity: 0;
          cursor: pointer;
      }
      .dark-theme .premium-tile {
        color: #000;
      }
      .premium-tile .icon {
          font-size: 24px;
          margin-bottom: 8px;
      }
      .premium-tile h4 {
          margin: 0 0 4px;
          font-size: 1rem;
          font-weight: 700;
          color: #fff;
      }
      .dark-theme .premium-tile h4 {
        color: #000;
      }
      .premium-tile p {
          font-size: 0.75rem;
          opacity: 0.9;
          margin: 0 0 12px;
      }
      .premium-tile .price {
          font-size: 1.1rem;
          font-weight: 700;
          background: rgba(0,0,0,0.2);
          color: #fff;
          padding: 4px 10px;
          border-radius: 99px;
          display: inline-block;
      }
      
      .news-card {
        position: relative;
        border-radius: var(--radius);
        overflow: hidden;
        box-shadow: var(--shadow);
        animation: fadeInUp .5s ease forwards;
        opacity: 0;
        cursor: pointer;
        min-height: 150px;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        padding: 16px;
        color: #fff;
      }
      .news-card::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: linear-gradient(to top, rgba(0,0,0,0.8) 20%, transparent);
        z-index: 1;
      }
      .news-card img {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: 0;
        transition: transform .3s ease;
      }
      .news-card:hover img {
        transform: scale(1.05);
      }
      .news-content {
        position: relative;
        z-index: 2;
      }
      .news-content h4 {
        margin: 0 0 4px;
        font-size: 1.1rem;
        font-weight: 700;
      }
      .news-content p {
        font-size: 0.8rem;
        opacity: 0.9;
      }

      .hotbar {
          position: fixed;
          bottom: 0;
          left: 0;
          right: 0;
          background: rgba(255,255,255,0.9);
          backdrop-filter: blur(8px);
          -webkit-backdrop-filter: blur(8px);
          border-top: 1px solid #e6ecf3;
          padding: 10px 16px;
          box-shadow: 0 -10px 40px rgba(39,50,65,0.08);
          z-index: 1000;
          transition: background-color var(--transition), border-color var(--transition);
      }
      .dark-theme .hotbar {
        background: rgba(25, 28, 50, 0.8);
        border-top: 1px solid rgba(255,255,255,0.1);
        box-shadow: 0 -10px 40px rgba(0,0,0,0.2);
      }
      .hotbar-content {
          max-width: 460px;
          margin: 0 auto;
          display: flex;
          justify-content: space-around;
          align-items: center;
      }
      .nav-item {
          display: flex;
          flex-direction: column;
          align-items: center;
          gap: 4px;
          font-size: 22px;
          color: var(--muted);
          cursor: pointer;
          transition: all var(--transition);
      }
      .nav-item:hover {
          color: var(--primary);
          transform: translateY(-2px);
      }
      .nav-item.active {
          color: var(--primary);
      }

      .popup-overlay {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(39, 50, 65, 0.5);
        backdrop-filter: blur(4px);
        -webkit-backdrop-filter: blur(4px);
        z-index: 2000;
        display: flex;
        align-items: center;
        justify-content: center;
        opacity: 0;
        visibility: hidden;
        transition: opacity .3s ease, visibility .3s ease;
      }
      .popup-overlay.visible {
        opacity: 1;
        visibility: visible;
      }
      .popup-content {
        background: #fff;
        padding: 24px;
        border-radius: var(--radius);
        box-shadow: 0 30px 70px -20px rgba(0,0,0,0.2);
        text-align: center;
        width: 90%;
        max-width: 320px;
        transform: scale(0.95);
        transition: transform .3s ease, background-color var(--transition), color var(--transition);
      }
      .dark-theme .popup-content {
        background: #1F2340;
        color: var(--text);
        border: 1px solid rgba(255,255,255,0.1);
      }
      .popup-overlay.visible .popup-content {
        transform: scale(1);
      }
      .popup-content h3 {
        margin: 0 0 8px;
        font-size: 1.2rem;
      }
      .dark-theme .popup-content h3 {
        color: #fff;
      }
      .popup-content p {
        margin: 0 0 20px;
        font-size: 0.9rem;
        color: var(--muted);
      }

      @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(15px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
      }
      .clickable:active {
        transform: scale(0.97);
        transition: transform 0.1s ease;
      }
    </style>
</head>
<body class="dark-theme">
    <div class="container">
      <div class="header">
        <div class="greeting">
          <div class="avatar">
            <div class="avatar-inner">B</div>
          </div>
          <div class="header-text">
            <div class="hi">Hi Bandreddy 👋</div>
            <div class="sub">Your journey is looking strong!</div>
          </div>
        </div>
        <div class="icon-btns">
          <div id="theme-toggle" class="icon-circle" title="Toggle Theme"><i class="fa-solid fa-sun"></i></div>
          <div class="icon-circle clickable" title="Messages"><i class="fa-solid fa-comment-dots"></i></div>
          <div class="icon-circle clickable" title="Notifications"><i class="fa-solid fa-bell"></i></div>
        </div>
      </div>

      <div class="card resume-card">
        <div class="circle">
          <svg width="80" height="80" viewBox="0 0 100 100">
            <circle cx="50" cy="50" r="45" stroke="rgba(255,255,255,0.1)" stroke-width="10" fill="none" />
            <circle id="progress-circle" cx="50" cy="50" r="45" stroke="var(--primary)" stroke-width="10" stroke-linecap="round" fill="none" style="transition: stroke-dashoffset 0.8s ease;"></circle>
          </svg>
          <div class="inner">
            <span id="progress-text">0%</span>
            <span class="inner-subtext">Complete</span>
          </div>
        </div>
        <div class="resume-info">
          <h3>Resume Readiness</h3>
          <p>Great progress! Only 3 sections remaining to achieve an 'All-Star' rating.</p>
          <div class="gamification-details">
            <div><span class="streak"><i class="fa-solid fa-star"></i> 7-Day Streak • <i class="fa-solid fa-award"></i> Resume Expert Badge</span></div>
            <div><span class="improvement"><i class="fa-solid fa-arrow-trend-up"></i> +15% improvement this week</span></div>
          </div>
          <div style="margin-top:12px; display:flex; gap:8px;">
            <button class="btn btn-primary clickable"><i class="fa-solid fa-wand-magic-sparkles"></i>Review</button>
            <button class="btn btn-secondary clickable"><i class="fa-solid fa-chart-line"></i>View Progress</button>
          </div>
        </div>
      </div>
      
      <div class="section-title">
        <h2><i class="fa-solid fa-bolt"></i> Quick Actions</h2>
      </div>
      <div class="quick-actions">
        <div class="action-tile clickable" style="animation-delay: .15s"><i class="fa-solid fa-user-tie"></i><span>Mock Interview</span></div>
        <div class="action-tile clickable" style="animation-delay: .2s"><i class="fa-solid fa-handshake-angle"></i><span>Expert Connect</span></div>
        <div class="action-tile clickable" style="animation-delay: .25s"><i class="fa-regular fa-file-alt"></i><span>Case Prep</span></div>
      </div>

      <div class="section-title" style="animation-delay: .3s">
        <h2><i class="fa-solid fa-gem"></i> Premium Services</h2>
      </div>
      <div class="premium-container" style="animation-delay: .35s; opacity: 0; animation: fadeInUp .5s ease forwards;">
        <div class="premium-scroller">
            <div class="premium-tile clickable">
                <div class="icon"><i class="fa-solid fa-user-tie"></i></div>
                <h4>1-on-1 Mock Interview</h4>
                <p>Practice with a real industry expert.</p>
                <div class="price">₹1,499</div>
            </div>
            <div class="premium-tile clickable">
                <div class="icon"><i class="fa-solid fa-file-invoice"></i></div>
                <h4>Expert Resume Review</h4>
                <p>Get detailed feedback in 48 hours.</p>
                <div class="price">₹999</div>
            </div>
            <div class="premium-tile clickable">
                <div class="icon"><i class="fa-solid fa-map-signs"></i></div>
                <h4>Personalized Career Plan</h4>
                <p>A custom roadmap to your dream job.</p>
                <div class="price">₹2,999</div>
            </div>
        </div>
      </div>

      <div class="section-title" style="animation-delay: .4s">
        <h2><i class="fa-solid fa-newspaper"></i> Daily News & Updates</h2>
        <div class="see-all clickable">More <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="news-card clickable" style="animation-delay: .45s">
          <img src="https://images.unsplash.com/photo-1614028674026-a0a187152b69?q=80&w=2070&auto=format&fit=crop" alt="Market news">
          <div class="news-content">
              <h4>Market Movers: Tech stocks surge on AI news</h4>
              <p>Business Today • 5 min read</p>
          </div>
      </div>

      <div class="section-title" style="animation-delay: .5s">
        <h2><i class="fa-solid fa-trophy"></i> Skill Challenges</h2>
         <div class="see-all clickable">More <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .55s">
          <div class="podcast-item">
              <i class="fa-solid fa-stopwatch"></i>
              <div class="podcast-info">
                  <h4>Weekly Aptitude Quiz</h4>
                  <p>Ends in 3 days • Top score wins a badge!</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>

      <div class="section-title" style="animation-delay: .6s">
        <h2><i class="fa-solid fa-users"></i> Recommended Mentors</h2>
        <div class="see-all clickable">See All <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .65s">
          <div class="mentor-card-vertical">
              <div class="mentor-photo">AS</div>
              <div class="mentor-info">
                  <h4>Animesh Singhai</h4>
                  <p>Assistant VP @ Genpact • <span class="star-rating">★★★★<i class="fa-solid fa-star-half-stroke"></i></span> (23)</p>
                  <p class="availability">Available Today</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .7s">
          <div class="mentor-card-vertical">
              <div class="mentor-photo">AN</div>
              <div class="mentor-info">
                  <h4>Anand Narayandas</h4>
                  <p>IIMA - Product @ HelloFresh • <span class="star-rating">★★★★★</span> (18)</p>
                  <p class="availability" style="color: var(--accent);">Next: Tomorrow</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .75s">
          <div class="mentor-card-vertical">
              <div class="mentor-photo">KR</div>
              <div class="mentor-info">
                  <h4>Kabeer Ravi</h4>
                  <p>Engagement Lead @ Mastercard • <span class="star-rating">★★★★★</span> (31)</p>
                  <p class="availability">Available Today</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>

      <div class="section-title" style="animation-delay: .8s">
        <h2><i class="fa-solid fa-briefcase"></i> Live Job Board</h2>
        <div class="see-all clickable">See All <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .85s">
          <div class="mentor-card-vertical">
              <div class="mentor-photo" style="background:#fff; padding: 8px;"><i class="fa-brands fa-google" style="color: #4285F4; font-size: 24px;"></i></div>
              <div class="mentor-info">
                  <h4>Product Manager Intern</h4>
                  <p>Google • Bengaluru, IN • Summer 2026</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .9s">
          <div class="mentor-card-vertical">
              <div class="mentor-photo" style="background:#fff; padding: 8px;"><i class="fa-solid fa-building-columns" style="color: #004D40; font-size: 24px;"></i></div>
              <div class="mentor-info">
                  <h4>Business Analyst</h4>
                  <p>Morgan Stanley • Mumbai, IN • Full-time</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: .95s">
        <div class="mentor-card-vertical">
            <div class="mentor-photo" style="background:#fff; padding: 8px;"><i class="fa-solid fa-building" style="color: #0077B5; font-size: 24px;"></i></div>
            <div class="mentor-info">
                <h4>Management Consultant</h4>
                <p>Deloitte • Gurugram, IN • Full-time</p>
            </div>
        </div>
        <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>
      
      <div class="section-title" style="animation-delay: 1s">
        <h2><i class="fa-solid fa-building"></i> Company Insights</h2>
        <div class="see-all clickable">More <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: 1.05s">
          <div class="podcast-item">
              <i class="fa-brands fa-google"></i>
              <div class="podcast-info">
                  <h4>Google Interview Debrief</h4>
                  <p>Read 5 recent interview experiences for the APM role.</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>

      <div class="section-title" style="animation-delay: 1.1s">
        <h2><i class="fa-solid fa-medal"></i> Success Stories</h2>
        <div class="see-all clickable">More <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="story-container" style="animation-delay: 1.15s; opacity: 0; animation: fadeInUp .5s ease forwards;">
        <div class="story-scroller">
            <div class="story-tile clickable">
                <img src="https://placehold.co/100x100/3EB6A5/FFFFFF?text=AR" alt="Aarav Reddy" class="story-photo">
                <h4>Aarav Reddy</h4>
                <p class="placement">Placed at Bain & Co.</p>
                <p class="quote">"The mentorship was a game-changer. My mentor helped me crack every case."</p>
            </div>
            <div class="story-tile clickable">
                <img src="https://placehold.co/100x100/5A6FA8/FFFFFF?text=SP" alt="Sneha Patel" class="story-photo">
                <h4>Sneha Patel</h4>
                <p class="placement">Intern @ Goldman Sachs</p>
                <p class="quote">"The daily news updates kept me sharp for my finance interviews. Highly recommend!"</p>
            </div>
            <div class="story-tile clickable">
                <img src="https://placehold.co/100x100/E3B23C/FFFFFF?text=RK" alt="Rohan Kumar" class="story-photo">
                <h4>Rohan Kumar</h4>
                <p class="placement">SDE @ Microsoft</p>
                <p class="quote">"The skill challenges were key. I practiced aptitude daily and it made all the difference."</p>
            </div>
        </div>
      </div>

      <div class="section-title" style="animation-delay: 1.2s">
        <h2><i class="fa-solid fa-lightbulb"></i> Unlock Key Concepts</h2>
        <div class="see-all clickable">See All <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="concept-grid">
          <div class="concept-card-new clickable" style="animation-delay: 1.25s">
              <div class="icon"><i class="fa-solid fa-chart-simple"></i></div>
              <h4>Analytics</h4>
              <p>Master data to drive business decisions.</p>
              <div class="read-now">Read Now</div>
          </div>
          <div class="concept-card-new clickable" style="animation-delay: 1.3s">
              <div class="icon"><i class="fa-solid fa-briefcase"></i></div>
              <h4>Consulting</h4>
              <p>Learn frameworks to solve complex problems.</p>
              <div class="read-now">Read Now</div>
          </div>
          <div class="concept-card-new clickable" style="animation-delay: 1.35s">
              <div class="icon"><i class="fa-solid fa-bullhorn"></i></div>
              <h4>Marketing</h4>
              <p>Understand funnels, branding, and growth.</p>
              <div class="read-now">Read Now</div>
          </div>
          <div class="concept-card-new clickable" style="animation-delay: 1.4s">
              <div class="icon"><i class="fa-solid fa-coins"></i></div>
              <h4>Finance</h4>
              <p>Grasp valuation, markets, and investments.</p>
              <div class="read-now">Read Now</div>
          </div>
      </div>

      <div class="section-title" style="animation-delay: 1.45s">
        <h2><i class="fa-solid fa-podcast"></i> Exclusive Podcasts</h2>
        <div class="see-all clickable">See All <i class="fa-solid fa-arrow-right-long"></i></div>
      </div>
      <div class="podcast-container" style="animation-delay: 1.5s; opacity: 0; animation: fadeInUp .5s ease forwards;">
        <div id="podcast-scroller" class="podcast-scroller">
            <div class="podcast-tile clickable">
                <div class="podcast-item">
                    <i class="fa-solid fa-circle-play"></i>
                    <div class="podcast-info">
                        <h4>Cracking the PM Interview</h4>
                        <p>with Google's Head of Product</p>
                    </div>
                </div>
            </div>
            <div class="podcast-tile clickable">
                <div class="podcast-item">
                    <i class="fa-solid fa-circle-play"></i>
                    <div class="podcast-info">
                        <h4>Consulting Case Secrets</h4>
                        <p>A deep dive with a McKinsey Partner</p>
                    </div>
                </div>
            </div>
            <div class="podcast-tile clickable">
                <div class="podcast-item">
                    <i class="fa-solid fa-circle-play"></i>
                    <div class="podcast-info">
                        <h4>The Art of Negotiation</h4>
                        <p>Learn to negotiate your salary like a pro.</p>
                    </div>
                </div>
            </div>
        </div>
        <div id="podcast-dots" class="scroll-dots"></div>
      </div>

      <div class="section-title" style="animation-delay: 1.55s">
        <h2><i class="fa-solid fa-users-line"></i> Community Hub</h2>
      </div>
      <div class="list-card clickable" style="animation-delay: 1.6s">
          <div class="podcast-item">
              <i class="fa-solid fa-puzzle-piece"></i>
              <div class="podcast-info">
                  <h4>Join the Consulting Prep Group</h4>
                  <p>Practice cases and guesstimates with peers.</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>
      <div class="list-card clickable" style="animation-delay: 1.65s">
          <div class="podcast-item">
              <i class="fa-brands fa-slack"></i>
              <div class="podcast-info">
                  <h4>Product Management Circle</h4>
                  <p>Discuss PM concepts, interview questions, and more.</p>
              </div>
          </div>
          <div class="arrow-icon"><i class="fa-solid fa-chevron-right"></i></div>
      </div>

    </div>

    <!-- Hotbar Footer -->
    <footer class="hotbar">
        <div class="hotbar-content">
            <a href="#" class="nav-item active clickable" aria-label="Home">
                <i class="fa-solid fa-house-chimney"></i>
            </a>
            <a href="#" class="nav-item clickable" aria-label="Schedule">
                <i class="fa-solid fa-calendar-check"></i>
            </a>
            <a href="#" class="nav-item clickable" aria-label="Mentors">
                <i class="fa-solid fa-user-group"></i>
            </a>
            <a href="#" class="nav-item clickable" aria-label="Insights">
                <i class="fa-solid fa-chart-pie"></i>
            </a>
        </div>
    </footer>

    <!-- Coming Soon Popup -->
    <div id="popup" class="popup-overlay">
        <div class="popup-content">
            <h3>🚀 Coming Soon!</h3>
            <p>This feature is under construction. We're working hard to bring it to you.</p>
            <button id="close-popup" class="btn btn-primary">Got it</button>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const themeToggle = document.getElementById('theme-toggle');
            const body = document.body;
            const themeIcon = themeToggle.querySelector('i');

            themeToggle.addEventListener('click', () => {
                body.classList.toggle('dark-theme');
                if (body.classList.contains('dark-theme')) {
                    themeIcon.classList.remove('fa-moon');
                    themeIcon.classList.add('fa-sun');
                } else {
                    themeIcon.classList.remove('fa-sun');
                    themeIcon.classList.add('fa-moon');
                }
            });

            const progressCircle = document.getElementById('progress-circle');
            const progressText = document.getElementById('progress-text');
            
            if (progressCircle && progressText) {
                const finalProgress = 78;
                const radius = progressCircle.r.baseVal.value;
                const circumference = 2 * Math.PI * radius;
                
                const offset = circumference - (finalProgress / 100) * circumference;

                progressCircle.style.strokeDasharray = circumference;
                progressCircle.style.strokeDashoffset = circumference;
                
                setTimeout(() => {
                    progressCircle.style.strokeDashoffset = offset;
                    animateValue(progressText, 0, finalProgress, 800);
                }, 300);
            }

            function animateValue(obj, start, end, duration) {
                let startTimestamp = null;
                const step = (timestamp) => {
                    if (!startTimestamp) startTimestamp = timestamp;
                    const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                    obj.innerHTML = Math.floor(progress * (end - start) + start) + "%";
                    if (progress < 1) {
                        window.requestAnimationFrame(step);
                    }
                };
                window.requestAnimationFrame(step);
            }

            // Podcast Auto-Scroller
            const scroller = document.getElementById('podcast-scroller');
            const dotsContainer = document.getElementById('podcast-dots');
            let autoScrollInterval;

            if (scroller && dotsContainer) {
                const podcasts = scroller.querySelectorAll('.podcast-tile');
                podcasts.forEach(() => {
                    const dot = document.createElement('div');
                    dot.classList.add('dot');
                    dotsContainer.appendChild(dot);
                });

                const dots = dotsContainer.querySelectorAll('.dot');
                if (dots.length > 0) dots[0].classList.add('active');
                
                let currentIndex = 0;

                function updateDots() {
                    const itemWidth = podcasts[0].offsetWidth + 12; // 12 is the gap
                    const activeIndex = Math.round(scroller.scrollLeft / itemWidth);
                    dots.forEach((dot, index) => {
                        dot.classList.toggle('active', index === activeIndex);
                    });
                }
                
                function startAutoScroll() {
                    autoScrollInterval = setInterval(() => {
                        currentIndex = (currentIndex + 1) % podcasts.length;
                        const itemWidth = podcasts[currentIndex].offsetWidth + 12;
                        scroller.scrollTo({ left: currentIndex * itemWidth });
                    }, 3000); // Change slide every 3 seconds
                }

                function stopAutoScroll() {
                    clearInterval(autoScrollInterval);
                }

                scroller.addEventListener('scroll', updateDots);
                scroller.addEventListener('mouseenter', stopAutoScroll);
                scroller.addEventListener('mouseleave', startAutoScroll);
                
                startAutoScroll();
            }

            // Popup functionality
            const popup = document.getElementById('popup');
            const closePopupButton = document.getElementById('close-popup');
            const clickableElements = document.querySelectorAll('.clickable');

            function showPopup(e) {
                e.preventDefault();
                e.stopPropagation();
                popup.classList.add('visible');
            }

            function hidePopup() {
                popup.classList.remove('visible');
            }

            clickableElements.forEach(el => {
                if (el.id !== 'theme-toggle') {
                    el.addEventListener('click', showPopup);
                }
            });

            closePopupButton.addEventListener('click', hidePopup);
            popup.addEventListener('click', (e) => {
                if (e.target === popup) {
                    hidePopup();
                }
            });
        });
    </script>
</body>
</html>

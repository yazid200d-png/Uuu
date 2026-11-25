<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>تيك توك | بث مباشر + منشورات</title>
  <!-- Font Awesome 6 (مجاني) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    }
    body {
      background: #0f0f0f;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }
    .app-container {
      max-width: 420px;
      width: 100%;
      height: 780px;
      background: #1a1a1a;
      border-radius: 32px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.8);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      position: relative;
      margin: 10px;
    }

    /* HEADER */
    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 18px;
      background: #121212;
      border-bottom: 1px solid #2a2a2a;
    }
    .header h1 {
      font-size: 20px;
      font-weight: 700;
      background: linear-gradient(135deg, #ff0050, #00f2ea);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .header-icons {
      display: flex;
      gap: 16px;
      font-size: 20px;
      color: #eee;
    }
    .header-icons i {
      cursor: pointer;
      transition: 0.2s;
    }
    .header-icons i:hover {
      color: #ff0050;
    }

    /* محتوى الفيديو (القسم الرئيسي) */
    .video-section {
      flex: 1;
      background: #0a0a0a;
      position: relative;
      overflow-y: auto;
      scroll-behavior: smooth;
      padding-bottom: 10px;
    }
    .video-card {
      position: relative;
      background: #1e1e1e;
      margin: 8px 12px;
      border-radius: 24px;
      overflow: hidden;
      box-shadow: 0 8px 20px rgba(0,0,0,0.6);
      aspect-ratio: 9 / 16;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
    }
    /* mock فيديو */
    .video-placeholder {
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 30% 30%, #3a2a3a, #0a0a0a);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 40px;
      color: #555;
    }
    .video-placeholder i {
      opacity: 0.3;
    }
    .video-overlay {
      position: relative;
      z-index: 2;
      padding: 16px 14px;
      background: linear-gradient(transparent, rgba(0,0,0,0.7) 70%);
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .video-user {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .video-user img {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      border: 2px solid #ff0050;
      object-fit: cover;
    }
    .video-user span {
      font-weight: 600;
      font-size: 16px;
    }
    .video-caption {
      font-size: 14px;
      opacity: 0.9;
      margin-bottom: 4px;
    }
    .video-actions {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .action-icons {
      display: flex;
      gap: 20px;
      font-size: 22px;
    }
    .action-icons i {
      cursor: pointer;
      transition: 0.2s;
    }
    .action-icons i:hover {
      color: #ff0050;
      transform: scale(1.1);
    }
    .comment-badge {
      background: #2a2a2a;
      padding: 4px 12px;
      border-radius: 40px;
      font-size: 13px;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    /* شريط التنقل السفلي */
    .bottom-nav {
      display: flex;
      justify-content: space-around;
      align-items: center;
      padding: 8px 10px 12px;
      background: #121212;
      border-top: 1px solid #2a2a2a;
      font-size: 22px;
      color: #aaa;
    }
    .bottom-nav i {
      cursor: pointer;
      transition: 0.2s;
    }
    .bottom-nav i.active {
      color: #ff0050;
    }
    .bottom-nav i:hover {
      color: #fff;
    }
    .nav-live {
      background: #ff0050;
      padding: 8px 18px;
      border-radius: 40px;
      color: #fff !important;
      font-size: 16px;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .nav-live i {
      color: #fff !important;
      font-size: 18px;
    }

    /* أقسام منبثقة (إعدادات، بث، تعليق، نشر) */
    .popup-panel {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: #1c1c1c;
      border-top-left-radius: 28px;
      border-top-right-radius: 28px;
      padding: 22px 18px 30px;
      z-index: 99;
      box-shadow: 0 -10px 30px rgba(0,0,0,0.8);
      transform: translateY(100%);
      transition: transform 0.3s ease;
      max-height: 75vh;
      overflow-y: auto;
      border: 1px solid #333;
    }
    .popup-panel.open {
      transform: translateY(0);
    }
    .popup-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 16px;
      font-size: 20px;
      font-weight: 600;
      border-bottom: 1px solid #333;
      padding-bottom: 12px;
    }
    .popup-header i {
      cursor: pointer;
      color: #ff0050;
    }
    .settings-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }
    .settings-item {
      background: #2a2a2a;
      padding: 12px 8px;
      border-radius: 14px;
      text-align: center;
      font-size: 14px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      cursor: pointer;
    }
    .settings-item i {
      font-size: 22px;
      color: #00f2ea;
    }
    .settings-item.active {
      border: 2px solid #ff0050;
    }
    .btn-live {
      background: #ff0050;
      border: none;
      color: #fff;
      padding: 12px;
      border-radius: 60px;
      font-size: 18px;
      font-weight: 700;
      width: 100%;
      margin-top: 10px;
      cursor: pointer;
    }
    .comment-box {
      display: flex;
      gap: 10px;
      margin-top: 10px;
    }
    .comment-box input {
      flex: 1;
      padding: 12px;
      border-radius: 40px;
      border: none;
      background: #2a2a2a;
      color: #fff;
      outline: none;
    }
    .comment-box button {
      background: #ff0050;
      border: none;
      color: #fff;
      padding: 0 20px;
      border-radius: 40px;
      font-weight: 600;
    }
    .coin-display {
      background: #2a2a2a;
      padding: 8px 14px;
      border-radius: 40px;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 16px;
      margin: 8px 0;
    }
    .upload-options {
      display: flex;
      gap: 20px;
      justify-content: center;
      margin: 16px 0;
      flex-wrap: wrap;
    }
    .upload-options label {
      background: #2a2a2a;
      padding: 10px 22px;
      border-radius: 40px;
      display: flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
    }
    .upload-options input {
      display: none;
    }

    /* زر إغلاق عام */
    .close-btn {
      color: #aaa;
      font-size: 24px;
      cursor: pointer;
    }

    /* تحسينات للشاشات الصغيرة */
    @media (max-width: 480px) {
      .app-container {
        height: 100vh;
        border-radius: 0;
        margin: 0;
      }
    }
  </style>
</head>
<body>

<div class="app-container" id="appContainer">

  <!-- HEADER -->
  <div class="header">
    <h1><i class="fab fa-tiktok"></i> تيك توك</h1>
    <div class="header-icons">
      <i class="fas fa-search"></i>
      <i class="fas fa-cog" onclick="togglePanel('settingsPanel')"></i>
    </div>
  </div>

  <!-- قسم الفيديوهات (mock) -->
  <div class="video-section" id="videoSection">
    <!-- بطاقة فيديو 1 -->
    <div class="video-card">
      <div class="video-placeholder"><i class="fas fa-play-circle"></i></div>
      <div class="video-overlay">
        <div class="video-user">
          <img src="https://i.pravatar.cc/60?img=11" alt="user">
          <span>@ahmed_live</span>
        </div>
        <div class="video-caption">🎵 أغنية جديدة #تحدي</div>
        <div class="video-actions">
          <div class="action-icons">
            <i class="fas fa-heart"></i>
            <i class="fas fa-comment" onclick="togglePanel('commentPanel')"></i>
            <i class="fas fa-share"></i>
          </div>
          <div class="comment-badge">
            <i class="fas fa-comment"></i> 24
          </div>
        </div>
      </div>
    </div>

    <!-- بطاقة فيديو 2 -->
    <div class="video-card">
      <div class="video-placeholder"><i class="fas fa-video"></i></div>
      <div class="video-overlay">
        <div class="video-user">
          <img src="https://i.pravatar.cc/60?img=25" alt="user">
          <span>@sara_art</span>
        </div>
        <div class="video-caption">✨ رسم ثلاثي الأبعاد</div>
        <div class="video-actions">
          <div class="action-icons">
            <i class="fas fa-heart"></i>
            <i class="fas fa-comment" onclick="togglePanel('commentPanel')"></i>
            <i class="fas fa-share"></i>
          </div>
          <div class="comment-badge">
            <i class="fas fa-comment"></i> 12
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- شريط سفلي -->
  <div class="bottom-nav">
    <i class="fas fa-home active"></i>
    <i class="fas fa-plus-circle" onclick="togglePanel('uploadPanel')"></i>
    <div class="nav-live" onclick="togglePanel('livePanel')">
      <i class="fas fa-broadcast-tower"></i> بث مباشر
    </div>
    <i class="fas fa-coins" onclick="togglePanel('coinsPanel')"></i>
    <i class="fas fa-user"></i>
  </div>

  <!-- ========== PANELS ========== -->

  <!-- لوحة الإعدادات -->
  <div class="popup-panel" id="settingsPanel">
    <div class="popup-header">
      <span><i class="fas fa-cog"></i> الإعدادات</span>
      <i class="fas fa-times close-btn" onclick="togglePanel('settingsPanel')"></i>
    </div>
    <div class="settings-grid">
      <div class="settings-item active"><i class="fas fa-moon"></i> الوضع الليلي</div>
      <div class="settings-item"><i class="fas fa-globe"></i> اللغة</div>
      <div class="settings-item"><i class="fas fa-lock"></i> الخصوصية</div>
      <div class="settings-item"><i class="fas fa-download"></i> جودة التحميل</div>
      <div class="settings-item"><i class="fas fa-bell"></i> الإشعارات</div>
      <div class="settings-item"><i class="fas fa-music"></i> الصوت</div>
    </div>
    <div style="margin-top:12px; background:#2a2a2a; padding:10px; border-radius:40px; text-align:center; font-size:14px;">
      <i class="fas fa-check-circle" style="color:#00f2ea;"></i> جميع الإعدادات مفعلة
    </div>
    <button class="btn-live" style="background:#333; color:#fff;" onclick="togglePanel('settingsPanel')">تطبيق</button>
  </div>

  <!-- لوحة التعليق -->
  <div class="popup-panel" id="commentPanel">
    <div class="popup-header">
      <span><i class="fas fa-comment"></i> التعليقات</span>
      <i class="fas fa-times close-btn" onclick="togglePanel('commentPanel')"></i>
    </div>
    <div style="background:#222; padding:8px 12px; border-radius:20px; margin-bottom:12px;">
      <p style="font-size:14px;"><i class="fas fa-user-circle"></i> @user1: فيديو رائع!</p>
      <p style="font-size:14px;"><i class="fas fa-user-circle"></i> @tiktoker: ❤️🔥</p>
    </div>
    <div class="comment-box">
      <input type="text" placeholder="اكتب تعليقاً...">
      <button><i class="fas fa-paper-plane"></i></button>
    </div>
  </div>

  <!-- لوحة البث المباشر -->
  <div class="popup-panel" id="livePanel">
    <div class="popup-header">
      <span><i class="fas fa-broadcast-tower" style="color:#ff0050;"></i> بث مباشر</span>
      <i class="fas fa-times close-btn" onclick="togglePanel('livePanel')"></i>
    </div>
    <div style="background:#0f0f0f; border-radius:24px; padding:20px; text-align:center; margin-bottom:12px; border:1px solid #ff0050;">
      <i class="fas fa-circle" style="color:#ff0050; animation: blink 1s infinite;"></i>
      <p style="margin-top:6px;">أنت على الهواء الآن</p>
      <div style="background:#222; padding:10px; border-radius:40px; margin:8px 0;">
        <i class="fas fa-user"></i> 45 مشاهد
      </div>
    </div>
    <button class="btn-live" onclick="alert('⏺️ بدء البث المباشر... (محاكاة)')">بدء البث</button>
    <div style="margin-top:12px; display:flex; gap:10px; justify-content:center;">
      <i class="fas fa-microphone" style="background:#333; padding:10px; border-radius:50%;"></i>
      <i class="fas fa-camera" style="background:#333; padding:10px; border-radius:50%;"></i>
      <i class="fas fa-filter" style="background:#333; padding:10px; border-radius:50%;"></i>
    </div>
  </div>

  <!-- لوحة العملات -->
  <div class="popup-panel" id="coinsPanel">
    <div class="popup-header">
      <span><i class="fas fa-coins" style="color:#ffd700;"></i> العملات</span>
      <i class="fas fa-times close-btn" onclick="togglePanel('coinsPanel')"></i>
    </div>
    <div class="coin-display"><i class="fas fa-coins" style="color:#ffd700;"></i> 2,450 عملة</div>
    <div style="display:flex; gap:10px; flex-wrap:wrap; margin:14px 0;">
      <div style="background:#2a2a2a; padding:8px 16px; border-radius:40px;">💎 100 = 1$</div>
      <div style="background:#2a2a2a; padding:8px 16px; border-radius:40px;">🎁 هدايا</div>
    </div>
    <button class="btn-live" style="background:#ffd700; color:#000;" onclick="alert('تم شحن 500 عملة (محاكاة)')">شحن عملات</button>
  </div>

  <!-- لوحة نشر / تحميل -->
  <div class="popup-panel" id="uploadPanel">
    <div class="popup-header">
      <span><i class="fas fa-upload"></i> نشر محتوى</span>
      <i class="fas fa-times close-btn" onclick="togglePanel('uploadPanel')"></i>
    </div>
    <div class="upload-options">
      <label><i class="fas fa-video"></i> فيديو <input type="file" accept="video/*"></label>
      <label><i class="fas fa-image"></i> صورة <input type="file" accept="image/*"></label>
      <label><i class="fas fa-music"></i> أغنية <input type="file" accept="audio/*"></label>
    </div>
    <div style="background:#2a2a2a; padding:10px; border-radius:20px; margin:8px 0;">
      <i class="fas fa-music" style="color:#00f2ea;"></i> إضافة أغنية للمنشور: <input type="text" placeholder="رابط الأغنية أو اسم" style="background:#111; border:none; padding:6px; border-radius:20px; width:70%; color:#fff;">
    </div>
    <button class="btn-live" onclick="alert('✅ تم النشر (محاكاة)')"><i class="fas fa-check"></i> نشر الآن</button>
  </div>

</div>

<script>
  // دالة toggle لكل اللوحات
  function togglePanel(panelId) {
    const panel = document.getElementById(panelId);
    if (!panel) return;
    // إغلاق جميع اللوحات الأخرى
    const allPanels = document.querySelectorAll('.popup-panel');
    allPanels.forEach(p => {
      if (p.id !== panelId) {
        p.classList.remove('open');
      }
    });
    // تبديل اللوحة المطلوبة
    panel.classList.toggle('open');
  }

  // إغلاق عند الضغط خارج اللوحة (اختياري)
  document.addEventListener('click', function(e) {
    const app = document.getElementById('appContainer');
    const panels = document.querySelectorAll('.popup-panel');
    panels.forEach(panel => {
      if (panel.classList.contains('open')) {
        // إذا كان الضغط خارج اللوحة وخارج الأزرار التي تفتحها
        if (!panel.contains(e.target) && !e.target.closest('.bottom-nav') && !e.target.closest('.header-icons') && !e.target.closest('.action-icons') && !e.target.closest('.nav-live')) {
          panel.classList.remove('open');
        }
      }
    });
  });

  // تفعيل الإعدادات (محاكاة)
  document.querySelectorAll('.settings-item').forEach(item => {
    item.addEventListener('click', function() {
      this.classList.toggle('active');
    });
  });

  // محاكاة تفاعل الأيقونات
  document.querySelectorAll('.action-icons i.fa-heart').forEach(heart => {
    heart.addEventListener('click', function() {
      this.style.color = this.style.color === 'red' ? '' : 'red';
    });
  });

  // تنبيه للبث المباشر من الناف السفلي
  document.querySelector('.nav-live')?.addEventListener('click', function(e) {
    // تم التعامل معه عبر onclick في html
  });

  console.log('✅ تطبيق تيك توك جاهز - جميع الميزات محاكاة');
</script>

<!-- مؤشر وميض للبث -->
<style>
  @keyframes blink {
    0% { opacity: 1; }
    50% { opacity: 0.2; }
    100% { opacity: 1; }
  }
</style>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Stratum — Kenya's trade &amp; discovery layer</title>
<style>
  :root{
    --bg:#12151C;
    --surface:#181C24;
    --surface-2:#1E232C;
    --line:#2A2F3A;
    --text:#EDEDE3;
    --text-dim:#9AA0AC;
    --accent:#D4A72C;
    --accent-ink:#1B1400;
    --manufacturer:#C97A3E;
    --wholesaler:#3E8E7E;
    --retailer:#D4A72C;
    --consumer:#6C6FC4;
    --font-display:'Avenir Next','Century Gothic','Futura',sans-serif;
    --font-body:'Inter','Helvetica Neue',Arial,sans-serif;
    --radius:10px;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:var(--font-body);
    line-height:1.5;
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3,h4{font-family:var(--font-display);margin:0;font-weight:700;letter-spacing:-0.01em;}
  a{color:inherit;text-decoration:none;}
  button{font-family:var(--font-body);cursor:pointer;}
  img,svg{display:block;max-width:100%;}
  :focus-visible{outline:2px solid var(--accent);outline-offset:2px;}
  .hidden{display:none !important;}

  /* ---------- Landing ---------- */
  #landing-nav{
    position:sticky;top:0;z-index:50;
    display:flex;align-items:center;justify-content:space-between;
    padding:18px 6vw;background:rgba(18,21,28,0.92);backdrop-filter:blur(6px);
    border-bottom:1px solid var(--line);
  }
  .logo{display:flex;align-items:center;gap:10px;font-size:20px;font-weight:800;font-family:var(--font-display);}
  .logo .mark{width:22px;height:22px;border-radius:3px;overflow:hidden;display:flex;flex-direction:column;}
  .logo .mark span{flex:1;}
  .logo .mark span:nth-child(1){background:var(--manufacturer);}
  .logo .mark span:nth-child(2){background:var(--wholesaler);}
  .logo .mark span:nth-child(3){background:var(--retailer);}
  .logo .mark span:nth-child(4){background:var(--consumer);}
  .nav-links{display:flex;gap:28px;align-items:center;color:var(--text-dim);font-size:15px;}
  .nav-links a:hover{color:var(--text);}
  .btn{
    display:inline-flex;align-items:center;justify-content:center;gap:8px;
    padding:11px 20px;border-radius:8px;border:1px solid transparent;
    font-size:15px;font-weight:600;background:var(--accent);color:var(--accent-ink);
  }
  .btn:hover{filter:brightness(1.08);}
  .btn-ghost{background:transparent;border:1px solid var(--line);color:var(--text);}
  .btn-ghost:hover{border-color:var(--text-dim);}
  .btn-sm{padding:7px 14px;font-size:13px;border-radius:7px;}

  .hero{
    display:grid;grid-template-columns:1.1fr 1fr;gap:48px;
    padding:80px 6vw 60px;align-items:center;max-width:1400px;margin:0 auto;
  }
  .hero h1{font-size:52px;line-height:1.05;}
  .hero p.sub{color:var(--text-dim);font-size:18px;max-width:520px;margin-top:18px;}
  .hero .ctas{display:flex;gap:14px;margin-top:32px;flex-wrap:wrap;}
  .strata-graphic{position:relative;height:380px;border-radius:14px;overflow:hidden;border:1px solid var(--line);}
  .strata-band{position:absolute;left:0;right:0;display:flex;align-items:center;padding:0 24px;font-weight:700;font-family:var(--font-display);color:#111;font-size:15px;}
  .strata-band small{display:block;font-family:var(--font-body);font-weight:500;font-size:12.5px;opacity:.75;margin-top:2px;}
  .band-1{top:0;height:26%;background:var(--manufacturer);color:#2A1300;transform:skewY(-2deg);transform-origin:left;}
  .band-2{top:24%;height:26%;background:var(--wholesaler);color:#04241D;}
  .band-3{top:49%;height:26%;background:var(--retailer);color:#241B00;transform:skewY(1deg);}
  .band-4{top:74%;height:26%;background:var(--consumer);color:#0E0F2E;}

  .role-strip{padding:10px 6vw 90px;max-width:1400px;margin:0 auto;}
  .role-strip h2{font-size:28px;margin-bottom:8px;}
  .role-strip>p{color:var(--text-dim);margin:0 0 34px;max-width:640px;}
  .role-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--line);border:1px solid var(--line);border-radius:12px;overflow:hidden;}
  .role-card{background:var(--surface);padding:26px 22px;min-height:210px;display:flex;flex-direction:column;}
  .role-chip{width:34px;height:6px;border-radius:3px;margin-bottom:16px;}
  .role-card h3{font-size:18px;margin-bottom:10px;}
  .role-card p{color:var(--text-dim);font-size:14px;flex:1;margin:0 0 16px;}
  .role-card button{width:100%;}

  .feature-section{padding:20px 6vw 100px;max-width:1400px;margin:0 auto;}
  .feature-section h2{font-size:28px;margin-bottom:34px;}
  .feature-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:22px;}
  .feature-card{border:1px solid var(--line);border-radius:12px;padding:22px;background:var(--surface);}
  .feature-card h4{font-size:16px;margin-bottom:8px;}
  .feature-card p{color:var(--text-dim);font-size:13.5px;margin:0;}

  footer.landing-footer{border-top:1px solid var(--line);padding:32px 6vw;color:var(--text-dim);font-size:13px;display:flex;justify-content:space-between;}

  @media (max-width:880px){
    .hero{grid-template-columns:1fr;padding-top:40px;}
    .hero h1{font-size:38px;}
    .role-grid{grid-template-columns:1fr 1fr;}
    .feature-grid{grid-template-columns:1fr;}
    .nav-links{display:none;}
  }

  /* ---------- App shell ---------- */
  #app{display:none;height:100vh;}
  #app.active{display:flex;}
  .app-sidebar{
    width:230px;flex-shrink:0;border-right:1px solid var(--line);
    display:flex;flex-direction:column;padding:20px 14px;background:var(--surface);
  }
  .app-sidebar .logo{padding:6px 10px 22px;font-size:17px;}
  .side-link{
    display:flex;align-items:center;gap:12px;padding:11px 12px;border-radius:8px;
    color:var(--text-dim);font-size:14.5px;font-weight:600;margin-bottom:2px;
  }
  .side-link .ic{width:18px;height:18px;flex-shrink:0;}
  .side-link:hover{background:var(--surface-2);color:var(--text);}
  .side-link.active{background:var(--surface-2);color:var(--text);box-shadow:inset 3px 0 0 var(--accent);}
  .side-sep{height:1px;background:var(--line);margin:14px 4px;}
  .side-role-badge{
    margin:auto 4px 0;padding:12px;border-radius:10px;background:var(--surface-2);
    border:1px solid var(--line);font-size:12.5px;
  }
  .side-role-badge .rname{font-weight:700;font-size:13.5px;margin-bottom:2px;}
  .role-dot{display:inline-block;width:8px;height:8px;border-radius:50%;margin-right:6px;}
  .switch-role-btn{width:100%;margin-top:8px;}

  .app-main{flex:1;overflow-y:auto;position:relative;}
  .topbar{
    position:sticky;top:0;z-index:20;display:flex;align-items:center;justify-content:space-between;
    padding:14px 26px;border-bottom:1px solid var(--line);background:rgba(18,21,28,0.9);backdrop-filter:blur(6px);
  }
  .topbar h2{font-size:19px;}
  .topbar .wallet{font-size:13px;color:var(--text-dim);background:var(--surface-2);padding:8px 12px;border-radius:8px;border:1px solid var(--line);}
  .view{padding:26px;max-width:1000px;margin:0 auto;}
  .view.wide{max-width:1200px;}

  /* Feed / posts */
  .post{border:1px solid var(--line);border-radius:12px;margin-bottom:20px;overflow:hidden;background:var(--surface);}
  .post-head{display:flex;align-items:center;gap:10px;padding:14px 16px;}
  .avatar{width:38px;height:38px;border-radius:50%;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:14px;color:#111;}
  .post-head .who{flex:1;}
  .post-head .name{font-weight:700;font-size:14px;}
  .post-head .meta{font-size:12px;color:var(--text-dim);}
  .sponsored-tag{font-size:11px;color:var(--text-dim);border:1px solid var(--line);border-radius:5px;padding:2px 7px;}
  .follow-btn{font-size:12.5px;padding:6px 12px;border-radius:7px;border:1px solid var(--accent);color:var(--accent);background:transparent;}
  .follow-btn.following{border-color:var(--line);color:var(--text-dim);}
  .video-box{
    height:340px;position:relative;display:flex;align-items:center;justify-content:center;
    color:rgba(255,255,255,.9);
  }
  .video-box .play{width:56px;height:56px;border-radius:50%;background:rgba(0,0,0,.35);display:flex;align-items:center;justify-content:center;}
  .video-box .play::after{content:'';border-left:16px solid #fff;border-top:10px solid transparent;border-bottom:10px solid transparent;margin-left:3px;}
  .video-box .dur{position:absolute;bottom:10px;right:12px;font-size:11.5px;background:rgba(0,0,0,.5);padding:2px 7px;border-radius:5px;}
  .post-caption{padding:12px 16px 4px;font-size:14px;}
  .post-caption b{font-weight:700;}
  .post-actions{display:flex;gap:6px;padding:8px 10px 14px;flex-wrap:wrap;}
  .pa-btn{
    display:flex;align-items:center;gap:6px;background:transparent;border:none;color:var(--text-dim);
    font-size:13px;padding:8px 10px;border-radius:7px;
  }
  .pa-btn:hover{background:var(--surface-2);color:var(--text);}
  .pa-btn.active{color:var(--accent);}
  .pa-btn svg{width:17px;height:17px;}
  .comments-box{border-top:1px solid var(--line);padding:12px 16px;}
  .comment-row{display:flex;gap:8px;margin-bottom:8px;font-size:13px;}
  .comment-row b{font-weight:700;}
  .comment-input-row{display:flex;gap:8px;margin-top:8px;}
  .comment-input-row input{
    flex:1;background:var(--surface-2);border:1px solid var(--line);color:var(--text);
    border-radius:20px;padding:8px 14px;font-size:13px;
  }
  .comment-input-row button{background:var(--accent);color:var(--accent-ink);border:none;border-radius:16px;padding:8px 14px;font-size:12.5px;font-weight:600;}

  /* generic UI bits */
  .card{border:1px solid var(--line);border-radius:12px;background:var(--surface);padding:18px;margin-bottom:16px;}
  .row-between{display:flex;align-items:center;justify-content:space-between;}
  .grid-2{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
  .grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:16px;}
  label.field{display:block;font-size:12.5px;color:var(--text-dim);margin-bottom:6px;font-weight:600;}
  input,select,textarea{
    width:100%;background:var(--surface-2);border:1px solid var(--line);color:var(--text);
    border-radius:8px;padding:10px 12px;font-size:14px;font-family:var(--font-body);
  }
  textarea{resize:vertical;}
  .field-wrap{margin-bottom:14px;}
  table{width:100%;border-collapse:collapse;font-size:13.5px;}
  th,td{text-align:left;padding:10px 8px;border-bottom:1px solid var(--line);}
  th{color:var(--text-dim);font-weight:600;font-size:12px;}
  .pill{display:inline-block;font-size:11.5px;padding:3px 9px;border-radius:20px;font-weight:600;}
  .pill.pending{background:#3a2f10;color:#e0b73f;}
  .pill.fulfilled{background:#12332a;color:#59c9a9;}
  .pill.active{background:#122e14;color:#5fd66f;}
  .pill.paused{background:#332222;color:#e08a8a;}
  .thumb{width:100%;aspect-ratio:4/3;border-radius:8px;margin-bottom:10px;}
  .empty-state{text-align:center;padding:60px 20px;color:var(--text-dim);}
  .empty-state h3{color:var(--text);margin-bottom:8px;font-size:17px;}
  .tabs{display:flex;gap:6px;border-bottom:1px solid var(--line);margin-bottom:20px;flex-wrap:wrap;}
  .tab-btn{padding:10px 4px;margin-right:16px;font-size:14px;font-weight:600;color:var(--text-dim);border-bottom:2px solid transparent;background:none;border-top:none;border-left:none;border-right:none;}
  .tab-btn.active{color:var(--text);border-bottom-color:var(--accent);}
  .status-row{display:flex;gap:12px;overflow-x:auto;padding-bottom:6px;margin-bottom:18px;}
  .status-bubble{flex-shrink:0;width:66px;text-align:center;font-size:11px;color:var(--text-dim);}
  .status-bubble .ring{width:58px;height:58px;border-radius:50%;padding:2px;border:2px solid var(--accent);margin:0 auto 5px;display:flex;align-items:center;justify-content:center;}
  .status-bubble .ring .avatar{width:100%;height:100%;}
  .toast{
    position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:var(--surface-2);
    border:1px solid var(--line);color:var(--text);padding:12px 20px;border-radius:10px;font-size:13.5px;
    z-index:200;opacity:0;transition:opacity .25s ease, transform .25s ease;pointer-events:none;
  }
  .toast.show{opacity:1;}
  .conv-list-item{display:flex;gap:10px;padding:12px;border-radius:8px;align-items:center;}
  .conv-list-item:hover{background:var(--surface-2);cursor:pointer;}
  .thread-msg{max-width:70%;padding:9px 13px;border-radius:12px;margin-bottom:8px;font-size:13.5px;}
  .thread-msg.me{background:var(--accent);color:var(--accent-ink);margin-left:auto;}
  .thread-msg.them{background:var(--surface-2);}
  .modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.55);display:flex;align-items:center;justify-content:center;z-index:300;padding:20px;}
  .modal-box{background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:24px;max-width:440px;width:100%;max-height:85vh;overflow-y:auto;}

  @media (max-width:760px){
    .app-sidebar{position:fixed;bottom:0;left:0;right:0;top:auto;width:100%;height:64px;flex-direction:row;
      border-right:none;border-top:1px solid var(--line);padding:8px 6px;z-index:60;align-items:center;overflow-x:auto;}
    .app-sidebar .logo,.side-sep,.side-role-badge{display:none;}
    .side-link{flex-direction:column;gap:3px;font-size:10px;padding:6px 10px;white-space:nowrap;}
    .app-main{padding-bottom:70px;}
    .view{padding:16px;}
    .grid-2,.grid-3{grid-template-columns:1fr;}
    .topbar{padding:12px 16px;}
  }
</style>
</head>
<body>

<!-- ============================= LANDING ============================= -->
<div id="landing">
  <nav id="landing-nav">
    <div class="logo"><span class="mark"><span></span><span></span><span></span><span></span></span> Stratum</div>
    <div class="nav-links">
      <a href="#roles-anchor">For your business</a>
      <a href="#features-anchor">Product</a>
      <a href="#" id="nav-login">Open Stratum</a>
    </div>
    <button class="btn btn-sm" id="nav-get-started">Get started</button>
  </nav>

  <section class="hero">
    <div>
      <h1>Kenya's trade, laid out in layers.</h1>
      <p class="sub">Stratum connects manufacturers, wholesalers, retailers and everyday shoppers on one platform — bulk orders at agreed prices, a video feed to discover goods and services nationwide, and advertising that funds all of it.</p>
      <div class="ctas">
        <button class="btn" id="hero-get-started">Get started free</button>
        <button class="btn btn-ghost" id="hero-see-demo">See how it works</button>
      </div>
    </div>
    <div class="strata-graphic">
      <div class="strata-band band-1">Manufacturer<small>Makes goods, sets wholesale price, runs ads</small></div>
      <div class="strata-band band-2">Wholesaler<small>Buys in bulk, restocks retailers</small></div>
      <div class="strata-band band-3">Retailer<small>Stocks shelves, sells to shoppers</small></div>
      <div class="strata-band band-4">Consumer<small>Discovers and buys on the feed</small></div>
    </div>
  </section>

  <section class="role-strip" id="roles-anchor">
    <h2>One layer at a time</h2>
    <p>Every account sits in one stratum of the trade chain, with tools built for what that layer actually does.</p>
    <div class="role-grid">
      <div class="role-card">
        <div class="role-chip" style="background:var(--manufacturer)"></div>
        <h3>Manufacturer</h3>
        <p>List products, set wholesale pricing and minimum order quantities, message retailers and wholesalers directly, and run paid ad campaigns into the consumer feed.</p>
        <button class="btn btn-ghost btn-sm enter-role" data-role="manufacturer">Enter as manufacturer</button>
      </div>
      <div class="role-card">
        <div class="role-chip" style="background:var(--wholesaler)"></div>
        <h3>Wholesaler</h3>
        <p>Buy directly from manufacturers at set bulk prices, hold stock, and resell to retailers across the country with your own markup.</p>
        <button class="btn btn-ghost btn-sm enter-role" data-role="wholesaler">Enter as wholesaler</button>
      </div>
      <div class="role-card">
        <div class="role-chip" style="background:var(--retailer)"></div>
        <h3>Retailer</h3>
        <p>Source stock from wholesalers or manufacturers, negotiate by message, and reach shoppers browsing the discovery feed.</p>
        <button class="btn btn-ghost btn-sm enter-role" data-role="retailer">Enter as retailer</button>
      </div>
      <div class="role-card">
        <div class="role-chip" style="background:var(--consumer)"></div>
        <h3>Consumer</h3>
        <p>Scroll a video feed of goods and services from all over Kenya. Like, comment, save, share, download and follow the sellers you trust.</p>
        <button class="btn btn-ghost btn-sm enter-role" data-role="consumer">Enter as consumer</button>
      </div>
    </div>
  </section>

  <section class="feature-section" id="features-anchor">
    <h2>Built into the platform</h2>
    <div class="feature-grid">
      <div class="feature-card"><h4>Video discovery feed</h4><p>A vertical feed where consumers find goods and services near them, with likes, comments, ratings, saves, downloads, shares and follows.</p></div>
      <div class="feature-card"><h4>Manufacturer ↔ everyone, messaging</h4><p>Manufacturers message consumers, retailers and wholesalers directly from one inbox, without leaving Stratum.</p></div>
      <div class="feature-card"><h4>Bulk ordering at set prices</h4><p>Wholesalers order straight from manufacturer catalogs. Manufacturers confirm and dispatch goods at the price they've set.</p></div>
      <div class="feature-card"><h4>Paid advertising</h4><p>Manufacturers fund campaigns that place sponsored posts in the consumer feed — this is how Stratum makes money.</p></div>
      <div class="feature-card"><h4>Personal &amp; business profiles</h4><p>Every account gets a profile with followers, following, bio and a status board for quick updates.</p></div>
      <div class="feature-card"><h4>Nationwide discovery</h4><p>Browse goods and services by category and county, from Nairobi to Mombasa, Kisumu, Eldoret and beyond.</p></div>
    </div>
  </section>

  <footer class="landing-footer">
    <span>© 2026 Stratum, Kenya</span>
    <span>A demo build — data is stored only in this browser.</span>
  </footer>
</div>

<!-- ============================= APP SHELL ============================= -->
<div id="app">
  <aside class="app-sidebar">
    <div class="logo"><span class="mark"><span></span><span></span><span></span><span></span></span> Stratum</div>
    <a class="side-link" data-view="feed"><span class="ic">🏠</span> Feed</a>
    <a class="side-link" data-view="discover"><span class="ic">🧭</span> Discover</a>
    <a class="side-link" data-view="dashboard"><span class="ic">📦</span> <span id="dash-label">Dashboard</span></a>
    <a class="side-link" data-view="messages"><span class="ic">💬</span> Messages</a>
    <a class="side-link" data-view="saved"><span class="ic">🔖</span> Saved</a>
    <a class="side-link" data-view="profile"><span class="ic">👤</span> Profile</a>
    <div class="side-sep"></div>
    <div class="side-role-badge">
      <div class="rname"><span class="role-dot" id="badge-dot"></span><span id="badge-name"></span></div>
      <div id="badge-role" style="color:var(--text-dim)"></div>
      <button class="btn btn-ghost btn-sm switch-role-btn" id="switch-role-btn">Switch account</button>
    </div>
  </aside>

  <main class="app-main">
    <div class="topbar">
      <h2 id="topbar-title">Feed</h2>
      <div id="topbar-right"></div>
    </div>
    <div class="view wide" id="view-root"></div>
  </main>
</div>

<div class="toast" id="toast"></div>
<div id="modal-root"></div>

<script>
/* ======================================================================
   STRATUM — single-file demo build
   All data lives in localStorage under 'stratum_v1'. This is a working
   front-end prototype: no server, but every interaction is functional
   and persists across reloads in this browser.
   ====================================================================== */

const ROLE_
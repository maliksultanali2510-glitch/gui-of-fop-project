<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Aetbar — Home Worker Platform</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600;700&family=Unbounded:wght@700;900&family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet"/>
<style>
/* ══════════════════════════════════════════════
   AETBAR GUI  ·  Dark Terminal Dashboard
   Font: Unbounded (display) + DM Sans (body)
         + JetBrains Mono (data/code)
   Aesthetic: Cyberpunk-terminal meets
   premium Pakistani fintech
══════════════════════════════════════════════ */
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:    #080c10;
  --bg2:   #0d1219;
  --bg3:   #111820;
  --bg4:   #16202c;
  --line:  #1d2d3e;
  --g:     #00e676;
  --g2:    #00ff88;
  --g-dim: #003d20;
  --g-glow:rgba(0,230,118,.18);
  --amber: #ffb300;
  --red:   #ff3d3d;
  --blue:  #40a9ff;
  --muted: #3d5a6e;
  --dim:   #2a3d4e;
  --text:  #c8dde8;
  --text2: #7a9bae;
  --text3: #3d5a6e;
  --white: #e8f4fa;
  --font-d:'Unbounded',sans-serif;
  --font-b:'DM Sans',sans-serif;
  --font-m:'JetBrains Mono',monospace;
}
html{scroll-behavior:smooth}
body{
  font-family:var(--font-b);
  background:var(--bg);
  color:var(--text);
  min-height:100vh;
  overflow-x:hidden;
}
/* scanline overlay */
body::before{
  content:'';
  position:fixed;inset:0;
  background:repeating-linear-gradient(
    0deg,
    transparent,transparent 2px,
    rgba(0,0,0,.06) 2px,rgba(0,0,0,.06) 4px
  );
  pointer-events:none;z-index:9999;
}

/* ── HEADER ── */
header{
  background:var(--bg2);
  border-bottom:1px solid var(--line);
  padding:0 28px;
  height:62px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  position:sticky;top:0;z-index:100;
}
.logo{display:flex;align-items:center;gap:12px}
.logo-mark{
  width:34px;height:34px;border-radius:8px;
  background:var(--g-dim);border:1.5px solid var(--g);
  display:flex;align-items:center;justify-content:center;
  box-shadow:0 0 12px var(--g-glow);
}
.logo-mark svg{width:18px;height:18px}
.logo-text{
  font-family:var(--font-d);
  font-size:1.1rem;font-weight:900;
  color:var(--white);letter-spacing:-.02em;
}
.logo-text em{color:var(--g);font-style:normal}
.header-right{display:flex;align-items:center;gap:10px}
.live-badge{
  display:flex;align-items:center;gap:6px;
  background:var(--g-dim);border:1px solid var(--g);
  border-radius:20px;padding:3px 10px;
  font-family:var(--font-m);font-size:.7rem;font-weight:600;color:var(--g);
  box-shadow:0 0 8px var(--g-glow);
}
.live-dot{width:6px;height:6px;border-radius:50%;background:var(--g);animation:blink 1.4s ease infinite;box-shadow:0 0 6px var(--g)}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}
.cpp-badge{
  font-family:var(--font-m);font-size:.68rem;font-weight:600;
  background:#1a2332;border:1px solid var(--blue);color:var(--blue);
  padding:3px 9px;border-radius:5px;
}

/* ── NAV ── */
nav{
  background:var(--bg3);
  border-bottom:1px solid var(--line);
  display:flex;gap:2px;padding:6px 20px;
  position:sticky;top:62px;z-index:99;
}
.nav-btn{
  font-family:var(--font-b);
  font-size:.82rem;font-weight:600;
  color:var(--text2);background:transparent;border:none;cursor:pointer;
  padding:7px 16px;border-radius:6px;transition:.15s;
  display:flex;align-items:center;gap:6px;
}
.nav-btn:hover{color:var(--text);background:var(--dim)}
.nav-btn.on{background:var(--g-dim);color:var(--g);border:1px solid rgba(0,230,118,.2)}

/* ── LAYOUT ── */
.shell{padding:20px 24px;max-width:1200px;margin:0 auto}
.page{display:none;animation:fadeUp .25s ease}
.page.on{display:block}
@keyframes fadeUp{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}

/* ── STAT CARDS ── */
.stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:10px;margin-bottom:18px}
.stat-card{
  background:var(--bg3);border:1px solid var(--line);border-radius:10px;
  padding:14px 16px;transition:.18s;cursor:default;position:relative;overflow:hidden;
}
.stat-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--g),transparent);
  transform:scaleX(0);transform-origin:left;transition:.3s;
}
.stat-card:hover{border-color:var(--g);box-shadow:0 0 16px var(--g-glow)}
.stat-card:hover::before{transform:scaleX(1)}
.stat-num{
  font-family:var(--font-d);font-size:1.6rem;font-weight:900;
  color:var(--g);line-height:1;margin-bottom:5px;
}
.stat-lbl{font-size:.72rem;color:var(--text2);font-weight:600;letter-spacing:.04em;text-transform:uppercase}

/* ── CARDS ── */
.card{
  background:var(--bg3);border:1px solid var(--line);
  border-radius:12px;margin-bottom:14px;overflow:hidden;
}
.card-head{
  padding:12px 18px;border-bottom:1px solid var(--line);
  display:flex;align-items:center;justify-content:space-between;
}
.card-title{
  font-family:var(--font-m);font-size:.8rem;font-weight:700;
  color:var(--text2);letter-spacing:.06em;text-transform:uppercase;
  display:flex;align-items:center;gap:8px;
}
.card-title-icon{color:var(--g)}
.card-count{
  font-family:var(--font-m);font-size:.72rem;
  background:var(--bg4);color:var(--text3);
  padding:2px 8px;border-radius:4px;border:1px solid var(--line);
}

/* ── TABLE ── */
.tbl-wrap{overflow-x:auto}
table{width:100%;border-collapse:collapse}
th{
  background:var(--bg);color:var(--text3);
  text-align:left;padding:8px 14px;
  font-family:var(--font-m);font-size:.68rem;
  font-weight:600;letter-spacing:.07em;text-transform:uppercase;
  border-bottom:1px solid var(--line);
}
td{
  padding:10px 14px;font-size:.84rem;color:var(--text);
  border-bottom:1px solid rgba(29,45,62,.6);transition:.12s;
}
tr:hover td{background:var(--bg4)}
tr:last-child td{border-bottom:none}
.mono{font-family:var(--font-m);font-size:.8rem}

/* ── BADGES ── */
.badge{
  display:inline-flex;align-items:center;gap:4px;
  font-family:var(--font-m);font-size:.67rem;font-weight:700;
  padding:2px 8px;border-radius:4px;letter-spacing:.04em;text-transform:uppercase;
}
.b-green{background:rgba(0,230,118,.1);color:var(--g);border:1px solid rgba(0,230,118,.2)}
.b-amber{background:rgba(255,179,0,.1);color:var(--amber);border:1px solid rgba(255,179,0,.2)}
.b-red{background:rgba(255,61,61,.1);color:var(--red);border:1px solid rgba(255,61,61,.2)}
.b-blue{background:rgba(64,169,255,.1);color:var(--blue);border:1px solid rgba(64,169,255,.2)}
.b-dim{background:var(--bg4);color:var(--text2);border:1px solid var(--line)}

/* ── RATING BAR ── */
.rbar{display:flex;align-items:center;gap:6px}
.rbar-track{width:48px;height:4px;background:var(--dim);border-radius:2px;overflow:hidden}
.rbar-fill{height:100%;background:linear-gradient(90deg,var(--amber),var(--g));border-radius:2px}
.rbar-val{font-family:var(--font-m);font-size:.74rem;color:var(--amber)}

/* ── SEARCH ── */
.search-wrap{padding:14px 18px;border-bottom:1px solid var(--line)}
.search-box{
  font-family:var(--font-m);font-size:.83rem;
  background:var(--bg);border:1.5px solid var(--line);
  color:var(--text);padding:8px 14px;border-radius:8px;
  width:100%;max-width:340px;outline:none;transition:.15s;
}
.search-box:focus{border-color:var(--g);box-shadow:0 0 8px var(--g-glow)}
.search-box::placeholder{color:var(--text3)}

/* ── EMPTY ── */
.empty{
  text-align:center;padding:40px;
  font-family:var(--font-m);font-size:.8rem;color:var(--text3);
}

/* ── GRID 2 ── */
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:14px}

/* ── WORKER PROFILE CARD ── */
.wk-row{
  display:flex;align-items:center;gap:12px;
  padding:10px 18px;border-bottom:1px solid rgba(29,45,62,.5);
  transition:.15s;
}
.wk-row:last-child{border-bottom:none}
.wk-row:hover{background:var(--bg4)}
.wk-ava{
  width:40px;height:40px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:1.3rem;flex-shrink:0;
}
.wk-info{flex:1;min-width:0}
.wk-name{font-weight:600;font-size:.88rem;color:var(--white)}
.wk-cat{font-size:.74rem;color:var(--text2);margin-top:1px}
.wk-right{text-align:right;flex-shrink:0}
.wk-rate{font-family:var(--font-m);font-weight:700;font-size:.84rem;color:var(--g)}
.wk-jobs{font-size:.7rem;color:var(--text3);margin-top:2px}

/* ── BOOKING ROW ── */
.bk-row{
  display:flex;align-items:center;justify-content:space-between;
  padding:10px 18px;border-bottom:1px solid rgba(29,45,62,.5);gap:12px;flex-wrap:wrap;
  transition:.15s;
}
.bk-row:hover{background:var(--bg4)}
.bk-row:last-child{border-bottom:none}
.bk-id{font-family:var(--font-m);font-size:.7rem;color:var(--text3)}
.bk-worker{font-weight:600;font-size:.85rem;color:var(--white)}
.bk-meta{font-size:.74rem;color:var(--text2);margin-top:1px}
.bk-amount{font-family:var(--font-m);font-weight:700;color:var(--g);font-size:.85rem}

/* ── ABOUT PAGE ── */
.about-hero{
  background:linear-gradient(135deg,var(--g-dim),rgba(0,0,0,0));
  border:1px solid rgba(0,230,118,.15);border-radius:14px;
  padding:28px;margin-bottom:14px;position:relative;overflow:hidden;
}
.about-hero::before{
  content:'AETBAR';
  position:absolute;right:-10px;top:50%;transform:translateY(-50%);
  font-family:var(--font-d);font-size:8rem;font-weight:900;
  color:rgba(0,230,118,.04);line-height:1;pointer-events:none;
}
.about-title{
  font-family:var(--font-d);font-size:2rem;font-weight:900;
  color:var(--g);letter-spacing:-.04em;margin-bottom:6px;
}
.about-urdu{font-size:1.1rem;color:var(--text2);margin-bottom:14px;font-style:italic}
.about-info p{font-size:.88rem;color:var(--text);line-height:1.7;margin-bottom:.5rem}
.about-info strong{color:var(--white)}
.chips{display:flex;flex-wrap:wrap;gap:6px;padding:14px 18px}
.chip{
  font-family:var(--font-m);font-size:.72rem;font-weight:600;
  background:var(--bg4);border:1px solid var(--line);color:var(--text2);
  padding:4px 10px;border-radius:5px;transition:.15s;
}
.chip:hover{border-color:var(--g);color:var(--g)}

/* ── CREDS TABLE ── */
.cred-table{padding:0 18px 14px}
.cred-item{
  display:flex;align-items:center;justify-content:space-between;
  padding:10px 14px;background:var(--bg);border:1px solid var(--line);
  border-radius:8px;margin-bottom:6px;gap:12px;flex-wrap:wrap;
}
.cred-role{font-family:var(--font-m);font-size:.75rem;color:var(--text2)}
.cred-phone{font-family:var(--font-m);font-size:.82rem;font-weight:700;color:var(--white)}
.cred-pass{font-family:var(--font-m);font-size:.8rem;color:var(--amber)}

/* ── FOOTER ── */
footer{
  border-top:1px solid var(--line);padding:16px 28px;
  display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px;
  font-family:var(--font-m);font-size:.72rem;color:var(--text3);
  background:var(--bg2);margin-top:32px;
}
footer span{color:var(--g)}

/* ── SCROLLBAR ── */
::-webkit-scrollbar{width:4px;height:4px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--dim);border-radius:2px}
::-webkit-scrollbar-thumb:hover{background:var(--muted)}

/* ── LOAD ANIM ── */
.stagger-in{animation:stIn .4s ease both}
@keyframes stIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:none}}

@media(max-width:700px){
  .grid2{grid-template-columns:1fr}
  .stats-row{grid-template-columns:repeat(2,1fr)}
  header{padding:0 14px}
  .logo-text{font-size:.95rem}
}
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">
    <div class="logo-mark">
      <svg viewBox="0 0 24 24" fill="none">
        <path d="M3 9.5L12 3l9 6.5V20a1 1 0 01-1 1H4a1 1 0 01-1-1V9.5z" stroke="#00e676" stroke-width="2" stroke-linejoin="round"/>
        <path d="M9 21V13h6v8" stroke="#00e676" stroke-width="2" stroke-linejoin="round"/>
      </svg>
    </div>
    <span class="logo-text">Aet<em>bar</em></span>
  </div>
  <div class="header-right">
    <div class="live-badge"><div class="live-dot"></div> LIVE DATA</div>
    <div class="cpp-badge">C++17 &bull; FOP Project</div>
  </div>
</header>

<!-- NAV -->
<nav>
  <button class="nav-btn on" onclick="show('dash',this)">
    <svg width="13" height="13" fill="none" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/><rect x="14" y="3" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/><rect x="3" y="14" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/><rect x="14" y="14" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/></svg>
    Dashboard
  </button>
  <button class="nav-btn" onclick="show('workers',this)">
    <svg width="13" height="13" fill="none" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2" stroke="currentColor" stroke-width="2"/><circle cx="9" cy="7" r="4" stroke="currentColor" stroke-width="2"/><path d="M23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75" stroke="currentColor" stroke-width="2"/></svg>
    Workers
  </button>
  <button class="nav-btn" onclick="show('bookings',this)">
    <svg width="13" height="13" fill="none" viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2" stroke="currentColor" stroke-width="2"/><path d="M16 2v4M8 2v4M3 10h18" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
    Bookings
  </button>
  <button class="nav-btn" onclick="show('users',this)">
    <svg width="13" height="13" fill="none" viewBox="0 0 24 24"><circle cx="12" cy="8" r="4" stroke="currentColor" stroke-width="2"/><path d="M4 20c0-4 3.582-7 8-7s8 3 8 7" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
    Users
  </button>
  <button class="nav-btn" onclick="show('about',this)">
    <svg width="13" height="13" fill="none" viewBox="0 0 24 24"><circle cx="12" cy="12" r="9" stroke="currentColor" stroke-width="2"/><path d="M12 8v4m0 4h.01" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
    About
  </button>
</nav>

<!-- ═══ DASHBOARD ═══ -->
<div id="dash" class="page on">
  <div class="shell">
    <div class="stats-row stagger-in" id="stats-row">
      <!-- filled by JS -->
    </div>
    <div class="grid2">
      <!-- Top Workers -->
      <div class="card stagger-in" style="animation-delay:.1s">
        <div class="card-head">
          <div class="card-title"><span class="card-title-icon">▲</span>Top Rated Workers</div>
          <span class="card-count" id="top-workers-count">—</span>
        </div>
        <div id="top-workers-list"></div>
      </div>
      <!-- Recent Bookings -->
      <div class="card stagger-in" style="animation-delay:.18s">
        <div class="card-head">
          <div class="card-title"><span class="card-title-icon">◆</span>Recent Bookings</div>
          <span class="card-count" id="recent-bookings-count">—</span>
        </div>
        <div id="recent-bookings-list"></div>
      </div>
    </div>
    <!-- Revenue breakdown -->
    <div class="card stagger-in" style="animation-delay:.26s">
      <div class="card-head">
        <div class="card-title"><span class="card-title-icon">$</span>Revenue Breakdown</div>
      </div>
      <div id="revenue-breakdown" style="padding:14px 18px;font-family:var(--font-m);font-size:.82rem;color:var(--text2);line-height:2"></div>
    </div>
  </div>
</div>

<!-- ═══ WORKERS ═══ -->
<div id="workers" class="page">
  <div class="shell">
    <div class="card">
      <div class="card-head">
        <div class="card-title"><span class="card-title-icon">▶</span>All Workers</div>
        <span class="card-count" id="workers-count">—</span>
      </div>
      <div class="search-wrap">
        <input class="search-box" id="worker-search" placeholder="Search name or category..." oninput="renderWorkers()"/>
      </div>
      <div class="tbl-wrap">
        <table>
          <thead><tr><th>ID</th><th>Name</th><th>Category</th><th>City</th><th>Rate / Day</th><th>Rating</th><th>Jobs</th><th>Status</th></tr></thead>
          <tbody id="workers-tbody"></tbody>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- ═══ BOOKINGS ═══ -->
<div id="bookings" class="page">
  <div class="shell">
    <div class="card">
      <div class="card-head">
        <div class="card-title"><span class="card-title-icon">◈</span>All Bookings</div>
        <span class="card-count" id="bookings-count">—</span>
      </div>
      <div class="tbl-wrap">
        <table>
          <thead><tr><th>ID</th><th>Worker</th><th>Package</th><th>Amount</th><th>Status</th><th>Payment</th><th>Start</th><th>End</th></tr></thead>
          <tbody id="bookings-tbody"></tbody>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- ═══ USERS ═══ -->
<div id="users" class="page">
  <div class="shell">
    <div class="card">
      <div class="card-head">
        <div class="card-title"><span class="card-title-icon">◉</span>Registered Users</div>
        <span class="card-count" id="users-count">—</span>
      </div>
      <div class="tbl-wrap">
        <table>
          <thead><tr><th>ID</th><th>Name</th><th>Phone</th><th>Role</th><th>Wallet (Rs)</th><th>Joined</th></tr></thead>
          <tbody id="users-tbody"></tbody>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- ═══ ABOUT ═══ -->
<div id="about" class="page">
  <div class="shell">
    <div class="about-hero stagger-in">
      <div class="about-title">AETBAR</div>
      <div class="about-urdu">اعتبار — Trust · Reliability · Pakistan</div>
      <div class="about-info">
        <p><strong>Platform:</strong> Pakistan's first verified home worker hiring platform</p>
        <p><strong>Mission:</strong> Connect CNIC-verified, police-cleared workers with families across Pakistan</p>
        <p><strong>Founder:</strong> Sultan Ali &nbsp;|&nbsp; <strong>Phone:</strong> 0331-5506907 &nbsp;|&nbsp; <strong>Email:</strong> contact@aetbar.pk</p>
        <p><strong>Cities:</strong> Islamabad · Lahore · Karachi · Rawalpindi</p>
      </div>
    </div>

    <div class="grid2">
      <div class="card stagger-in" style="animation-delay:.08s">
        <div class="card-head">
          <div class="card-title"><span class="card-title-icon">{ }</span>C++ Concepts Used</div>
        </div>
        <div class="chips">
          <span class="chip">Structs</span>
          <span class="chip">Enums</span>
          <span class="chip">Arrays</span>
          <span class="chip">Bubble Sort</span>
          <span class="chip">Functions</span>
          <span class="chip">Nested Loops</span>
          <span class="chip">for / while</span>
          <span class="chip">if / else</span>
          <span class="chip">Switch-Case</span>
          <span class="chip">File I/O</span>
          <span class="chip">Structs</span>
          <span class="chip">CSV Parsing</span>
          <span class="chip">string / stoi / stof</span>
          <span class="chip">Error Handling</span>
        </div>
      </div>

      <div class="card stagger-in" style="animation-delay:.14s">
        <div class="card-head">
          <div class="card-title"><span class="card-title-icon">🔑</span>Login Credentials</div>
        </div>
        <div class="cred-table">
          <div class="cred-item">
            <div><div class="cred-role">EMPLOYER</div><div class="cred-phone">03001234567</div></div>
            <div class="cred-pass">Password: 1234</div>
          </div>
          <div class="cred-item">
            <div><div class="cred-role">ADMIN</div><div class="cred-phone">admin</div></div>
            <div class="cred-pass">Password: admin123</div>
          </div>
        </div>
      </div>
    </div>

    <!-- How it works -->
    <div class="card stagger-in" style="animation-delay:.2s">
      <div class="card-head">
        <div class="card-title"><span class="card-title-icon">▷</span>Data Flow</div>
      </div>
      <div style="padding:16px 20px;font-family:var(--font-m);font-size:.78rem;color:var(--text2);line-height:2.2">
        <span style="color:var(--g)">workers.csv</span> ←→ loadWorkers() / saveWorkers() &nbsp;|&nbsp;
        <span style="color:var(--g)">users.csv</span> ←→ loadUsers() / saveUsers() &nbsp;|&nbsp;
        <span style="color:var(--g)">bookings.csv</span> ←→ loadBookings() / saveBookings()<br/>
        Data lives in same directory as <span style="color:var(--amber)">aetbar.exe</span>.
        GUI reads CSV files from the same folder and displays live data.
      </div>
    </div>
  </div>
</div>

<footer>
  <span>AETBAR © 2025 — Sultan Ali &nbsp;|&nbsp; 0331-5506907</span>
  <span>FOP C++ Project &nbsp;·&nbsp; <span>Data from CSV files</span></span>
</footer>

<!-- ═══════════ JAVASCRIPT ═══════════ -->
<script>
/* ─── Default seed data (same as C++ seed()) ─── */
let WW = [
  {id:1,name:"Fatima Khan",   cat:"Maid",        city:"Islamabad",phone:"03119876543",rate:800,  rating:4.9,jobs:87,verified:true, busy:false,date:"25-04-2025"},
  {id:2,name:"Muhammad Ali",  cat:"Cook",        city:"Islamabad",phone:"03211112222",rate:1200, rating:4.8,jobs:63,verified:true, busy:false,date:"25-04-2025"},
  {id:3,name:"Zahid Butt",    cat:"Electrician", city:"Islamabad",phone:"03334445566",rate:2000, rating:4.7,jobs:44,verified:true, busy:true, date:"25-04-2025"},
  {id:4,name:"Rukhsana Naz",  cat:"Clothes",     city:"Islamabad",phone:"03005556677",rate:600,  rating:5.0,jobs:29,verified:true, busy:false,date:"25-04-2025"},
  {id:5,name:"Imran Haider",  cat:"Security",    city:"Islamabad",phone:"03123334444",rate:1500, rating:4.6,jobs:18,verified:true, busy:false,date:"25-04-2025"},
  {id:6,name:"Asif Khan",     cat:"Plumber",     city:"Islamabad",phone:"03007778888",rate:1800, rating:4.5,jobs:32,verified:true, busy:false,date:"25-04-2025"},
];
let UU = [
  {id:1,name:"Ahmed Raza",phone:"03001234567",role:"employer",wallet:5200,date:"25-04-2025"},
  {id:2,name:"Admin",     phone:"admin",      role:"admin",   wallet:0,   date:"25-04-2025"},
];
let BB = [
  {id:1001,uid:1,wid:1,wname:"Fatima Khan",  sdate:"01-04-2025",edate:"07-04-2025",pkg:1,amt:4200, status:1,pay:3},
  {id:1002,uid:1,wid:2,wname:"Muhammad Ali", sdate:"05-04-2025",edate:"05-04-2025",pkg:0,amt:1200, status:2,pay:0},
  {id:1003,uid:1,wid:4,wname:"Rukhsana Naz", sdate:"10-04-2025",edate:"09-05-2025",pkg:2,amt:7656, status:1,pay:1},
  {id:1004,uid:1,wid:5,wname:"Imran Haider", sdate:"15-04-2025",edate:"21-04-2025",pkg:1,amt:5250, status:0,pay:3},
];

const PKG  = ["Daily","Weekly","Monthly"];
const PAY  = ["Easypaisa","JazzCash","Cash","Wallet"];
const STAT = ["pending","completed","cancelled"];
const CATS_ICONS = {Maid:"🧹",Cook:"👨‍🍳",Electrician:"⚡",Clothes:"👔",Security:"🛡️",Plumber:"🔧",Gardener:"🌿",Carpenter:"🪚",Painter:"🎨",Labourer:"⛏️","Baby Sitter":"👶"};
const CATS_BG = {Maid:"#003d20",Cook:"#3d2200",Electrician:"#3d2d00",Clothes:"#001a3d",Security:"#1a1a1a",Plumber:"#002a3d",Gardener:"#003d15"};

/* ─── CSV Parser ─── */
function parseCSV(text, headers) {
  const lines = text.trim().split('\n').filter(l => l.trim());
  return lines.map(line => {
    const vals = line.split(',').map(v => (v||'').trim());
    const obj = {};
    headers.forEach((h,i) => obj[h] = vals[i] ?? '');
    return obj;
  });
}

/* ─── Load CSV files (works when served from same folder) ─── */
async function loadCSV() {
  const wH = ['id','name','cat','city','phone','rate','rating','jobs','verified','busy','date'];
  const uH = ['id','name','phone','pass','role','wallet','date'];
  const bH = ['id','uid','wid','wname','sdate','edate','addr','pkg','amt','status','pay'];

  try {
    const wr = await fetch('workers.csv');
    if (wr.ok) { const rows = parseCSV(await wr.text(), wH); if (rows.length) WW = rows.map(r => ({...r,id:+r.id,rate:+r.rate,rating:+r.rating,jobs:+r.jobs,verified:r.verified==='1',busy:r.busy==='1'})); }
  } catch(_) {}
  try {
    const ur = await fetch('users.csv');
    if (ur.ok) { const rows = parseCSV(await ur.text(), uH); if (rows.length) UU = rows.map(r => ({...r,id:+r.id,wallet:+r.wallet})); }
  } catch(_) {}
  try {
    const br = await fetch('bookings.csv');
    if (br.ok) { const rows = parseCSV(await br.text(), bH); if (rows.length) BB = rows.map(r => ({...r,id:+r.id,uid:+r.uid,wid:+r.wid,pkg:+r.pkg,amt:+r.amt,status:+r.status,pay:+r.pay})); }
  } catch(_) {}
}

/* ─── Helpers ─── */
function statBadge(s) {
  const cls = ['b-amber','b-green','b-red'][s] || 'b-dim';
  return `<span class="badge ${cls}">${STAT[s]||'unknown'}</span>`;
}
function ratingBar(r) {
  const pct = (r/5)*100;
  return `<div class="rbar"><div class="rbar-track"><div class="rbar-fill" style="width:${pct}%"></div></div><span class="rbar-val">${parseFloat(r).toFixed(1)}</span></div>`;
}
function workerBadge(verified, busy) {
  if (!verified) return `<span class="badge b-amber">PENDING</span>`;
  if (busy)      return `<span class="badge b-red">BUSY</span>`;
  return `<span class="badge b-green">FREE</span>`;
}

/* ─── Dashboard ─── */
function renderDash() {
  const verified = WW.filter(w => w.verified).length;
  const pending  = WW.filter(w => !w.verified).length;
  const completed = BB.filter(b => b.status === 1).length;
  const revenue  = BB.filter(b => b.status === 1).reduce((a,b) => a + b.amt*0.1, 0);
  const totalAmt = BB.reduce((a,b) => a + b.amt, 0);

  document.getElementById('stats-row').innerHTML = `
    <div class="stat-card"><div class="stat-num">${WW.length}</div><div class="stat-lbl">Workers</div></div>
    <div class="stat-card"><div class="stat-num" style="color:var(--g)">${verified}</div><div class="stat-lbl">Verified</div></div>
    <div class="stat-card"><div class="stat-num" style="color:var(--amber)">${pending}</div><div class="stat-lbl">Pending</div></div>
    <div class="stat-card"><div class="stat-num">${BB.length}</div><div class="stat-lbl">Bookings</div></div>
    <div class="stat-card"><div class="stat-num" style="color:var(--g)">${completed}</div><div class="stat-lbl">Completed</div></div>
    <div class="stat-card"><div class="stat-num">${UU.length}</div><div class="stat-lbl">Users</div></div>
    <div class="stat-card"><div class="stat-num" style="color:var(--g)">Rs ${Math.round(revenue).toLocaleString()}</div><div class="stat-lbl">Revenue (10%)</div></div>
  `;

  // Top workers
  const top = [...WW].filter(w=>w.verified).sort((a,b)=>b.rating-a.rating).slice(0,5);
  document.getElementById('top-workers-count').textContent = `${top.length} workers`;
  document.getElementById('top-workers-list').innerHTML = top.map(w => `
    <div class="wk-row">
      <div class="wk-ava" style="background:${CATS_BG[w.cat]||'#1a2332'}">${CATS_ICONS[w.cat]||'👤'}</div>
      <div class="wk-info">
        <div class="wk-name">${w.name}</div>
        <div class="wk-cat">${w.cat} · ${w.city}</div>
      </div>
      <div class="wk-right">
        <div class="wk-rate">Rs ${parseInt(w.rate).toLocaleString()}</div>
        <div class="wk-jobs">${w.jobs} jobs · ${ratingBar(w.rating)}</div>
      </div>
    </div>`).join('') || `<div class="empty">No verified workers</div>`;

  // Recent bookings
  const recent = [...BB].reverse().slice(0,5);
  document.getElementById('recent-bookings-count').textContent = `${recent.length} recent`;
  document.getElementById('recent-bookings-list').innerHTML = recent.map(b => `
    <div class="bk-row">
      <div>
        <div class="bk-id">#${b.id}</div>
        <div class="bk-worker">${b.wname}</div>
        <div class="bk-meta">${PKG[b.pkg]} · ${b.sdate}</div>
      </div>
      <div style="text-align:right">
        <div class="bk-amount">Rs ${parseInt(b.amt).toLocaleString()}</div>
        <div style="margin-top:4px">${statBadge(b.status)}</div>
      </div>
    </div>`).join('') || `<div class="empty">No bookings yet</div>`;

  // Revenue breakdown
  document.getElementById('revenue-breakdown').innerHTML = `
    <span style="color:var(--white)">Total Booking Value:</span> Rs ${totalAmt.toLocaleString()} &nbsp;|&nbsp;
    <span style="color:var(--white)">Platform Fee (10%):</span> <span style="color:var(--g)">Rs ${Math.round(revenue).toLocaleString()}</span> &nbsp;|&nbsp;
    <span style="color:var(--white)">Completed Jobs:</span> ${completed} &nbsp;|&nbsp;
    <span style="color:var(--white)">Cancelled:</span> <span style="color:var(--red)">${BB.filter(b=>b.status===2).length}</span> &nbsp;|&nbsp;
    <span style="color:var(--white)">Pending:</span> <span style="color:var(--amber)">${BB.filter(b=>b.status===0).length}</span>
  `;
}

/* ─── Workers page ─── */
function renderWorkers() {
  const q = (document.getElementById('worker-search')?.value || '').toLowerCase();
  const list = WW.filter(w => !q || w.name.toLowerCase().includes(q) || w.cat.toLowerCase().includes(q));
  document.getElementById('workers-count').textContent = `${list.length} / ${WW.length}`;
  document.getElementById('workers-tbody').innerHTML = list.map(w => `
    <tr>
      <td class="mono">${w.id}</td>
      <td style="font-weight:600;color:var(--white)">${w.name}</td>
      <td><span style="display:flex;align-items:center;gap:5px">${CATS_ICONS[w.cat]||''} ${w.cat}</span></td>
      <td style="color:var(--text2)">${w.city}</td>
      <td class="mono" style="color:var(--g)">Rs ${parseInt(w.rate).toLocaleString()}</td>
      <td>${ratingBar(w.rating)}</td>
      <td class="mono" style="color:var(--text2)">${w.jobs}</td>
      <td>${workerBadge(w.verified,w.busy)}</td>
    </tr>`).join('') || `<tr><td colspan="8"><div class="empty">No workers found</div></td></tr>`;
}

/* ─── Bookings page ─── */
function renderBookings() {
  document.getElementById('bookings-count').textContent = `${BB.length} total`;
  document.getElementById('bookings-tbody').innerHTML = BB.map(b => `
    <tr>
      <td class="mono" style="color:var(--text2)">#${b.id}</td>
      <td style="font-weight:600;color:var(--white)">${b.wname}</td>
      <td><span class="badge b-dim">${PKG[b.pkg]||'?'}</span></td>
      <td class="mono" style="color:var(--g)">Rs ${parseInt(b.amt).toLocaleString()}</td>
      <td>${statBadge(b.status)}</td>
      <td style="color:var(--text2)">${PAY[b.pay]||'?'}</td>
      <td class="mono" style="font-size:.76rem">${b.sdate||'-'}</td>
      <td class="mono" style="font-size:.76rem">${b.edate||'-'}</td>
    </tr>`).join('') || `<tr><td colspan="8"><div class="empty">No bookings yet</div></td></tr>`;
}

/* ─── Users page ─── */
function renderUsers() {
  document.getElementById('users-count').textContent = `${UU.length} users`;
  document.getElementById('users-tbody').innerHTML = UU.map(u => `
    <tr>
      <td class="mono">${u.id}</td>
      <td style="font-weight:600;color:var(--white)">${u.name}</td>
      <td class="mono" style="color:var(--text2)">${u.phone}</td>
      <td>${u.role==='admin'?'<span class="badge b-red">ADMIN</span>':'<span class="badge b-blue">EMPLOYER</span>'}</td>
      <td class="mono" style="color:var(--g)">Rs ${parseInt(u.wallet||0).toLocaleString()}</td>
      <td class="mono" style="font-size:.76rem;color:var(--text3)">${u.date||'-'}</td>
    </tr>`).join('') || `<tr><td colspan="6"><div class="empty">No users</div></td></tr>`;
}

/* ─── Tab switching ─── */
function show(id, btn) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('on'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('on'));
  document.getElementById(id).classList.add('on');
  if (btn) btn.classList.add('on');
  // Render page on demand
  if (id === 'workers')  renderWorkers();
  if (id === 'bookings') renderBookings();
  if (id === 'users')    renderUsers();
}

/* ─── Boot ─── */
async function boot() {
  await loadCSV();
  renderDash();
  renderWorkers();
  renderBookings();
  renderUsers();
}
boot();
</script>
</body>
</html>

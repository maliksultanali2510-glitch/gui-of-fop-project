
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Aetbar</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Segoe UI',sans-serif;background:#0f172a;color:#e2e8f0}

/* LOGIN */
#loginPage{display:flex;justify-content:center;align-items:center;height:100vh}
#loginPage .card{width:300px;text-align:center}

/* HEADER */
header{background:linear-gradient(135deg,#1e40af,#7c3aed);padding:16px 26px}
header h1{font-size:1.5rem;color:#fff}
header p{color:#bfdbfe;font-size:.82rem}

/* NAV */
nav{background:#1e293b;display:flex;gap:4px;padding:6px 16px;border-bottom:1px solid #334155}
nav button{background:transparent;color:#94a3b8;border:none;padding:7px 14px;border-radius:6px;cursor:pointer;font-size:.85rem}
nav button.active,nav button:hover{background:#3b82f6;color:#fff}

/* PAGES */
.page{display:none;padding:18px 24px;max-width:1060px;margin:0 auto}
.page.active{display:block}

/* CARD */
.card{background:#1e293b;border-radius:10px;padding:16px;margin-bottom:12px;border:1px solid #334155}
.card h2{font-size:.93rem;color:#93c5fd;margin-bottom:10px}

/* TABLE */
table{width:100%;border-collapse:collapse}
th{background:#0f172a;color:#64748b;text-align:left;padding:8px 10px;font-size:.75rem;text-transform:uppercase}
td{padding:8px 10px;border-bottom:1px solid #1e293b;font-size:.85rem}
tr:hover td{background:#263148}

/* TAGS */
.tag{display:inline-block;padding:2px 9px;border-radius:20px;font-size:.72rem;font-weight:600}
.v{background:#065f46;color:#6ee7b7}
.p{background:#78350f;color:#fcd34d}
.b{background:#7f1d1d;color:#fca5a5}
.fr{background:#1e3a5f;color:#93c5fd}
.co{background:#065f46;color:#6ee7b7}
.ca{background:#4c1d95;color:#c4b5fd}
.pe{background:#334155;color:#94a3b8}
.ad{background:#7f1d1d;color:#fca5a5}

/* DASH */
.sg{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:9px;margin-bottom:14px}
.st{background:#0f172a;border-radius:9px;padding:13px;text-align:center;border:1px solid #334155}
.st .n{font-size:1.8rem;font-weight:700;color:#60a5fa}
.st .l{font-size:.75rem;color:#64748b;margin-top:2px}

/* INPUT */
input{background:#0f172a;border:1px solid #334155;color:#e2e8f0;padding:7px 12px;border-radius:7px;font-size:.84rem;width:260px;margin-bottom:11px}
input:focus{outline:none;border-color:#3b82f6}

/* RATING */
.rb{background:#334155;border-radius:3px;height:5px;display:inline-block;width:44px;vertical-align:middle;margin-right:4px;overflow:hidden}
.rf{background:#fbbf24;height:100%}

.empty{text-align:center;padding:28px;color:#475569}
.btn{padding:6px 12px;border:none;border-radius:6px;cursor:pointer}
.primary{background:#3b82f6;color:#fff}
.danger{background:#ef4444;color:#fff}
</style>
</head>

<body>

<!-- LOGIN -->
<div id="loginPage">
  <div class="card">
    <h2>🔐 Login</h2>
    <input id="phone" placeholder="Phone / Username">
    <input id="pass" type="password" placeholder="Password">
    <button class="btn primary" onclick="login()">Login</button>
    <p id="err" style="color:#f87171;margin-top:8px;font-size:.8rem"></p>
  </div>
</div>

<!-- APP -->
<div id="app" style="display:none">

<header>
<h1>★ AETBAR</h1>
<p>Pakistan Home Worker Platform — Live Data</p>
<button class="btn danger" onclick="logout()" style="float:right">Logout</button>
</header>

<nav>
<button class="active" onclick="show('dash',this)">Dashboard</button>
<button onclick="show('wp',this)">Workers</button>
<button onclick="show('bp',this)">Bookings</button>
<button onclick="show('up',this)">Users</button>
<button onclick="show('ap',this)">About</button>
</nav>

<div id="dash" class="page active">
<div class="sg" id="st"></div>

<div class="card">
<h2>Top Rated Workers</h2>
<table><thead><tr>
<th>Name</th><th>Category</th><th>City</th><th>Rate</th><th>Rating</th><th>Status</th>
</tr></thead><tbody id="tW"></tbody></table>
</div>

<div class="card">
<h2>Recent Bookings</h2>
<table><thead><tr>
<th>ID</th><th>Worker</th><th>Package</th><th>Amount</th><th>Status</th><th>Start</th>
</tr></thead><tbody id="rB"></tbody></table>
</div>
</div>

<div id="wp" class="page">
<input id="ws" placeholder="Search..." oninput="rW()">
<div class="card">
<h2>All Workers</h2>
<table><thead><tr>
<th>ID</th><th>Name</th><th>Category</th><th>City</th><th>Rate</th><th>Rating</th><th>Jobs</th><th>Status</th>
</tr></thead><tbody id="wT"></tbody></table>
</div>
</div>

<div id="bp" class="page">
<div class="card">
<h2>Bookings</h2>
<table><thead><tr>
<th>ID</th><th>Worker</th><th>Pkg</th><th>Amount</th><th>Status</th><th>Payment</th><th>Start</th><th>End</th>
</tr></thead><tbody id="bT"></tbody></table>
</div>
</div>

<div id="up" class="page">
<div class="card">
<h2>Users</h2>
<table><thead><tr>
<th>ID</th><th>Name</th><th>Phone</th><th>Role</th><th>Wallet</th><th>Joined</th>
</tr></thead><tbody id="uT"></tbody></table>
</div>
</div>

<div id="ap" class="page">
<div class="card">
<h2>About</h2>
<p>Aetbar means TRUST in Urdu. Platform for verified workers.</p>
</div>
</div>

</div>

<script>

/* LOGIN */
function login(){
  const phone=document.getElementById('phone').value;
  const pass=document.getElementById('pass').value;

  if(
    (phone==='admin' && pass==='admin123') ||
    (phone==='03001234567' && pass==='1234')
  ){
    document.getElementById('loginPage').style.display='none';
    document.getElementById('app').style.display='block';
    load();
  }else{
    document.getElementById('err').innerText="Invalid credentials";
  }
}

function logout(){
  document.getElementById('app').style.display='none';
  document.getElementById('loginPage').style.display='flex';
}

/* NAV */
function show(id,btn){
document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
document.querySelectorAll('nav button').forEach(b=>b.classList.remove('active'));
document.getElementById(id).classList.add('active');
btn.classList.add('active');
}

/* HELPERS */
const pkgN=['Daily','Weekly','Monthly'];
const payN=['Easypaisa','JazzCash','Cash','Wallet'];
const stN=['pending','completed','cancelled'];

function vtag(v,b){
return v==='1'&&b==='1'?'<span class="tag b">Busy</span>':
v==='1'?'<span class="tag v">Verified</span> <span class="tag fr">Free</span>':
'<span class="tag p">Pending</span>';
}

function stag(s){
const c=s==='completed'?'co':s==='cancelled'?'ca':'pe';
return '<span class="tag '+c+'">'+s+'</span>';
}

function rb(r){
const p=(parseFloat(r)||0)/5*100;
return '<span class="rb"><span class="rf" style="width:'+p+'%"></span></span>'+r;
}

/* DATA */
let WW=[
{id:'1',name:'Fatima Khan',cat:'Maid',city:'Islamabad',rate:'800',rating:'4.9',jobs:'87',verified:'1',busy:'0'},
{id:'2',name:'Muhammad Ali',cat:'Cook',city:'Islamabad',rate:'1200',rating:'4.8',jobs:'63',verified:'1',busy:'0'},
{id:'3',name:'Zahid Butt',cat:'Electrician',city:'Islamabad',rate:'2000',rating:'4.7',jobs:'44',verified:'1',busy:'1'},
{id:'4',name:'Rukhsana Naz',cat:'Clothes',city:'Islamabad',rate:'600',rating:'5.0',jobs:'29',verified:'1',busy:'0'},
{id:'5',name:'Imran Haider',cat:'Security',city:'Islamabad',rate:'1500',rating:'4.6',jobs:'18',verified:'1',busy:'0'},
{id:'6',name:'Asif Khan',cat:'Plumber',city:'Islamabad',rate:'1800',rating:'4.5',jobs:'32',verified:'1',busy:'0'}
];

let UU=[
{id:'1',name:'Ahmed Raza',phone:'03001234567',role:'employer',wallet:'5200',date:'25-04-2025'},
{id:'2',name:'Admin',phone:'admin',role:'admin',wallet:'0',date:'25-04-2025'},
{id:'3',name:'Sara Khan',phone:'03009876543',role:'employer',wallet:'3000',date:'20-04-2025'}
];

let BB=[
{id:'1001',wname:'Fatima Khan',sdate:'01-04-2025',edate:'07-04-2025',pkg:'1',amt:'4200',status:'1',pay:'3'},
{id:'1002',wname:'Muhammad Ali',sdate:'05-04-2025',edate:'05-04-2025',pkg:'0',amt:'1200',status:'2',pay:'0'},
{id:'1003',wname:'Rukhsana Naz',sdate:'10-04-2025',edate:'09-05-2025',pkg:'2',amt:'7656',status:'1',pay:'1'},
{id:'1004',wname:'Imran Haider',sdate:'15-04-2025',edate:'21-04-2025',pkg:'1',amt:'5250',status:'0',pay:'3'}
];

/* DASH */
function dash(){
const ver=WW.filter(w=>w.verified==='1').length;
const rev=BB.filter(b=>stN[parseInt(b.status)]==='completed')
.reduce((a,b)=>a+parseFloat(b.amt||0),0)*.1;

document.getElementById('st').innerHTML=
`<div class="st"><div class="n">${WW.length}</div><div class="l">Workers</div></div>
<div class="st"><div class="n">${ver}</div><div class="l">Verified</div></div>
<div class="st"><div class="n">${BB.length}</div><div class="l">Bookings</div></div>
<div class="st"><div class="n">${UU.length}</div><div class="l">Users</div></div>
<div class="st"><div class="n">Rs ${Math.round(rev)}</div><div class="l">Revenue</div></div>`;

const top=[...WW].sort((a,b)=>b.rating-a.rating).slice(0,5);
document.getElementById('tW').innerHTML=top.map(w=>`
<tr>
<td>${w.name}</td>
<td>${w.cat}</td>
<td>${w.city}</td>
<td>Rs ${w.rate}</td>
<td>${rb(w.rating)}</td>
<td>${vtag(w.verified,w.busy)}</td>
</tr>`).join('');

document.getElementById('rB').innerHTML=BB.slice(-4).reverse().map(b=>`
<tr>
<td>#${b.id}</td>
<td>${b.wname}</td>
<td>${pkgN[b.pkg]}</td>
<td>Rs ${b.amt}</td>
<td>${stag(stN[b.status])}</td>
<td>${b.sdate}</td>
</tr>`).join('');
}

/* WORKERS */
function rW(){
const q=(document.getElementById('ws').value||'').toLowerCase();
const list=WW.filter(w=>w.name.toLowerCase().includes(q)||w.cat.toLowerCase().includes(q));

document.getElementById('wT').innerHTML=list.map(w=>`
<tr>
<td>${w.id}</td>
<td>${w.name}</td>
<td>${w.cat}</td>
<td>${w.city}</td>
<td>Rs ${w.rate}</td>
<td>${rb(w.rating)}</td>
<td>${w.jobs}</td>
<td>${vtag(w.verified,w.busy)}</td>
</tr>`).join('')||'<tr><td colspan="8" class="empty">No workers found</td></tr>';
}

/* BOOKINGS */
function rB(){
document.getElementById('bT').innerHTML=BB.map(b=>`
<tr>
<td>#${b.id}</td>
<td>${b.wname}</td>
<td>${pkgN[b.pkg]}</td>
<td>Rs ${b.amt}</td>
<td>${stag(stN[b.status])}</td>
<td>${payN[b.pay]}</td>
<td>${b.sdate}</td>
<td>${b.edate}</td>
</tr>`).join('');
}

/* USERS */
function rU(){
document.getElementById('uT').innerHTML=UU.map(u=>`
<tr>
<td>${u.id}</td>
<td>${u.name}</td>
<td>${u.phone}</td>
<td><span class="tag ${u.role==='admin'?'ad':'fr'}">${u.role}</span></td>
<td>Rs ${u.wallet}</td>
<td>${u.date}</td>
</tr>`).join('');
}

function load(){dash();rW();rB();rU();}

</script>

</body>
</html>
```

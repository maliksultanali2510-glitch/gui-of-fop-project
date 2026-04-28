
<html lang="en"><head><meta charset="UTF-8"><title>Aetbar</title>
<style>*{box-sizing:border-box;margin:0;padding:0}body{font-family:'Segoe UI',sans-serif;background:#0f172a;color:#e2e8f0}
header{background:linear-gradient(135deg,#1e40af,#7c3aed);padding:16px 26px}header h1{font-size:1.5rem;color:#fff}header p{color:#bfdbfe;font-size:.82rem}
nav{background:#1e293b;display:flex;gap:4px;padding:6px 16px;border-bottom:1px solid #334155}
nav button{background:transparent;color:#94a3b8;border:none;padding:7px 14px;border-radius:6px;cursor:pointer;font-size:.85rem}
nav button.active,nav button:hover{background:#3b82f6;color:#fff}
.page{display:none;padding:18px 24px;max-width:1060px;margin:0 auto}.page.active{display:block}
.card{background:#1e293b;border-radius:10px;padding:16px;margin-bottom:12px;border:1px solid #334155}
.card h2{font-size:.93rem;color:#93c5fd;margin-bottom:10px}
table{width:100%;border-collapse:collapse}th{background:#0f172a;color:#64748b;text-align:left;padding:8px 10px;font-size:.75rem;text-transform:uppercase}
td{padding:8px 10px;border-bottom:1px solid #1e293b;font-size:.85rem}tr:hover td{background:#263148}
.tag{display:inline-block;padding:2px 9px;border-radius:20px;font-size:.72rem;font-weight:600}
.v{background:#065f46;color:#6ee7b7}.p{background:#78350f;color:#fcd34d}.b{background:#7f1d1d;color:#fca5a5}
.fr{background:#1e3a5f;color:#93c5fd}.co{background:#065f46;color:#6ee7b7}.ca{background:#4c1d95;color:#c4b5fd}
.pe{background:#334155;color:#94a3b8}.ad{background:#7f1d1d;color:#fca5a5}
.sg{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:9px;margin-bottom:14px}
.st{background:#0f172a;border-radius:9px;padding:13px;text-align:center;border:1px solid #334155}
.st .n{font-size:1.8rem;font-weight:700;color:#60a5fa}.st .l{font-size:.75rem;color:#64748b;margin-top:2px}
input{background:#0f172a;border:1px solid #334155;color:#e2e8f0;padding:7px 12px;border-radius:7px;font-size:.84rem;width:260px;margin-bottom:11px}
input:focus{outline:none;border-color:#3b82f6}.rb{background:#334155;border-radius:3px;height:5px;display:inline-block;width:44px;vertical-align:middle;margin-right:4px;overflow:hidden}
.rf{background:#fbbf24;height:100%}.chips{display:flex;flex-wrap:wrap;gap:6px;margin-top:8px}
.chip{background:#1e3a5f;color:#93c5fd;padding:3px 10px;border-radius:20px;font-size:.75rem}.empty{text-align:center;padding:28px;color:#475569}</style></head><body>
<header><h1>&#9733; AETBAR</h1><p>Pakistan Home Worker Platform &mdash; Live Data</p></header>
<nav><button class="active" onclick="show('dash',this)">Dashboard</button><button onclick="show('wp',this)">Workers</button>
<button onclick="show('bp',this)">Bookings</button><button onclick="show('up',this)">Users</button><button onclick="show('ap',this)">About</button></nav>
<div id="dash" class="page active"><div class="sg" id="st"></div>
<div class="card"><h2>&#127775; Top Rated Workers</h2><table><thead><tr><th>Name</th><th>Category</th><th>City</th><th>Rate/Day</th><th>Rating</th><th>Status</th></tr></thead><tbody id="tW"></tbody></table></div>
<div class="card"><h2>&#128203; Recent Bookings</h2><table><thead><tr><th>ID</th><th>Worker</th><th>Package</th><th>Amount</th><th>Status</th><th>Start</th></tr></thead><tbody id="rB"></tbody></table></div></div>
<div id="wp" class="page"><input id="ws" placeholder="Search name or category..." oninput="rW()">
<div class="card"><h2>&#128119; All Workers</h2><table><thead><tr><th>ID</th><th>Name</th><th>Category</th><th>City</th><th>Rate</th><th>Rating</th><th>Jobs</th><th>Status</th></tr></thead><tbody id="wT"></tbody></table></div></div>
<div id="bp" class="page"><div class="card"><h2>&#128197; All Bookings</h2><table><thead><tr><th>ID</th><th>Worker</th><th>Pkg</th><th>Amount</th><th>Status</th><th>Payment</th><th>Start</th><th>End</th></tr></thead><tbody id="bT"></tbody></table></div></div>
<div id="up" class="page"><div class="card"><h2>&#128100; All Users</h2><table><thead><tr><th>ID</th><th>Name</th><th>Phone</th><th>Role</th><th>Wallet</th><th>Joined</th></tr></thead><tbody id="uT"></tbody></table></div></div>
<div id="ap" class="page">
<div class="card"><h2>&#9432; About Aetbar</h2><p style="line-height:1.9;color:#cbd5e1"><b style="color:#93c5fd">Aetbar</b> means <i>TRUST</i> in Urdu.<br>Pakistan platform for verified home workers. CNIC-verified and police-cleared.<br><br><b style="color:#93c5fd">Founder:</b> Sultan Ali &nbsp;|&nbsp;<b style="color:#93c5fd">Phone:</b> 0331-5506907 &nbsp;|&nbsp;<b style="color:#93c5fd">Cities:</b> Islamabad, Lahore, Karachi</p></div>
<div class="card"><h2>&#128187; C++ Concepts Used</h2><div class="chips"><span class="chip">Structs</span><span class="chip">Enums</span><span class="chip">Arrays</span><span class="chip">Bubble Sort</span><span class="chip">Functions</span><span class="chip">Nested Loops</span><span class="chip">for/while</span><span class="chip">if/else</span><span class="chip">Switch-Case</span><span class="chip">File I/O</span></div></div>
<div class="card"><h2>&#128274; Login Credentials</h2><table><thead><tr><th>Role</th><th>Phone</th><th>Password</th></tr></thead><tbody><tr><td>Employer</td><td>03001234567</td><td>1234</td></tr><tr><td>Admin</td><td>admin</td><td>admin123</td></tr></tbody></table></div></div>
<script>
function show(id,btn){document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));document.querySelectorAll('nav button').forEach(b=>b.classList.remove('active'));document.getElementById(id).classList.add('active');if(btn)btn.classList.add('active');}
function csv(t){const l=t.trim().split('\n').filter(x=>x.trim());if(l.length<2)return[];const h=l[0].split(',').map(x=>x.trim());return l.slice(1).map(r=>{const v=r.split(',');const o={};h.forEach((k,i)=>o[k]=(v[i]||'').trim());return o;});}
const pkgN=['Daily','Weekly','Monthly'],payN=['Easypaisa','JazzCash','Cash','Wallet'],stN=['pending','completed','cancelled'];
function vtag(v,b){return v==='1'&&b==='1'?'<span class="tag b">Busy</span>':v==='1'?'<span class="tag v">Verified</span> <span class="tag fr">Free</span>':'<span class="tag p">Pending</span>';}
function stag(s){const c=s==='completed'?'co':s==='cancelled'?'ca':'pe';return'<span class="tag '+c+'">'+s+'</span>';}
function rb(r){const p=(parseFloat(r)||0)/5*100;return'<span class="rb"><span class="rf" style="width:'+p+'%"></span></span>'+r;}
let WW=[{id:'1',name:'Fatima Khan',cat:'Maid',city:'Islamabad',rate:'800',rating:'4.9',jobs:'87',verified:'1',busy:'0'},{id:'2',name:'Muhammad Ali',cat:'Cook',city:'Islamabad',rate:'1200',rating:'4.8',jobs:'63',verified:'1',busy:'0'},{id:'3',name:'Zahid Butt',cat:'Electrician',city:'Islamabad',rate:'2000',rating:'4.7',jobs:'44',verified:'1',busy:'1'},{id:'4',name:'Rukhsana Naz',cat:'Clothes',city:'Islamabad',rate:'600',rating:'5.0',jobs:'29',verified:'1',busy:'0'},{id:'5',name:'Imran Haider',cat:'Security',city:'Islamabad',rate:'1500',rating:'4.6',jobs:'18',verified:'1',busy:'0'},{id:'6',name:'Asif Khan',cat:'Plumber',city:'Islamabad',rate:'1800',rating:'4.5',jobs:'32',verified:'1',busy:'0'}];
let UU=[{id:'1',name:'Ahmed Raza',phone:'03001234567',role:'employer',wallet:'5200',date:'25-04-2025'},{id:'2',name:'Admin',phone:'admin',role:'admin',wallet:'0',date:'25-04-2025'},{id:'3',name:'Sara Khan',phone:'03009876543',role:'employer',wallet:'3000',date:'20-04-2025'}];
let BB=[{id:'1001',wname:'Fatima Khan',sdate:'01-04-2025',edate:'07-04-2025',pkg:'1',amt:'4200',status:'1',pay:'3'},{id:'1002',wname:'Muhammad Ali',sdate:'05-04-2025',edate:'05-04-2025',pkg:'0',amt:'1200',status:'2',pay:'0'},{id:'1003',wname:'Rukhsana Naz',sdate:'10-04-2025',edate:'09-05-2025',pkg:'2',amt:'7656',status:'1',pay:'1'},{id:'1004',wname:'Imran Haider',sdate:'15-04-2025',edate:'21-04-2025',pkg:'1',amt:'5250',status:'0',pay:'3'}];
async function load(){
  try{const r=await fetch('workers.csv');if(r.ok){const d=csv(await r.text());if(d.length)WW=d;}}catch(_){}
  try{const r=await fetch('users.csv');if(r.ok){const d=csv(await r.text());if(d.length)UU=d;}}catch(_){}
  try{const r=await fetch('bookings.csv');if(r.ok){const d=csv(await r.text());if(d.length)BB=d;}}catch(_){}
  dash();rW();rB();rU();
}
function dash(){
  const ver=WW.filter(w=>w.verified==='1').length,rev=BB.filter(b=>stN[parseInt(b.status)]==='completed').reduce((a,b)=>a+parseFloat(b.amt||0),0)*.1;
  document.getElementById('st').innerHTML=`<div class="st"><div class="n">${WW.length}</div><div class="l">Workers</div></div><div class="st"><div class="n">${ver}</div><div class="l">Verified</div></div><div class="st"><div class="n">${BB.length}</div><div class="l">Bookings</div></div><div class="st"><div class="n">${UU.length}</div><div class="l">Users</div></div><div class="st"><div class="n">Rs ${Math.round(rev)}</div><div class="l">Revenue</div></div>`;
  const top=[...WW].filter(w=>w.verified==='1').sort((a,b)=>parseFloat(b.rating)-parseFloat(a.rating)).slice(0,5);
  document.getElementById('tW').innerHTML=top.map(w=>`<tr><td>${w.name}</td><td>${w.cat}</td><td>${w.city}</td><td>Rs ${parseInt(w.rate)}</td><td>${rb(w.rating)}</td><td>${vtag(w.verified,w.busy)}</td></tr>`).join('');
  document.getElementById('rB').innerHTML=BB.slice(-4).reverse().map(b=>`<tr><td>#${b.id}</td><td>${b.wname}</td><td>${pkgN[parseInt(b.pkg)]}</td><td>Rs ${parseInt(b.amt)}</td><td>${stag(stN[parseInt(b.status)])}</td><td>${b.sdate}</td></tr>`).join('');
}
function rW(){const q=(document.getElementById('ws').value||'').toLowerCase();const l=WW.filter(w=>!q||(w.name||'').toLowerCase().includes(q)||(w.cat||'').toLowerCase().includes(q));document.getElementById('wT').innerHTML=l.map(w=>`<tr><td>${w.id}</td><td>${w.name}</td><td>${w.cat}</td><td>${w.city}</td><td>Rs ${parseInt(w.rate)}</td><td>${rb(w.rating)}</td><td>${w.jobs}</td><td>${vtag(w.verified,w.busy)}</td></tr>`).join('')||'<tr><td colspan="8" class="empty">No workers found.</td></tr>';}
function rB(){document.getElementById('bT').innerHTML=BB.map(b=>`<tr><td>#${b.id}</td><td>${b.wname}</td><td>${pkgN[parseInt(b.pkg)]}</td><td>Rs ${parseInt(b.amt)}</td><td>${stag(stN[parseInt(b.status)])}</td><td>${payN[parseInt(b.pay)]}</td><td>${b.sdate}</td><td>${b.edate}</td></tr>`).join('')||'<tr><td colspan="8" class="empty">No bookings yet.</td></tr>';}
function rU(){document.getElementById('uT').innerHTML=UU.map(u=>`<tr><td>${u.id}</td><td>${u.name}</td><td>${u.phone}</td><td><span class="tag ${u.role==='admin'?'ad':'fr'}">${u.role}</span></td><td>Rs ${parseInt(u.wallet)}</td><td>${u.date||'-'}</td></tr>`).join('')||'<tr><td colspan="6" class="empty">No users.</td></tr>';}
load();
</script></body></html>

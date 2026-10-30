# index-luubarberv1
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="LuuBarber">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="theme-color" content="#0c0c0e">
<title>LuuBarber</title>
<link rel="apple-touch-icon" href="data:image/png;base64,__ICON__">
<link rel="icon" href="data:image/png;base64,__ICON__">
<style>
:root{--bg:#0c0c0e;--card:#16161a;--card2:#1f1f25;--line:#2a2a30;--gold:#d4a94f;--gold2:#f3d98e;--txt:#f5f5f7;--mut:#8e8e96;--red:#ff5a4f;--green:#34d36b}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{margin:0}
body{background:var(--bg);color:var(--txt);font-family:-apple-system,system-ui,"Segoe UI",sans-serif;padding:env(safe-area-inset-top) 0 calc(100px + env(safe-area-inset-bottom));-webkit-user-select:none;user-select:none;overflow-x:hidden}
input{-webkit-user-select:text;user-select:text}
button{font:inherit;color:inherit;border:0;background:none;cursor:pointer}
svg{width:1em;height:1em}
.glow{position:fixed;inset:-25% -25% auto;height:60%;background:radial-gradient(closest-side,rgba(212,169,79,.22),transparent);pointer-events:none;animation:breathe 6s ease-in-out infinite}
header{display:flex;align-items:center;gap:12px;padding:22px 18px 6px;max-width:600px;margin:auto;position:relative}
.logo{width:46px;height:46px;border-radius:14px;display:grid;place-items:center;font-size:24px;color:#111;background:linear-gradient(135deg,var(--gold2),var(--gold));box-shadow:0 6px 20px rgba(212,169,79,.35)}
.logo svg{animation:snip 3.5s ease-in-out infinite}
header h1{margin:0;font-size:24px;letter-spacing:1px;background:linear-gradient(90deg,var(--gold2),var(--gold));-webkit-background-clip:text;background-clip:text;color:transparent}
header p{margin:2px 0 0;color:var(--mut);font-size:13px}
main{padding:8px 16px;max-width:600px;margin:auto;position:relative}
.page{display:none}.page.active{display:block;animation:rise .45s both}
.step{display:flex;align-items:center;gap:10px;font-weight:700;font-size:17px;margin:22px 0 12px}
.n{width:26px;height:26px;border-radius:50%;display:grid;place-items:center;font-size:13px;color:#111;background:linear-gradient(135deg,var(--gold2),var(--gold))}
.card{background:var(--card);border:1px solid var(--line);border-radius:18px;padding:14px;margin-bottom:12px}
.mut{color:var(--mut);font-size:14px}
.days{display:flex;gap:8px;overflow-x:auto;padding:6px 2px 12px;scrollbar-width:none}
.days::-webkit-scrollbar{display:none}
.day{flex:0 0 64px;text-align:center;padding:10px 0;border-radius:16px;background:var(--card);border:1.5px solid var(--line);transition:transform .2s,background .2s,box-shadow .2s}
.day b{display:block;font-size:22px;margin:2px 0}
.day small{color:var(--mut);text-transform:uppercase;font-size:10.5px;letter-spacing:.5px}
.day:active,.slot:active,.svc:active,.h:active{transform:scale(.94)}
.day.sel{background:linear-gradient(160deg,var(--gold2),var(--gold));border-color:transparent;transform:translateY(-2px);box-shadow:0 8px 20px rgba(212,169,79,.3)}
.day.sel *{color:#111}
.day:disabled{opacity:.25;pointer-events:none}
.grp{color:var(--mut);font-size:12px;text-transform:uppercase;letter-spacing:1px;margin:12px 0 8px}
.slots{display:grid;grid-template-columns:repeat(4,1fr);gap:8px}
.slot{padding:12px 0;border-radius:12px;background:var(--card);border:1.5px solid var(--line);font-size:15px;transition:transform .15s,background .2s,border-color .2s}
.slot.sel{background:rgba(212,169,79,.16);border-color:var(--gold);color:var(--gold2);font-weight:700}
.slot:disabled{opacity:.22;text-decoration:line-through}
.svcs{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.svc{display:flex;flex-direction:column;align-items:flex-start;gap:4px;padding:12px;border-radius:14px;background:var(--card);border:1.5px solid var(--line);text-align:left;transition:transform .15s,background .2s,border-color .2s}
.svc:last-child:nth-child(odd){grid-column:1/-1}
.svc svg{font-size:21px;color:var(--gold)}
.svc b{font-size:14px}.svc small{color:var(--mut)}
.svc.sel{border-color:var(--gold);background:rgba(212,169,79,.12)}
input{width:100%;padding:15px;margin-bottom:10px;border-radius:14px;border:1.5px solid var(--line);background:var(--card);color:var(--txt);font-size:16px;outline:0;transition:border-color .2s,box-shadow .2s}
input:focus{border-color:var(--gold);box-shadow:0 0 0 4px rgba(212,169,79,.15)}
.sum{display:none;align-items:center;gap:12px;margin:14px 0;padding:12px 14px;border-radius:16px;background:rgba(212,169,79,.1);border:1px solid rgba(212,169,79,.35)}
.sum.on{display:flex;animation:pop .35s both}
.sum svg{font-size:24px;color:var(--gold)}
.sum div{display:flex;flex-direction:column}.sum small{color:var(--mut)}
.btn{display:flex;align-items:center;justify-content:center;gap:8px;width:100%;padding:16px;border-radius:16px;font-weight:700;font-size:17px;text-decoration:none;color:#111;background:linear-gradient(135deg,var(--gold2),var(--gold));box-shadow:0 8px 22px rgba(212,169,79,.28);transition:transform .15s,opacity .2s}
.btn:active{transform:scale(.97)}.btn:disabled{opacity:.35;box-shadow:none}
.btn svg{font-size:20px}
.wa{background:#25d366;box-shadow:none}.snap{background:#fffc00;box-shadow:none}.alt{background:var(--card2);color:var(--txt);box-shadow:none}
.sheet .btn{margin-top:10px}
.sheet{position:fixed;inset:0;display:flex;align-items:flex-end;background:rgba(0,0,0,0);visibility:hidden;transition:background .3s,visibility .3s;z-index:20}
.sheet.open{background:rgba(0,0,0,.6);visibility:visible}
.box{width:100%;max-width:600px;margin:auto;background:var(--card);border-radius:26px 26px 0 0;padding:26px 20px calc(20px + env(safe-area-inset-bottom));text-align:center;transform:translateY(100%);transition:transform .45s cubic-bezier(.2,1,.3,1)}
.sheet.open .box{transform:none}
.box h3{margin:10px 0 4px;font-size:22px}.box p{margin:0 0 8px;color:var(--mut)}
.chk{width:76px;height:76px;stroke:var(--green);fill:none;stroke-width:3;stroke-linecap:round;stroke-linejoin:round}
.chk circle{stroke-dasharray:151;stroke-dashoffset:151;animation:draw .6s .2s forwards}
.chk path{stroke-dasharray:40;stroke-dashoffset:40;animation:draw .4s .7s forwards}
nav{position:fixed;left:12px;right:12px;bottom:calc(10px + env(safe-area-inset-bottom));max-width:576px;margin:auto;display:flex;background:rgba(28,28,32,.82);-webkit-backdrop-filter:blur(22px);backdrop-filter:blur(22px);border:1px solid var(--line);border-radius:24px;overflow:hidden;z-index:10}
nav button{flex:1;padding:11px 0 9px;font-size:11px;color:var(--mut);display:flex;flex-direction:column;align-items:center;gap:3px;transition:color .25s}
nav svg{font-size:23px;transition:transform .3s cubic-bezier(.3,1.6,.5,1)}
nav button.active{color:var(--gold)}nav button.active svg{transform:translateY(-2px) scale(1.15)}
.pill{position:absolute;top:0;left:0;width:33.333%;display:flex;justify-content:center;transition:transform .4s cubic-bezier(.3,1.3,.5,1)}
.pill:after{content:"";width:34px;height:3px;background:var(--gold);border-radius:0 0 4px 4px;box-shadow:0 0 12px var(--gold)}
.row{display:flex;justify-content:space-between;align-items:center;gap:8px}
.bar{height:6px;background:#2a2a30;border-radius:4px;overflow:hidden;margin:10px 0}
.bar i{display:block;height:100%;width:0;background:linear-gradient(90deg,var(--green),#8af0a8);transition:width .9s cubic-bezier(.2,1,.3,1)}
.hours{display:flex;flex-wrap:wrap;gap:6px}
.h{padding:7px 10px;border-radius:9px;font-size:13px;transition:transform .15s}
.h.free{background:rgba(52,211,107,.14);color:var(--green)}
.h.busy{background:rgba(255,90,79,.12);color:var(--red);text-decoration:line-through}
.tag{background:var(--gold);color:#111;border-radius:6px;padding:2px 6px;font-size:11px;font-weight:700;margin-left:6px}
.tools{display:flex;gap:8px;margin-bottom:12px}
.tools button{flex:1;padding:12px;border-radius:12px;border:1px solid var(--line);background:var(--card);font-size:14px}
.small{border:1px solid var(--red)!important;color:var(--red);border-radius:10px;padding:8px 12px;font-size:13px}
#toast{position:fixed;left:50%;bottom:calc(96px + env(safe-area-inset-bottom));transform:translate(-50%,20px);background:var(--card2);border:1px solid var(--line);padding:12px 18px;border-radius:14px;opacity:0;transition:.3s;pointer-events:none;z-index:30;white-space:nowrap}
#toast.on{opacity:1;transform:translate(-50%,0)}
@keyframes rise{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:none}}
@keyframes pop{from{opacity:0;transform:scale(.92)}to{opacity:1;transform:none}}
@keyframes draw{to{stroke-dashoffset:0}}
@keyframes snip{0%,60%,100%{transform:rotate(0)}70%{transform:rotate(-14deg)}80%{transform:rotate(10deg)}90%{transform:rotate(-6deg)}}
@keyframes breathe{50%{opacity:.55}}
@keyframes shake{25%{transform:translateX(-8px)}75%{transform:translateX(8px)}}
.a{animation:rise .4s backwards;animation-delay:calc(var(--d,0)*28ms)}
.shake{animation:shake .35s}
.out{opacity:0;transform:translateX(30px);transition:.25s}
@media(prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
</style>
</head>
<body>
<div class="glow"></div>
<header><div class="logo" data-i="scissors"></div><div><h1>LUUBARBER</h1><p>Ton rendez-vous en 30 secondes</p></div></header>
<main>
  <section id="book" class="page active">
    <div class="step"><span class="n">1</span>Choisis un jour</div>
    <div class="days" id="days"></div>
    <div class="step"><span class="n">2</span>Choisis une heure</div>
    <div id="slots"></div>
    <div class="step"><span class="n">3</span>Ta prestation</div>
    <div class="svcs" id="svcs"></div>
    <div class="step"><span class="n">4</span>Tes infos</div>
    <input id="name" placeholder="Ton prénom" autocomplete="given-name">
    <input id="phone" type="tel" placeholder="Téléphone" autocomplete="tel">
    <div class="sum" id="sum"></div>
    <button class="btn" id="confirm" disabled><span data-i="check"></span>Confirmer le rendez-vous</button>
  </section>

  <section id="avail" class="page">
    <div class="step">Créneaux restants</div>
    <p class="mut">Touche un créneau vert pour le réserver.</p>
    <div id="availList"></div>
  </section>

  <section id="admin" class="page">
    <div class="step">Espace barbier</div>
    <div id="lock">
      <input id="pin" type="password" inputmode="numeric" placeholder="Code PIN">
      <button class="btn" id="unlock"><span data-i="lock"></span>Entrer</button>
    </div>
    <div id="adminBox" style="display:none">
      <div class="tools"><button id="export">Sauvegarder</button><button id="import">Restaurer</button></div>
      <input type="file" id="file" accept=".json" style="display:none">
      <div id="adminList"></div>
    </div>
  </section>
</main>

<nav>
  <i class="pill"></i>
  <button class="active" data-p="book"><span data-i="calendar"></span>Réserver</button>
  <button data-p="avail"><span data-i="clock"></span>Créneaux</button>
  <button data-p="admin"><span data-i="lock"></span>Barbier</button>
</nav>

<div class="sheet" id="sheet"><div class="box" id="sheetBody"></div></div>
<div id="toast"></div>

<script>
/* ====== RÉGLAGES (modifie ici) ====== */
const OPEN = 9, CLOSE = 19, STEP = 30;   // 9h → 19h, créneaux de 30 min
const PAUSE = [12, 14];                  // pause midi (mets [0,0] pour la désactiver)
const CLOSED_DAYS = [0, 1];              // 0=dimanche, 1=lundi (fermés)
const DAYS_AHEAD = 14;                   // nombre de jours réservables
const PIN = "1234";                      // CHANGE CE CODE !
const SHOP_PHONE = "33600000000";        // TON n° WhatsApp, format international sans le +
const SNAP_USER = "luubarber";           // TON pseudo Snapchat (sans le @)
const S = [["Coupe homme",15,"scissors"],["Dégradé",18,"bars"],["Barbe",10,"drop"],["Coupe + barbe",25,"spark"],["Enfant",12,"smile"]];
/* ==================================== */

const KEY="luubarber_rdv", $=s=>document.querySelector(s);
const load=()=>{try{return JSON.parse(localStorage.getItem(KEY)||"{}")}catch(e){return{}}};
const save=d=>{try{localStorage.setItem(KEY,JSON.stringify(d))}catch(e){toast("Impossible d'enregistrer")}};
const pad=n=>String(n).padStart(2,"0");
const iso=d=>`${d.getFullYear()}-${pad(d.getMonth()+1)}-${pad(d.getDate())}`;
const esc=s=>String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const JOURS=["dim","lun","mar","mer","jeu","ven","sam"], MOIS=["jan","fév","mar","avr","mai","juin","juil","août","sep","oct","nov","déc"];
const hoursList=()=>{const a=[];for(let m=OPEN*60;m<CLOSE*60;m+=STEP){if(m>=PAUSE[0]*60&&m<PAUSE[1]*60)continue;a.push(`${pad(Math.floor(m/60))}:${pad(m%60)}`)}return a};
function openDays(){const o=[],t=new Date();t.setHours(0,0,0,0);for(let i=0;i<=DAYS_AHEAD;i++){const d=new Date(t);d.setDate(t.getDate()+i);o.push(d)}return o}
const isPast=(ds,t)=>new Date(`${ds}T${t}:00`)<=new Date();
const isFree=(db,ds,t)=>!db[ds+"_"+t]&&!isPast(ds,t);

/* Icônes */
const P={scissors:'<circle cx="6" cy="6" r="3"/><circle cx="6" cy="18" r="3"/><path d="M20 4 8.1 15.9M14.5 14.5 20 20M8.1 8.1 12 12"/>',
calendar:'<rect x="3" y="4" width="18" height="18" rx="3"/><path d="M16 2v4M8 2v4M3 10h18"/>',
clock:'<circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/>',
lock:'<rect x="4" y="11" width="16" height="10" rx="3"/><path d="M8 11V7a4 4 0 0 1 8 0v4"/>',
check:'<path d="M5 13l4 4L19 7"/>',
bars:'<path d="M5 20V10M10 20V6M15 20v-8M20 20V4"/>',
drop:'<path d="M12 3s6 6 6 11a6 6 0 0 1-12 0c0-5 6-11 6-11z"/>',
spark:'<path d="M12 3l1.8 4.7 4.7 1.8-4.7 1.8L12 16l-1.8-4.7-4.7-1.8 4.7-1.8zM19 16l.8 2.2L22 19l-2.2.8L19 22l-.8-2.2L16 19l2.2-.8z"/>',
smile:'<circle cx="12" cy="12" r="9"/><path d="M8 14s1.5 2 4 2 4-2 4-2M9 9h.01M15 9h.01"/>',
chat:'<path d="M21 12a8 8 0 0 1-11.7 7L3 21l2-6.1A8 8 0 1 1 21 12z"/>',
ghost:'<path d="M12 3a6 6 0 0 0-6 6v9l2.5-1.5L10 19l2-1.5 2 1.5 1.5-2.5L18 18V9a6 6 0 0 0-6-6zM9.5 10h.01M14.5 10h.01"/>'};
const ico=n=>`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">${P[n]}</svg>`;
const paint=(r=document)=>r.querySelectorAll("[data-i]").forEach(e=>e.innerHTML=ico(e.dataset.i));
let tt;const toast=m=>{const t=$("#toast");t.textContent=m;t.classList.add("on");clearTimeout(tt);tt=setTimeout(()=>t.classList.remove("on"),2200)};
const tap=()=>{try{navigator.vibrate&&navigator.vibrate(8)}catch(e){}};

let selDay=iso(openDays().find(d=>!CLOSED_DAYS.includes(d.getDay()))), selTime=null, selSvc=0, dayEls=[];

function renderDays(){
  const box=$("#days");box.innerHTML="";dayEls=[];
  openDays().forEach((d,i)=>{
    const ds=iso(d),el=document.createElement("button");
    el.className="day a";el.style.setProperty("--d",i);el.disabled=CLOSED_DAYS.includes(d.getDay());
    el.innerHTML=`<small>${i?JOURS[d.getDay()]:"auj."}</small><b>${d.getDate()}</b><small>${MOIS[d.getMonth()]}</small>`;
    el.onclick=()=>{tap();selDay=ds;selTime=null;markDays();renderSlots(true);check()};
    box.appendChild(el);dayEls.push([el,ds]);
  });
  markDays();
}
function markDays(){
  dayEls.forEach(([el,ds])=>{el.classList.toggle("sel",ds===selDay);if(ds===selDay)el.scrollIntoView({inline:"center",block:"nearest",behavior:"smooth"})});
  sum();
}
function renderSlots(anim){
  const box=$("#slots"),db=load();let i=0;box.innerHTML="";
  [["Matin",h=>h<"13"],["Après-midi",h=>h>="13"]].forEach(([t,f])=>{
    const hs=hoursList().filter(f);if(!hs.length)return;
    box.insertAdjacentHTML("beforeend",`<div class="grp">${t}</div>`);
    const g=document.createElement("div");g.className="slots";
    hs.forEach(h=>{
      const el=document.createElement("button"),free=isFree(db,selDay,h);
      el.className="slot"+(anim?" a":"")+(h===selTime?" sel":"");el.style.setProperty("--d",i++);el.textContent=h;el.disabled=!free;
      el.onclick=()=>{tap();selTime=h;renderSlots();sum();check()};
      g.appendChild(el);
    });
    box.appendChild(g);
  });
}
function renderSvcs(){
  const box=$("#svcs");box.innerHTML="";
  S.forEach((v,i)=>{
    const el=document.createElement("button");el.className="svc a"+(i===selSvc?" sel":"");el.style.setProperty("--d",i);
    el.innerHTML=`${ico(v[2])}<b>${v[0]}</b><small>${v[1]} €</small>`;
    el.onclick=()=>{tap();selSvc=i;[...box.children].forEach((c,j)=>c.classList.toggle("sel",j===i));sum()};
    box.appendChild(el);
  });
}
function sum(){
  const s=$("#sum");if(!selDay||!selTime){s.classList.remove("on");return}
  const d=new Date(selDay+"T00:00"),v=S[selSvc];
  s.innerHTML=`<span data-i="calendar"></span><div><b>${JOURS[d.getDay()]} ${d.getDate()} ${MOIS[d.getMonth()]} · ${selTime}</b><small>${v[0]} · ${v[1]} €</small></div>`;
  paint(s);s.classList.add("on");
}
function check(){$("#confirm").disabled=!(selDay&&selTime&&$("#name").value.trim()&&$("#phone").value.replace(/\D/g,"").length>=8)}
["#name","#phone"].forEach(s=>$(s).addEventListener("input",check));

$("#confirm").onclick=()=>{
  const db=load(),k=selDay+"_"+selTime;
  if(db[k]){toast("Ce créneau vient d'être pris");renderSlots();return}
  const name=$("#name").value.trim(),phone=$("#phone").value.trim(),v=S[selSvc],service=`${v[0]} – ${v[1]} €`;
  db[k]={name,phone,service};save(db);
  const d=new Date(selDay+"T00:00"),quand=`${JOURS[d.getDay()]} ${d.getDate()}/${d.getMonth()+1} à ${selTime}`;
  const msg=`Bonjour, c'est ${name} (${phone}). Je confirme mon RDV ${quand} pour : ${service}.`;
  $("#sheetBody").innerHTML=`<svg class="chk" viewBox="0 0 52 52"><circle cx="26" cy="26" r="24"/><path d="M15 27l8 8 14-16"/></svg>
    <h3>C'est réservé !</h3><p>${esc(quand)}<br>${esc(service)}</p>
    <a class="btn wa" target="_blank" rel="noopener" href="https://wa.me/${SHOP_PHONE}?text=${encodeURIComponent(msg)}"><span data-i="chat"></span>Prévenir sur WhatsApp</a>
    <a class="btn snap" id="snapBtn" target="_blank" rel="noopener" href="https://www.snapchat.com/add/${encodeURIComponent(SNAP_USER)}"><span data-i="ghost"></span>Prévenir sur Snapchat</a>
    <p style="margin-top:10px;font-size:13px">Sur Snap, le message est copié : colle-le dans la discussion.</p>
    <button class="btn alt" id="close">Fermer</button>`;
  paint($("#sheetBody"));
  $("#snapBtn").onclick=()=>{try{navigator.clipboard.writeText(msg)}catch(e){}};
  $("#close").onclick=()=>$("#sheet").classList.remove("open");
  $("#sheet").classList.add("open");
  selTime=null;$("#name").value="";$("#phone").value="";renderSlots();sum();check();
};
$("#sheet").onclick=e=>{if(e.target.id==="sheet")e.target.classList.remove("open")};

function renderAvail(){
  const db=load(),box=$("#availList"),all=hoursList();let i=0;box.innerHTML="";
  openDays().forEach(d=>{
    if(CLOSED_DAYS.includes(d.getDay()))return;
    const ds=iso(d),free=all.filter(h=>isFree(db,ds,h)).length,pct=Math.round(free/all.length*100);
    const c=document.createElement("div");c.className="card a";c.style.setProperty("--d",i++);
    c.innerHTML=`<div class="row"><b>${JOURS[d.getDay()].toUpperCase()} ${d.getDate()} ${MOIS[d.getMonth()]}</b>
      <span style="color:${free?"var(--green)":"var(--red)"}">${free?free+" libre"+(free>1?"s":""):"Complet"}</span></div>
      <div class="bar"><i data-w="${pct}"></i></div>
      <div class="hours">${all.filter(h=>!isPast(ds,h)).map(h=>{const b=db[ds+"_"+h];return `<button class="h ${b?"busy":"free"}" ${b?"disabled":""} data-d="${ds}" data-t="${h}">${h}</button>`}).join("")}</div>`;
    box.appendChild(c);
  });
  requestAnimationFrame(()=>requestAnimationFrame(()=>box.querySelectorAll(".bar i").forEach(e=>e.style.width=e.dataset.w+"%")));
}
$("#availList").onclick=e=>{
  const h=e.target.closest(".h.free");if(!h)return;
  tap();selDay=h.dataset.d;selTime=h.dataset.t;markDays();renderSlots(true);check();go("book");
};

function renderAdmin(){
  const db=load(),box=$("#adminList"),today=iso(new Date());
  const keys=Object.keys(db).filter(k=>k.slice(0,10)>=today).sort();
  if(!keys.length){box.innerHTML='<p class="mut">Aucun rendez-vous à venir.</p>';return}
  box.innerHTML="";
  keys.forEach((k,i)=>{
    const [d,t]=k.split("_"),r=db[k],dt=new Date(d+"T00:00");
    const el=document.createElement("div");el.className="card a";el.style.setProperty("--d",i);
    el.innerHTML=`<div class="row"><div><b>${JOURS[dt.getDay()]} ${dt.getDate()}/${pad(dt.getMonth()+1)} · ${t}</b>${d===today?'<span class="tag">AUJOURD\'HUI</span>':""}<br>
      ${esc(r.name)} · <a style="color:var(--gold)" href="tel:${esc(r.phone)}">${esc(r.phone)}</a><br><span class="mut">${esc(r.service)}</span></div>
      <button class="small">Annuler</button></div>`;
    el.querySelector("button").onclick=()=>{if(confirm("Annuler ce RDV ?")){el.classList.add("out");setTimeout(()=>{delete db[k];save(db);renderAdmin()},250)}};
    box.appendChild(el);
  });
}
$("#unlock").onclick=()=>{
  if($("#pin").value===PIN){$("#lock").style.display="none";$("#adminBox").style.display="block";renderAdmin()}
  else{toast("Code incorrect");const l=$("#lock");l.classList.remove("shake");void l.offsetWidth;l.classList.add("shake")}
};
$("#export").onclick=()=>{const a=document.createElement("a");a.href=URL.createObjectURL(new Blob([JSON.stringify(load())],{type:"application/json"}));a.download="luubarber-"+iso(new Date())+".json";a.click()};
$("#import").onclick=()=>$("#file").click();
$("#file").onchange=e=>{const f=e.target.files[0];if(!f)return;const r=new FileReader();r.onload=()=>{try{save({...load(),...JSON.parse(r.result)});renderAdmin();toast("Restauré ✓")}catch(x){toast("Fichier invalide")}};r.readAsText(f)};

const pages=["book","avail","admin"];
function go(p){
  document.querySelectorAll(".page").forEach(x=>x.classList.toggle("active",x.id===p));
  document.querySelectorAll("nav button").forEach(b=>b.classList.toggle("active",b.dataset.p===p));
  $(".pill").style.transform=`translateX(${pages.indexOf(p)*100}%)`;
  if(p==="avail")renderAvail();if(p==="book")renderSlots();
  window.scrollTo({top:0,behavior:"smooth"});
}
document.querySelectorAll("nav button").forEach(b=>b.onclick=()=>{tap();go(b.dataset.p)});

paint();renderDays();renderSlots(true);renderSvcs();
</script>
</body>
</html>

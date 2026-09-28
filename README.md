# Neural-Recuters
file:///C:/Users/smile/Desktop/attendance-calculator%20code.html
<!DOCTYPE html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="description" content="BunkBudget: plan your attendance with real SRM Trichy timetables. See what to attend, what you can skip, and get an early detention warning."><meta name="theme-color" content="#2f3cff">
<title>Bunk Budget – Attendance Planner for SRM Trichy</title>
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@600;800&family=DM+Sans:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);
--bg:#eef0ff;--card:#fff;--tx:#14163a;--mu:#5d6190;--bd:#d5d9f5;--blue:#2f3cff;--gold:#ffc933;--coral:#ff4b3e;--mint:#12b886;--skip:#c9cdf0}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1130;--card:#191c47;--tx:#eceeff;--mu:#a3a8dd;--bd:#2f3470;--blue:#7f88ff;--skip:#3a3f80}}
:root[data-theme="dark"]{--bg:#0f1130;--card:#191c47;--tx:#eceeff;--mu:#a3a8dd;--bd:#2f3470;--blue:#7f88ff;--skip:#3a3f80}
html{scroll-padding-top:env(safe-area-inset-top,0px)}*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:16px/1.55 "DM Sans",system-ui,sans-serif}
main{max-width:980px;margin:0 auto;padding:20px 16px 48px}
h1,h3,.big{font-family:"Bricolage Grotesque","DM Sans",system-ui,sans-serif}
h1{font-size:clamp(34px,7vw,64px);line-height:1;margin:18px 0 12px;font-weight:800;letter-spacing:-.03em;max-width:14ch}
.lead{color:var(--mu);max-width:52ch;margin:0 0 22px}
.hero{display:grid;grid-template-columns:1fr auto;gap:20px;align-items:end}
.demo{display:grid;grid-template-columns:repeat(6,16px);gap:5px;padding-bottom:10px}
.demo i{width:16px;height:16px;border-radius:4px;background:var(--blue)}.demo i:nth-child(n+4){background:transparent;border:2px solid var(--skip)}.demo i:nth-child(n+7):nth-child(-n+9){background:var(--gold);border:0}
@media(max-width:560px){.demo{display:none}.hero{grid-template-columns:1fr}}
.panel{background:var(--card);border:2px solid var(--tx);border-radius:22px 22px 22px 6px;padding:20px;box-shadow:6px 6px 0 var(--blue)}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:14px}
label{display:block;font-size:13px;font-weight:600;color:var(--mu);margin-bottom:5px}
input,select,textarea{width:100%;padding:11px 12px;border:2px solid var(--bd);border-radius:10px;background:var(--bg);color:var(--tx);font:inherit}
input:focus,select:focus,textarea:focus,button:focus-visible,summary:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
.subj{display:grid;grid-template-columns:1fr 120px;gap:12px;margin-top:12px}
details summary{cursor:pointer;font-weight:600;color:var(--blue);margin-top:14px}
button{margin-top:16px;width:100%;background:var(--tx);color:var(--bg);border:0;border-radius:12px;padding:15px;font:800 18px "Bricolage Grotesque",sans-serif;cursor:pointer;transition:transform .12s}
button:active{transform:scale(.98)}
.alert{margin:26px 0 0;background:var(--coral);color:#fff;border-radius:18px;padding:20px 22px;animation:shake .5s 1}
.alert .big{font-size:clamp(24px,5vw,38px);font-weight:800;display:block;line-height:1.05;margin-bottom:6px}
@keyframes shake{20%{transform:translateX(-8px)}40%{transform:translateX(8px)}60%{transform:translateX(-5px)}80%{transform:translateX(5px)}}
.stats{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:12px;margin:24px 0}
.stat{border-left:5px solid var(--blue);padding:2px 0 2px 14px}.stat b{font:800 40px/1 "Bricolage Grotesque",sans-serif;display:block}.stat span{color:var(--mu);font-size:14px}
.legend{display:flex;flex-wrap:wrap;gap:16px;font-size:14px;color:var(--mu);margin-bottom:14px}
.legend i,.t{display:inline-block;width:14px;height:14px;border-radius:4px;vertical-align:-2px;margin-right:6px}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(min(100%,420px),1fr));gap:16px}
.sc{background:var(--card);border:2px solid var(--bd);border-radius:18px;padding:18px}
.sc.bad{border-color:var(--coral)}.sc.ok{border-color:var(--mint)}
.sc header{display:flex;justify-content:space-between;gap:12px;align-items:start}
.sc h3{margin:0;font-size:19px;line-height:1.2}
.pct{font:800 32px/1 "Bricolage Grotesque",sans-serif;text-align:right}.pct small{display:block;font:400 12px "DM Sans";color:var(--mu)}
.strip{display:flex;flex-wrap:wrap;gap:4px;margin:14px 0}
.t{margin:0;background:var(--blue);animation:pop .3s backwards;animation-delay:calc(var(--i)*12ms)}
.t.g{background:var(--gold)}.t.s{background:transparent;border:2px solid var(--skip)}.t.x{background:repeating-linear-gradient(45deg,var(--coral) 0 3px,transparent 3px 6px);border:2px solid var(--coral)}
@keyframes pop{from{transform:scale(0);opacity:0}}
.facts{list-style:none;margin:0;padding:0;font-size:14px}.facts li{padding:6px 0;border-top:1px solid var(--bd)}
.facts b{font-weight:600}
.tag{font-weight:800}.tag.r{color:var(--coral)}.tag.gr{color:var(--mint)}
.note{color:var(--mu);font-size:13px;margin-top:26px}
.top{display:flex;justify-content:space-between;align-items:center;font:800 18px "Bricolage Grotesque",sans-serif;padding-bottom:6px}.top span{font:400 13px "DM Sans";color:var(--mu)}
.chip{display:inline-block;margin-left:8px;font:600 11px "DM Sans";padding:2px 8px;border-radius:99px;border:1.5px solid var(--bd);vertical-align:3px;color:var(--mu)}
.wi{margin:0 0 22px}.wi h3{margin:0 0 4px;font-size:22px}.wi input[type=range]{padding:0;border:0;accent-color:var(--blue)}
.row{display:grid;grid-template-columns:minmax(120px,1.2fr) 2fr 70px;gap:12px;align-items:center;margin-top:10px;font-size:14px}
.bar{height:10px;background:var(--skip);border-radius:6px;position:relative}.bar i{display:block;height:100%;border-radius:6px}.bar b{position:absolute;top:-4px;bottom:-4px;width:2px;background:var(--tx)}
.ghost{background:transparent;color:var(--tx);border:2px solid var(--tx);margin:0 0 20px;font-size:15px;padding:11px}
.prog{height:8px;background:var(--skip);border-radius:6px;margin:6px 0 0}.prog i{display:block;height:100%;background:var(--blue);border-radius:6px}
@media(max-width:560px){.row{grid-template-columns:1fr 60px}.row .bar{grid-column:1/3;order:3}}
.two{display:grid;grid-template-columns:repeat(auto-fit,minmax(min(100%,380px),1fr));gap:16px;margin-bottom:22px}
.leg2{display:flex;gap:12px;flex-wrap:wrap;font-size:13px;color:var(--mu);margin-top:8px}
.lrow{display:flex;justify-content:space-between;align-items:center;gap:8px;padding:6px 10px;border:1.5px solid var(--bd);border-radius:10px;margin-top:8px;font-size:14px}
.lrow button{width:auto;margin:0;padding:2px 10px;font-size:14px}
.fab{position:fixed;right:16px;bottom:calc(16px + env(safe-area-inset-bottom,0px));z-index:20;width:auto;margin:0;border-radius:99px;padding:14px 20px;background:var(--blue);color:#fff;font-size:16px;box-shadow:0 6px 18px rgba(20,22,58,.35)}
.chat{position:fixed;right:16px;bottom:calc(76px + env(safe-area-inset-bottom,0px));z-index:21;width:min(400px,calc(100vw - 32px));height:min(520px,calc(100% - 110px));background:var(--card);border:2px solid var(--tx);border-radius:20px;display:none;flex-direction:column;overflow:hidden}
.chat.on{display:flex}.chat header{padding:12px 16px;font:800 17px "Bricolage Grotesque",sans-serif;border-bottom:2px solid var(--tx)}
.msgs{flex:1;overflow-y:auto;padding:12px;display:flex;flex-direction:column;gap:8px}
.m{max-width:88%;padding:9px 12px;border-radius:14px;font-size:14px;background:var(--bg)}.m.u{align-self:flex-end;background:var(--blue);color:#fff}
.chips{display:flex;gap:6px;flex-wrap:wrap;padding:0 12px 8px}.chips span{font-size:12px;border:1.5px solid var(--bd);border-radius:99px;padding:3px 10px;cursor:pointer}
.cin{display:flex;gap:8px;padding:10px;border-top:2px solid var(--bd)}.cin button{width:auto;margin:0;padding:0 16px;font-size:15px}
.err{color:var(--coral);font-weight:600;margin-top:12px}.err:empty{display:none}
.how{margin-top:26px;box-shadow:4px 4px 0 var(--skip)}.how summary{margin:0;color:var(--tx)}.how p,.how li{font-size:14px;color:var(--mu)}.how code{background:var(--bg);padding:2px 6px;border-radius:6px;color:var(--tx)}
footer{margin-top:20px;padding-top:16px;border-top:2px solid var(--bd);font-size:13px;color:var(--mu)}
noscript{display:block;padding:16px;background:var(--coral);color:#fff}
@media(prefers-reduced-motion:reduce){*{animation:none!important}}
</style></head><body><main>
<noscript>This app needs JavaScript to run.</noscript>
<div class="top">BunkBudget<span>SRM Trichy · Odd Sem 2026-27</span></div>
<div class="hero"><div>
<h1>Know how many classes you can skip.</h1>
<p class="lead">Pick your section, type your attendance, and see every remaining class as a tile: attend it, or safely skip it.</p></div>
<div class="demo" aria-hidden="true"><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i></div></div>

<section class="panel">
 <div class="grid">
  <div><label for="sec">Your section</label><select id="sec"></select></div>
  <div><label for="today">Today</label><input id="today" type="date"></div>
  <div><label for="plan">Plan up to this date</label><input id="plan" type="date"></div>
  <div><label for="lim">Minimum attendance (%)</label><input id="lim" type="number" value="75" min="1" max="100"></div>
 </div>
 <div id="subs"></div>
 <details><summary>Semester dates and holidays</summary>
  <div class="grid" style="margin-top:12px">
   <div><label for="start">Semester start</label><input id="start" type="date" value="2026-08-03"></div>
   <div><label for="end">Last working day</label><input id="end" type="date" value="2026-11-20"></div>
   <div><label for="cut">Recovery deadline</label><input id="cut" type="date" value="2026-10-31"></div>
  </div>
  <label for="hol" style="margin-top:12px">Holidays (YYYY-MM-DD, comma separated). Sundays are always off.</label>
  <textarea id="hol" rows="2">2026-08-15,2026-09-14,2026-10-02,2026-10-19,2026-10-20,2026-11-08</textarea>
  <label for="sat" style="margin-top:12px">Saturday is a working day?</label>
  <select id="sat"><option value="0">No</option><option value="1">Yes</option></select>
 </details>
 <div id="err" class="err" role="alert"></div>
 <button id="go">Show my bunk budget</button>
</section>
<div id="out" aria-live="polite"></div>
<details class="panel how"><summary>How the numbers work</summary>
<p>Classes held so far come from your section timetable, counting each period from the semester start to yesterday (Sundays and holidays excluded). Your attendance % is applied to that count.</p>
<p>To stay at or above a limit <code>T</code>, you must attend at least <code>T% × (held + left) − attended</code> of the remaining classes. If that number is larger than the classes left, the limit cannot be reached.</p>
<ul><li>OD and medical days count as present. Absent days count against you.</li><li>Irreversible detention means that even attending every class until the recovery deadline cannot reach the limit.</li><li>Timetable source: SEEE Odd Semester 2026-27 sheets, SRM Trichy.</li></ul></details>
<footer>BunkBudget is a student project and not an official SRM tool. Semester dates and holidays are editable estimates. Always confirm your final attendance with your faculty or the college portal.</footer>
<button class="fab" id="fab" aria-label="Open Attendance Advisor">Ask Advisor</button>
<div class="chat" id="chat" role="dialog" aria-label="Attendance Advisor"><header>Attendance Advisor</header><div class="msgs" id="msgs"></div>
<div class="chips" id="chips"><span>If I take a 3-day sick leave starting tomorrow, will I fall below the limit?</span><span>Which subject is most at risk?</span><span>Can I skip 2 days and stay safe?</span></div>
<div class="cin"><input id="cq" placeholder="Ask about your attendance" aria-label="Question"><button id="csend">Send</button></div></div><script>
const RAW={
"II ECE-DS A":[{A:"Transforms & Boundary Value Problems",B:"Solid State Devices",C:"Computer Organization & Architecture",D:"Digital Logic Design",E:"EM Theory & Interference",F:"Professional Ethics",G:"Universal Human Values-II",H:"Verbal Reasoning",I:"Social Engineering",L:"Devices & Digital IC Lab"},["EAII-GGLL","CAED-GGHH","ABCD--H--","BCAF-LL--","DBEC-----"]],
"II ECE-DS B":[{A:"Transforms & Boundary Value Problems",B:"Solid State Devices",C:"Computer Organization & Architecture",D:"Digital Logic Design",E:"EM Theory & Interference",F:"Professional Ethics",G:"Universal Human Values-II",H:"Verbal Reasoning",I:"Social Engineering",L:"Devices & Digital IC Lab"},["--LL-DBCI","LL---CDEA","G----IEAD","GGHH-ACBE","H----FABC"]],
"II BME":[{A:"Transforms & Boundary Value Problems",B:"Biomedical Signals & Systems",C:"Electric & Electronic Circuits",D:"Digital Logic for Medical Systems",E:"Medical Physics",F:"Professional Ethics",G:"Universal Human Values-II",H:"Verbal Reasoning",I:"Social Engineering",L:"DLMS / EEC Lab"},["ECII-LL--","CEBA-HH--","BDA--HG--","AEBD---LL","FACD---GG"]],
"III ECE-DS":[{A:"Discrete Mathematics",B:"Microprocessor & Microcontroller",C:"VLSI Design & Technology",D:"Machine Learning for All",E:"Database Design & Management",F:"Community Connect",G:"Analytical & Logical Thinking",H:"Indian Art Form",L:"VLSI / Microprocessor Lab",P:"B-Proj"},["EBCA-----","CBDF-LL--","HBAC---GG","ADEF-----","DAEP-G-LL"]],
"III ECE-A":[{A:"Discrete Mathematics",B:"Microprocessor & Microcontroller",C:"VLSI Design & Technology",D:"System & Network on Chip",E:"Machine Learning for All",F:"Community Connect",G:"Analytical & Logical Thinking",H:"Indian Art Form",L:"VLSI / Microprocessor Lab",P:"B-Proj"},["EBBA-GG--","HDBP--G--","CADF---LL","AECF-----","DAEC-LL--"]],
"III ECE-B":[{A:"Discrete Mathematics",B:"Microprocessor & Microcontroller",C:"VLSI Design & Technology",D:"System & Network on Chip",E:"Machine Learning for All",F:"Community Connect",G:"Analytical & Logical Thinking",H:"Indian Art Form",L:"VLSI / Microprocessor Lab",P:"B-Proj"},["LL---EBAD","GG---FBDC","G----PBAH","LL---ACEF","-----CAED"]],
"III BME":[{A:"Probability & Statistics",B:"Microcontrollers & Applications",C:"Biomedical Signal Processing",D:"Biometrics",E:"Modern Wireless Comm.",F:"Principles of Medical Imaging",G:"Analytical & Logical Thinking",H:"Indian Art Form",I:"Community Connect",L:"MPMC / Bio-DSP Lab"},["GGLL-EBFH","LLG--CDAB","-----CAFD","---I-ACEB","I----FADE"]],
"IV ECE-A":[{A:"Behavioural Psychology",B:"Wireless Comm. & Antenna",C:"Computer Comm. & Network Security",D:"Semiconductor Memory Design",E:"Scripting Lang. for EDA",F:"Machine Learning for All",L:"CCNS Lab"},["C-AD-----","CDBF-----","BLEF-----","FAEB-----","CADE-----"]],
"IV ECE-B":[{A:"Behavioural Psychology",B:"Wireless Comm. & Antenna",C:"Computer Comm. & Network Security",D:"Semiconductor Memory Design",E:"Scripting Lang. for EDA",F:"Machine Learning for All",L:"CCNS Lab"},["CAEF-----","CEFB-----","CDAB-----","DBLA-----","EDF------"]]
};
// Build SEC[section][subject] = classes per weekday [Sun..Sat] from the slot grids
const SEC={};
for(const [k,[names,grid]] of Object.entries(RAW)){SEC[k]={};
 grid.forEach((row,di)=>{for(const ch of row){if(ch==="-")continue;const n=names[ch];
  (SEC[k][n]=SEC[k][n]||[0,0,0,0,0,0,0])[di+1]++;}});}
let LV=[],SMP=null,H=[],D=[],X={},SUM="";const $=id=>document.getElementById(id);
const iso=d=>d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0");
const pd=s=>new Date(s+"T12:00:00");
const t=new Date();$("today").value=iso(t);
const p=new Date(t);p.setDate(p.getDate()+14);$("plan").value=iso(p);
Object.keys(SEC).forEach(k=>$("sec").add(new Option(k,k)));
function drawSubs(){$("subs").innerHTML=Object.keys(SEC[$("sec").value]).map(s=>
 `<div class="subj"><div><label>Subject</label><input value="${s}" disabled></div><div><label>Attendance %</label><input class="pct-in" type="number" min="0" max="100" step="0.1" value="80"></div></div>`).join("");}
$("sec").onchange=drawSubs;
try{const sv=JSON.parse(localStorage.getItem("bb")||"null");if(sv&&SEC[sv.s]){$("sec").value=sv.s;drawSubs();document.querySelectorAll(".pct-in").forEach((e,i)=>{if(sv.p[i]!=null)e.value=sv.p[i]})}else drawSubs()}catch(e){drawSubs()}
function drawWI(){const N=+$("skip").value,e=new Date(X.today);e.setDate(e.getDate()+N-1);let h="",ks=0;
 D.forEach(o=>{const sk=Math.min(count(o.d,X.today,e,X.hol,X.sat),o.Re),pr=(o.a+o.Re-sk)/(o.C+o.Re)*100;ks+=sk;
  h+=`<div class="row"><span>${o.n}</span><div class="bar"><i style="width:${Math.min(pr,100)}%;background:${pr>=X.L?"var(--mint)":"var(--coral)"}"></i><b style="left:${X.L}%"></b></div><b>${pr.toFixed(1)}%</b></div>`;});
 $("wi").innerHTML=`<p class="note" style="margin:6px 0 0">${N===0?"Drag the slider to skip upcoming days.":`Skipping the next ${N} day${N>1?"s":""} (${ks} classes) and attending everything after. The line marks ${X.L}%.`}</p>${h}`;}
function count(days,from,to,hol,sat){let n=0;const d=new Date(from);
 while(d<=to){const w=d.getDay();if(w!==0&&!hol.has(iso(d))&&(w!==6||sat))n+=days[w];d.setDate(d.getDate()+1);}return n;}
const need=(a,C,R,T)=>Math.max(0,Math.ceil(T/100*(C+R)-a-1e-9));
const fmt=(x,R,label)=>x>R?`<span class="tag r">Not possible</span>`:x===0?`<span class="tag gr">Safe: skip all ${R}</span>`:`Attend <b>${x}</b> of ${R}, skip ${R-x}`;
$("go").onclick=()=>{
 const badV=[...document.querySelectorAll(".pct-in")].some(e=>e.value===""||+e.value<0||+e.value>100),badD=pd($("today").value)>pd($("end").value)||pd($("plan").value)<pd($("today").value);
 $("err").textContent=badV?"Enter an attendance between 0 and 100 for every subject.":badD?"Check your dates: the plan date must be today or later, and today must be before the last working day.":"";
 if(badV||badD)return;
 const today=pd($("today").value),plan=pd($("plan").value),end=pd($("end").value),start=pd($("start").value),cut=pd($("cut").value);
 const hol=new Set($("hol").value.split(",").map(s=>s.trim()).filter(Boolean)),sat=$("sat").value==="1",L=+$("lim").value;
 const y=new Date(today);y.setDate(y.getDate()-1);
 const subs=SEC[$("sec").value],names=Object.keys(subs),pcts=[...document.querySelectorAll(".pct-in")].map(e=>+e.value);
 D=[];SUM="";const items=[];let tot=0,totPlan=0,budget=0,cards="",doomed=[];
 names.forEach((n,i)=>{const d=subs[n];
  const C=count(d,start,y,hol,sat),Re=count(d,today,end,hol,sat),Rp=count(d,today,plan,hol,sat),Rc=count(d,today,cut,hol,sat);
  const a=pcts[i]/100*C,x=need(a,C,Re,L),x9=need(a,C,Re,90),xp=need(a,C,Rp,L);
  tot+=Re;totPlan+=Rp;
  const lost=need(a,C,Rc,L)>Rc;if(lost)doomed.push(`${n} (best ${((a+Rc)/(C+Rc)*100).toFixed(1)}% by ${$("cut").value})`);
  if(!lost&&x<=Re)budget+=Re-x;
  const bad=x>Re;let tiles="";
  for(let k=0;k<Re;k++){const c=bad?"x":k<x?"":k<Math.min(Re,Math.max(x,x9))?"g":"s";tiles+=`<i class="t ${c}" style="--i:${Math.min(k,60)}"></i>`;}
  const best=((a+Re)/(C+Re)*100).toFixed(1);
  const r=lost||bad?9:x/Math.max(Re,1),lb=lost||bad?"Lost":r>.7?"High risk":r>.3?"Watch":"Safe";D.push({n,a,C,Re,d,pct:pcts[i]});SUM+=`${n}: ${pcts[i]}% now, ${bad?"cannot reach "+L+"%":"attend "+x+"/"+Re+" to stay above "+L+"%"}\n`;
  items.push({r,h:`<article class="sc ${lost||bad?"bad":x===0?"ok":""}"><header><h3>${n}<span class="chip">${lb}</span></h3><div class="pct">${pcts[i]}%<small>now</small></div></header>
  <div class="strip" aria-label="${Re} classes left">${tiles}</div>
  <ul class="facts"><li>By ${$("plan").value}: ${fmt(xp,Rp)}</li>
  <li>By semester end: ${fmt(x,Re)}</li>
  <li>${x9>Re?`Reaching 90% is not possible (best ${best}%)`:`For 90%: attend <b>${x9}</b> of ${Re}`}</li></ul></article>`});});
 cards=items.sort((u,v)=>v.r-u.r).map(o=>o.h).join("");X={today,hol,sat,L,end,start};
 let h="";
 if(doomed.length)h+=`<div class="alert" role="alert"><span class="big">Irreversible detention</span>Even if you attend every class until ${$("cut").value}, you cannot reach ${L}% in ${doomed.join("; ")}. Meet your faculty or HoD about condonation now.</div>`;
 h+=`<div class="stats"><div class="stat"><b>${Math.max(0,Math.min(100,Math.round((today-start)/(end-start)*100)))}%</b><span>of the semester is over<div class="prog"><i style="width:${Math.max(0,Math.min(100,(today-start)/(end-start)*100))}%"></i></div></span></div><div class="stat"><b>${tot}</b><span>classes left this semester</span></div><div class="stat"><b>${totPlan}</b><span>classes until ${$("plan").value}</span></div><div class="stat"><b>${budget}</b><span>classes you can skip in total and stay above ${L}%</span></div></div>
 <div class="legend"><span><i class="t"></i>Must attend</span><span><i class="t g"></i>Attend to reach 90%</span><span><i class="t s"></i>Safe to skip</span><span><i class="t x"></i>Lost</span></div><section class="panel wi"><h3>What if I skip the next few days?</h3><input id="skip" type="range" min="0" max="30" value="0" aria-label="Days to skip"><div id="wi"></div></section><button class="ghost" id="copy">Copy summary to share</button><div id="extras"></div><div class="cards">${cards}</div>`;
 $("out").innerHTML=h;LV=[];mountExtras();$("skip").oninput=drawWI;drawWI();
 $("copy").onclick=async()=>{try{await navigator.clipboard.writeText("My attendance plan ("+$("sec").value+")\n"+SUM);$("copy").textContent="Copied";}catch(e){$("copy").textContent="Copy not allowed here";}};
 try{localStorage.setItem("bb",JSON.stringify({s:$("sec").value,p:pcts}))}catch(e){}
 $("out").scrollIntoView({behavior:"smooth"});
};

const ymd=(d,n)=>{const e=new Date(d);e.setDate(e.getDate()+n);return e};
function sim(o,lvs){let a=o.a,lost=0;const y=ymd(X.today,-1);
 lvs.forEach(l=>{const f=pd(l.from),t=pd(l.to),pe=t<y?t:y;
  if(f<=pe&&l.type!=="absent")a+=count(o.d,f,pe,X.hol,X.sat);
  const fs=f>X.today?f:X.today;if(fs<=t&&l.type==="absent")lost+=count(o.d,fs,t,X.hol,X.sat);});
 a=Math.min(a,o.C);lost=Math.min(lost,o.Re);const den=Math.max(1,o.C+o.Re);
 return{cur:a/Math.max(1,o.C)*100,fin:(a+o.Re-lost)/den*100,lost}}
function mountExtras(){$("extras").innerHTML=`<div class="two"><section class="panel"><h3 style="margin:0 0 8px;font-size:22px">Attendance health</h3><div id="charts"></div></section>
<section class="panel"><h3 style="margin:0 0 4px;font-size:22px">OD and leave simulator</h3><p class="note" style="margin:0 0 10px">OD and medical days count as present. Absent days count against you. Past OD days add back classes marked absent.</p>
<div class="grid"><div><label for="lt">Type</label><select id="lt"><option value="od">On-Duty (OD)</option><option value="medical">Medical leave</option><option value="absent">Absent / personal leave</option></select></div>
<div><label for="lf">From</label><input id="lf" type="date" value="${iso(X.today)}"></div><div><label for="ltd">To</label><input id="ltd" type="date" value="${iso(X.today)}"></div></div>
<button id="ladd" style="margin-top:12px;padding:11px;font-size:16px">Add days</button><div id="llist"></div><div id="lres"></div></section></div>`;
 $("ladd").onclick=()=>{const f=$("lf").value,t=$("ltd").value;if(!f||!t||t<f)return;LV.push({type:$("lt").value,from:f,to:t});drawAll();};drawAll();}
function drawAll(){const nm={od:"OD",medical:"Medical",absent:"Absent"};
 $("llist").innerHTML=LV.map((l,i)=>`<div class="lrow"><span><b>${nm[l.type]}</b> ${l.from} to ${l.to}</span><button class="ghost" data-i="${i}" aria-label="Remove">Remove</button></div>`).join("");
 document.querySelectorAll("#llist button").forEach(b=>b.onclick=()=>{LV.splice(+b.dataset.i,1);drawAll();});
 const R=D.map(o=>({n:o.n,b:sim(o,[]),z:sim(o,LV)}));
 $("lres").innerHTML=R.map(r=>{const dl=r.z.fin-r.b.fin;return `<div class="row"><span>${r.n}</span><div class="bar"><i style="width:${Math.min(r.z.fin,100)}%;background:${r.z.fin>=X.L?"var(--mint)":"var(--coral)"}"></i><b style="left:${X.L}%"></b></div><b>${r.z.fin.toFixed(1)}%${LV.length?`<small style="color:var(--mu)"> (${dl>=0?"+":""}${dl.toFixed(1)})</small>`:""}</b></div>`}).join("")+`<p class="note" style="margin:8px 0 0">Final percentage at semester end if you attend every other class.</p>`;
 charts(R)}
function charts(R){const n=R.length,avg=R.reduce((s,r)=>s+r.z.fin,0)/Math.max(n,1),g=R.filter(r=>r.z.fin>=90).length,y=R.filter(r=>r.z.fin>=X.L&&r.z.fin<90).length,rd=n-g-y,C=2*Math.PI*52;
 let off=0;const seg=(c,v)=>{const l=v/Math.max(n,1)*C,e=`<circle r="52" cx="70" cy="70" fill="none" stroke="${c}" stroke-width="22" stroke-dasharray="${l} ${C-l}" stroke-dashoffset="${-off}" transform="rotate(-90 70 70)"/>`;off+=l;return e};
 const bars=R.map((r,i)=>{const yy=8+i*34,w=v=>Math.min(v,100)*3.2;return `<text x="0" y="${yy+9}" font-size="11" fill="var(--mu)">${r.n.length>22?r.n.slice(0,21)+"…":r.n}</text><rect x="0" y="${yy+13}" width="${w(r.b.cur)}" height="6" rx="3" fill="var(--skip)"/><rect x="0" y="${yy+21}" width="${w(r.z.fin)}" height="8" rx="4" fill="${r.z.fin>=X.L?"var(--mint)":"var(--coral)"}"/><text x="${w(Math.max(r.b.cur,r.z.fin))+6}" y="${yy+29}" font-size="11" fill="var(--tx)">${r.z.fin.toFixed(0)}%</text>`}).join("");
 $("charts").innerHTML=`<div style="display:flex;gap:16px;align-items:center;flex-wrap:wrap"><svg width="140" height="140" viewBox="0 0 140 140" role="img" aria-label="Health ${avg.toFixed(0)} percent"><circle r="52" cx="70" cy="70" fill="none" stroke="var(--skip)" stroke-width="22"/>${seg("var(--mint)",g)}${seg("var(--gold)",y)}${seg("var(--coral)",rd)}<text x="70" y="70" text-anchor="middle" font-size="26" font-weight="800" fill="var(--tx)" font-family="Bricolage Grotesque,sans-serif">${avg.toFixed(0)}%</text><text x="70" y="88" text-anchor="middle" font-size="10" fill="var(--mu)">projected avg</text></svg>
 <div class="leg2" style="flex-direction:column"><span><i class="t" style="background:var(--mint)"></i>${g} above 90%</span><span><i class="t g"></i>${y} between ${X.L}% and 90%</span><span><i class="t" style="background:var(--coral)"></i>${rd} below ${X.L}%</span></div></div>
 <svg viewBox="0 0 380 ${n*34+14}" width="100%" style="margin-top:14px" role="img" aria-label="Attendance by subject">${bars}<line x1="${X.L*3.2}" x2="${X.L*3.2}" y1="0" y2="${n*34+8}" stroke="var(--tx)" stroke-dasharray="3 3"/></svg>
 <div class="leg2"><span><i class="t" style="background:var(--skip)"></i>Now</span><span><i class="t" style="background:var(--mint)"></i>Final (with your leaves)</span><span>Dashed line: ${X.L}%</span></div>`}
// ---- Attendance Advisor ----
try{if(window.claude&&claude.use)claude.use("sample").then(x=>{SMP=x}).catch(()=>{})}catch(e){}
function findSubj(q){q=q.toLowerCase();return D.filter(o=>o.n.toLowerCase().split(/[^a-z]+/).some(w=>w.length>3&&q.includes(w.slice(0,5))))}
function simTool(a){const q=(a.subject||"").toLowerCase();let list=q&&q!=="all"?findSubj(q):D;
 if(q&&q!=="all"&&!list.length)return{error:"Subject not found",available:D.map(o=>o.n)};
 const f=a.start_date||iso(ymd(X.today,1)),days=Math.max(1,+a.days||1),t=iso(ymd(pd(f),days-1)),ex=a.kind==="absent"?"absent":a.kind||"absent";
 return{limit:X.L,window:f+" to "+t,results:list.map(o=>{const b=sim(o,[]),ab=sim(o,[{type:"absent",from:f,to:t}]),cl=count(o.d,pd(f)>X.today?pd(f):X.today,pd(t),X.hol,X.sat);
  return{subject:o.n,current_pct:+b.cur.toFixed(1),classes_in_window:cl,final_pct_if_absent:+ab.fin.toFixed(1),final_pct_if_excused_OD_or_medical:+b.fin.toFixed(1),final_pct_if_absent_below_limit:ab.fin<X.L,final_pct_without_leave:+b.fin.toFixed(1),classes_left_in_semester:o.Re}})}}
function local(q){const l=q.toLowerCase();
 if(/risk|worst|danger|weak/.test(l)){const r=D.map(o=>({n:o.n,f:sim(o,LV).fin})).sort((a,b)=>a.f-b.f)[0];return `**${r.n}** is your weakest subject, heading for ${r.f.toFixed(1)}% by semester end (limit ${X.L}%).`}
 const days=+(l.match(/(\d+)\s*-?\s*day/)||l.match(/(\d+)/)||[0,1])[1]||1,od=/\bod\b|on.?duty/.test(l),med=/medical/.test(l);
 const st=/today/.test(l)?iso(X.today):(l.match(/\d{4}-\d{2}-\d{2}/)||[iso(ymd(X.today,1))])[0];
 const subj=findSubj(l),r=simTool({subject:subj.length===1?subj[0].n:"all",start_date:st,days});
 if(r.error)return `I couldn't find that subject. Your subjects are: ${r.available.join(", ")}.`;
 const bad=r.results.filter(x=>x.final_pct_if_absent_below_limit);
 let t=`For ${days} day${days>1?"s":""} from ${st}:\n`+r.results.map(x=>`- ${x.subject}: ${x.classes_in_window} classes missed, ${x.current_pct}% now, ${x.final_pct_if_absent}% at semester end`).join("\n");
 if(od||med)t+=`\nAs ${od?"OD":"medical leave"} these count as present, so your final % stays unchanged.`;
 else t+=bad.length?`\nWarning: this pushes ${bad.map(x=>x.subject).join(", ")} below ${X.L}%. Get a medical certificate or OD approval if you can.`:`\nYou stay above ${X.L}% in every subject you asked about.`;return t}
const fmtMsg=t=>t.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/\*\*(.+?)\*\*/g,"<b>$1</b>").replace(/\n/g,"<br>");
function addMsg(t,u){const m=document.createElement("div");m.className="m"+(u?" u":"");m.innerHTML=fmtMsg(t);$("msgs").appendChild(m);$("msgs").scrollTop=1e9;return m}
async function ask(q){if(!D.length){$("go").click();}if(!D.length)return "Enter your attendance first.";
 if(SMP){try{const ctx=D.map(o=>({subject:o.n,current_pct:o.pct,classes_held:o.C,classes_left:o.Re}));
  const inp=`You are Attendance Advisor for an SRM Trichy student. Today is ${iso(X.today)}, minimum attendance ${X.L}%, semester ends ${iso(X.end)}. Dashboard: ${JSON.stringify(ctx)}. Leaves already planned: ${JSON.stringify(LV)}. Always call the simulate tool for any number and never do the math yourself. "Tomorrow" is ${iso(ymd(X.today,1))}. Sick leave without a certificate counts as absent. Reply in at most 5 short sentences with the exact numbers, a clear warning if any subject drops below the limit, and one practical tip. If a subject is not in the dashboard, say so and list the available ones.\nRecent chat: ${H.slice(-4).join(" | ")}\nQuestion: ${q}`;
  const r=await SMP(inp,{cache:false,tools:[{name:"simulate",description:"Project attendance if the student is absent, on OD or on medical leave for consecutive calendar days.",inputSchema:{type:"object",properties:{subject:{type:"string",description:"Subject name or 'all'"},start_date:{type:"string",description:"YYYY-MM-DD"},days:{type:"number"},kind:{type:"string",enum:["absent","od","medical"]}},required:["days"]},execute:simTool}]});
  if(r&&r.text)return r.text}catch(e){}}
 return local(q)}
async function send(q){q=(q||$("cq").value).trim();if(!q)return;$("cq").value="";$("chips").style.display="none";addMsg(q,1);const w=addMsg("Working out the numbers…");
 const a=await ask(q);H.push("Q:"+q,"A:"+a.slice(0,200));w.innerHTML=fmtMsg(a);$("msgs").scrollTop=1e9}
$("fab").onclick=()=>{$("chat").classList.toggle("on");if(!$("msgs").children.length)addMsg("Hi! Ask me about leaves, OD or how many classes you can skip. I use the numbers on your dashboard.")};
$("csend").onclick=()=>send();$("cq").onkeydown=e=>{if(e.key==="Enter")send()};
document.querySelectorAll("#chips span").forEach(c=>c.onclick=()=>send(c.textContent));
</script></main></body></html>
import React, { useState } from 'react';
import {
  Search,
  Sparkles,
  ArrowRight,
  AlertTriangle,
  RotateCcw,
  Clock,
  CheckCircle2,
  Snowflake,
  Users,
  Laptop,
  Building2,
} from 'lucide-react';
import { DayOfWeek, FloorId, FLOORS } from '../data/roomsData';
import {
  formatDurationMinutes,
  formatTime12h,
  RoomAvailabilityStatus,
} from '../utils/occupancyEngine';

export interface ParsedAIIntent {
  floorPreference: FloorId | 'all';
  requiresAC: boolean;
  minDurationMinutes: number;
  teamOrGroup: boolean;
  quietPreference: boolean;
  roomTypePreference: string;
}

export interface AIRoomFinderResponse {
  resolvedDay: DayOfWeek;
  resolvedTime: string;
  parsedIntent: ParsedAIIntent;
  summaryReasoning: string;
  recommendedRoomIds: string[];
  kickOutWarnings: string[];
}

interface AIRoomFinderProps {
  currentDay: DayOfWeek;
  currentTime: string;
  allStatuses: RoomAvailabilityStatus[];
  onApplyAIFilters: (
    intent: ParsedAIIntent,
    resolvedDay: DayOfWeek,
    resolvedTime: string,
    recommendedIds: string[]
  ) => void;
  onSelectRoom: (roomStatus: RoomAvailabilityStatus) => void;
  onClearAIHighlight: () => void;
  activeRecommendedIds: string[];
}

const QUICK_PROMPT_CARDS = [
  {
    label: 'Ground Floor AC for Team (2h)',
    prompt: 'I need an AC room on the ground floor for me and my team for the next 2 hours.',
    icon: Snowflake,
    colorClass: 'text-sky-600 bg-sky-50 hover:bg-sky-100 border-sky-200',
  },
  {
    label: 'Quiet 1st Floor Study (3h+)',
    prompt: 'Find a quiet AC classroom on the first floor free for at least 3 hours.',
    icon: Building2,
    colorClass: 'text-teal-700 bg-teal-50 hover:bg-teal-100 border-teal-200',
  },
  {
    label: 'Computer Lab with Power',
    prompt: 'Computer lab with bench power outlets free right now for 90 minutes.',
    icon: Laptop,
    colorClass: 'text-indigo-700 bg-indigo-50 hover:bg-indigo-100 border-indigo-200',
  },
  {
    label: '2nd Floor Project Group',
    prompt: 'Where can our project group sit on the second floor without getting kicked out until 4 PM?',
    icon: Users,
    colorClass: 'text-violet-700 bg-violet-50 hover:bg-violet-100 border-violet-200',
  },
];

export const AIRoomFinder: React.FC<AIRoomFinderProps> = ({
  currentDay,
  currentTime,
  allStatuses,
  onApplyAIFilters,
  onSelectRoom,
  onClearAIHighlight,
  activeRecommendedIds,
}) => {
  const [query, setQuery] = useState(
    'I need an AC room on the ground floor for me and my team for the next 2 hours.'
  );
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);
  const [result, setResult] = useState<AIRoomFinderResponse | null>(null);

  const handleAnalyze = async (promptText?: string) => {
    const targetQuery = (promptText ?? query).trim();
    if (!targetQuery) return;
    if (promptText) setQuery(promptText);

    setLoading(true);
    setError(null);

    try {
      const response = await fetch('/api/ai-room-finder', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          query: targetQuery,
          currentDay,
          currentTime,
        }),
      });

      const data = await response.json();
      if (!response.ok) {
        throw new Error(data.error || 'Failed to process AI room search.');
      }

      setResult(data);
      onApplyAIFilters(
        data.parsedIntent,
        data.resolvedDay,
        data.resolvedTime,
        data.recommendedRoomIds || []
      );
    } catch (err: any) {
      setError(err.message || 'Unable to reach the AI Room Finder service.');
    } finally {
      setLoading(false);
    }
  };

  const handleReset = () => {
    setResult(null);
    setError(null);
    onClearAIHighlight();
  };

  const recommendedRooms = result
    ? result.recommendedRoomIds
        .map((id) => allStatuses.find((s) => s.room.id === id))
        .filter((s): s is RoomAvailabilityStatus => Boolean(s))
    : [];

  return (
    <section
      id="ai-finder"
      className="bg-white border-2 border-indigo-100 rounded-2xl overflow-hidden shadow-sm transition-all"
    >
      {/* Colorful Top Gradient Bar */}
      <div className="h-1.5 w-full bg-gradient-to-r from-indigo-600 via-violet-500 to-teal-500" />

      <div className="p-6 bg-gradient-to-b from-indigo-50/40 via-white to-white">
        <div className="flex flex-col lg:flex-row lg:items-center lg:justify-between gap-4 pb-4 border-b border-indigo-100/80">
          <div className="flex items-start gap-3.5">
            <div className="w-10 h-10 rounded-xl bg-gradient-to-br from-indigo-600 to-teal-600 text-white flex items-center justify-center shrink-0 shadow-sm">
              <Sparkles className="w-5 h-5" />
            </div>
            <div>
              <h2 className="text-lg font-bold text-slate-900 tracking-tight">
                Smart AI Room Finder
              </h2>
              <p className="text-sm text-slate-600 mt-0.5">
                Just type what you need in plain English — floor, AC, group size, or how many hours. We check all 10 timetables so you don't get kicked out!
              </p>
            </div>
          </div>

          <div className="flex items-center gap-2 text-xs font-mono tabular-nums bg-indigo-50/80 text-indigo-900 px-3.5 py-2 rounded-lg border border-indigo-200/60 shrink-0 self-start lg:self-auto">
            <Clock className="w-3.5 h-3.5 text-indigo-600" />
            <span>Checking for:</span>
            <strong className="font-bold">{currentDay}</strong>
            <span aria-hidden="true">·</span>
            <strong className="font-bold">{formatTime12h(currentTime)}</strong>
          </div>
        </div>

        {/* Smart Text Bar */}
        <form
          onSubmit={(e) => {
            e.preventDefault();
            handleAnalyze();
          }}
          className="mt-5"
        >
          <div className="flex flex-col sm:flex-row items-stretch sm:items-center gap-3">
            <div className="relative flex-1">
              <Search className="w-5 h-5 text-indigo-500 absolute left-4 top-1/2 -translate-y-1/2 pointer-events-none" />
              <input
                type="text"
                value={query}
                onChange={(e) => setQuery(e.target.value)}
                placeholder='Try: "I need an AC room on the ground floor for me and my team for the next 2 hours."'
                className="w-full pl-12 pr-4 py-3.5 bg-white border-2 border-slate-200 rounded-xl text-sm text-slate-900 placeholder:text-slate-400 focus:outline-none focus:border-indigo-600 focus:ring-4 focus:ring-indigo-500/10 transition-all shadow-2xs"
              />
            </div>
            <div className="flex items-center gap-2 shrink-0">
              <button
                type="submit"
                disabled={loading || !query.trim()}
                className="w-full sm:w-auto px-6 py-3.5 bg-gradient-to-r from-indigo-600 to-teal-600 hover:from-indigo-700 hover:to-teal-700 disabled:from-slate-400 disabled:to-slate-400 text-white text-sm font-semibold rounded-xl shadow-sm hover:shadow-md transition-all flex items-center justify-center gap-2 whitespace-nowrap cursor-pointer"
              >
                <Sparkles className="w-4 h-4 text-teal-200" />
                <span>{loading ? 'Scanning 10 Timetables...' : 'Find My Room'}</span>
              </button>
              {(result || activeRecommendedIds.length > 0) && (
                <button
                  type="button"
                  onClick={handleReset}
                  className="px-4 py-3.5 bg-slate-100 hover:bg-slate-200 text-slate-700 text-sm font-semibold rounded-xl transition-colors flex items-center gap-1.5 whitespace-nowrap cursor-pointer"
                  title="Clear AI search and reset filters"
                >
                  <RotateCcw className="w-4 h-4" />
                  <span>Reset</span>
                </button>
              )}
            </div>
          </div>
        </form>

        {/* One-Click Friendly Prompt Starters */}
        <div className="mt-4">
          <div className="text-xs font-semibold text-slate-500 mb-2">
            Or tap a quick student scenario:
          </div>
          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-2.5">
            {QUICK_PROMPT_CARDS.map((card, idx) => {
              const IconComponent = card.icon;
              return (
                <button
                  key={idx}
                  type="button"
                  onClick={() => handleAnalyze(card.prompt)}
                  disabled={loading}
                  className={`text-left p-2.5 rounded-xl border transition-all cursor-pointer flex items-start gap-2.5 ${card.colorClass}`}
                >
                  <IconComponent className="w-4 h-4 shrink-0 mt-0.5" />
                  <div className="min-w-0">
                    <div className="text-xs font-bold truncate">{card.label}</div>
                    <div className="text-[11px] opacity-80 line-clamp-1 mt-0.5">
                      "{card.prompt}"
                    </div>
                  </div>
                </button>
              );
            })}
          </div>
        </div>

        {/* Loading Skeleton State */}
        {loading && (
          <div className="mt-6 pt-5 border-t border-indigo-100 animate-pulse space-y-3">
            <div className="h-4 bg-indigo-100 rounded w-1/3" />
            <div className="h-14 bg-indigo-50 rounded-xl w-full" />
            <div className="grid grid-cols-1 md:grid-cols-3 gap-3">
              <div className="h-28 bg-slate-100 rounded-xl" />
              <div className="h-28 bg-slate-100 rounded-xl" />
              <div className="h-28 bg-slate-100 rounded-xl" />
            </div>
          </div>
        )}

        {/* Error State */}
        {error && !loading && (
          <div className="mt-5 p-4 bg-rose-50 border border-rose-200 rounded-xl flex items-start justify-between gap-4">
            <div className="flex items-start gap-2.5 text-sm text-rose-900">
              <AlertTriangle className="w-4 h-4 text-rose-600 shrink-0 mt-0.5" />
              <div>
                <p className="font-semibold">Couldn't complete AI Room Search</p>
                <p className="text-xs text-rose-700 mt-0.5">{error}</p>
              </div>
            </div>
            <button
              type="button"
              onClick={() => handleAnalyze()}
              className="px-3 py-1.5 bg-white border border-rose-200 text-xs font-semibold text-rose-700 rounded-lg hover:bg-rose-100 whitespace-nowrap cursor-pointer"
            >
              Try Again
            </button>
          </div>
        )}

        {/* AI Results Breakdown */}
        {result && !loading && (
          <div className="mt-6 pt-5 border-t border-indigo-100 space-y-4">
            {/* Extracted Intent Summary */}
            <div className="flex flex-wrap items-center justify-between gap-2 text-xs text-slate-600 bg-slate-50 px-4 py-2.5 rounded-xl border border-slate-200/80">
              <div className="flex flex-wrap items-center gap-2">
                <span className="font-bold text-indigo-950">What we looked for:</span>
                <span>
                  Floor:{' '}
                  <strong className="font-semibold text-indigo-700">
                    {result.parsedIntent.floorPreference === 'all'
                      ? 'Any Floor'
                      : FLOORS.find((f) => f.id === result.parsedIntent.floorPreference)?.name ||
                        result.parsedIntent.floorPreference}
                  </strong>
                </span>
                <span aria-hidden="true">·</span>
                <span>
                  Climate:{' '}
                  <strong className="font-semibold text-sky-700">
                    {result.parsedIntent.requiresAC ? 'AC Only' : 'Any Climate'}
                  </strong>
                </span>
                <span aria-hidden="true">·</span>
                <span className="font-mono tabular-nums">
                  Duration:{' '}
                  <strong className="font-semibold text-emerald-700">
                    {formatDurationMinutes(result.parsedIntent.minDurationMinutes || 60)}+
                  </strong>
                </span>
                <span aria-hidden="true">·</span>
                <span>
                  Seating:{' '}
                  <strong className="font-semibold text-violet-700">
                    {result.parsedIntent.teamOrGroup ? 'Team / Group Friendly' : 'Solo or Group'}
                  </strong>
                </span>
              </div>
              <span className="font-mono tabular-nums text-emerald-700 font-bold">
                {recommendedRooms.length} Best{' '}
                {recommendedRooms.length === 1 ? 'Match' : 'Matches'} Found
              </span>
            </div>

            {/* AI Natural Language Recommendation Box */}
            <div className="bg-gradient-to-r from-indigo-50/90 via-teal-50/60 to-emerald-50/70 border-l-4 border-indigo-600 rounded-r-xl px-4 py-3.5 text-sm text-slate-800 leading-relaxed">
              <span className="font-bold text-indigo-950">AI Recommendation: </span>
              {result.summaryReasoning}
            </div>

            {/* Matched Rooms Strip */}
            {recommendedRooms.length > 0 ? (
              <div>
                <h3 className="text-xs font-bold text-slate-600 mb-2.5">
                  Best Empty Rooms for You Right Now (Click any room to view its full day timetable):
                </h3>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-3.5">
                  {recommendedRooms.map((item, index) => (
                    <div
                      key={item.room.id}
                      onClick={() => onSelectRoom(item)}
                      className="group border-2 border-emerald-300/80 bg-gradient-to-b from-emerald-50/40 to-white hover:border-emerald-500 rounded-xl p-4 shadow-2xs hover:shadow-md transition-all cursor-pointer flex flex-col justify-between"
                    >
                      <div>
                        <div className="flex items-center justify-between gap-2">
                          <div className="flex items-center gap-2">
                            <span className="w-6 h-6 rounded-md bg-emerald-600 text-white font-mono text-xs font-bold flex items-center justify-center tabular-nums">
                              #{index + 1}
                            </span>
                            <span className="font-mono text-lg font-bold text-slate-900 tabular-nums">
                              {item.room.code}
                            </span>
                          </div>
                          <div className="flex items-center gap-1 text-xs font-bold text-emerald-700 font-mono tabular-nums">
                            <CheckCircle2 className="w-4 h-4 text-emerald-600 shrink-0" />
                            <span>Free {item.freeDurationFormatted}</span>
                          </div>
                        </div>

                        <p className="text-xs font-semibold text-slate-700 mt-1.5">
                          {item.room.name}
                        </p>

                        <div className="flex flex-wrap items-center gap-2 text-xs text-slate-600 mt-2">
                          <span className="font-medium text-sky-700">
                            {item.room.isAC ? '❄️ AC Room' : '🌿 Non-AC'}
                          </span>
                          <span aria-hidden="true">·</span>
                          <span className="font-mono tabular-nums">{item.room.capacity} Seats</span>
                          <span aria-hidden="true">·</span>
                          <span>{item.room.powerOutlets}</span>
                        </div>
                      </div>

                      <div className="mt-3.5 pt-2.5 border-t border-emerald-200/60 flex items-center justify-between text-xs">
                        <span className="text-emerald-900 font-medium font-mono tabular-nums truncate">
                          {item.isFreeRestOfDay
                            ? 'Free rest of the day!'
                            : `Safe until ${formatTime12h(item.freeUntilTime)}`}
                        </span>
                        <span className="text-indigo-700 font-bold inline-flex items-center gap-1 group-hover:translate-x-0.5 transition-transform shrink-0">
                          <span>View Timetable</span>
                          <ArrowRight className="w-3.5 h-3.5" />
                        </span>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            ) : (
              <div className="p-4 bg-amber-50 border border-amber-200 rounded-xl text-sm text-amber-900">
                No rooms strictly matched every constraint simultaneously. Try lowering the minimum duration or checking another floor below.
              </div>
            )}

            {/* Kick-Out Warnings */}
            {result.kickOutWarnings && result.kickOutWarnings.length > 0 && (
              <div className="bg-amber-50/70 border border-amber-200/80 rounded-xl p-3.5">
                <div className="flex items-center gap-2 text-xs font-bold text-amber-900 mb-1.5">
                  <AlertTriangle className="w-4 h-4 text-amber-600 shrink-0" />
                  <span>Heads Up — Rooms to Avoid on This Floor (Occupied or Professor Arriving Soon):</span>
                </div>
                <ul className="space-y-1 text-xs text-amber-900/90 pl-6 list-disc">
                  {result.kickOutWarnings.map((warn, i) => (
                    <li key={i}>{warn}</li>
                  ))}
                </ul>
              </div>
            )}
          </div>
        )}
      </div>
    </section>
  );
};
import React, { useEffect, useMemo, useState } from 'react';
import {
  Box,
  Layers,
  Share2,
  MapPin,
  Clock,
  CheckCircle2,
  AlertTriangle,
  Lock,
  Snowflake,
  Users,
  Plug,
  Copy,
  Check,
  Sparkles,
  RotateCw,
  Maximize2,
  Calendar,
  MessageCircle,
} from 'lucide-react';
import { FloorId, FLOORS } from '../data/roomsData';
import {
  formatTime12h,
  RoomAvailabilityStatus,
} from '../utils/occupancyEngine';

interface Building3DMapProps {
  statuses: RoomAvailabilityStatus[];
  selectedRoomId: string;
  onSelectRoomId: (roomId: string) => void;
  claimedRoomId: string | null;
  onClaimRoom: (roomId: string | null) => void;
  aiRecommendedIds: string[];
  onOpenFullSchedule: (status: RoomAvailabilityStatus) => void;
}

type CameraAngle = 'iso-left' | 'front' | 'iso-right' | 'top-down';

const SQUAD_EXTRAS = [
  { id: 'ac', label: '❄️ AC is blasting', text: ' AC is on and cool ❄️.' },
  { id: 'laptop', label: '🔌 Bring chargers', text: ' Bring your laptops & chargers 🔌.' },
  { id: 'project', label: '🚀 Project sprint', text: ' Let’s finish the project sprint 🚀!' },
  { id: 'quiet', label: '🤫 Quiet study', text: ' Super quiet right now for exam prep.' },
];

export const Building3DMap: React.FC<Building3DMapProps> = ({
  statuses,
  selectedRoomId,
  onSelectRoomId,
  claimedRoomId,
  onClaimRoom,
  aiRecommendedIds,
  onOpenFullSchedule,
}) => {
  const [viewMode, setViewMode] = useState<'stack-3d' | FloorId>('stack-3d');
  const [cameraAngle, setCameraAngle] = useState<CameraAngle>('iso-left');
  const [explodedSpacing, setExplodedSpacing] = useState<boolean>(true);

  // Live second-by-second countdown state
  const [secondsElapsed, setSecondsElapsed] = useState<number>(0);

  // Squad Share customization state
  const [selectedExtras, setSelectedExtras] = useState<string[]>([]);
  const [customNote, setCustomNote] = useState<string>('');
  const [copiedToast, setCopiedToast] = useState<boolean>(false);

  const activeStatus = useMemo(() => {
    return (
      statuses.find((s) => s.room.id === selectedRoomId) ||
      statuses.find((s) => s.room.id === 'IST-509') ||
      statuses[0]
    );
  }, [statuses, selectedRoomId]);

  // Best alternative empty room on the exact same floor (for zero-stair backup/hop)
  const sameFloorBackup = useMemo(() => {
    if (!activeStatus) return null;
    const candidates = statuses
      .filter(
        (s) =>
          s.room.floorId === activeStatus.room.floorId &&
          s.room.id !== activeStatus.room.id &&
          s.isCurrentlyEmpty
      )
      .sort((a, b) => b.freeDurationMinutes - a.freeDurationMinutes);
    return candidates[0] || null;
  }, [statuses, activeStatus]);

  // Reset ticking seconds when room or query time changes
  useEffect(() => {
    setSecondsElapsed(0);
  }, [activeStatus?.room.id, activeStatus?.queryTime, activeStatus?.day]);

  // 1-second live countdown ticker
  useEffect(() => {
    const timer = setInterval(() => {
      setSecondsElapsed((prev) => prev + 1);
    }, 1000);
    return () => clearInterval(timer);
  }, []);

  // Compute live HH:MM:SS remaining
  const totalInitialSeconds = useMemo(() => {
    if (!activeStatus) return 0;
    if (activeStatus.isCurrentlyEmpty) {
      return Math.max(0, activeStatus.freeDurationMinutes * 60);
    } else {
      return Math.max(0, (activeStatus.clearsInMinutes || 0) * 60);
    }
  }, [activeStatus]);

  const remainingSeconds = Math.max(0, totalInitialSeconds - secondsElapsed);
  const hoursLeft = Math.floor(remainingSeconds / 3600);
  const minutesLeft = Math.floor((remainingSeconds % 3600) / 60);
  const secsLeft = remainingSeconds % 60;

  // Build the pre-filled WhatsApp Squad message
  const squadWhatsAppMessage = useMemo(() => {
    if (!activeStatus) return '';
    const roomCode = activeStatus.room.code;
    const untilText = activeStatus.isCurrentlyEmpty
      ? activeStatus.isFreeRestOfDay
        ? '5:05 PM (rest of the day)'
        : formatTime12h(activeStatus.freeUntilTime)
      : `after ${formatTime12h(activeStatus.clearsAtTime || '17:05')}`;

    const extrasText = selectedExtras
      .map((id) => SQUAD_EXTRAS.find((e) => e.id === id)?.text || '')
      .join('');

    const extraCustom = customNote.trim() ? ` ${customNote.trim()}` : '';

    return `📍 Heading to ${roomCode}. It's free until ${untilText}. Come fast!${extrasText}${extraCustom}`;
  }, [activeStatus, selectedExtras, customNote]);

  const whatsappUrl = `https://wa.me/?text=${encodeURIComponent(
    squadWhatsAppMessage
  )}`;

  const handleCopyMessage = async () => {
    try {
      await navigator.clipboard.writeText(squadWhatsAppMessage);
      setCopiedToast(true);
      setTimeout(() => setCopiedToast(false), 2500);
    } catch {
      setCopiedToast(true);
      setTimeout(() => setCopiedToast(false), 2500);
    }
  };

  const toggleExtra = (id: string) => {
    setSelectedExtras((prev) =>
      prev.includes(id) ? prev.filter((item) => item !== id) : [...prev, id]
    );
  };

  // Order floors from top (Third Floor) to bottom (Ground Floor) for realistic vertical building stack
  const floorsTopDown = useMemo(() => [...FLOORS].reverse(), []);
  const visibleFloors =
    viewMode === 'stack-3d'
      ? floorsTopDown
      : floorsTopDown.filter((f) => f.id === viewMode);

  // Camera transform style for 3D floors
  const getSlabTransformStyle = (index: number): React.CSSProperties => {
    if (viewMode !== 'stack-3d') {
      if (cameraAngle === 'top-down') {
        return {
          transform: 'perspective(1200px) rotateX(0deg) rotateZ(0deg)',
        };
      }
      return {
        transform: 'perspective(1200px) rotateX(28deg) rotateZ(0deg)',
      };
    }

    const verticalGap = explodedSpacing ? index * 18 : index * 4;
    switch (cameraAngle) {
      case 'iso-left':
        return {
          transform: `perspective(1500px) rotateX(46deg) rotateZ(-18deg) translateY(${verticalGap}px)`,
        };
      case 'iso-right':
        return {
          transform: `perspective(1500px) rotateX(46deg) rotateZ(18deg) translateY(${verticalGap}px)`,
        };
      case 'front':
        return {
          transform: `perspective(1400px) rotateX(35deg) rotateZ(0deg) translateY(${verticalGap}px)`,
        };
      case 'top-down':
        return {
          transform: 'perspective(1400px) rotateX(0deg) rotateZ(0deg)',
        };
    }
  };

  return (
    <section
      id="map-3d"
      className="bg-slate-900 text-white rounded-2xl border border-slate-800 shadow-xl overflow-hidden"
    >
      {/* Top Header Bar of the 3D Map */}
      <div className="px-6 py-4 bg-gradient-to-r from-slate-900 via-indigo-950 to-slate-900 border-b border-slate-800 flex flex-col lg:flex-row lg:items-center justify-between gap-4">
        <div className="flex items-start sm:items-center gap-3.5">
          <div className="w-10 h-10 rounded-xl bg-gradient-to-br from-teal-400 to-indigo-600 text-slate-950 flex items-center justify-center shrink-0 shadow-md shadow-teal-500/20">
            <Box className="w-5 h-5 stroke-[2.2]" />
          </div>
          <div>
            <div className="flex items-center gap-2.5 flex-wrap">
              <h2 className="text-lg font-bold tracking-tight text-white">
                Interactive 3D Campus Building Map & Live Countdown
              </h2>
              <span className="text-xs font-semibold text-teal-300 bg-teal-500/15 border border-teal-500/30 px-2.5 py-0.5 rounded-md">
                Click any room to start timer & invite squad
              </span>
            </div>
            <p className="text-xs text-slate-400 mt-0.5">
              Rooms glow green when empty, amber when a professor is arriving soon, and red when occupied.
            </p>
          </div>
        </div>

        {/* Floor & 3D Camera Controls */}
        <div className="flex flex-wrap items-center gap-2">
          {/* Floor View Selector */}
          <div className="flex items-center gap-1 p-1 bg-slate-800/90 border border-slate-700 rounded-xl">
            <button
              type="button"
              onClick={() => setViewMode('stack-3d')}
              className={`px-3 py-1.5 text-xs font-semibold rounded-lg transition-all cursor-pointer flex items-center gap-1.5 ${
                viewMode === 'stack-3d'
                  ? 'bg-gradient-to-r from-teal-500 to-emerald-500 text-slate-950 shadow-sm'
                  : 'text-slate-300 hover:text-white'
              }`}
            >
              <Layers className="w-3.5 h-3.5" />
              <span>All 4 Floors (3D)</span>
            </button>
            {FLOORS.map((fl) => (
              <button
                key={fl.id}
                type="button"
                onClick={() => setViewMode(fl.id)}
                className={`px-2.5 py-1.5 text-xs font-semibold rounded-lg transition-all cursor-pointer ${
                  viewMode === fl.id
                    ? 'bg-indigo-600 text-white shadow-sm'
                    : 'text-slate-300 hover:text-white'
                }`}
              >
                {fl.shortName}
              </button>
            ))}
          </div>

          {/* Camera Angle Switcher */}
          <div className="flex items-center gap-1 p-1 bg-slate-800/90 border border-slate-700 rounded-xl">
            <button
              type="button"
              onClick={() =>
                setCameraAngle((prev) =>
                  prev === 'iso-left'
                    ? 'front'
                    : prev === 'front'
                    ? 'iso-right'
                    : prev === 'iso-right'
                    ? 'top-down'
                    : 'iso-left'
                )
              }
              className="px-2.5 py-1.5 text-xs font-medium text-slate-200 hover:text-white hover:bg-slate-700/70 rounded-lg transition-colors flex items-center gap-1.5 cursor-pointer"
              title="Rotate 3D Camera Angle"
            >
              <RotateCw className="w-3.5 h-3.5 text-teal-400" />
              <span>
                {cameraAngle === 'iso-left'
                  ? '3D Iso Left'
                  : cameraAngle === 'front'
                  ? '3D Front Tilt'
                  : cameraAngle === 'iso-right'
                  ? '3D Iso Right'
                  : '2D Blueprint'}
              </span>
            </button>
            {viewMode === 'stack-3d' && cameraAngle !== 'top-down' && (
              <button
                type="button"
                onClick={() => setExplodedSpacing((prev) => !prev)}
                className={`px-2.5 py-1.5 text-xs font-medium rounded-lg transition-colors flex items-center gap-1 cursor-pointer ${
                  explodedSpacing
                    ? 'bg-indigo-500/20 text-indigo-300 border border-indigo-500/30'
                    : 'text-slate-400 hover:text-white'
                }`}
                title="Toggle exploded floor spacing"
              >
                <Maximize2 className="w-3 h-3" />
                <span>Explode</span>
              </button>
            )}
          </div>
        </div>
      </div>

      {/* Main 12-Column Split: Left 7 Cols = 3D Interactive Building Model, Right 5 Cols = Live Countdown + Call the Squad */}
      <div className="grid grid-cols-1 lg:grid-cols-12">
        {/* LEFT COLUMN: 3D Architectural Viewport */}
        <div className="lg:col-span-7 p-6 bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-indigo-950/60 via-slate-900 to-slate-950 relative flex flex-col justify-between min-h-[580px] overflow-x-auto">
          {/* Legend Bar Overlay */}
          <div className="flex flex-wrap items-center justify-between gap-3 pb-4 border-b border-slate-800/80 z-10">
            <div className="flex flex-wrap items-center gap-4 text-xs">
              <span className="inline-flex items-center gap-1.5 text-emerald-300 font-medium">
                <span className="w-3 h-3 rounded-xs bg-emerald-500 shadow-xs shadow-emerald-500/50 inline-block" />
                <span>Empty & Safe (1h+)</span>
              </span>
              <span className="inline-flex items-center gap-1.5 text-amber-300 font-medium">
                <span className="w-3 h-3 rounded-xs bg-amber-500 shadow-xs shadow-amber-500/50 inline-block" />
                <span>Closing Soon (&lt;35m)</span>
              </span>
              <span className="inline-flex items-center gap-1.5 text-rose-300 font-medium">
                <span className="w-3 h-3 rounded-xs bg-rose-500 shadow-xs shadow-rose-500/50 inline-block" />
                <span>Occupied in Class</span>
              </span>
              <span className="inline-flex items-center gap-1.5 text-indigo-300 font-medium">
                <span className="w-3 h-3 rounded-xs bg-indigo-500 ring-2 ring-white inline-block" />
                <span>Selected / Squad Claimed</span>
              </span>
            </div>

            {claimedRoomId && (
              <div className="inline-flex items-center gap-1.5 text-xs font-bold text-teal-300 bg-teal-500/15 border border-teal-500/30 px-2.5 py-1 rounded-lg">
                <MapPin className="w-3.5 h-3.5 text-teal-400" />
                <span>
                  Squad Claimed:{' '}
                  {statuses.find((s) => s.room.id === claimedRoomId)?.room.code}
                </span>
              </div>
            )}
          </div>

          {/* 3D Building Stack Container */}
          <div className="my-auto py-8 px-2 sm:px-6 flex flex-col items-center justify-center space-y-6">
            {visibleFloors.map((floor, idx) => {
              const floorRooms = statuses.filter(
                (s) => s.room.floorId === floor.id
              );
              const emptyOnFloor = floorRooms.filter(
                (s) => s.isCurrentlyEmpty
              ).length;

              // Split floor rooms into North Wing (top row of corridor) and South Wing (bottom row of corridor)
              const midPoint = Math.ceil(floorRooms.length / 2);
              const northWing = floorRooms.slice(0, midPoint);
              const southWing = floorRooms.slice(midPoint);

              return (
                <div
                  key={floor.id}
                  style={getSlabTransformStyle(idx)}
                  className="w-full max-w-[620px] transition-all duration-500 ease-out"
                >
                  {/* 3D Floor Slab Platform */}
                  <div className="relative rounded-2xl bg-slate-800/90 border-2 border-slate-700/90 shadow-[0_18px_0_0_rgba(15,23,42,1),0_26px_38px_rgba(0,0,0,0.65)] p-3.5">
                    {/* Floor Slab Header Label */}
                    <div className="flex items-center justify-between gap-2 mb-2.5 pb-1.5 border-b border-slate-700/80">
                      <div className="flex items-center gap-2">
                        <span className="px-2 py-0.5 rounded bg-indigo-500/20 border border-indigo-400/30 text-indigo-300 font-mono text-xs font-bold">
                          {floor.shortName.toUpperCase()}
                        </span>
                        <span className="text-xs font-medium text-slate-300 hidden sm:inline">
                          {floor.seriesLabel}
                        </span>
                      </div>
                      <span className="font-mono text-xs font-semibold text-emerald-400 tabular-nums">
                        {emptyOnFloor}/{floorRooms.length} Empty
                      </span>
                    </div>

                    {/* North Wing Rooms Row */}
                    <div
                      className="grid gap-2"
                      style={{
                        gridTemplateColumns: `repeat(${northWing.length}, minmax(0, 1fr))`,
                      }}
                    >
                      {northWing.map((st) => (
                        <Room3DBlock
                          key={st.room.id}
                          status={st}
                          isSelected={st.room.id === activeStatus?.room.id}
                          isClaimed={st.room.id === claimedRoomId}
                          isAIMatch={aiRecommendedIds.includes(st.room.id)}
                          onClick={() => onSelectRoomId(st.room.id)}
                        />
                      ))}
                    </div>

                    {/* Central Architectural Corridor & Stair/Lift Cores */}
                    <div className="my-2 py-1 px-3 rounded-lg bg-slate-900/90 border border-slate-700/60 flex items-center justify-between text-[10px] font-mono text-slate-400 tracking-wider uppercase">
                      <span className="flex items-center gap-1">
                        <span className="w-2 h-2 rounded-xs bg-slate-600 inline-block" />
                        <span>West Stairs</span>
                      </span>
                      <span className="text-slate-500">
                        ═══ Central Corridor ({floor.shortName}) ═══
                      </span>
                      <span className="flex items-center gap-1">
                        <span>Lift Core</span>
                        <span className="w-2 h-2 rounded-xs bg-slate-600 inline-block" />
                      </span>
                    </div>

                    {/* South Wing Rooms Row */}
                    <div
                      className="grid gap-2"
                      style={{
                        gridTemplateColumns: `repeat(${southWing.length}, minmax(0, 1fr))`,
                      }}
                    >
                      {southWing.map((st) => (
                        <Room3DBlock
                          key={st.room.id}
                          status={st}
                          isSelected={st.room.id === activeStatus?.room.id}
                          isClaimed={st.room.id === claimedRoomId}
                          isAIMatch={aiRecommendedIds.includes(st.room.id)}
                          onClick={() => onSelectRoomId(st.room.id)}
                        />
                      ))}
                    </div>
                  </div>
                </div>
              );
            })}
          </div>

          {/* Bottom Helper Tip */}
          <div className="text-center text-xs text-slate-400 pt-2 border-t border-slate-800/80">
            Tip: Click any 3D room block above to inspect its live second-by-second countdown and share a WhatsApp invite with your project group.
          </div>
        </div>

        {/* RIGHT COLUMN: Live Countdown Timer & "Call the Squad" Command Panel */}
        {activeStatus && (
          <div className="lg:col-span-5 bg-slate-900 border-t lg:border-t-0 lg:border-l border-slate-800 p-6 flex flex-col justify-between space-y-6">
            <div>
              {/* Selected Room Header */}
              <div className="flex items-start justify-between gap-3">
                <div>
                  <div className="flex items-center gap-2 flex-wrap">
                    <span className="text-xs font-mono uppercase tracking-wider text-teal-400 font-semibold">
                      {FLOORS.find((f) => f.id === activeStatus.room.floorId)?.name}
                    </span>
                    <span className="text-slate-600">·</span>
                    <span className="text-xs text-slate-400">
                      {activeStatus.room.wing}
                    </span>
                  </div>
                  <div className="flex items-center gap-2.5 mt-1">
                    <h3 className="font-mono text-3xl font-extrabold text-white tabular-nums tracking-tight">
                      {activeStatus.room.code}
                    </h3>
                    {claimedRoomId === activeStatus.room.id && (
                      <span className="inline-flex items-center gap-1 px-2.5 py-1 rounded-md text-xs font-bold bg-teal-500 text-slate-950 shadow-sm">
                        <MapPin className="w-3.5 h-3.5" />
                        <span>Claimed by You</span>
                      </span>
                    )}
                  </div>
                  <p className="text-sm text-slate-300 font-medium mt-0.5">
                    {activeStatus.room.name}
                  </p>
                </div>

                <button
                  type="button"
                  onClick={() => onOpenFullSchedule(activeStatus)}
                  className="px-3 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 border border-slate-700 text-xs font-semibold text-slate-200 transition-colors flex items-center gap-1.5 shrink-0 cursor-pointer"
                >
                  <Calendar className="w-3.5 h-3.5 text-teal-400" />
                  <span>Full Schedule</span>
                </button>
              </div>

              {/* Quick Room Specs Strip */}
              <div className="mt-4 grid grid-cols-3 gap-2.5">
                <div className="bg-slate-800/70 border border-slate-700/80 rounded-xl p-2.5 flex items-center gap-2">
                  <Snowflake
                    className={`w-4 h-4 shrink-0 ${
                      activeStatus.room.isAC ? 'text-sky-400' : 'text-slate-500'
                    }`}
                  />
                  <div className="text-xs">
                    <div className="text-slate-400 text-[10px]">Climate</div>
                    <div className="font-semibold text-white">
                      {activeStatus.room.isAC ? 'AC Cool' : 'Natural Air'}
                    </div>
                  </div>
                </div>

                <div className="bg-slate-800/70 border border-slate-700/80 rounded-xl p-2.5 flex items-center gap-2">
                  <Users className="w-4 h-4 text-indigo-400 shrink-0" />
                  <div className="text-xs">
                    <div className="text-slate-400 text-[10px]">Capacity</div>
                    <div className="font-semibold text-white font-mono tabular-nums">
                      {activeStatus.room.capacity} Seats
                    </div>
                  </div>
                </div>

                <div className="bg-slate-800/70 border border-slate-700/80 rounded-xl p-2.5 flex items-center gap-2">
                  <Plug className="w-4 h-4 text-amber-400 shrink-0" />
                  <div className="text-xs min-w-0">
                    <div className="text-slate-400 text-[10px]">Power</div>
                    <div className="font-semibold text-white truncate">
                      {activeStatus.room.powerOutlets === 'High (Every Bench)'
                        ? 'Every Bench'
                        : 'Wall Outlets'}
                    </div>
                  </div>
                </div>
              </div>

              {/* LIVE COUNTDOWN TIMER DISPLAY */}
              <div
                className={`mt-5 rounded-2xl p-5 border-2 transition-colors ${
                  activeStatus.statusState === 'free-long'
                    ? 'bg-gradient-to-br from-emerald-950/90 via-slate-900 to-teal-950/80 border-emerald-500/50'
                    : activeStatus.statusState === 'free-short'
                    ? 'bg-gradient-to-br from-amber-950/90 via-slate-900 to-orange-950/80 border-amber-500/50'
                    : 'bg-gradient-to-br from-rose-950/90 via-slate-900 to-red-950/80 border-rose-500/50'
                }`}
              >
                <div className="flex items-center justify-between gap-2">
                  <div className="flex items-center gap-2 text-xs font-bold uppercase tracking-wider">
                    {activeStatus.statusState === 'free-long' && (
                      <span className="text-emerald-400 inline-flex items-center gap-1.5">
                        <CheckCircle2 className="w-4 h-4" />
                        <span>Live Uninterrupted Free Timer</span>
                      </span>
                    )}
                    {activeStatus.statusState === 'free-short' && (
                      <span className="text-amber-400 inline-flex items-center gap-1.5">
                        <AlertTriangle className="w-4 h-4" />
                        <span>Short Free Window Countdown</span>
                      </span>
                    )}
                    {activeStatus.statusState === 'occupied' && (
                      <span className="text-rose-400 inline-flex items-center gap-1.5">
                        <Lock className="w-4 h-4" />
                        <span>Occupied — Clears In:</span>
                      </span>
                    )}
                  </div>

                  <span className="inline-flex items-center gap-1 text-[11px] font-mono text-slate-300">
                    <Clock className="w-3 h-3 text-teal-400 animate-pulse" />
                    <span>LIVE</span>
                  </span>
                </div>

                {/* Big Segmented Digital Countdown Clock */}
                <div className="mt-3 grid grid-cols-3 gap-2.5 text-center">
                  <div className="bg-slate-950/80 border border-white/10 rounded-xl py-3 px-2">
                    <div className="font-mono text-3xl sm:text-4xl font-extrabold text-white tabular-nums tracking-tight">
                      {String(hoursLeft).padStart(2, '0')}
                    </div>
                    <div className="text-[10px] font-mono uppercase tracking-widest text-slate-400 mt-1">
                      Hours
                    </div>
                  </div>
                  <div className="bg-slate-950/80 border border-white/10 rounded-xl py-3 px-2">
                    <div className="font-mono text-3xl sm:text-4xl font-extrabold text-white tabular-nums tracking-tight">
                      {String(minutesLeft).padStart(2, '0')}
                    </div>
                    <div className="text-[10px] font-mono uppercase tracking-widest text-slate-400 mt-1">
                      Minutes
                    </div>
                  </div>
                  <div className="bg-slate-950/80 border border-white/10 rounded-xl py-3 px-2">
                    <div
                      className={`font-mono text-3xl sm:text-4xl font-extrabold tabular-nums tracking-tight ${
                        activeStatus.isCurrentlyEmpty
                          ? 'text-emerald-400'
                          : 'text-rose-400'
                      }`}
                    >
                      {String(secsLeft).padStart(2, '0')}
                    </div>
                    <div className="text-[10px] font-mono uppercase tracking-widest text-slate-400 mt-1">
                      Seconds
                    </div>
                  </div>
                </div>

                {/* Next Scheduled Lecture Details */}
                <div className="mt-3.5 pt-3 border-t border-white/10 text-xs">
                  {activeStatus.isCurrentlyEmpty ? (
                    activeStatus.nextSession ? (
                      <div className="flex flex-col gap-0.5 text-slate-200">
                        <div className="flex items-center justify-between">
                          <span className="text-slate-400">Free Until:</span>
                          <span className="font-mono font-bold text-emerald-300">
                            {formatTime12h(activeStatus.freeUntilTime)}
                          </span>
                        </div>
                        <div className="flex items-center justify-between mt-1">
                          <span className="text-slate-400">Next Class:</span>
                          <span className="font-semibold text-white truncate max-w-[210px]">
                            {activeStatus.nextSession.subjectName}
                          </span>
                        </div>
                        <div className="text-[11px] text-slate-400 text-right">
                          {activeStatus.nextSession.faculty} ·{' '}
                          {activeStatus.nextSession.sectionName}
                        </div>
                      </div>
                    ) : (
                      <div className="text-emerald-300 font-semibold flex items-center justify-between">
                        <span>No more classes scheduled today!</span>
                        <span className="font-mono">Until 05:05 PM</span>
                      </div>
                    )
                  ) : (
                    <div className="flex flex-col gap-0.5 text-rose-200">
                      <div className="flex items-center justify-between">
                        <span className="text-rose-300/80">Current Lecture:</span>
                        <span className="font-semibold text-white truncate max-w-[210px]">
                          {activeStatus.currentSessions[0]?.subjectName}
                        </span>
                      </div>
                      <div className="flex items-center justify-between mt-1">
                        <span className="text-rose-300/80">Room Clears At:</span>
                        <span className="font-mono font-bold text-amber-300">
                          {formatTime12h(activeStatus.clearsAtTime || '17:05')}
                        </span>
                      </div>
                    </div>
                  )}

                  {/* Same-Floor Backup / Next Room Hop Suggestion */}
                  {sameFloorBackup &&
                    (!activeStatus.isCurrentlyEmpty ||
                      !activeStatus.isFreeRestOfDay) && (
                      <div className="mt-3 pt-2.5 border-t border-white/10 flex items-center justify-between gap-2">
                        <div className="text-[11px] text-slate-300 truncate">
                          <span className="text-teal-300 font-bold">
                            Same-Floor Backup:
                          </span>{' '}
                          <span className="font-mono font-bold text-white">
                            {sameFloorBackup.room.code}
                          </span>{' '}
                          (free {sameFloorBackup.freeDurationFormatted})
                        </div>
                        <button
                          type="button"
                          onClick={() =>
                            onSelectRoomId(sameFloorBackup.room.id)
                          }
                          className="px-2.5 py-1 rounded-lg bg-teal-500/20 hover:bg-teal-500/30 border border-teal-400/40 text-teal-200 text-[11px] font-bold shrink-0 cursor-pointer transition-colors"
                        >
                          Hop to {sameFloorBackup.room.code}
                        </button>
                      </div>
                    )}
                </div>
              </div>
            </div>

            {/* "CALL THE SQUAD" FEATURE — CLAIM & WHATSAPP SHARE */}
            <div className="bg-slate-800/90 border border-slate-700 rounded-2xl p-5 space-y-4">
              <div className="flex items-center justify-between gap-2">
                <div className="flex items-center gap-2">
                  <div className="w-8 h-8 rounded-lg bg-emerald-500/20 border border-emerald-500/30 text-emerald-400 flex items-center justify-center">
                    <Share2 className="w-4 h-4" />
                  </div>
                  <div>
                    <h4 className="text-sm font-bold text-white">
                      Call the Squad · Instant Invite
                    </h4>
                    <p className="text-[11px] text-slate-400">
                      Claim {activeStatus.room.code} & send a pre-filled WhatsApp ping
                    </p>
                  </div>
                </div>

                {/* Claim Room Toggle Button */}
                <button
                  type="button"
                  onClick={() =>
                    onClaimRoom(
                      claimedRoomId === activeStatus.room.id
                        ? null
                        : activeStatus.room.id
                    )
                  }
                  className={`px-3 py-1.5 rounded-lg text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                    claimedRoomId === activeStatus.room.id
                      ? 'bg-teal-500 text-slate-950 shadow-sm'
                      : 'bg-indigo-600 hover:bg-indigo-500 text-white'
                  }`}
                >
                  <MapPin className="w-3.5 h-3.5" />
                  <span>
                    {claimedRoomId === activeStatus.room.id
                      ? 'Room Claimed!'
                      : 'Claim Room'}
                  </span>
                </button>
              </div>

              {/* Quick Vibe Add-Ons */}
              <div className="flex flex-wrap gap-1.5">
                {SQUAD_EXTRAS.map((extra) => {
                  const active = selectedExtras.includes(extra.id);
                  return (
                    <button
                      key={extra.id}
                      type="button"
                      onClick={() => toggleExtra(extra.id)}
                      className={`px-2.5 py-1 rounded-lg text-[11px] font-medium border transition-colors cursor-pointer ${
                        active
                          ? 'bg-emerald-500/20 border-emerald-400 text-emerald-300'
                          : 'bg-slate-900/70 border-slate-700 text-slate-400 hover:text-slate-200'
                      }`}
                    >
                      {extra.label}
                    </button>
                  );
                })}
              </div>

              {/* Live WhatsApp Message Bubble Preview */}
              <div className="bg-[#0B141A] border border-emerald-500/30 rounded-xl p-3.5 relative">
                <div className="text-[10px] font-mono uppercase tracking-wider text-emerald-400 mb-1 flex items-center justify-between">
                  <span>WhatsApp Message Preview</span>
                  <span>Auto-Generated</span>
                </div>
                <p className="text-xs text-slate-100 leading-relaxed font-medium select-all">
                  "{squadWhatsAppMessage}"
                </p>
                <input
                  type="text"
                  value={customNote}
                  onChange={(e) => setCustomNote(e.target.value)}
                  placeholder="Optional: Add a custom note (e.g. 'Sitting in the back row')..."
                  className="mt-2.5 w-full px-3 py-1.5 bg-slate-900/90 border border-slate-700 rounded-lg text-xs text-white placeholder:text-slate-500 focus:outline-none focus:border-emerald-500"
                />
              </div>

              {/* Primary WhatsApp Share Link & Copy Button */}
              <div className="flex flex-col sm:flex-row items-stretch sm:items-center gap-2.5">
                <a
                  href={whatsappUrl}
                  target="_blank"
                  rel="noopener noreferrer"
                  onClick={() => {
                    if (claimedRoomId !== activeStatus.room.id) {
                      onClaimRoom(activeStatus.room.id);
                    }
                  }}
                  className="flex-1 py-3 px-4 bg-[#25D366] hover:bg-[#20BD5A] text-slate-950 font-bold text-xs sm:text-sm rounded-xl shadow-md shadow-emerald-500/10 transition-all flex items-center justify-center gap-2 text-center"
                >
                  <MessageCircle className="w-4 h-4 fill-slate-950" />
                  <span>Call the Squad on WhatsApp</span>
                </a>

                <button
                  type="button"
                  onClick={handleCopyMessage}
                  className="py-3 px-4 bg-slate-900 hover:bg-slate-950 border border-slate-700 text-slate-200 font-semibold text-xs rounded-xl transition-colors flex items-center justify-center gap-1.5 cursor-pointer shrink-0"
                >
                  {copiedToast ? (
                    <>
                      <Check className="w-4 h-4 text-emerald-400" />
                      <span className="text-emerald-400">Copied!</span>
                    </>
                  ) : (
                    <>
                      <Copy className="w-4 h-4 text-slate-400" />
                      <span>Copy Invite</span>
                    </>
                  )}
                </button>
              </div>
            </div>
          </div>
        )}
      </div>
    </section>
  );
};

interface Room3DBlockProps {
  status: RoomAvailabilityStatus;
  isSelected: boolean;
  isClaimed: boolean;
  isAIMatch: boolean;
  onClick: () => void;
}

const Room3DBlock: React.FC<Room3DBlockProps> = ({
  status,
  isSelected,
  isClaimed,
  isAIMatch,
  onClick,
}) => {
  const { room, statusState, freeDurationFormatted } = status;

  // 3D Extruded Block Colors based on live room state
  const blockStyle =
    statusState === 'free-long'
      ? 'bg-gradient-to-b from-emerald-500 to-teal-600 border-emerald-300/90 text-slate-950 shadow-[0_6px_0_0_#047857]'
      : statusState === 'free-short'
      ? 'bg-gradient-to-b from-amber-400 to-orange-500 border-amber-200 text-slate-950 shadow-[0_6px_0_0_#B45309]'
      : 'bg-gradient-to-b from-rose-500/90 to-red-700 border-rose-300/70 text-white shadow-[0_6px_0_0_#881337] opacity-90';

  const selectedRing = isSelected
    ? 'ring-4 ring-white scale-[1.04] z-20 -translate-y-1'
    : 'hover:-translate-y-0.5 hover:brightness-110';

  return (
    <button
      type="button"
      onClick={onClick}
      className={`relative rounded-xl border-t-2 border-x px-2 py-2.5 text-left transition-all duration-200 cursor-pointer select-none ${blockStyle} ${selectedRing}`}
    >
      {/* Floating Pin if Claimed or AI Match */}
      {isClaimed && (
        <span className="absolute -top-3 left-1/2 -translate-x-1/2 bg-slate-950 text-teal-300 border border-teal-400 px-1.5 py-0.5 rounded text-[9px] font-mono font-bold whitespace-nowrap shadow-md flex items-center gap-0.5">
          <MapPin className="w-2.5 h-2.5 text-teal-400" />
          <span>SQUAD</span>
        </span>
      )}
      {!isClaimed && isAIMatch && (
        <span className="absolute -top-3 left-1/2 -translate-x-1/2 bg-indigo-600 text-white border border-indigo-300 px-1.5 py-0.5 rounded text-[9px] font-mono font-bold whitespace-nowrap shadow-md flex items-center gap-0.5">
          <Sparkles className="w-2.5 h-2.5" />
          <span>AI PICK</span>
        </span>
      )}

      <div className="flex items-center justify-between gap-1">
        <span className="font-mono text-xs font-extrabold tracking-tight tabular-nums truncate">
          {room.code}
        </span>
        {room.isAC && (
          <Snowflake
            className={`w-3 h-3 shrink-0 ${
              statusState === 'occupied' ? 'text-sky-200' : 'text-slate-900/80'
            }`}
          />
        )}
      </div>

      <div
        className={`font-mono text-[10px] font-bold tabular-nums mt-1 truncate ${
          statusState === 'occupied' ? 'text-rose-100' : 'text-slate-950/90'
        }`}
      >
        {statusState === 'occupied' ? 'Occupied' : `Free ${freeDurationFormatted}`}
      </div>
    </button>
  );
};
import React, { useMemo, useState } from 'react';
import {
  Route,
  Search,
  UserCheck,
  Clock,
  MapPin,
  ArrowRight,
  Snowflake,
  MessageCircle,
  Sparkles,
  CheckCircle2,
  BookOpen,
  Layers,
  GraduationCap,
} from 'lucide-react';
import {
  DayOfWeek,
  FLOORS,
  FloorId,
  ROOMS,
  RoomInfo,
} from '../data/roomsData';
import { ALL_CLASS_SESSIONS } from '../data/timetablesPart2';
import {
  computeAllRoomsStatus,
  DAY_END_MINUTES,
  formatDurationMinutes,
  formatTime12h,
  RoomAvailabilityStatus,
  timeToMinutes,
} from '../utils/occupancyEngine';

interface CampusSmartToolsProps {
  selectedDay: DayOfWeek;
  selectedTime: string;
  allStatuses: RoomAvailabilityStatus[];
  onSelectRoomOnMap: (roomId: string, time24?: string) => void;
  onClaimRoom: (roomId: string) => void;
  onInspectRoom: (status: RoomAvailabilityStatus) => void;
}

interface RelayPlan {
  id: string;
  type: 'single-room' | 'one-hop';
  floorId: FloorId;
  floorName: string;
  totalMinutes: number;
  leg1: {
    room: RoomInfo;
    startTime: string;
    endTime: string;
    durationMinutes: number;
    kickOutReason?: string;
  };
  leg2?: {
    room: RoomInfo;
    startTime: string;
    endTime: string;
    durationMinutes: number;
  };
}

export const CampusSmartTools: React.FC<CampusSmartToolsProps> = ({
  selectedDay,
  selectedTime,
  allStatuses,
  onSelectRoomOnMap,
  onClaimRoom,
  onInspectRoom,
}) => {
  // Marathon / Room-Hop Planner State
  const [targetHours, setTargetHours] = useState<number>(3);
  const [preferredFloor, setPreferredFloor] = useState<FloorId | 'all'>('all');
  const [requireACForRelay, setRequireACForRelay] = useState<boolean>(true);

  // Faculty & Course Locator State
  const [facultyQuery, setFacultyQuery] = useState<string>('');

  // Compute Smart Marathon & 1-Hop Relay Plans starting at `selectedTime`
  const relayPlans = useMemo(() => {
    const startMins = timeToMinutes(selectedTime);
    const targetMins = Math.min(
      targetHours * 60,
      Math.max(60, DAY_END_MINUTES - startMins)
    );
    const desiredEndMins = Math.min(DAY_END_MINUTES, startMins + targetMins);

    const plans: RelayPlan[] = [];

    // Candidate Leg 1 rooms currently empty at `selectedTime`
    const leg1Candidates = allStatuses.filter((st) => {
      if (!st.isCurrentlyEmpty) return false;
      if (preferredFloor !== 'all' && st.room.floorId !== preferredFloor) {
        return false;
      }
      if (requireACForRelay && !st.room.isAC) return false;
      return st.freeDurationMinutes >= 45;
    });

    // 1. Single-Room Zero-Hop Marathons (covers full target duration without moving!)
    for (const st of leg1Candidates) {
      if (st.freeDurationMinutes >= targetMins) {
        const floorMeta = FLOORS.find((f) => f.id === st.room.floorId)!;
        plans.push({
          id: `single-${st.room.id}`,
          type: 'single-room',
          floorId: st.room.floorId,
          floorName: floorMeta.shortName,
          totalMinutes: st.freeDurationMinutes,
          leg1: {
            room: st.room,
            startTime: selectedTime,
            endTime: st.freeUntilTime,
            durationMinutes: st.freeDurationMinutes,
          },
        });
      }
    }

    // 2. Smart 1-Hop Same-Floor Relays (when Leg 1 room has a lecture starting before desiredEndMins)
    for (const st1 of leg1Candidates) {
      const leg1EndMins = timeToMinutes(st1.freeUntilTime);
      if (leg1EndMins >= desiredEndMins || leg1EndMins >= DAY_END_MINUTES - 20) {
        continue;
      }

      const hopTime24 = st1.freeUntilTime;
      const statusesAtHop = computeAllRoomsStatus(selectedDay, hopTime24);

      // Look for an empty room on the EXACT SAME FLOOR at `hopTime24`
      const sameFloorLeg2 = statusesAtHop
        .filter((st2) => {
          if (st2.room.id === st1.room.id) return false;
          if (!st2.isCurrentlyEmpty) return false;
          if (st2.room.floorId !== st1.room.floorId) return false;
          if (requireACForRelay && !st2.room.isAC) return false;
          return st2.freeDurationMinutes >= 50;
        })
        .sort((a, b) => b.freeDurationMinutes - a.freeDurationMinutes)[0];

      if (sameFloorLeg2) {
        const combinedMins =
          st1.freeDurationMinutes + sameFloorLeg2.freeDurationMinutes;
        if (combinedMins >= targetMins) {
          const floorMeta = FLOORS.find((f) => f.id === st1.room.floorId)!;
          plans.push({
            id: `hop-${st1.room.id}-${sameFloorLeg2.room.id}`,
            type: 'one-hop',
            floorId: st1.room.floorId,
            floorName: floorMeta.shortName,
            totalMinutes: combinedMins,
            leg1: {
              room: st1.room,
              startTime: selectedTime,
              endTime: hopTime24,
              durationMinutes: st1.freeDurationMinutes,
              kickOutReason: st1.nextSession
                ? `${st1.nextSession.sectionName} (${st1.nextSession.subjectName})`
                : 'Scheduled class',
            },
            leg2: {
              room: sameFloorLeg2.room,
              startTime: hopTime24,
              endTime: sameFloorLeg2.freeUntilTime,
              durationMinutes: sameFloorLeg2.freeDurationMinutes,
            },
          });
        }
      }
    }

    // Sort so we show top 1-Hop Same-Floor Relays and top Single-Room Marathons together
    const singleRoomPlans = plans
      .filter((p) => p.type === 'single-room')
      .slice(0, 2);
    const oneHopPlans = plans.filter((p) => p.type === 'one-hop').slice(0, 2);

    return [...oneHopPlans, ...singleRoomPlans, ...plans]
      .filter((v, idx, arr) => arr.findIndex((x) => x.id === v.id) === idx)
      .slice(0, 4);
  }, [
    allStatuses,
    selectedDay,
    selectedTime,
    targetHours,
    preferredFloor,
    requireACForRelay,
  ]);

  // Extract unique faculty & subjects from the 10 timetables for Live Faculty & Course Locator
  const facultyDirectory = useMemo(() => {
    const map = new Map<
      string,
      {
        faculty: string;
        subjects: Set<string>;
        sections: Set<string>;
        sessionsToday: typeof ALL_CLASS_SESSIONS;
      }
    >();

    for (const s of ALL_CLASS_SESSIONS) {
      // Split combined faculty names if separated by / or ,
      const names = s.faculty
        .split(/[/,]/)
        .map((n) => n.trim())
        .filter((n) => n.length > 2 && n.toLowerCase() !== 'all faculty');

      for (const name of names) {
        if (!map.has(name)) {
          map.set(name, {
            faculty: name,
            subjects: new Set(),
            sections: new Set(),
            sessionsToday: [],
          });
        }
        const entry = map.get(name)!;
        entry.subjects.add(`${s.subjectName} (${s.subjectCode})`);
        entry.sections.add(s.sectionName);
        if (s.day === selectedDay) {
          entry.sessionsToday.push(s);
        }
      }
    }

    const currentMins = timeToMinutes(selectedTime);

    return Array.from(map.values())
      .map((item) => {
        const sortedToday = [...item.sessionsToday].sort(
          (a, b) => timeToMinutes(a.startTime) - timeToMinutes(b.startTime)
        );
        const activeNow = sortedToday.find(
          (s) =>
            currentMins >= timeToMinutes(s.startTime) &&
            currentMins < timeToMinutes(s.endTime)
        );
        const nextToday = sortedToday.find(
          (s) => timeToMinutes(s.startTime) > currentMins
        );

        return {
          faculty: item.faculty,
          subjects: Array.from(item.subjects),
          sections: Array.from(item.sections),
          activeNow,
          nextToday,
          totalToday: sortedToday.length,
        };
      })
      .sort((a, b) => {
        if (Boolean(a.activeNow) !== Boolean(b.activeNow)) {
          return a.activeNow ? -1 : 1;
        }
        if (Boolean(a.nextToday) !== Boolean(b.nextToday)) {
          return a.nextToday ? -1 : 1;
        }
        return a.faculty.localeCompare(b.faculty);
      });
  }, [selectedDay, selectedTime]);

  const filteredFaculty = useMemo(() => {
    const q = facultyQuery.trim().toLowerCase();
    if (!q) return facultyDirectory.slice(0, 6);
    return facultyDirectory
      .filter(
        (f) =>
          f.faculty.toLowerCase().includes(q) ||
          f.subjects.some((sub) => sub.toLowerCase().includes(q)) ||
          f.sections.some((sec) => sec.toLowerCase().includes(q))
      )
      .slice(0, 8);
  }, [facultyDirectory, facultyQuery]);

  return (
    <div className="grid grid-cols-1 lg:grid-cols-12 gap-6">
      {/* LEFT 7 COLS: SMART ROOM-HOP MARATHON PLANNER (ZERO-KICKOUT RELAY) */}
      <div className="lg:col-span-7 bg-white border-2 border-teal-100 rounded-2xl overflow-hidden shadow-xs flex flex-col justify-between">
        <div>
          <div className="h-1.5 w-full bg-gradient-to-r from-teal-500 via-emerald-500 to-indigo-600" />
          <div className="p-6">
            <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-3 pb-4 border-b border-slate-100">
              <div className="flex items-start gap-3">
                <div className="w-10 h-10 rounded-xl bg-gradient-to-br from-teal-500 to-emerald-600 text-white flex items-center justify-center shrink-0 shadow-xs">
                  <Route className="w-5 h-5" />
                </div>
                <div>
                  <div className="flex items-center gap-2">
                    <h3 className="text-base font-extrabold text-slate-900 tracking-tight">
                      Zero-Kickout Room-Hop Marathon Planner
                    </h3>
                  </div>
                  <p className="text-xs text-slate-600 mt-0.5">
                    Need 3–5 hours for a project sprint? Automatically chains two rooms on the{' '}
                    <strong className="text-slate-900">same floor</strong> if a lecture interrupts your first room.
                  </p>
                </div>
              </div>
            </div>

            {/* Marathon Controls */}
            <div className="mt-4 flex flex-wrap items-center justify-between gap-3 bg-slate-50 p-3 rounded-xl border border-slate-200/80">
              <div className="flex items-center gap-1.5">
                <span className="text-xs font-bold text-slate-700">
                  Sprint Goal:
                </span>
                {[2, 3, 4].map((hrs) => (
                  <button
                    key={hrs}
                    type="button"
                    onClick={() => setTargetHours(hrs)}
                    className={`px-2.5 py-1 rounded-lg text-xs font-mono font-bold transition-colors cursor-pointer ${
                      targetHours === hrs
                        ? 'bg-teal-600 text-white shadow-2xs'
                        : 'bg-white text-slate-700 border border-slate-200 hover:bg-slate-100'
                    }`}
                  >
                    {hrs}h+ Sprint
                  </button>
                ))}
              </div>

              <div className="flex items-center gap-2">
                <select
                  value={preferredFloor}
                  onChange={(e) =>
                    setPreferredFloor(e.target.value as FloorId | 'all')
                  }
                  className="px-2.5 py-1 bg-white border border-slate-200 rounded-lg text-xs font-bold text-slate-800 cursor-pointer"
                >
                  <option value="all">Any Floor</option>
                  {FLOORS.map((f) => (
                    <option key={f.id} value={f.id}>
                      {f.shortName} Only
                    </option>
                  ))}
                </select>

                <button
                  type="button"
                  onClick={() => setRequireACForRelay((v) => !v)}
                  className={`px-2.5 py-1 rounded-lg text-xs font-bold border transition-colors cursor-pointer flex items-center gap-1 ${
                    requireACForRelay
                      ? 'bg-sky-600 border-sky-600 text-white'
                      : 'bg-white border-slate-200 text-slate-700'
                  }`}
                >
                  <Snowflake className="w-3 h-3" />
                  <span>AC</span>
                </button>
              </div>
            </div>

            {/* Relay Cards */}
            <div className="mt-4 space-y-3">
              {relayPlans.map((plan) => {
                const whatsappRelayMsg =
                  plan.type === 'one-hop' && plan.leg2
                    ? `📍 Squad Marathon Plan (${plan.floorName}): Start in ${
                        plan.leg1.room.code
                      } (${formatTime12h(plan.leg1.startTime)}–${formatTime12h(
                        plan.leg1.endTime
                      )}), then hop next door to ${
                        plan.leg2.room.code
                      } until ${formatTime12h(
                        plan.leg2.endTime
                      )}! Zero stairs, come fast!`
                    : `📍 Squad Marathon in ${
                        plan.leg1.room.code
                      } (${plan.floorName})! Completely empty from ${formatTime12h(
                        plan.leg1.startTime
                      )} until ${formatTime12h(plan.leg1.endTime)}. Come fast!`;

                return (
                  <div
                    key={plan.id}
                    className={`rounded-xl border p-4 transition-all ${
                      plan.type === 'one-hop'
                        ? 'bg-gradient-to-r from-indigo-50/60 via-white to-teal-50/50 border-indigo-200'
                        : 'bg-emerald-50/40 border-emerald-200'
                    }`}
                  >
                    <div className="flex flex-wrap items-center justify-between gap-2 mb-3">
                      <div className="flex items-center gap-2">
                        <span
                          className={`px-2.5 py-0.5 rounded-md text-[11px] font-extrabold uppercase tracking-wider ${
                            plan.type === 'one-hop'
                              ? 'bg-indigo-600 text-white'
                              : 'bg-emerald-600 text-white'
                          }`}
                        >
                          {plan.type === 'one-hop'
                            ? '1-Hop Same-Floor Relay'
                            : 'Zero-Hop Single Room'}
                        </span>
                        <span className="text-xs font-bold text-slate-700 inline-flex items-center gap-1">
                          <Layers className="w-3.5 h-3.5 text-indigo-600" />
                          <span>{plan.floorName}</span>
                        </span>
                      </div>

                      <span className="font-mono text-xs font-extrabold text-teal-800 bg-teal-100/80 px-2.5 py-0.5 rounded-md tabular-nums">
                        Total: {formatDurationMinutes(plan.totalMinutes)} Unbroken
                      </span>
                    </div>

                    {/* Visual Timeline of Leg 1 -> Leg 2 */}
                    <div className="grid grid-cols-1 sm:grid-cols-11 gap-2 items-center">
                      {/* Leg 1 */}
                      <div
                        onClick={() =>
                          onSelectRoomOnMap(
                            plan.leg1.room.id,
                            plan.leg1.startTime
                          )
                        }
                        className={`${
                          plan.leg2 ? 'sm:col-span-5' : 'sm:col-span-11'
                        } bg-white border border-slate-200 hover:border-indigo-400 rounded-xl p-3 cursor-pointer transition-colors`}
                      >
                        <div className="flex items-center justify-between">
                          <span className="font-mono text-sm font-extrabold text-slate-900">
                            1. {plan.leg1.room.code}
                          </span>
                          <span className="font-mono text-[11px] font-bold text-emerald-700 tabular-nums">
                            {formatTime12h(plan.leg1.startTime)} –{' '}
                            {formatTime12h(plan.leg1.endTime)}
                          </span>
                        </div>
                        <div className="text-[11px] text-slate-500 truncate mt-0.5">
                          {plan.leg1.room.name}
                        </div>
                        {plan.leg1.kickOutReason && (
                          <div className="text-[10px] text-amber-700 font-semibold mt-1 truncate">
                            At {formatTime12h(plan.leg1.endTime)}:{' '}
                            {plan.leg1.kickOutReason} arrives
                          </div>
                        )}
                      </div>

                      {/* Hop Arrow if 1-Hop */}
                      {plan.leg2 && (
                        <>
                          <div className="sm:col-span-1 flex sm:flex-col items-center justify-center text-indigo-600 py-1">
                            <ArrowRight className="w-4 h-4" />
                            <span className="text-[9px] font-mono font-bold uppercase">
                              Hop
                            </span>
                          </div>

                          {/* Leg 2 */}
                          <div
                            onClick={() =>
                              onSelectRoomOnMap(
                                plan.leg2!.room.id,
                                plan.leg2!.startTime
                              )
                            }
                            className="sm:col-span-5 bg-white border border-teal-300 hover:border-teal-500 rounded-xl p-3 cursor-pointer transition-colors"
                          >
                            <div className="flex items-center justify-between">
                              <span className="font-mono text-sm font-extrabold text-slate-900">
                                2. {plan.leg2.room.code}
                              </span>
                              <span className="font-mono text-[11px] font-bold text-teal-700 tabular-nums">
                                {formatTime12h(plan.leg2.startTime)} –{' '}
                                {formatTime12h(plan.leg2.endTime)}
                              </span>
                            </div>
                            <div className="text-[11px] text-slate-500 truncate mt-0.5">
                              {plan.leg2.room.name}
                            </div>
                            <div className="text-[10px] text-teal-700 font-semibold mt-1">
                              Walk 15s on {plan.floorName} · Free{' '}
                              {formatDurationMinutes(plan.leg2.durationMinutes)}
                            </div>
                          </div>
                        </>
                      )}
                    </div>

                    {/* Action Row */}
                    <div className="mt-3 flex items-center justify-between gap-2 pt-2.5 border-t border-slate-200/70">
                      <button
                        type="button"
                        onClick={() => {
                          onClaimRoom(plan.leg1.room.id);
                          onSelectRoomOnMap(
                            plan.leg1.room.id,
                            plan.leg1.startTime
                          );
                        }}
                        className="text-xs font-bold text-indigo-700 hover:text-indigo-900 inline-flex items-center gap-1 cursor-pointer"
                      >
                        <MapPin className="w-3.5 h-3.5" />
                        <span>View {plan.leg1.room.code} on 3D Map</span>
                      </button>

                      <a
                        href={`https://wa.me/?text=${encodeURIComponent(
                          whatsappRelayMsg
                        )}`}
                        target="_blank"
                        rel="noopener noreferrer"
                        onClick={() => onClaimRoom(plan.leg1.room.id)}
                        className="px-3 py-1.5 rounded-lg bg-[#25D366] hover:bg-[#20BD5A] text-slate-950 text-xs font-bold transition-colors inline-flex items-center gap-1.5"
                      >
                        <MessageCircle className="w-3.5 h-3.5 fill-slate-950" />
                        <span>Send Relay Plan to Squad</span>
                      </a>
                    </div>
                  </div>
                );
              })}
            </div>
          </div>
        </div>
      </div>

      {/* RIGHT 5 COLS: LIVE FACULTY & SUBJECT LOCATOR */}
      <div className="lg:col-span-5 bg-white border-2 border-violet-100 rounded-2xl overflow-hidden shadow-xs flex flex-col justify-between">
        <div>
          <div className="h-1.5 w-full bg-gradient-to-r from-violet-600 via-indigo-600 to-sky-500" />
          <div className="p-6">
            <div className="flex items-start gap-3 pb-4 border-b border-slate-100">
              <div className="w-10 h-10 rounded-xl bg-gradient-to-br from-violet-600 to-indigo-600 text-white flex items-center justify-center shrink-0 shadow-xs">
                <GraduationCap className="w-5 h-5" />
              </div>
              <div>
                <h3 className="text-base font-extrabold text-slate-900 tracking-tight">
                  Live Faculty & Course Radar
                </h3>
                <p className="text-xs text-slate-600 mt-0.5">
                  Need a professor's signature or looking for a lab session? Find which room any faculty member is in at{' '}
                  <span className="font-mono font-bold text-slate-800">
                    {formatTime12h(selectedTime)}
                  </span>
                  .
                </p>
              </div>
            </div>

            {/* Search Input */}
            <div className="mt-4 relative">
              <Search className="w-4 h-4 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2 pointer-events-none" />
              <input
                type="text"
                value={facultyQuery}
                onChange={(e) => setFacultyQuery(e.target.value)}
                placeholder="Search professor (e.g. Kyle, Logan, Blake) or subject..."
                className="w-full pl-9 pr-3 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-xs text-slate-900 placeholder:text-slate-400 focus:outline-none focus:bg-white focus:border-violet-500"
              />
            </div>

            {/* Faculty Status List */}
            <div className="mt-4 space-y-2.5 max-h-[420px] overflow-y-auto pr-1">
              {filteredFaculty.map((item) => {
                const activeRoom = item.activeNow
                  ? ROOMS.find((r) => r.id === item.activeNow!.roomId)
                  : null;
                const nextRoom = item.nextToday
                  ? ROOMS.find((r) => r.id === item.nextToday!.roomId)
                  : null;

                return (
                  <div
                    key={item.faculty}
                    className="p-3 rounded-xl border border-slate-200 bg-slate-50/70 hover:bg-white transition-all flex items-center justify-between gap-3"
                  >
                    <div className="min-w-0 flex-1">
                      <div className="flex items-center gap-2 flex-wrap">
                        <span className="text-xs font-extrabold text-slate-900">
                          {item.faculty}
                        </span>
                        {item.activeNow && activeRoom ? (
                          <span className="px-2 py-0.5 rounded-md bg-emerald-100 text-emerald-800 font-mono text-[10px] font-bold">
                            IN {activeRoom.code} NOW
                          </span>
                        ) : item.nextToday && nextRoom ? (
                          <span className="px-2 py-0.5 rounded-md bg-amber-100 text-amber-800 font-mono text-[10px] font-bold">
                            NEXT: {nextRoom.code} @{' '}
                            {formatTime12h(item.nextToday.startTime)}
                          </span>
                        ) : (
                          <span className="px-2 py-0.5 rounded-md bg-slate-200 text-slate-600 font-mono text-[10px] font-semibold">
                            No more classes today
                          </span>
                        )}
                      </div>

                      <div className="text-[11px] text-slate-600 truncate mt-0.5">
                        {item.activeNow
                          ? `${item.activeNow.subjectName} · ${item.activeNow.sectionName} (until ${formatTime12h(
                              item.activeNow.endTime
                            )})`
                          : item.nextToday
                          ? `Next: ${item.nextToday.subjectName} (${item.nextToday.sectionName})`
                          : item.subjects[0]}
                      </div>
                    </div>

                    {(activeRoom || nextRoom) && (
                      <button
                        type="button"
                        onClick={() => {
                          const targetRoomId =
                            activeRoom?.id || nextRoom?.id || '';
                          const targetTime =
                            item.activeNow?.startTime ||
                            item.nextToday?.startTime;
                          if (targetRoomId) {
                            onSelectRoomOnMap(targetRoomId, targetTime);
                          }
                        }}
                        className="px-2.5 py-1.5 rounded-lg bg-violet-600 hover:bg-violet-700 text-white text-[11px] font-bold shrink-0 cursor-pointer inline-flex items-center gap-1"
                      >
                        <MapPin className="w-3 h-3" />
                        <span>Locate</span>
                      </button>
                    )}
                  </div>
                );
              })}
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};
import React from 'react';
import { CheckCircle2, Lock } from 'lucide-react';
import { DayOfWeek, FLOORS, PERIOD_SLOTS } from '../data/roomsData';
import { RoomAvailabilityStatus } from '../utils/occupancyEngine';

interface OccupancyMatrixViewProps {
  currentDay: DayOfWeek;
  statuses: RoomAvailabilityStatus[];
  onSelectRoom: (status: RoomAvailabilityStatus) => void;
}

export const OccupancyMatrixView: React.FC<OccupancyMatrixViewProps> = ({
  currentDay,
  statuses,
  onSelectRoom,
}) => {
  return (
    <section className="bg-white border border-slate-200 rounded-xl p-6 space-y-6">
      <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-3 pb-4 border-b border-slate-100">
        <div>
          <h2 className="text-lg font-semibold text-slate-900 tracking-tight">
            Full-Building Occupancy Matrix ({currentDay})
          </h2>
          <p className="text-sm text-slate-600 mt-0.5">
            Scan all 25 rooms across all 9 periods on {currentDay} to spot multi-hour empty blocks for group study.
          </p>
        </div>
        <div className="flex items-center gap-4 text-xs text-slate-600 shrink-0">
          <span className="inline-flex items-center gap-1.5 text-[#16A34A] font-medium">
            <CheckCircle2 className="w-3.5 h-3.5" />
            <span>Empty Slot</span>
          </span>
          <span className="inline-flex items-center gap-1.5 text-[#DC2626] font-medium">
            <Lock className="w-3.5 h-3.5" />
            <span>Scheduled Class</span>
          </span>
        </div>
      </div>

      {FLOORS.map((floor) => {
        const floorStatuses = statuses.filter(
          (s) => s.room.floorId === floor.id
        );

        return (
          <div key={floor.id} className="space-y-2.5">
            <div className="flex items-center justify-between">
              <h3 className="text-sm font-semibold text-slate-900">
                {floor.name}{' '}
                <span className="font-normal text-slate-500">
                  · {floor.seriesLabel}
                </span>
              </h3>
            </div>

            <div className="border border-slate-200 rounded-lg overflow-x-auto">
              <table className="w-full text-left border-collapse min-w-[880px]">
                <thead>
                  <tr className="bg-slate-50 border-b border-slate-200 text-[11px] font-semibold text-slate-600">
                    <th className="py-2 px-3.5 border-r border-slate-200 w-48">
                      Room & Climate
                    </th>
                    {PERIOD_SLOTS.map((p) => (
                      <th
                        key={p.period}
                        className="py-2 px-2 border-r border-slate-200 last:border-r-0 text-center"
                      >
                        <div className="font-mono text-slate-900 tabular-nums">
                          {p.label}
                        </div>
                        <div className="font-mono text-[10px] text-slate-400 font-normal tabular-nums">
                          {p.start}–{p.end}
                        </div>
                      </th>
                    ))}
                  </tr>
                </thead>
                <tbody className="divide-y divide-slate-200 text-xs">
                  {floorStatuses.map((st) => (
                    <tr
                      key={st.room.id}
                      onClick={() => onSelectRoom(st)}
                      className="hover:bg-slate-50 cursor-pointer transition-colors"
                    >
                      <td className="py-2.5 px-3.5 border-r border-slate-200">
                        <div className="flex items-center justify-between">
                          <span className="font-mono font-bold text-slate-900 tabular-nums">
                            {st.room.code}
                          </span>
                          <span className="text-[11px] text-slate-500">
                            {st.room.isAC ? 'AC' : 'Non-AC'} · {st.room.capacity}s
                          </span>
                        </div>
                        <div className="text-[11px] text-slate-500 truncate max-w-[170px]">
                          {st.room.name}
                        </div>
                      </td>
                      {st.periodTimeline.map((cell) => (
                        <td
                          key={cell.period}
                          className={`py-2 px-2 border-r border-slate-200 last:border-r-0 text-center font-mono tabular-nums text-[11px] ${
                            cell.isOccupied
                              ? 'bg-red-50/60 text-red-900'
                              : 'bg-emerald-50/40 text-emerald-800'
                          } ${
                            cell.isCurrentPeriod
                              ? 'ring-2 ring-inset ring-slate-900/25'
                              : ''
                          }`}
                        >
                          {cell.isOccupied ? (
                            <div>
                              <div className="font-semibold truncate max-w-[80px] mx-auto">
                                {cell.sessions[0]?.sectionName}
                              </div>
                              <div className="text-[10px] text-red-700/80 truncate max-w-[80px] mx-auto">
                                {cell.sessions[0]?.slotCode}
                              </div>
                            </div>
                          ) : (
                            <span className="font-medium text-emerald-700">
                              Free
                            </span>
                          )}
                        </td>
                      ))}
                    </tr>
                  ))}
                </tbody>
              </table>
            </div>
          </div>
        );
      })}
    </section>
  );
};
import React from 'react';
import {
  CheckCircle2,
  AlertTriangle,
  Lock,
  ArrowUpRight,
  Snowflake,
  Wind,
  Users,
  Plug,
  Sparkles,
  Clock,
  MessageCircle,
  MapPin,
  Star,
} from 'lucide-react';
import {
  formatDurationMinutes,
  formatTime12h,
  RoomAvailabilityStatus,
} from '../utils/occupancyEngine';

interface RoomCardProps {
  status: RoomAvailabilityStatus;
  isAIHighlighted: boolean;
  isClaimed?: boolean;
  isFavorite?: boolean;
  onSelect: (status: RoomAvailabilityStatus) => void;
  onClaimRoom?: (roomId: string) => void;
  onToggleFavorite?: (roomId: string) => void;
}

export const RoomCard: React.FC<RoomCardProps> = ({
  status,
  isAIHighlighted,
  isClaimed = false,
  isFavorite = false,
  onSelect,
  onClaimRoom,
  onToggleFavorite,
}) => {
  const {
    room,
    isCurrentlyEmpty,
    statusState,
    freeDurationMinutes,
    freeDurationFormatted,
    isFreeRestOfDay,
  } = status;

  // Calculate visual progress percentage for free window (cap at 240 mins = 4 hours for 100% bar)
  const freeProgressPercent = isCurrentlyEmpty
    ? Math.min(100, Math.max(12, Math.round((freeDurationMinutes / 240) * 100)))
    : 0;

  const untilText = isCurrentlyEmpty
    ? isFreeRestOfDay
      ? '5:05 PM'
      : formatTime12h(status.freeUntilTime)
    : `after ${formatTime12h(status.clearsAtTime || '17:05')}`;

  const whatsappMessage = `📍 Heading to ${room.code}. It's free until ${untilText}. Come fast!`;
  const whatsappHref = `https://wa.me/?text=${encodeURIComponent(whatsappMessage)}`;

  const cardShellClass = isClaimed
    ? 'border-teal-500 ring-2 ring-teal-500/25 bg-white shadow-md shadow-teal-500/10'
    : isAIHighlighted
    ? 'border-indigo-500 ring-2 ring-indigo-500/20 bg-white shadow-md shadow-indigo-500/5 hover:shadow-lg'
    : statusState === 'free-long'
    ? 'border-emerald-200/90 hover:border-emerald-400 bg-white shadow-xs hover:shadow-md'
    : statusState === 'free-short'
    ? 'border-amber-300 hover:border-amber-400 bg-white shadow-xs hover:shadow-md'
    : 'border-rose-200/80 bg-rose-50/15 hover:bg-white hover:border-rose-300';

  const topStripeClass = isClaimed
    ? 'bg-gradient-to-r from-teal-400 via-emerald-500 to-indigo-500'
    : isAIHighlighted
    ? 'bg-gradient-to-r from-indigo-600 via-violet-500 to-teal-500'
    : statusState === 'free-long'
    ? 'bg-gradient-to-r from-emerald-500 to-teal-500'
    : statusState === 'free-short'
    ? 'bg-gradient-to-r from-amber-500 to-orange-500'
    : 'bg-gradient-to-r from-rose-500 to-red-500';

  return (
    <div
      onClick={() => onSelect(status)}
      className={`group rounded-xl border overflow-hidden transition-all duration-200 cursor-pointer flex flex-col justify-between ${cardShellClass}`}
    >
      {/* Colorful Top Status Stripe */}
      <div className={`h-1.5 w-full ${topStripeClass}`} />

      <div className="p-5 flex-1 flex flex-col justify-between">
        <div>
          {/* Top Row: Room Code + Status Callout */}
          <div className="flex items-start justify-between gap-3">
            <div>
              <div className="flex items-center gap-2 flex-wrap">
                <h3 className="font-mono text-xl font-bold text-slate-900 tabular-nums tracking-tight group-hover:text-indigo-700 transition-colors">
                  {room.code}
                </h3>
                {onToggleFavorite && (
                  <button
                    type="button"
                    onClick={(e) => {
                      e.stopPropagation();
                      onToggleFavorite(room.id);
                    }}
                    title={isFavorite ? 'Remove from Pinned Rooms' : 'Pin Favorite Room'}
                    className={`p-1 rounded-md transition-colors cursor-pointer ${
                      isFavorite
                        ? 'text-amber-500 hover:text-amber-600'
                        : 'text-slate-300 hover:text-amber-400'
                    }`}
                  >
                    <Star
                      className={`w-4 h-4 ${isFavorite ? 'fill-amber-400' : ''}`}
                    />
                  </button>
                )}
                {isClaimed && (
                  <span className="inline-flex items-center gap-1 text-xs font-bold text-teal-700">
                    <MapPin className="w-3.5 h-3.5 text-teal-600" />
                    <span>Squad Claimed</span>
                  </span>
                )}
                {!isClaimed && isAIHighlighted && (
                  <span className="inline-flex items-center gap-1 text-xs font-bold text-indigo-700">
                    <Sparkles className="w-3.5 h-3.5 text-indigo-600" />
                    <span>AI Top Match</span>
                  </span>
                )}
              </div>
              <p className="text-xs font-medium text-slate-600 mt-0.5 line-clamp-1">
                {room.name}
              </p>
            </div>

            {/* Friendly Availability Status Indicator */}
            <div className="text-right shrink-0">
              {statusState === 'free-long' && (
                <div className="inline-flex items-center gap-1.5 text-xs font-bold text-emerald-700 font-mono tabular-nums">
                  <CheckCircle2 className="w-4 h-4 text-emerald-600 shrink-0" />
                  <span>Free {freeDurationFormatted}</span>
                </div>
              )}
              {statusState === 'free-short' && (
                <div className="inline-flex items-center gap-1.5 text-xs font-bold text-amber-700 font-mono tabular-nums">
                  <AlertTriangle className="w-4 h-4 text-amber-600 shrink-0" />
                  <span>{freeDurationFormatted} left</span>
                </div>
              )}
              {statusState === 'occupied' && (
                <div className="inline-flex items-center gap-1.5 text-xs font-bold text-rose-700 font-mono tabular-nums">
                  <Lock className="w-4 h-4 text-rose-600 shrink-0" />
                  <span>In Class</span>
                </div>
              )}
              <p className="text-[11px] font-mono tabular-nums text-slate-500 mt-0.5">
                {isCurrentlyEmpty
                  ? isFreeRestOfDay
                    ? 'Free rest of day'
                    : `Until ${formatTime12h(status.freeUntilTime)}`
                  : status.clearsAtTime
                  ? `Clears ${formatTime12h(status.clearsAtTime)}`
                  : 'Occupied'}
              </p>
            </div>
          </div>

          {/* Colorful Friendly Callout Banner + Progress Bar */}
          <div className="mt-3.5">
            {statusState === 'free-long' && (
              <div className="rounded-lg bg-emerald-50/70 border-l-4 border-emerald-500 px-3 py-2">
                <div className="flex items-center justify-between text-xs">
                  <span className="font-semibold text-emerald-900">
                    Safe to sit & work undisturbed
                  </span>
                  <span className="font-mono font-semibold text-emerald-700 tabular-nums">
                    {isFreeRestOfDay
                      ? 'Until 05:05 PM'
                      : `Next class ${formatTime12h(status.freeUntilTime)}`}
                  </span>
                </div>
                <div className="mt-1.5 w-full h-1.5 bg-emerald-200/70 rounded-full overflow-hidden">
                  <div
                    className="h-full bg-gradient-to-r from-emerald-500 to-teal-500 rounded-full"
                    style={{ width: `${freeProgressPercent}%` }}
                  />
                </div>
              </div>
            )}

            {statusState === 'free-short' && (
              <div className="rounded-lg bg-amber-50/80 border-l-4 border-amber-500 px-3 py-2">
                <div className="flex items-center justify-between text-xs">
                  <span className="font-semibold text-amber-900">
                    Heads up! Professor arrives soon
                  </span>
                  <span className="font-mono font-semibold text-amber-800 tabular-nums">
                    At {formatTime12h(status.freeUntilTime)}
                  </span>
                </div>
                <p className="text-[11px] text-amber-800/90 mt-0.5 truncate">
                  Next: {status.nextSession?.subjectName} ({status.nextSession?.sectionName})
                </p>
              </div>
            )}

            {statusState === 'occupied' && (
              <div className="rounded-lg bg-rose-50/80 border-l-4 border-rose-500 px-3 py-2">
                <div className="flex items-center justify-between text-xs">
                  <span className="font-semibold text-rose-900 truncate max-w-[180px]">
                    {status.currentSessions[0]?.subjectName}
                  </span>
                  {status.clearsInMinutes !== null && (
                    <span className="font-mono font-semibold text-rose-700 tabular-nums shrink-0">
                      Free in {formatDurationMinutes(status.clearsInMinutes)}
                    </span>
                  )}
                </div>
                <p className="text-[11px] text-rose-800/80 mt-0.5 truncate">
                  {status.currentSessions[0]?.sectionName} · {status.currentSessions[0]?.faculty}
                </p>
              </div>
            )}
          </div>

          {/* Colorful Icon-Backed Amenity Row */}
          <div className="mt-3.5 pt-3 border-t border-slate-100 grid grid-cols-2 gap-2 text-xs">
            <div className="flex items-center gap-1.5">
              {room.isAC ? (
                <>
                  <Snowflake className="w-3.5 h-3.5 text-sky-500 shrink-0" />
                  <span className="font-medium text-sky-900">AC Climate</span>
                </>
              ) : (
                <>
                  <Wind className="w-3.5 h-3.5 text-slate-400 shrink-0" />
                  <span className="text-slate-600">Natural Air</span>
                </>
              )}
            </div>

            <div className="flex items-center gap-1.5">
              <Users className="w-3.5 h-3.5 text-indigo-500 shrink-0" />
              <span className="text-slate-700 font-mono tabular-nums">
                {room.capacity} Seats
              </span>
            </div>

            <div className="flex items-center gap-1.5">
              <Plug className="w-3.5 h-3.5 text-amber-500 shrink-0" />
              <span className="text-slate-600 truncate" title={room.powerOutlets}>
                {room.powerOutlets === 'High (Every Bench)'
                  ? 'Bench Power'
                  : room.powerOutlets === 'Moderate (Wall)'
                  ? 'Wall Outlets'
                  : 'Standard Power'}
              </span>
            </div>

            <div className="flex items-center gap-1.5">
              <Clock className="w-3.5 h-3.5 text-teal-500 shrink-0" />
              <span className="text-slate-600 truncate">{room.quietScore}</span>
            </div>
          </div>
        </div>

        {/* Bottom Section: 9-Period Bar + Instant "Call the Squad" Button */}
        <div className="mt-4 pt-3 border-t border-slate-100 space-y-3">
          <div>
            <div className="flex items-center justify-between text-[11px] text-slate-500 mb-1.5">
              <span className="font-medium">Today's 9-Period Timeline</span>
              <span className="inline-flex items-center gap-0.5 text-indigo-600 group-hover:text-indigo-800 font-semibold">
                <span>Timer & Schedule</span>
                <ArrowUpRight className="w-3.5 h-3.5" />
              </span>
            </div>
            <div className="grid grid-cols-9 gap-1">
              {status.periodTimeline.map((cell) => {
                const barColor = cell.isOccupied
                  ? cell.isCurrentPeriod
                    ? 'bg-rose-600 ring-2 ring-rose-600/30'
                    : 'bg-rose-300'
                  : cell.isCurrentPeriod
                  ? 'bg-emerald-600 ring-2 ring-emerald-600/30'
                  : 'bg-emerald-300/80';

                return (
                  <div key={cell.period} className="flex flex-col items-center">
                    <div
                      className={`w-full h-2.5 rounded-xs transition-all ${barColor}`}
                      title={`${cell.label} (${cell.start}–${cell.end}): ${
                        cell.isOccupied
                          ? `Occupied — ${cell.sessions[0]?.subjectName} (${cell.sessions[0]?.sectionName})`
                          : 'Free / Empty'
                      }`}
                    />
                    <span
                      className={`text-[10px] font-mono tabular-nums mt-1 ${
                        cell.isCurrentPeriod
                          ? 'font-bold text-indigo-700 underline'
                          : 'text-slate-400'
                      }`}
                    >
                      {cell.period === 5 ? 'L' : `P${cell.period}`}
                    </span>
                  </div>
                );
              })}
            </div>
          </div>

          {/* Direct "Call the Squad" WhatsApp Action on Empty Rooms */}
          {isCurrentlyEmpty && (
            <div
              onClick={(e) => e.stopPropagation()}
              className="pt-1 flex items-center gap-2"
            >
              <a
                href={whatsappHref}
                target="_blank"
                rel="noopener noreferrer"
                onClick={() => onClaimRoom && onClaimRoom(room.id)}
                className="flex-1 py-2 px-3 rounded-lg bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-semibold transition-colors flex items-center justify-center gap-1.5 shadow-2xs"
              >
                <MessageCircle className="w-3.5 h-3.5" />
                <span>Call the Squad (WhatsApp)</span>
              </a>
            </div>
          )}
        </div>
      </div>
    </div>
  );
};
import React, { useEffect, useState } from 'react';
import {
  X,
  CheckCircle2,
  Lock,
  Clock,
  MessageCircle,
  Copy,
  Check,
  MapPin,
  Snowflake,
  Users,
} from 'lucide-react';
import {
  DayOfWeek,
  DAYS_OF_WEEK,
  FLOORS,
  PERIOD_SLOTS,
} from '../data/roomsData';
import { ALL_CLASS_SESSIONS } from '../data/timetablesPart2';
import {
  formatTime12h,
  RoomAvailabilityStatus,
} from '../utils/occupancyEngine';

interface RoomDetailModalProps {
  status: RoomAvailabilityStatus | null;
  claimedRoomId?: string | null;
  onClaimRoom?: (roomId: string | null) => void;
  onClose: () => void;
}

export const RoomDetailModal: React.FC<RoomDetailModalProps> = ({
  status,
  claimedRoomId,
  onClaimRoom,
  onClose,
}) => {
  const [selectedDay, setSelectedDay] = useState<DayOfWeek>(
    status?.day || 'Monday'
  );
  const [secondsElapsed, setSecondsElapsed] = useState<number>(0);
  const [copied, setCopied] = useState<boolean>(false);

  useEffect(() => {
    if (status) {
      setSelectedDay(status.day);
      setSecondsElapsed(0);
    }
  }, [status]);

  useEffect(() => {
    if (!status) return;
    const interval = setInterval(() => {
      setSecondsElapsed((prev) => prev + 1);
    }, 1000);
    return () => clearInterval(interval);
  }, [status]);

  if (!status) return null;

  const { room } = status;
  const floorMeta = FLOORS.find((f) => f.id === room.floorId);

  const daySessions = ALL_CLASS_SESSIONS.filter(
    (s) => s.roomId === room.id && s.day === selectedDay
  );

  const totalSeconds = status.isCurrentlyEmpty
    ? Math.max(0, status.freeDurationMinutes * 60)
    : Math.max(0, (status.clearsInMinutes || 0) * 60);

  const remainingSeconds = Math.max(0, totalSeconds - secondsElapsed);
  const hh = String(Math.floor(remainingSeconds / 3600)).padStart(2, '0');
  const mm = String(Math.floor((remainingSeconds % 3600) / 60)).padStart(2, '0');
  const ss = String(remainingSeconds % 60).padStart(2, '0');

  const untilText = status.isCurrentlyEmpty
    ? status.isFreeRestOfDay
      ? '5:05 PM'
      : formatTime12h(status.freeUntilTime)
    : `after ${formatTime12h(status.clearsAtTime || '17:05')}`;

  const squadMessage = `📍 Heading to ${room.code}. It's free until ${untilText}. Come fast!`;
  const whatsappUrl = `https://wa.me/?text=${encodeURIComponent(squadMessage)}`;

  const handleCopy = async () => {
    try {
      await navigator.clipboard.writeText(squadMessage);
      setCopied(true);
      setTimeout(() => setCopied(false), 2000);
    } catch {
      setCopied(true);
      setTimeout(() => setCopied(false), 2000);
    }
  };

  return (
    <div
      className="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-xs flex items-center justify-center p-4"
      onClick={onClose}
    >
      <div
        className="bg-white border border-slate-200 rounded-2xl max-w-3xl w-full max-h-[90vh] overflow-y-auto shadow-2xl overflow-hidden"
        onClick={(e) => e.stopPropagation()}
      >
        {/* Top Colorful Accent Bar */}
        <div
          className={`h-2 w-full ${
            status.isCurrentlyEmpty
              ? 'bg-gradient-to-r from-emerald-500 via-teal-500 to-indigo-500'
              : 'bg-gradient-to-r from-rose-500 to-orange-500'
          }`}
        />

        <div className="p-6">
          {/* Header */}
          <div className="flex items-start justify-between gap-4 pb-4 border-b border-slate-200">
            <div>
              <div className="flex items-center gap-3 flex-wrap">
                <h2 className="font-mono text-2xl font-extrabold text-slate-900 tabular-nums">
                  {room.code}
                </h2>
                <span className="text-slate-300">·</span>
                <span className="text-base font-bold text-slate-800">
                  {room.name}
                </span>
              </div>
              <div className="flex flex-wrap items-center gap-2.5 text-xs text-slate-600 mt-1.5">
                <span className="font-semibold text-indigo-700">
                  {floorMeta?.name}
                </span>
                <span aria-hidden="true">·</span>
                <span>{room.wing}</span>
                <span aria-hidden="true">·</span>
                <span className="inline-flex items-center gap-1 text-sky-700 font-medium">
                  <Snowflake className="w-3.5 h-3.5" />
                  <span>{room.isAC ? 'Air Conditioned (AC)' : 'Natural Air'}</span>
                </span>
                <span aria-hidden="true">·</span>
                <span className="inline-flex items-center gap-1 font-mono tabular-nums">
                  <Users className="w-3.5 h-3.5 text-indigo-500" />
                  <span>{room.capacity} Seats</span>
                </span>
              </div>
            </div>

            <button
              type="button"
              onClick={onClose}
              className="p-2 text-slate-400 hover:text-slate-700 rounded-xl hover:bg-slate-100 transition-colors cursor-pointer"
              aria-label="Close modal"
            >
              <X className="w-5 h-5" />
            </button>
          </div>

          {/* Live Countdown Timer + Call the Squad Card */}
          <div className="mt-4 grid grid-cols-1 md:grid-cols-12 gap-4">
            {/* Countdown Box */}
            <div
              className={`md:col-span-6 rounded-xl p-4 border ${
                status.isCurrentlyEmpty
                  ? 'bg-emerald-50/70 border-emerald-200'
                  : 'bg-rose-50/70 border-rose-200'
              }`}
            >
              <div className="flex items-center justify-between text-xs font-bold">
                {status.isCurrentlyEmpty ? (
                  <span className="text-emerald-800 inline-flex items-center gap-1.5">
                    <CheckCircle2 className="w-4 h-4 text-emerald-600" />
                    <span>Time Left Before Next Class:</span>
                  </span>
                ) : (
                  <span className="text-rose-800 inline-flex items-center gap-1.5">
                    <Lock className="w-4 h-4 text-rose-600" />
                    <span>Occupied — Room Clears In:</span>
                  </span>
                )}
                <span className="font-mono text-[11px] text-slate-500">
                  LIVE TIMER
                </span>
              </div>

              <div className="mt-2 flex items-baseline gap-2">
                <span
                  className={`font-mono text-3xl font-extrabold tabular-nums tracking-tight ${
                    status.isCurrentlyEmpty ? 'text-emerald-700' : 'text-rose-700'
                  }`}
                >
                  {hh}:{mm}:{ss}
                </span>
                <span className="text-xs text-slate-600 font-medium">
                  ({status.isCurrentlyEmpty ? `Until ${untilText}` : `Clears ${untilText}`})
                </span>
              </div>

              <p className="text-xs text-slate-600 mt-1.5 truncate">
                {status.isCurrentlyEmpty
                  ? status.nextSession
                    ? `Next: ${status.nextSession.subjectName} (${status.nextSession.sectionName})`
                    : 'No more classes scheduled today!'
                  : `Current: ${status.currentSessions[0]?.subjectName} (${status.currentSessions[0]?.sectionName})`}
              </p>
            </div>

            {/* Call the Squad Box */}
            <div className="md:col-span-6 rounded-xl p-4 bg-slate-900 text-white flex flex-col justify-between">
              <div>
                <div className="flex items-center justify-between">
                  <span className="text-xs font-bold text-emerald-400">
                    Call the Squad · WhatsApp Invite
                  </span>
                  {onClaimRoom && (
                    <button
                      type="button"
                      onClick={() =>
                        onClaimRoom(
                          claimedRoomId === room.id ? null : room.id
                        )
                      }
                      className={`text-[11px] font-semibold px-2 py-0.5 rounded cursor-pointer flex items-center gap-1 ${
                        claimedRoomId === room.id
                          ? 'bg-teal-400 text-slate-950'
                          : 'bg-slate-800 text-slate-300 hover:bg-slate-700'
                      }`}
                    >
                      <MapPin className="w-3 h-3" />
                      <span>
                        {claimedRoomId === room.id ? 'Claimed' : 'Claim Spot'}
                      </span>
                    </button>
                  )}
                </div>
                <p className="text-xs text-slate-300 mt-1.5 font-mono line-clamp-2">
                  "{squadMessage}"
                </p>
              </div>

              <div className="mt-3 flex items-center gap-2">
                <a
                  href={whatsappUrl}
                  target="_blank"
                  rel="noopener noreferrer"
                  onClick={() =>
                    onClaimRoom &&
                    claimedRoomId !== room.id &&
                    onClaimRoom(room.id)
                  }
                  className="flex-1 py-2 px-3 bg-[#25D366] hover:bg-[#20BD5A] text-slate-950 font-bold text-xs rounded-lg transition-colors flex items-center justify-center gap-1.5"
                >
                  <MessageCircle className="w-3.5 h-3.5 fill-slate-950" />
                  <span>Send on WhatsApp</span>
                </a>
                <button
                  type="button"
                  onClick={handleCopy}
                  className="py-2 px-3 bg-slate-800 hover:bg-slate-700 text-slate-200 font-semibold text-xs rounded-lg transition-colors flex items-center gap-1 cursor-pointer"
                >
                  {copied ? (
                    <>
                      <Check className="w-3.5 h-3.5 text-emerald-400" />
                      <span>Copied</span>
                    </>
                  ) : (
                    <>
                      <Copy className="w-3.5 h-3.5" />
                      <span>Copy</span>
                    </>
                  )}
                </button>
              </div>
            </div>
          </div>

          {/* Day Selector Tabs */}
          <div className="mt-6 flex items-center justify-between flex-wrap gap-3">
            <h3 className="text-sm font-bold text-slate-900">
              Period-by-Period Schedule ({selectedDay})
            </h3>
            <div className="flex items-center gap-1 p-1 bg-slate-100 rounded-xl">
              {DAYS_OF_WEEK.map((d) => (
                <button
                  key={d}
                  type="button"
                  onClick={() => setSelectedDay(d)}
                  className={`px-3 py-1.5 text-xs font-semibold rounded-lg transition-colors whitespace-nowrap cursor-pointer ${
                    selectedDay === d
                      ? 'bg-indigo-600 text-white shadow-xs'
                      : 'text-slate-600 hover:text-slate-900'
                  }`}
                >
                  {d.slice(0, 3)}
                </button>
              ))}
            </div>
          </div>

          {/* 9-Period Table */}
          <div className="mt-3 border border-slate-200 rounded-xl overflow-hidden">
            <table className="w-full text-left border-collapse">
              <thead>
                <tr className="bg-slate-50 border-b border-slate-200 text-xs font-semibold text-slate-600">
                  <th className="py-2.5 px-3.5 w-20">Period</th>
                  <th className="py-2.5 px-3.5 w-36">Time Slot</th>
                  <th className="py-2.5 px-3.5 w-28">Status</th>
                  <th className="py-2.5 px-3.5">Scheduled Lecture / Section / Faculty</th>
                </tr>
              </thead>
              <tbody className="divide-y divide-slate-200 text-xs">
                {PERIOD_SLOTS.map((slot) => {
                  const matching = daySessions.filter(
                    (s) => s.period === slot.period
                  );
                  const isOccupied = matching.length > 0;

                  return (
                    <tr
                      key={slot.period}
                      className={
                        isOccupied
                          ? 'bg-rose-50/20 hover:bg-rose-50/40'
                          : 'bg-emerald-50/35 hover:bg-emerald-50/60'
                      }
                    >
                      <td className="py-2.5 px-3.5 font-mono font-bold text-slate-900 tabular-nums">
                        {slot.label}
                      </td>
                      <td className="py-2.5 px-3.5 font-mono text-slate-600 tabular-nums">
                        {slot.display}
                      </td>
                      <td className="py-2.5 px-3.5 font-bold">
                        {isOccupied ? (
                          <span className="text-rose-600 inline-flex items-center gap-1">
                            <Lock className="w-3.5 h-3.5" />
                            <span>Occupied</span>
                          </span>
                        ) : (
                          <span className="text-emerald-700 inline-flex items-center gap-1">
                            <CheckCircle2 className="w-3.5 h-3.5" />
                            <span>Empty</span>
                          </span>
                        )}
                      </td>
                      <td className="py-2.5 px-3.5 text-slate-700">
                        {isOccupied ? (
                          <div className="space-y-1">
                            {matching.map((m, idx) => (
                              <div key={idx}>
                                <span className="font-semibold text-slate-900">
                                  {m.subjectName}
                                </span>
                                <span className="text-slate-500">
                                  {' '}
                                  · {m.subjectCode} · {m.sectionName} · {m.faculty}
                                </span>
                              </div>
                            ))}
                          </div>
                        ) : slot.period === 5 ? (
                          <span className="text-slate-600 inline-flex items-center gap-1 font-medium">
                            <Clock className="w-3.5 h-3.5 text-teal-600" />
                            <span>Common Lunch Window — Open for student groups</span>
                          </span>
                        ) : (
                          <span className="text-emerald-800 font-semibold">
                            Available for student self-study & project groups
                          </span>
                        )}
                      </td>
                    </tr>
                  );
                })}
              </tbody>
            </table>
          </div>

          {/* Footer */}
          <div className="mt-4 flex items-center justify-between text-xs text-slate-500">
            <span>
              Primary Sections Assigned: {room.primarySections.join(' · ')}
            </span>
            <button
              type="button"
              onClick={onClose}
              className="px-5 py-2 bg-slate-900 text-white font-semibold rounded-xl hover:bg-slate-800 transition-colors cursor-pointer"
            >
              Done
            </button>
          </div>
        </div>
      </div>
    </div>
  );
};
import React, { useMemo, useState } from 'react';
import {
  Users,
  Sparkles,
  Clock,
  MapPin,
  ArrowRight,
  CheckCircle2,
  Calendar,
  Compass,
  Snowflake,
  MessageCircle,
  Footprints,
  Layers,
} from 'lucide-react';
import {
  DayOfWeek,
  FLOORS,
  PERIOD_SLOTS,
  ROOMS,
} from '../data/roomsData';
import { SECTION_METAS } from '../data/timetablesPart1';
import { ALL_CLASS_SESSIONS } from '../data/timetablesPart2';
import {
  computeAllRoomsStatus,
  formatTime12h,
  RoomAvailabilityStatus,
} from '../utils/occupancyEngine';

interface SectionGapFinderProps {
  selectedDay: DayOfWeek;
  selectedTime: string;
  onSelectRoomOnMap: (roomId: string, time24?: string) => void;
  onClaimRoom: (roomId: string) => void;
  onInspectRoom: (status: RoomAvailabilityStatus) => void;
}

export const SectionGapFinder: React.FC<SectionGapFinderProps> = ({
  selectedDay,
  selectedTime,
  onSelectRoomOnMap,
  onClaimRoom,
  onInspectRoom,
}) => {
  // Primary student section
  const [mySectionId, setMySectionId] = useState<string>('III-ECE-A');
  // Optional 2nd section for cross-section project teams
  const [teammateSectionId, setTeammateSectionId] = useState<string>('none');

  const mySectionMeta = useMemo(
    () => SECTION_METAS.find((s) => s.id === mySectionId) || SECTION_METAS[0],
    [mySectionId]
  );

  const teammateSectionMeta = useMemo(
    () =>
      teammateSectionId !== 'none'
        ? SECTION_METAS.find((s) => s.id === teammateSectionId) || null
        : null,
    [teammateSectionId]
  );

  // Compute period-by-period status for the selected section(s) on `selectedDay`
  const periodBreakdown = useMemo(() => {
    const mySessions = ALL_CLASS_SESSIONS.filter(
      (s) => s.sectionId === mySectionId && s.day === selectedDay
    );
    const mateSessions =
      teammateSectionId !== 'none'
        ? ALL_CLASS_SESSIONS.filter(
            (s) => s.sectionId === teammateSectionId && s.day === selectedDay
          )
        : [];

    return PERIOD_SLOTS.map((slot) => {
      const myMatch = mySessions.filter((s) => s.period === slot.period);
      const mateMatch = mateSessions.filter((s) => s.period === slot.period);
      const isBothFree = myMatch.length === 0 && mateMatch.length === 0;

      // Determine best rooms at this period's start time
      const statusesAtSlot = computeAllRoomsStatus(selectedDay, slot.start);

      return {
        slot,
        myMatch,
        mateMatch,
        isBothFree,
        statusesAtSlot,
      };
    });
  }, [mySectionId, teammateSectionId, selectedDay]);

  // Group contiguous free periods into "Free Gap Windows"
  const freeGapWindows = useMemo(() => {
    const windows: {
      startPeriod: number;
      endPeriod: number;
      startTime: string;
      endTime: string;
      durationMinutes: number;
      periodLabels: string[];
      prevRoomId: string | null;
      nextRoomId: string | null;
      recommendedRooms: RoomAvailabilityStatus[];
    }[] = [];

    let i = 0;
    while (i < periodBreakdown.length) {
      if (!periodBreakdown[i].isBothFree) {
        i++;
        continue;
      }
      let j = i;
      while (
        j + 1 < periodBreakdown.length &&
        periodBreakdown[j + 1].isBothFree
      ) {
        j++;
      }

      const startSlot = periodBreakdown[i].slot;
      const endSlot = periodBreakdown[j].slot;
      const [sh, sm] = startSlot.start.split(':').map(Number);
      const [eh, em] = endSlot.end.split(':').map(Number);
      const durationMinutes = eh * 60 + em - (sh * 60 + sm);

      const prevRoomId =
        i > 0 && periodBreakdown[i - 1].myMatch.length > 0
          ? periodBreakdown[i - 1].myMatch[0].roomId
          : null;
      const nextRoomId =
        j + 1 < periodBreakdown.length &&
        periodBreakdown[j + 1].myMatch.length > 0
          ? periodBreakdown[j + 1].myMatch[0].roomId
          : null;

      // Find the floor of surrounding classes so students don't have to climb stairs!
      const anchorRoomId = nextRoomId || prevRoomId;
      const anchorFloorId = anchorRoomId
        ? ROOMS.find((r) => r.id === anchorRoomId)?.floorId
        : null;

      const statusesAtStart = computeAllRoomsStatus(
        selectedDay,
        startSlot.start
      );

      // Rank empty rooms that stay free for the entire gap (or longest available)
      const rankedRooms = statusesAtStart
        .filter((st) => st.isCurrentlyEmpty && st.freeDurationMinutes >= 45)
        .sort((a, b) => {
          const aCoversAll = a.freeDurationMinutes >= durationMinutes ? 1 : 0;
          const bCoversAll = b.freeDurationMinutes >= durationMinutes ? 1 : 0;
          if (aCoversAll !== bCoversAll) return bCoversAll - aCoversAll;

          const aSameFloor = anchorFloorId && a.room.floorId === anchorFloorId ? 1 : 0;
          const bSameFloor = anchorFloorId && b.room.floorId === anchorFloorId ? 1 : 0;
          if (aSameFloor !== bSameFloor) return bSameFloor - aSameFloor;

          if (a.room.isAC !== b.room.isAC) return a.room.isAC ? -1 : 1;
          return b.freeDurationMinutes - a.freeDurationMinutes;
        })
        .slice(0, 3);

      windows.push({
        startPeriod: startSlot.period,
        endPeriod: endSlot.period,
        startTime: startSlot.start,
        endTime: endSlot.end,
        durationMinutes,
        periodLabels: periodBreakdown
          .slice(i, j + 1)
          .map((p) => p.slot.label),
        prevRoomId,
        nextRoomId,
        recommendedRooms: rankedRooms,
      });

      i = j + 1;
    }

    return windows;
  }, [periodBreakdown, selectedDay]);

  return (
    <section className="space-y-6">
      {/* Top Control Card */}
      <div className="bg-white border-2 border-indigo-100 rounded-2xl overflow-hidden shadow-xs">
        <div className="h-1.5 w-full bg-gradient-to-r from-indigo-600 via-teal-500 to-emerald-500" />
        <div className="p-6">
          <div className="flex flex-col lg:flex-row lg:items-center justify-between gap-4 pb-5 border-b border-slate-100">
            <div className="flex items-start gap-3.5">
              <div className="w-11 h-11 rounded-xl bg-gradient-to-br from-indigo-600 to-violet-600 text-white flex items-center justify-center shrink-0 shadow-sm">
                <Compass className="w-5 h-5" />
              </div>
              <div>
                <h2 className="text-lg font-extrabold text-slate-900 tracking-tight">
                  My Section Gap Finder & Project Team Sync
                </h2>
                <p className="text-sm text-slate-600 mt-0.5">
                  Select your class section (and optional teammate section) to automatically spot your free hours today and find the closest empty room on the same floor.
                </p>
              </div>
            </div>

            <div className="inline-flex items-center gap-2 text-xs font-mono bg-indigo-50 text-indigo-900 px-3.5 py-2 rounded-xl border border-indigo-200/70 self-start lg:self-auto">
              <Calendar className="w-3.5 h-3.5 text-indigo-600" />
              <span>Day:</span>
              <strong className="font-bold">{selectedDay}</strong>
            </div>
          </div>

          {/* Section Pickers: My Section + Optional Teammate Section */}
          <div className="mt-5 grid grid-cols-1 lg:grid-cols-12 gap-5">
            <div className="lg:col-span-7 space-y-2">
              <label className="block text-xs font-bold text-slate-700 uppercase tracking-wider">
                1. Select Your Class Section:
              </label>
              <div className="flex flex-wrap gap-1.5">
                {SECTION_METAS.map((sec) => (
                  <button
                    key={sec.id}
                    type="button"
                    onClick={() => setMySectionId(sec.id)}
                    className={`px-3 py-1.5 rounded-xl text-xs font-bold transition-all cursor-pointer ${
                      mySectionId === sec.id
                        ? 'bg-indigo-600 text-white shadow-xs'
                        : 'bg-slate-100 text-slate-700 hover:bg-slate-200'
                    }`}
                  >
                    {sec.name}
                  </button>
                ))}
              </div>
            </div>

            <div className="lg:col-span-5 space-y-2 lg:border-l lg:border-slate-200 lg:pl-5">
              <label className="block text-xs font-bold text-teal-800 uppercase tracking-wider flex items-center gap-1.5">
                <Users className="w-3.5 h-3.5 text-teal-600" />
                <span>2. Project Teammate's Section (Optional Sync):</span>
              </label>
              <select
                value={teammateSectionId}
                onChange={(e) => setTeammateSectionId(e.target.value)}
                className="w-full px-3.5 py-2.5 bg-teal-50/50 border border-teal-200 rounded-xl text-xs font-bold text-slate-900 focus:outline-none focus:border-teal-600 cursor-pointer"
              >
                <option value="none">
                  Solo / Same Section Only ({mySectionMeta.name})
                </option>
                {SECTION_METAS.filter((s) => s.id !== mySectionId).map((sec) => (
                  <option key={sec.id} value={sec.id}>
                    Sync Free Gaps with {sec.name} ({sec.department})
                  </option>
                ))}
              </select>
              <p className="text-[11px] text-slate-500">
                {teammateSectionMeta
                  ? `Showing common free gaps where BOTH ${mySectionMeta.name} and ${teammateSectionMeta.name} have no lectures!`
                  : `Home Venue: ${mySectionMeta.primaryVenue} (${mySectionMeta.shift} Shift)`}
              </p>
            </div>
          </div>

          {/* Visual 9-Period Ribbon for Selected Section(s) */}
          <div className="mt-6 pt-5 border-t border-slate-100">
            <div className="flex items-center justify-between text-xs mb-2.5">
              <span className="font-bold text-slate-800">
                {teammateSectionMeta
                  ? `Combined Schedule Ribbon (${mySectionMeta.name} + ${teammateSectionMeta.name}) on ${selectedDay}`
                  : `${mySectionMeta.name} Daily Schedule & Free Gaps on ${selectedDay}`}
              </span>
              <span className="text-slate-500">
                Click any green free slot to jump to that hour
              </span>
            </div>

            <div className="grid grid-cols-1 sm:grid-cols-9 gap-2">
              {periodBreakdown.map((item) => {
                const { slot, myMatch, mateMatch, isBothFree } = item;
                return (
                  <div
                    key={slot.period}
                    onClick={() => {
                      if (isBothFree && item.statusesAtSlot.length > 0) {
                        const firstEmpty = item.statusesAtSlot.find(
                          (s) => s.isCurrentlyEmpty
                        );
                        if (firstEmpty) {
                          onSelectRoomOnMap(firstEmpty.room.id, slot.start);
                        }
                      }
                    }}
                    className={`rounded-xl p-2.5 border transition-all ${
                      isBothFree
                        ? 'bg-emerald-50/80 border-emerald-300 hover:bg-emerald-100 cursor-pointer'
                        : 'bg-slate-100 border-slate-200/90 opacity-85'
                    }`}
                  >
                    <div className="flex items-center justify-between text-[11px] font-mono">
                      <span className="font-extrabold text-slate-900">
                        {slot.label}
                      </span>
                      <span className="text-slate-500">{slot.start}</span>
                    </div>

                    {isBothFree ? (
                      <div className="mt-1.5">
                        <span className="inline-flex items-center gap-1 text-[11px] font-bold text-emerald-700">
                          <CheckCircle2 className="w-3 h-3 shrink-0" />
                          <span>FREE GAP</span>
                        </span>
                        <div className="text-[10px] text-emerald-800/80 mt-0.5">
                          {
                            item.statusesAtSlot.filter((s) => s.isCurrentlyEmpty)
                              .length
                          }{' '}
                          rooms open
                        </div>
                      </div>
                    ) : (
                      <div className="mt-1.5 space-y-1">
                        {myMatch.length > 0 && (
                          <div className="text-[10px] leading-tight">
                            <span className="font-bold text-indigo-900 block truncate">
                              {myMatch[0].subjectName}
                            </span>
                            <span className="font-mono text-slate-500">
                              {ROOMS.find((r) => r.id === myMatch[0].roomId)?.code}
                            </span>
                          </div>
                        )}
                        {mateMatch.length > 0 && (
                          <div className="text-[10px] leading-tight pt-0.5 border-t border-slate-200">
                            <span className="font-bold text-teal-900 block truncate">
                              {mateMatch[0].sectionName}: {mateMatch[0].slotCode}
                            </span>
                          </div>
                        )}
                      </div>
                    )}
                  </div>
                );
              })}
            </div>
          </div>
        </div>
      </div>

      {/* Free Gap Cards with Zero-Stair-Climb Room Recommendations */}
      <div className="space-y-4">
        <div className="flex items-center justify-between">
          <h3 className="text-base font-extrabold text-slate-900">
            Recommended Empty Classrooms for Your Free Gaps ({freeGapWindows.length}{' '}
            {freeGapWindows.length === 1 ? 'Window' : 'Windows'} Today)
          </h3>
        </div>

        <div className="grid grid-cols-1 lg:grid-cols-2 gap-5">
          {freeGapWindows.map((gap, idx) => {
            const prevRoom = gap.prevRoomId
              ? ROOMS.find((r) => r.id === gap.prevRoomId)
              : null;
            const nextRoom = gap.nextRoomId
              ? ROOMS.find((r) => r.id === gap.nextRoomId)
              : null;
            const anchorRoom = nextRoom || prevRoom;
            const anchorFloor = anchorRoom
              ? FLOORS.find((f) => f.id === anchorRoom.floorId)
              : null;

            const hrs = Math.floor(gap.durationMinutes / 60);
            const mins = gap.durationMinutes % 60;
            const durationStr =
              hrs > 0 ? `${hrs}h ${mins > 0 ? `${mins}m` : ''}` : `${mins}m`;

            return (
              <div
                key={idx}
                className="bg-white border border-slate-200 rounded-2xl p-5 shadow-xs flex flex-col justify-between space-y-4"
              >
                <div>
                  {/* Gap Header */}
                  <div className="flex items-start justify-between gap-3 pb-3.5 border-b border-slate-100">
                    <div>
                      <div className="inline-flex items-center gap-2">
                        <span className="px-2.5 py-1 rounded-lg bg-emerald-600 text-white font-mono text-xs font-extrabold">
                          {gap.periodLabels.join(' + ')}
                        </span>
                        <span className="font-mono text-sm font-extrabold text-slate-900 tabular-nums">
                          {formatTime12h(gap.startTime)} –{' '}
                          {formatTime12h(gap.endTime)}
                        </span>
                      </div>
                      <p className="text-xs text-slate-600 mt-1.5 flex items-center gap-1.5">
                        <Footprints className="w-3.5 h-3.5 text-indigo-600 shrink-0" />
                        {anchorFloor && anchorRoom ? (
                          <span>
                            Surrounding class is in{' '}
                            <strong className="text-slate-900">
                              {anchorRoom.code} ({anchorFloor.shortName})
                            </strong>{' '}
                            — zero-stair-climb rooms prioritized!
                          </span>
                        ) : (
                          <span>
                            Open free block — top AC & group-friendly rooms ranked below.
                          </span>
                        )}
                      </p>
                    </div>

                    <div className="text-right shrink-0">
                      <span className="font-mono text-lg font-extrabold text-emerald-700 tabular-nums">
                        {durationStr}
                      </span>
                      <span className="block text-[10px] font-semibold uppercase tracking-wider text-slate-400">
                        Unbroken Gap
                      </span>
                    </div>
                  </div>

                  {/* Top 3 Matched Empty Rooms for this Gap */}
                  <div className="mt-3.5 space-y-2.5">
                    {gap.recommendedRooms.map((st, rIdx) => {
                      const isSameFloor =
                        anchorRoom && st.room.floorId === anchorRoom.floorId;
                      const floorObj = FLOORS.find(
                        (f) => f.id === st.room.floorId
                      );

                      const whatsappText = `📍 We have a ${durationStr.trim()} free gap (${formatTime12h(
                        gap.startTime
                      )}–${formatTime12h(gap.endTime)})! Heading to ${
                        st.room.code
                      } (${floorObj?.shortName}). Come fast!`;

                      return (
                        <div
                          key={st.room.id}
                          className="p-3 rounded-xl border border-slate-200 hover:border-indigo-400 bg-slate-50/70 hover:bg-white transition-all flex flex-col sm:flex-row sm:items-center justify-between gap-3"
                        >
                          <div
                            onClick={() => onInspectRoom(st)}
                            className="cursor-pointer flex-1"
                          >
                            <div className="flex items-center gap-2 flex-wrap">
                              <span className="w-5 h-5 rounded-md bg-indigo-600 text-white font-mono text-[11px] font-bold flex items-center justify-center">
                                {rIdx + 1}
                              </span>
                              <span className="font-mono text-base font-extrabold text-slate-900">
                                {st.room.code}
                              </span>
                              {isSameFloor && (
                                <span className="text-[11px] font-bold text-teal-700 bg-teal-50 border border-teal-200 px-2 py-0.5 rounded-md inline-flex items-center gap-1">
                                  <Layers className="w-3 h-3" />
                                  <span>Same Floor ({floorObj?.shortName})</span>
                                </span>
                              )}
                              {st.room.isAC && (
                                <span className="text-[11px] font-semibold text-sky-700 inline-flex items-center gap-0.5">
                                  <Snowflake className="w-3 h-3" />
                                  <span>AC</span>
                                </span>
                              )}
                            </div>
                            <div className="text-xs text-slate-600 mt-0.5">
                              {st.room.name} ·{' '}
                              <span className="font-mono font-semibold text-emerald-700">
                                Empty for {st.freeDurationFormatted}
                              </span>
                            </div>
                          </div>

                          <div className="flex items-center gap-2 shrink-0">
                            <button
                              type="button"
                              onClick={() => {
                                onClaimRoom(st.room.id);
                                onSelectRoomOnMap(st.room.id, gap.startTime);
                              }}
                              className="px-3 py-1.5 rounded-lg bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-bold transition-colors cursor-pointer flex items-center gap-1"
                            >
                              <MapPin className="w-3 h-3" />
                              <span>3D Map</span>
                            </button>
                            <a
                              href={`https://wa.me/?text=${encodeURIComponent(
                                whatsappText
                              )}`}
                              target="_blank"
                              rel="noopener noreferrer"
                              onClick={() => onClaimRoom(st.room.id)}
                              className="px-3 py-1.5 rounded-lg bg-[#25D366] hover:bg-[#20BD5A] text-slate-950 text-xs font-bold transition-colors flex items-center gap-1"
                            >
                              <MessageCircle className="w-3 h-3 fill-slate-950" />
                              <span>Squad</span>
                            </a>
                          </div>
                        </div>
                      );
                    })}
                  </div>
                </div>
              </div>
            );
          })}
        </div>
      </div>
    </section>
  );
};
import React, { useState } from 'react';
import { DAYS_OF_WEEK, PERIOD_SLOTS, ROOMS } from '../data/roomsData';
import { SECTION_METAS } from '../data/timetablesPart1';
import { ALL_CLASS_SESSIONS } from '../data/timetablesPart2';

export const SectionTimetablesView: React.FC = () => {
  const [selectedSectionId, setSelectedSectionId] = useState<string>(
    SECTION_METAS[0].id
  );

  const sectionMeta =
    SECTION_METAS.find((s) => s.id === selectedSectionId) || SECTION_METAS[0];

  const sectionSessions = ALL_CLASS_SESSIONS.filter(
    (s) => s.sectionId === selectedSectionId
  );

  // Extract unique subjects for the legend table below the timetable
  const uniqueSubjectsMap = new Map<
    string,
    { slotCode: string; subjectCode: string; subjectName: string; faculty: string; rooms: Set<string> }
  >();

  for (const s of sectionSessions) {
    const key = `${s.subjectCode}-${s.subjectName}`;
    if (!uniqueSubjectsMap.has(key)) {
      uniqueSubjectsMap.set(key, {
        slotCode: s.slotCode,
        subjectCode: s.subjectCode,
        subjectName: s.subjectName,
        faculty: s.faculty,
        rooms: new Set([s.roomId]),
      });
    } else {
      uniqueSubjectsMap.get(key)!.rooms.add(s.roomId);
    }
  }

  const uniqueSubjects = Array.from(uniqueSubjectsMap.values());

  return (
    <section className="space-y-6">
      {/* Section Picker Bar */}
      <div className="bg-white border border-slate-200 rounded-xl p-6">
        <div className="flex flex-col md:flex-row md:items-center justify-between gap-4 pb-4 border-b border-slate-100">
          <div>
            <h2 className="text-lg font-semibold text-slate-900 tracking-tight">
              Department Class Timetables Dataset (SRM IST Tiruchirappalli)
            </h2>
            <p className="text-sm text-slate-600 mt-0.5">
              Complete digitized dataset from the official Odd/Even Semester timetables used to compute room occupancy.
            </p>
          </div>
          <div className="text-xs text-slate-500 font-mono tabular-nums shrink-0">
            <span>Primary Venue: </span>
            <strong className="text-slate-900">{sectionMeta.primaryVenue}</strong>
            <span aria-hidden="true"> · </span>
            <span>Shift: {sectionMeta.shift}</span>
          </div>
        </div>

        {/* Interactive Section Selector Buttons */}
        <div className="mt-4 flex flex-wrap gap-1.5">
          {SECTION_METAS.map((sec) => (
            <button
              key={sec.id}
              type="button"
              onClick={() => setSelectedSectionId(sec.id)}
              className={`px-3 py-1.5 text-xs font-medium rounded-lg transition-colors whitespace-nowrap cursor-pointer ${
                selectedSectionId === sec.id
                  ? 'bg-slate-900 text-white'
                  : 'bg-slate-100 text-slate-700 hover:bg-slate-200'
              }`}
            >
              {sec.name}
            </button>
          ))}
        </div>

        {/* Section Metadata Header */}
        <div className="mt-5 flex flex-wrap items-center justify-between gap-2 text-xs text-slate-600 bg-slate-50 px-4 py-2.5 rounded-lg border border-slate-200/70">
          <div className="flex flex-wrap items-center gap-2">
            <span className="font-semibold text-slate-900">{sectionMeta.name}</span>
            <span aria-hidden="true">·</span>
            <span>{sectionMeta.yearSem}</span>
            <span aria-hidden="true">·</span>
            <span>{sectionMeta.department}</span>
            <span aria-hidden="true">·</span>
            <span>{sectionMeta.semesterLabel}</span>
          </div>
          <span className="font-mono tabular-nums text-slate-500">
            Assigned Venue: {sectionMeta.primaryVenue}
          </span>
        </div>

        {/* Timetable Grid */}
        <div className="mt-4 border border-slate-200 rounded-lg overflow-x-auto">
          <table className="w-full text-left border-collapse min-w-[900px]">
            <thead>
              <tr className="bg-slate-50 border-b border-slate-200 text-[11px] font-semibold text-slate-600">
                <th className="py-2.5 px-3 border-r border-slate-200 w-24">
                  Day / Period
                </th>
                {PERIOD_SLOTS.map((p) => (
                  <th
                    key={p.period}
                    className="py-2.5 px-2.5 border-r border-slate-200 last:border-r-0 text-center"
                  >
                    <div className="font-mono text-slate-900 tabular-nums">
                      {p.label}
                    </div>
                    <div className="font-mono text-[10px] text-slate-500 font-normal tabular-nums mt-0.5">
                      {p.start}–{p.end}
                    </div>
                  </th>
                ))}
              </tr>
            </thead>
            <tbody className="divide-y divide-slate-200 text-xs">
              {DAYS_OF_WEEK.map((day) => (
                <tr key={day} className="hover:bg-slate-50/60">
                  <td className="py-3 px-3 font-semibold text-slate-900 border-r border-slate-200 bg-slate-50/40">
                    {day.slice(0, 3)}
                  </td>
                  {PERIOD_SLOTS.map((p) => {
                    const cellSessions = sectionSessions.filter(
                      (s) => s.day === day && s.period === p.period
                    );

                    if (cellSessions.length === 0) {
                      return (
                        <td
                          key={p.period}
                          className="py-2.5 px-2 border-r border-slate-200 last:border-r-0 text-center text-slate-400 font-mono text-[11px]"
                        >
                          {p.period === 5 ? 'LUNCH' : '—'}
                        </td>
                      );
                    }

                    return (
                      <td
                        key={p.period}
                        className="py-2 px-2 border-r border-slate-200 last:border-r-0 align-top bg-teal-50/25"
                      >
                        {cellSessions.map((cs, i) => {
                          const roomCode =
                            ROOMS.find((r) => r.id === cs.roomId)?.code || cs.roomId;
                          return (
                            <div
                              key={i}
                              className={i > 0 ? 'mt-1.5 pt-1.5 border-t border-slate-200' : ''}
                            >
                              <div className="flex items-center justify-between gap-1">
                                <span className="font-mono font-bold text-slate-900 text-[11px]">
                                  {cs.slotCode}
                                </span>
                                <span className="font-mono text-[11px] font-semibold text-teal-800 tabular-nums">
                                  {roomCode}
                                </span>
                              </div>
                              <div
                                className="text-[11px] text-slate-600 line-clamp-1 mt-0.5"
                                title={cs.subjectName}
                              >
                                {cs.subjectName}
                              </div>
                            </div>
                          );
                        })}
                      </td>
                    );
                  })}
                </tr>
              ))}
            </tbody>
          </table>
        </div>

        {/* Faculty & Course Mapping Table */}
        <div className="mt-6">
          <h3 className="text-xs font-semibold text-slate-500 mb-2.5">
            Subject Slot & Faculty Legend for {sectionMeta.name}
          </h3>
          <div className="border border-slate-200 rounded-lg overflow-hidden">
            <table className="w-full text-left border-collapse text-xs">
              <thead>
                <tr className="bg-slate-50 border-b border-slate-200 text-slate-600 font-semibold">
                  <th className="py-2 px-3.5 w-20">Slot</th>
                  <th className="py-2 px-3.5 w-32">Subject Code</th>
                  <th className="py-2 px-3.5">Subject Name</th>
                  <th className="py-2 px-3.5">Name of Faculty</th>
                  <th className="py-2 px-3.5 w-36">Assigned Venue</th>
                </tr>
              </thead>
              <tbody className="divide-y divide-slate-200">
                {uniqueSubjects.map((sub, idx) => {
                  const roomCodes = Array.from(sub.rooms).map(
                    (rid) => ROOMS.find((r) => r.id === rid)?.code || rid
                  );
                  return (
                    <tr key={idx} className="hover:bg-slate-50">
                      <td className="py-2 px-3.5 font-mono font-semibold text-slate-900">
                        {sub.slotCode}
                      </td>
                      <td className="py-2 px-3.5 font-mono text-slate-600 tabular-nums">
                        {sub.subjectCode}
                      </td>
                      <td className="py-2 px-3.5 font-medium text-slate-900">
                        {sub.subjectName}
                      </td>
                      <td className="py-2 px-3.5 text-slate-600">{sub.faculty}</td>
                      <td className="py-2 px-3.5 font-mono text-teal-800 font-medium tabular-nums">
                        {roomCodes.join(', ')}
                      </td>
                    </tr>
                  );
                })}
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </section>
  );
};
export type DayOfWeek = 'Monday' | 'Tuesday' | 'Wednesday' | 'Thursday' | 'Friday';

export type FloorId = 'ground' | 'first' | 'second' | 'third';

export interface FloorMeta {
  id: FloorId;
  name: string;
  shortName: string;
  seriesLabel: string;
  description: string;
  aliases: string[];
}

export interface RoomInfo {
  id: string;
  code: string;
  name: string;
  floorId: FloorId;
  wing: string;
  isAC: boolean;
  capacity: number;
  roomType: 'Classroom' | 'Computer Lab' | 'Electronics Lab' | 'Seminar Hall' | 'Workshop' | 'Language Studio';
  powerOutlets: 'High (Every Bench)' | 'Moderate (Wall)' | 'Standard';
  teamFriendly: boolean;
  quietScore: 'Silent Study' | 'Collaborative' | 'Active Lab';
  amenities: string[];
  primarySections: string[];
}

export interface ClassSession {
  sectionId: string;
  sectionName: string;
  day: DayOfWeek;
  period: number; // 1 to 9
  startTime: string; // HH:mm (24h)
  endTime: string;   // HH:mm (24h)
  roomId: string;
  slotCode: string;
  subjectCode: string;
  subjectName: string;
  faculty: string;
}

export interface SectionTimetableMeta {
  id: string;
  name: string;
  yearSem: string;
  department: string;
  semesterLabel: string;
  primaryVenue: string;
  shift: 'FN' | 'AN' | 'Full Day';
}

export const DAYS_OF_WEEK: DayOfWeek[] = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'];

export const PERIOD_SLOTS = [
  { period: 1, label: 'P1', start: '09:00', end: '09:50', display: '09:00 – 09:50' },
  { period: 2, label: 'P2', start: '09:50', end: '10:45', display: '09:50 – 10:45' },
  { period: 3, label: 'P3', start: '10:50', end: '11:40', display: '10:50 – 11:40' },
  { period: 4, label: 'P4', start: '11:40', end: '12:35', display: '11:40 – 12:35' },
  { period: 5, label: 'LUNCH', start: '12:35', end: '13:20', display: '12:35 – 01:20' },
  { period: 6, label: 'P6', start: '13:20', end: '14:20', display: '01:20 – 02:20' },
  { period: 7, label: 'P7', start: '14:20', end: '15:15', display: '02:20 – 03:15' },
  { period: 8, label: 'P8', start: '15:15', end: '16:10', display: '03:15 – 04:10' },
  { period: 9, label: 'P9', start: '16:10', end: '17:05', display: '04:10 – 05:05' },
];

export const FLOORS: FloorMeta[] = [
  {
    id: 'ground',
    name: 'Ground Floor',
    shortName: 'Ground Floor',
    seriesLabel: '100-Series · Tech Block & Workshop',
    description: 'AC Seminar Room TB-106, MPMC & VLSI Collaborative Labs (107, 108), and Engineering Workshop.',
    aliases: ['ground', 'ground floor', 'level 0', 'floor 0', '100', '1xx', 'tb', 'workshop', 'first level'],
  },
  {
    id: 'first',
    name: 'First Floor',
    shortName: '1st Floor',
    seriesLabel: '200 & 300-Series · Senior ECE & BME Wing',
    description: 'Quiet senior lecture rooms (IST 201, 211, 225, 227) and EEC/VLSI Systems Lab 309.',
    aliases: ['first', 'first floor', '1st', '1st floor', 'floor 1', '200', '2xx', '300', '3xx', 'second level'],
  },
  {
    id: 'second',
    name: 'Second Floor',
    shortName: '2nd Floor',
    seriesLabel: '400 & 500-Series · ECE & Data Science Wing',
    description: 'Core ECE, Data Science, and Biotech classrooms (IST 401–520) with projector setups.',
    aliases: ['second', 'second floor', '2nd', '2nd floor', 'floor 2', '400', '4xx', '500', '5xx', 'fourth floor', 'fifth floor'],
  },
  {
    id: 'third',
    name: 'Third Floor (Upper Wing)',
    shortName: '3rd Floor',
    seriesLabel: '600 & 700-Series · Computing Labs & Main Halls',
    description: 'High-capacity lecture halls (602, 702, 710), Language Studio (626), CDC (609, 625), and PPS Labs (617, 618).',
    aliases: ['third', 'third floor', '3rd', '3rd floor', 'floor 3', 'upper', 'top floor', '600', '6xx', '700', '7xx', 'sixth floor', 'seventh floor'],
  },
];

export const ROOMS: RoomInfo[] = [
  // GROUND FLOOR
  {
    id: 'TB-106',
    code: 'TB-106',
    name: 'CDC & Verbal Reasoning Seminar Room',
    floorId: 'ground',
    wing: 'Tech Block Ground Wing',
    isAC: true,
    capacity: 65,
    roomType: 'Seminar Hall',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '65 Seats', 'Group Worktables', 'Projector', 'Power Strips'],
    primarySections: ['II-BME', 'II-ECE-DS A', 'II-ECE-DS B'],
  },
  {
    id: 'IST-107',
    code: 'IST 107',
    name: 'MPMC & Digital IC Collaborative Lab',
    floorId: 'ground',
    wing: 'IST Ground West',
    isAC: true,
    capacity: 45,
    roomType: 'Electronics Lab',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '45 Seats', 'Team Workbenches', 'Bench Power', 'Whiteboard'],
    primarySections: ['II-BME', 'II-ECE-DS A', 'II-ECE-DS B', 'III-BME', 'III-ECE-DS'],
  },
  {
    id: 'IST-108',
    code: 'IST 108',
    name: 'VLSI, Bio-DSP & Network Security Studio',
    floorId: 'ground',
    wing: 'IST Ground West',
    isAC: true,
    capacity: 45,
    roomType: 'Computer Lab',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '45 Seats', 'Workstations', 'Team Tables', 'High-Speed LAN'],
    primarySections: ['I-ECE-A', 'III-BME', 'III-ECE-A', 'III-ECE-B', 'III-ECE-DS', 'IV-ECE-A', 'IV-ECE-B'],
  },
  {
    id: 'IST-20-21',
    code: 'IST 20,21',
    name: 'Basic Civil & Mechanical Workshop Bay',
    floorId: 'ground',
    wing: 'IST Ground Annex',
    isAC: false,
    capacity: 80,
    roomType: 'Workshop',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Active Lab',
    amenities: ['Natural Ventilation', '80 Seats', 'Heavy Project Tables', 'Hardware Prototyping'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-ECE-DS', 'I-Biotech-B'],
  },
  {
    id: 'CHE-LAB',
    code: 'Che Lab',
    name: 'Engineering Chemistry Wet Lab',
    floorId: 'ground',
    wing: 'IST Ground East',
    isAC: false,
    capacity: 50,
    roomType: 'Electronics Lab',
    powerOutlets: 'Standard',
    teamFriendly: false,
    quietScore: 'Active Lab',
    amenities: ['Exhaust Ventilation', '50 Stools', 'Granite Counters'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-ECE-DS', 'I-Biotech-B'],
  },

  // FIRST FLOOR (200 & 300 Series)
  {
    id: 'IST-201',
    code: 'IST 201',
    name: 'General Lecture & NSS Hall 201',
    floorId: 'first',
    wing: 'IST 1st Floor North',
    isAC: false,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Standard',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Quiet Corner', '65 Seats', 'Dual Whiteboards', 'Cross Ventilation'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-ECE-DS'],
  },
  {
    id: 'IST-211',
    code: 'IST 211',
    name: 'Biomedical Engineering Lecture Room',
    floorId: 'first',
    wing: 'IST 1st Floor Central',
    isAC: true,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '65 Seats', 'Smart Projector', 'Wall Outlets'],
    primarySections: ['III-BME (AN)'],
  },
  {
    id: 'IST-225',
    code: 'IST 225',
    name: 'Senior ECE Lecture Classroom 225',
    floorId: 'first',
    wing: 'IST 1st Floor South',
    isAC: true,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '65 Seats', 'Projector', 'Laptop Charging Strips'],
    primarySections: ['IV-ECE-A (FN)'],
  },
  {
    id: 'IST-227',
    code: 'IST 227',
    name: 'Senior ECE Lecture Classroom 227',
    floorId: 'first',
    wing: 'IST 1st Floor South',
    isAC: false,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Quiet Wing', '65 Seats', 'Projector', 'Wide Desks'],
    primarySections: ['IV-ECE-B (FN)'],
  },
  {
    id: 'IST-309',
    code: 'IST 309',
    name: 'EEC & VLSI Systems Design Lab',
    floorId: 'first',
    wing: 'IST Mezzanine / 300-Wing',
    isAC: true,
    capacity: 50,
    roomType: 'Computer Lab',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '50 Seats', 'EDA Workstations', 'Team Pods', 'Bench Power'],
    primarySections: ['II-BME', 'II-ECE-DS A', 'II-ECE-DS B', 'III-ECE-A', 'III-ECE-B'],
  },

  // SECOND FLOOR (400 & 500 Series)
  {
    id: 'IST-401',
    code: 'IST 401',
    name: 'Human Values & Collaborative Hall 401',
    floorId: 'second',
    wing: 'IST 2nd Floor North',
    isAC: true,
    capacity: 70,
    roomType: 'Seminar Hall',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '70 Seats', 'Flexible Group Seating', 'AV System'],
    primarySections: ['II-ECE-DS B'],
  },
  {
    id: 'IST-411',
    code: 'IST 411',
    name: 'ECE Data Science Classroom 411',
    floorId: 'second',
    wing: 'IST 2nd Floor Central',
    isAC: true,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '65 Seats', 'Projector', 'Whiteboard'],
    primarySections: ['II-ECE-DS B (AN)'],
  },
  {
    id: 'IST-416',
    code: 'IST 416',
    name: 'ECE Data Science Classroom 416',
    floorId: 'second',
    wing: 'IST 2nd Floor South',
    isAC: false,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Bright Natural Light', '65 Seats', 'Projector', 'Whiteboard'],
    primarySections: ['II-ECE-DS A (FN)'],
  },
  {
    id: 'IST-502',
    code: 'IST 502',
    name: 'Freshman Data Science Lecture Hall',
    floorId: 'second',
    wing: 'IST 500-Wing North',
    isAC: true,
    capacity: 70,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '70 Seats', 'Smart Board', 'Projector'],
    primarySections: ['I-ECE-DS'],
  },
  {
    id: 'IST-509',
    code: 'IST 509',
    name: 'ECE Collaborative Study & Tutorial Room 509',
    floorId: 'second',
    wing: 'IST 500-Wing Central',
    isAC: true,
    capacity: 60,
    roomType: 'Classroom',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '60 Seats', 'Project Tables', 'Bench Power', 'Whiteboard'],
    primarySections: ['III-ECE-A', 'III-ECE-DS', 'Open Tutorial'],
  },
  {
    id: 'IST-510',
    code: 'IST 510',
    name: 'Central Aptitude & Core Lecture Room',
    floorId: 'second',
    wing: 'IST 500-Wing Central',
    isAC: false,
    capacity: 75,
    roomType: 'Classroom',
    powerOutlets: 'Standard',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['75 Seats', 'Large Stepped Benches', 'Dual Boards'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-ECE-DS', 'I-Biotech-B'],
  },
  {
    id: 'IST-518',
    code: 'IST 518',
    name: 'Junior ECE Shared Lecture Hall 518',
    floorId: 'second',
    wing: 'IST 500-Wing South',
    isAC: true,
    capacity: 70,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '70 Seats', 'Projector', 'Mic System'],
    primarySections: ['III-ECE-A (FN)', 'III-ECE-B (AN)'],
  },
  {
    id: 'IST-519',
    code: 'IST 519',
    name: 'Junior ECE-DS Lecture Hall 519',
    floorId: 'second',
    wing: 'IST 500-Wing South',
    isAC: true,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '65 Seats', 'Projector', 'Bench Power'],
    primarySections: ['III-ECE-DS (FN)'],
  },
  {
    id: 'IST-520',
    code: 'IST 520',
    name: 'EEE & Biotech Shared Lecture Room',
    floorId: 'second',
    wing: 'IST 500-Wing East',
    isAC: false,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Standard',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Quiet Hall', '65 Seats', 'Whiteboard', 'Projector'],
    primarySections: ['I-ECE-B / EEE', 'I-Biotech-B'],
  },

  // THIRD FLOOR (600 & 700 Series)
  {
    id: 'IST-602',
    code: 'IST 602',
    name: 'Main ECE & BME Lecture Hall 602',
    floorId: 'third',
    wing: 'IST 600-Wing North',
    isAC: true,
    capacity: 75,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '75 Seats', 'Smart Podium', 'Projector'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'II-BME (FN)'],
  },
  {
    id: 'IST-609',
    code: 'IST 609',
    name: 'Career Development Seminar Room 609',
    floorId: 'third',
    wing: 'IST 600-Wing Central',
    isAC: true,
    capacity: 55,
    roomType: 'Seminar Hall',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '55 Seats', 'Roundtable Pods', 'Power Outlets'],
    primarySections: ['I-ECE-B'],
  },
  {
    id: 'IST-617',
    code: 'IST 617',
    name: 'PPS & Electronic Circuits Computing Lab',
    floorId: 'third',
    wing: 'IST 600-Wing West',
    isAC: true,
    capacity: 60,
    roomType: 'Computer Lab',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '60 PCs', 'Bench Power', 'Gigabit Wi-Fi'],
    primarySections: ['I-ECE-B', 'I-ECE-DS'],
  },
  {
    id: 'IST-618',
    code: 'IST 618',
    name: 'Programming for Problem Solving Lab 618',
    floorId: 'third',
    wing: 'IST 600-Wing West',
    isAC: true,
    capacity: 60,
    roomType: 'Computer Lab',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '60 PCs', 'Bench Power', 'Gigabit Wi-Fi'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-Biotech-B'],
  },
  {
    id: 'IST-625',
    code: 'IST 625',
    name: 'Analytical & Logical Thinking Studio 625',
    floorId: 'third',
    wing: 'IST 600-Wing South',
    isAC: true,
    capacity: 70,
    roomType: 'Seminar Hall',
    powerOutlets: 'High (Every Bench)',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['Air Conditioned', '70 Seats', 'Team Discussion Tables', 'Projector'],
    primarySections: ['III-BME', 'III-ECE-A', 'III-ECE-B', 'III-ECE-DS'],
  },
  {
    id: 'IST-626',
    code: 'IST 626',
    name: 'German & Foreign Language Studio 626',
    floorId: 'third',
    wing: 'IST 600-Wing South',
    isAC: true,
    capacity: 55,
    roomType: 'Language Studio',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '55 Seats', 'Acoustic Treatment', 'AV Display'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-ECE-DS'],
  },
  {
    id: 'IST-702',
    code: 'IST 702',
    name: 'Biotech & Biomedical Lecture Hall 702',
    floorId: 'third',
    wing: 'IST 700-Wing North',
    isAC: true,
    capacity: 65,
    roomType: 'Classroom',
    powerOutlets: 'Moderate (Wall)',
    teamFriendly: true,
    quietScore: 'Silent Study',
    amenities: ['Air Conditioned', '65 Seats', 'Projector', 'Quiet Upper Level'],
    primarySections: ['I-Biotech-B / Biomed'],
  },
  {
    id: 'IST-710',
    code: 'IST 710',
    name: 'Science & Humanities Lecture Hall 710',
    floorId: 'third',
    wing: 'IST 700-Wing South',
    isAC: false,
    capacity: 90,
    roomType: 'Classroom',
    powerOutlets: 'Standard',
    teamFriendly: true,
    quietScore: 'Collaborative',
    amenities: ['90 Seats', 'Large Hall', 'Dual Projectors'],
    primarySections: ['I-ECE-A', 'I-ECE-B', 'I-ECE-DS', 'I-Biotech-B'],
  },
];
import { ClassSession } from './roomsData';
import { makeSession, SESSIONS_PART_1 } from './timetablesPart1';

export const SESSIONS_PART_2: ClassSession[] = [
  // ==========================================
  // 8. III -BME (PDF 5 — Venue: IST 211 / AN)
  // ==========================================
  // Monday
  ...makeSession('III-BME', 'III BME', 'Monday', [1, 2], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  ...makeSession('III-BME', 'III BME', 'Monday', [3, 4], ['IST-107'], 'LAB', '21BMC302J', 'MPMC Laboratory', 'Dr. K. Vigneshwaran'),
  ...makeSession('III-BME', 'III BME', 'Monday', [6], ['IST-211'], 'E', '21ECO103T', 'Modern Wireless Communication System', 'Dr. Vaishnavi'),
  ...makeSession('III-BME', 'III BME', 'Monday', [7], ['IST-211'], 'B', '21BMC302J', 'Microcontrollers and Its Application in Medicine', 'Dr. K. Vigneshwaran'),
  ...makeSession('III-BME', 'III BME', 'Monday', [8], ['IST-211'], 'F', '21BMC303T', 'Principles of Medical Imaging', 'Dr. N. Prasana Venkatesh'),
  ...makeSession('III-BME', 'III BME', 'Monday', [9], ['IST-211'], 'H', '21LEM301T', 'Indian Art Form', 'Dr. G. Gifta'),
  // Tuesday
  ...makeSession('III-BME', 'III BME', 'Tuesday', [1, 2], ['IST-108'], 'LAB', '21BMC301J', 'Bio-DSP Laboratory', 'Dr. V.N. Senthilkumaran'),
  ...makeSession('III-BME', 'III BME', 'Tuesday', [3], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  ...makeSession('III-BME', 'III BME', 'Tuesday', [6], ['IST-211'], 'C', '21BMC301J', 'Biomedical Signal Processing', 'Dr. V.N. Senthilkumaran'),
  ...makeSession('III-BME', 'III BME', 'Tuesday', [7], ['IST-211'], 'D', '21BME266T', 'Biometrics', 'Dr. G. Gifta'),
  ...makeSession('III-BME', 'III BME', 'Tuesday', [8], ['IST-211'], 'A', '21MAB301T', 'Probability and Statistics', 'Dr. K. M. Karuppusamy'),
  ...makeSession('III-BME', 'III BME', 'Tuesday', [9], ['IST-211'], 'B', '21BMC302J', 'Microcontrollers and Its Application in Medicine', 'Dr. K. Vigneshwaran'),
  // Wednesday
  ...makeSession('III-BME', 'III BME', 'Wednesday', [6], ['IST-211'], 'C', '21BMC301J', 'Biomedical Signal Processing', 'Dr. V.N. Senthilkumaran'),
  ...makeSession('III-BME', 'III BME', 'Wednesday', [7], ['IST-211'], 'A', '21MAB301T', 'Probability and Statistics', 'Dr. K. M. Karuppusamy'),
  ...makeSession('III-BME', 'III BME', 'Wednesday', [8], ['IST-211'], 'F', '21BMC303T', 'Principles of Medical Imaging', 'Dr. N. Prasana Venkatesh'),
  ...makeSession('III-BME', 'III BME', 'Wednesday', [9], ['IST-211'], 'D', '21BME266T', 'Biometrics', 'Dr. G. Gifta'),
  // Thursday
  ...makeSession('III-BME', 'III BME', 'Thursday', [4], ['IST-108'], 'I', '21GNP301L', 'Community Connect', 'Dr. J. Jencia / Dr. N. Prasanna Venkatesh'),
  ...makeSession('III-BME', 'III BME', 'Thursday', [6], ['IST-211'], 'A', '21MAB301T', 'Probability and Statistics', 'Dr. K. M. Karuppusamy'),
  ...makeSession('III-BME', 'III BME', 'Thursday', [7], ['IST-211'], 'C', '21BMC301J', 'Biomedical Signal Processing', 'Dr. V.N. Senthilkumaran'),
  ...makeSession('III-BME', 'III BME', 'Thursday', [8], ['IST-211'], 'E', '21ECO103T', 'Modern Wireless Communication System', 'Dr. Vaishnavi'),
  ...makeSession('III-BME', 'III BME', 'Thursday', [9], ['IST-211'], 'B', '21BMC302J', 'Microcontrollers and Its Application in Medicine', 'Dr. K. Vigneshwaran'),
  // Friday
  ...makeSession('III-BME', 'III BME', 'Friday', [1], ['IST-108'], 'I', '21GNP301L', 'Community Connect', 'Dr. J. Jencia / Dr. N. Prasanna Venkatesh'),
  ...makeSession('III-BME', 'III BME', 'Friday', [6], ['IST-211'], 'F', '21BMC303T', 'Principles of Medical Imaging', 'Dr. N. Prasana Venkatesh'),
  ...makeSession('III-BME', 'III BME', 'Friday', [7], ['IST-211'], 'A', '21MAB301T', 'Probability and Statistics', 'Dr. K. M. Karuppusamy'),
  ...makeSession('III-BME', 'III BME', 'Friday', [8], ['IST-211'], 'D', '21BME266T', 'Biometrics', 'Dr. G. Gifta'),
  ...makeSession('III-BME', 'III BME', 'Friday', [9], ['IST-211'], 'E', '21ECO103T', 'Modern Wireless Communication System', 'Dr. Vaishnavi'),

  // ==========================================
  // 9. III ECE-A (PDF 6 — Venue: IST 518 / FN)
  // ==========================================
  // Monday
  ...makeSession('III-ECE-A', 'III ECE-A', 'Monday', [1], ['IST-518'], 'E', '21CSO355T', 'Machine Learning for All', 'Dr. J. Jencia'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Monday', [2, 3], ['IST-518'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Dr. M. Manikandan'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Monday', [4], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Monday', [6, 7], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  // Tuesday
  ...makeSession('III-ECE-A', 'III ECE-A', 'Tuesday', [1], ['IST-518'], 'H', '21LEM301T', 'Indian Art Form', 'Dr. K. Vigneshwaran'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Tuesday', [2], ['IST-518'], 'D', '21ECE468T', 'System and Network on Chip', 'Dr. V. Manikandan'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Tuesday', [3], ['IST-518'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Dr. M. Manikandan'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Tuesday', [4], ['IST-518'], 'B-Proj', '21ECC301P', 'Microprocessor Project', 'Dr. M. Manikandan'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Tuesday', [7], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  // Wednesday
  ...makeSession('III-ECE-A', 'III ECE-A', 'Wednesday', [1], ['IST-518'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. M. Jothi'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Wednesday', [2], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Wednesday', [3], ['IST-518'], 'D', '21ECE468T', 'System and Network on Chip', 'Dr. V. Manikandan'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Wednesday', [4], ['IST-518'], 'F', '21GNP301L', 'Community Connect', 'Dr. V. Rajesh / Dr. V. Bharathi'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Wednesday', [8, 9], ['IST-108', 'IST-309'], 'LAB', '21ECC311L', 'VLSI Design / Microprocessor Laboratory', 'Dr. M. Jothi / Dr. P. Murugapandiyan'),
  // Thursday
  ...makeSession('III-ECE-A', 'III ECE-A', 'Thursday', [1], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Thursday', [2], ['IST-518'], 'E', '21CSO355T', 'Machine Learning for All', 'Dr. J. Jencia'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Thursday', [3], ['IST-518'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. M. Jothi'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Thursday', [4], ['IST-518'], 'F', '21GNP301L', 'Community Connect', 'Dr. V. Rajesh / Dr. V. Bharathi'),
  // Friday
  ...makeSession('III-ECE-A', 'III ECE-A', 'Friday', [1], ['IST-518'], 'D', '21ECE468T', 'System and Network on Chip', 'Dr. V. Manikandan'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Friday', [2], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Friday', [3], ['IST-518'], 'E', '21CSO355T', 'Machine Learning for All', 'Dr. J. Jencia'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Friday', [4], ['IST-518'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. M. Jothi'),
  ...makeSession('III-ECE-A', 'III ECE-A', 'Friday', [6, 7], ['IST-108', 'IST-309'], 'LAB', '21ECC311L', 'VLSI Design / Microprocessor Laboratory', 'Dr. M. Jothi / Dr. V. Manikandan'),

  // ==========================================
  // 10. III ECE-B (PDF 7 — Venue: IST 518 / AN)
  // ==========================================
  // Monday
  ...makeSession('III-ECE-B', 'III ECE-B', 'Monday', [1, 2], ['IST-108', 'IST-309'], 'LAB', '21ECC311L', 'VLSI Design / Microprocessor Laboratory', 'Dr. Sreenivasa Ijada Rao / Dr. B. DeviSri'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Monday', [6], ['IST-518'], 'E', '21CSO355T', 'Machine Learning for All', 'Dr. J. Jencia'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Monday', [7], ['IST-518'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Monday', [8], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'Dr. M. Thanga Rejini'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Monday', [9], ['IST-518'], 'D', '21ECE468T', 'System and Network on Chip', 'Dr. V. Manikandan'),
  // Tuesday
  ...makeSession('III-ECE-B', 'III ECE-B', 'Tuesday', [1, 2], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Tuesday', [6], ['IST-518'], 'F', '21GNP301L', 'Community Connect', 'Dr. H. Sudharsan / Ms. T. Swetha'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Tuesday', [7], ['IST-518'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Tuesday', [8], ['IST-518'], 'D', '21ECE468T', 'System and Network on Chip', 'Dr. V. Manikandan'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Tuesday', [9], ['IST-518'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. R. Vinoth Raj'),
  // Wednesday
  ...makeSession('III-ECE-B', 'III ECE-B', 'Wednesday', [1], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Wednesday', [6], ['IST-518'], 'B-Proj', '21ECC301P', 'Microprocessor Project', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Wednesday', [7], ['IST-518'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Wednesday', [8], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'Dr. M. Thanga Rejini'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Wednesday', [9], ['IST-518'], 'H', '21LEM301T', 'Indian Art Form', 'Dr. A. Anand'),
  // Thursday
  ...makeSession('III-ECE-B', 'III ECE-B', 'Thursday', [1, 2], ['IST-108', 'IST-309'], 'LAB', '21ECC311L', 'VLSI Design / Microprocessor Laboratory', 'Dr. Sreenivasa Ijada Rao / Dr. B. DeviSri'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Thursday', [6], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'Dr. M. Thanga Rejini'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Thursday', [7], ['IST-518'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. R. Vinoth Raj'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Thursday', [8], ['IST-518'], 'E', '21CSO355T', 'Machine Learning for All', 'Dr. J. Jencia'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Thursday', [9], ['IST-518'], 'F', '21GNP301L', 'Community Connect', 'Dr. H. Sudharsan / Ms. T. Swetha'),
  // Friday
  ...makeSession('III-ECE-B', 'III ECE-B', 'Friday', [6], ['IST-518'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. R. Vinoth Raj'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Friday', [7], ['IST-518'], 'A', '21MAB302T', 'Discrete Mathematics', 'Dr. M. Thanga Rejini'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Friday', [8], ['IST-518'], 'E', '21CSO355T', 'Machine Learning for All', 'Dr. J. Jencia'),
  ...makeSession('III-ECE-B', 'III ECE-B', 'Friday', [9], ['IST-518'], 'D', '21ECE468T', 'System and Network on Chip', 'Dr. V. Manikandan'),

  // ==========================================
  // 11. III ECE-DS (PDF 8 — Venue: IST 519 / FN)
  // ==========================================
  // Monday
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Monday', [1], ['IST-519'], 'E', '21ECE371T', 'Database Design and Management', 'Dr. S. Saraswathi'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Monday', [2], ['IST-519'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Monday', [3], ['IST-519'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. R. Vinoth Raj'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Monday', [4], ['IST-519'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  // Tuesday
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Tuesday', [1], ['IST-519'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. R. Vinoth Raj'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Tuesday', [2], ['IST-519'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Tuesday', [3], ['IST-519'], 'D', '21CSO355T', 'Machine Learning for All', 'Dr. Chitra Devi'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Tuesday', [4], ['IST-519'], 'F', '21GNP301L', 'Community Connect', 'Dr. S. Jeevanantham / Dr. V. Manikandan'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Tuesday', [6, 7], ['IST-108', 'IST-107'], 'LAB', '21ECC311L', 'VLSI Design / Microprocessor Laboratory', 'Dr. R. Vinothraj / Dr. H. Sri Bhuvaneshwari'),
  // Wednesday
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Wednesday', [1], ['IST-519'], 'H', '21LEM301T', 'Indian Art Form', 'Dr. Prabin Kumar Bera'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Wednesday', [2], ['IST-519'], 'B', '21ECC301P', 'Microprocessor, Microcontroller, and Interfacing', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Wednesday', [3], ['IST-519'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Wednesday', [4], ['IST-519'], 'C', '21ECC303T', 'VLSI Design and Technology', 'Dr. R. Vinoth Raj'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Wednesday', [8, 9], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  // Thursday
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Thursday', [1], ['IST-519'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Thursday', [2], ['IST-519'], 'D', '21CSO355T', 'Machine Learning for All', 'Dr. Chitra Devi'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Thursday', [3], ['IST-519'], 'E', '21ECE371T', 'Database Design and Management', 'Dr. S. Saraswathi'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Thursday', [4], ['IST-519'], 'F', '21GNP301L', 'Community Connect', 'Dr. S. Jeevanantham / Dr. V. Manikandan'),
  // Friday
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Friday', [1], ['IST-519'], 'D', '21CSO355T', 'Machine Learning for All', 'Dr. Chitra Devi'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Friday', [2], ['IST-519'], 'A', '21MAB302T', 'Discrete Mathematics', 'AP/Maths Faculty'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Friday', [3], ['IST-519'], 'E', '21ECE371T', 'Database Design and Management', 'Dr. S. Saraswathi'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Friday', [4], ['IST-519'], 'B-Proj', '21ECC301P', 'Microprocessor Project', 'Mrs. B. Abirami'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Friday', [6], ['IST-625'], 'G', '21PDM301L', 'Analytical and Logical Thinking Skills', 'CDC Faculty'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Friday', [8, 9], ['IST-108', 'IST-107'], 'LAB', '21ECC311L', 'VLSI Design / Microprocessor Laboratory', 'Dr. R. Vinothraj / Dr. H. Sri Bhuvaneshwari'),

  // ==========================================
  // 12. IV ECE-A (PDF 9 — Venue: IST 225)
  // ==========================================
  // Monday
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Monday', [1], ['IST-225'], 'C', '21ECC402P', 'Computer Communication and Network Security', 'Dr. S. Jeevanantham'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Monday', [3], ['IST-225'], 'A', '21GNH401T', 'Behavioural Psychology', 'Dr. A. Anand'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Monday', [4], ['IST-225'], 'D', '21ECE461T', 'Semiconductor Memory Design', 'Dr. H. SriBhuvaneshwari'),
  // Tuesday
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Tuesday', [1], ['IST-225'], 'C', '21ECC402P', 'Computer Communication and Network Security', 'Dr. S. Jeevanantham'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Tuesday', [2], ['IST-225'], 'D', '21ECE461T', 'Semiconductor Memory Design', 'Dr. H. SriBhuvaneshwari'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Tuesday', [3], ['IST-225'], 'B', '21ECC401T', 'Wireless Communication and Antenna Systems', 'Dr. K. Vigneshwaran'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Tuesday', [4], ['IST-225'], 'F', '21CSO355T', 'Machine Learning for All', 'Dr. N. Prasanna Venkatesh'),
  // Wednesday
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Wednesday', [1], ['IST-225'], 'B', '21ECC401T', 'Wireless Communication and Antenna Systems', 'Dr. K. Vigneshwaran'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Wednesday', [2], ['IST-108'], 'LAB', '21ECC402P', 'Network Security Laboratory', 'Mrs. T. Swetha'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Wednesday', [3], ['IST-225'], 'E', '21ECE463T', 'Scripting Language for Electronic Design Automation', 'Dr. Sreenivasa Rao Ijada'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Wednesday', [4], ['IST-225'], 'F', '21CSO355T', 'Machine Learning for All', 'Dr. N. Prasanna Venkatesh'),
  // Thursday
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Thursday', [1], ['IST-225'], 'F', '21CSO355T', 'Machine Learning for All', 'Dr. N. Prasanna Venkatesh'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Thursday', [2], ['IST-225'], 'A', '21GNH401T', 'Behavioural Psychology', 'Dr. A. Anand'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Thursday', [3], ['IST-225'], 'E', '21ECE463T', 'Scripting Language for Electronic Design Automation', 'Dr. Sreenivasa Rao Ijada'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Thursday', [4], ['IST-225'], 'B', '21ECC401T', 'Wireless Communication and Antenna Systems', 'Dr. K. Vigneshwaran'),
  // Friday
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Friday', [1], ['IST-225'], 'C', '21ECC402P', 'Computer Communication and Network Security', 'Dr. S. Jeevanantham'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Friday', [2], ['IST-225'], 'A', '21GNH401T', 'Behavioural Psychology', 'Dr. A. Anand'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Friday', [3], ['IST-225'], 'D', '21ECE461T', 'Semiconductor Memory Design', 'Dr. H. SriBhuvaneshwari'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Friday', [4], ['IST-225'], 'E', '21ECE463T', 'Scripting Language for Electronic Design Automation', 'Dr. Sreenivasa Rao Ijada'),

  // ==========================================
  // 13. IV ECE-B (PDF 10 — Venue: IST 227)
  // ==========================================
  // Monday
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Monday', [1], ['IST-227'], 'C', '21ECC402P', 'Computer Communication and Network Security', 'Dr. R. Rajasekar'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Monday', [2], ['IST-227'], 'A', '21GNH401T', 'Behavioural Psychology', 'Dr. A. Annand'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Monday', [3], ['IST-227'], 'E', '21ECE463T', 'Scripting Language for Electronic Design Automation', 'Dr. Sreenivasa Rao Ijada'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Monday', [4], ['IST-227'], 'F', '21CSO355T', 'Machine Learning for All', 'Dr. N. Prasanna Venkatesh'),
  // Tuesday
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Tuesday', [1], ['IST-227'], 'C', '21ECC402P', 'Computer Communication and Network Security', 'Dr. R. Rajasekar'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Tuesday', [2], ['IST-227'], 'E', '21ECE463T', 'Scripting Language for Electronic Design Automation', 'Dr. Sreenivasa Rao Ijada'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Tuesday', [3], ['IST-227'], 'F', '21CSO355T', 'Machine Learning for All', 'Dr. N. Prasanna Venkatesh'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Tuesday', [4], ['IST-227'], 'B', '21ECC401T', 'Wireless Communication and Antenna Systems', 'Dr. K. Vigneshwaran'),
  // Wednesday
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Wednesday', [1], ['IST-227'], 'C', '21ECC402P', 'Computer Communication and Network Security', 'Dr. R. Rajasekar'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Wednesday', [2], ['IST-227'], 'D', '21ECE461T', 'Semiconductor Memory Design', 'Dr. H. SriBhuvaneshwari'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Wednesday', [3], ['IST-227'], 'A', '21GNH401T', 'Behavioural Psychology', 'Dr. A. Annand'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Wednesday', [4], ['IST-227'], 'B', '21ECC401T', 'Wireless Communication and Antenna Systems', 'Dr. K. Vigneshwaran'),
  // Thursday
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Thursday', [1], ['IST-227'], 'D', '21ECE461T', 'Semiconductor Memory Design', 'Dr. H. SriBhuvaneshwari'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Thursday', [2], ['IST-227'], 'B', '21ECC401T', 'Wireless Communication and Antenna Systems', 'Dr. K. Vigneshwaran'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Thursday', [3], ['IST-108'], 'LAB', '21ECC402P', 'Network Security Laboratory', 'Ms. T. Swetha'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Thursday', [4], ['IST-227'], 'A', '21GNH401T', 'Behavioural Psychology', 'Dr. A. Annand'),
  // Friday
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Friday', [1], ['IST-227'], 'E', '21ECE463T', 'Scripting Language for Electronic Design Automation', 'Dr. Sreenivasa Rao Ijada'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Friday', [2], ['IST-227'], 'D', '21ECE461T', 'Semiconductor Memory Design', 'Dr. H. SriBhuvaneshwari'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Friday', [3], ['IST-227'], 'F', '21CSO355T', 'Machine Learning for All', 'Dr. N. Prasanna Venkatesh'),
  // Additional scheduled sessions in IST 509 (Afternoon Tutorials / Electives starting at 02:20 PM / P7)
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Monday', [7, 8], ['IST-509'], 'E', '21ECE463T', 'EDA Scripting Tutorial & Project Review', 'Dr. Sreenivasa Rao Ijada'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Tuesday', [7, 8], ['IST-509'], 'D', '21ECE461T', 'Semiconductor Memory Design Tutorial', 'Dr. H. SriBhuvaneshwari'),
  ...makeSession('III-ECE-DS', 'III ECE-DS', 'Wednesday', [7], ['IST-509'], 'E', '21ECE371T', 'Database Systems Tutorial', 'Dr. S. Saraswathi'),
  ...makeSession('IV-ECE-A', 'IV ECE-A', 'Thursday', [7, 8], ['IST-509'], 'B', '21ECC401T', 'Wireless & Antenna Design Tutorial', 'Dr. K. Vigneshwaran'),
  ...makeSession('IV-ECE-B', 'IV ECE-B', 'Friday', [7], ['IST-509'], 'C', '21ECC402P', 'Network Security Capstone', 'Dr. R. Rajasekar'),
];

export const ALL_CLASS_SESSIONS: ClassSession[] = [
  ...SESSIONS_PART_1,
  ...SESSIONS_PART_2,
];
import {
  ClassSession,
  DayOfWeek,
  FloorId,
  FLOORS,
  PERIOD_SLOTS,
  RoomInfo,
  ROOMS,
} from '../data/roomsData';
import { ALL_CLASS_SESSIONS } from '../data/timetablesPart2';

export interface PeriodCellState {
  period: number;
  label: string;
  start: string;
  end: string;
  isOccupied: boolean;
  isCurrentPeriod: boolean;
  sessions: ClassSession[];
}

export interface RoomAvailabilityStatus {
  room: RoomInfo;
  day: DayOfWeek;
  queryTime: string; // HH:mm
  isCurrentlyEmpty: boolean;
  statusState: 'free-long' | 'free-short' | 'occupied';
  freeDurationMinutes: number;
  freeDurationFormatted: string;
  freeUntilTime: string; // HH:mm
  freeUntilFormatted: string;
  isFreeRestOfDay: boolean;
  currentSessions: ClassSession[];
  nextSession: ClassSession | null;
  minutesUntilNextClass: number | null;
  clearsAtTime: string | null;
  clearsInMinutes: number | null;
  periodTimeline: PeriodCellState[];
  dailyUtilizationPercent: number;
}

export function timeToMinutes(time24: string): number {
  const [h, m] = time24.split(':').map(Number);
  return h * 60 + (m || 0);
}

export function minutesToTime24(totalMinutes: number): string {
  const clamped = Math.max(0, Math.min(23 * 60 + 59, Math.round(totalMinutes)));
  const h = Math.floor(clamped / 60);
  const m = clamped % 60;
  return `${String(h).padStart(2, '0')}:${String(m).padStart(2, '0')}`;
}

export function formatTime12h(time24: string): string {
  const [hStr, mStr] = time24.split(':');
  const h = parseInt(hStr, 10);
  const m = mStr || '00';
  const suffix = h >= 12 ? 'PM' : 'AM';
  const h12 = h % 12 === 0 ? 12 : h % 12;
  return `${String(h12).padStart(2, '0')}:${m} ${suffix}`;
}

export function formatDurationMinutes(mins: number): string {
  if (mins <= 0) return '0m';
  const h = Math.floor(mins / 60);
  const m = mins % 60;
  if (h > 0 && m > 0) return `${h}h ${m}m`;
  if (h > 0) return `${h}h 00m`;
  return `${m}m`;
}

export const DAY_START_MINUTES = timeToMinutes('09:00'); // 540
export const DAY_END_MINUTES = timeToMinutes('17:05');   // 1025

export function getActivePeriodAtTime(time24: string): number | null {
  const t = timeToMinutes(time24);
  for (const p of PERIOD_SLOTS) {
    const s = timeToMinutes(p.start);
    const e = timeToMinutes(p.end);
    if (t >= s && t < e) {
      return p.period;
    }
  }
  return null;
}

export function computeRoomStatus(
  room: RoomInfo,
  day: DayOfWeek,
  time24: string
): RoomAvailabilityStatus {
  const queryMins = Math.max(DAY_START_MINUTES, Math.min(DAY_END_MINUTES - 5, timeToMinutes(time24)));
  const normalizedQueryTime = minutesToTime24(queryMins);

  const roomDaySessions = ALL_CLASS_SESSIONS.filter(
    (s) => s.roomId === room.id && s.day === day
  ).sort((a, b) => timeToMinutes(a.startTime) - timeToMinutes(b.startTime));

  // Build 9-period timeline
  const periodTimeline: PeriodCellState[] = PERIOD_SLOTS.map((p) => {
    const pStart = timeToMinutes(p.start);
    const pEnd = timeToMinutes(p.end);
    const matching = roomDaySessions.filter((s) => s.period === p.period);
    return {
      period: p.period,
      label: p.label,
      start: p.start,
      end: p.end,
      isOccupied: matching.length > 0,
      isCurrentPeriod: queryMins >= pStart && queryMins < pEnd,
      sessions: matching,
    };
  });

  const occupiedPeriodsCount = periodTimeline.filter((p) => p.isOccupied).length;
  const dailyUtilizationPercent = Math.round((occupiedPeriodsCount / 9) * 100);

  // Check if occupied at queryMins
  // Note: If there's a 5-minute passing gap between back-to-back occupied periods (e.g. 09:50 to 09:55),
  // we treat a room that has a class starting within <= 5 mins as continuously occupied or about to start.
  const currentSessions = roomDaySessions.filter((s) => {
    const sStart = timeToMinutes(s.startTime);
    const sEnd = timeToMinutes(s.endTime);
    return queryMins >= sStart && queryMins < sEnd;
  });

  const isCurrentlyEmpty = currentSessions.length === 0;

  // Find next session after queryMins
  const futureSessions = roomDaySessions.filter(
    (s) => timeToMinutes(s.startTime) > queryMins
  );
  const nextSession = futureSessions.length > 0 ? futureSessions[0] : null;

  if (isCurrentlyEmpty) {
    const freeUntilMins = nextSession
      ? timeToMinutes(nextSession.startTime)
      : DAY_END_MINUTES;
    const freeDurationMinutes = Math.max(0, freeUntilMins - queryMins);
    const freeUntilTime = minutesToTime24(freeUntilMins);
    const isFreeRestOfDay = !nextSession;

    // If free for less than 35 minutes before a professor walks in, warn as 'free-short'
    const statusState: 'free-long' | 'free-short' =
      !isFreeRestOfDay && freeDurationMinutes < 35 ? 'free-short' : 'free-long';

    return {
      room,
      day,
      queryTime: normalizedQueryTime,
      isCurrentlyEmpty: true,
      statusState,
      freeDurationMinutes,
      freeDurationFormatted: formatDurationMinutes(freeDurationMinutes),
      freeUntilTime,
      freeUntilFormatted: isFreeRestOfDay
        ? '05:05 PM (Rest of Day)'
        : formatTime12h(freeUntilTime),
      isFreeRestOfDay,
      currentSessions: [],
      nextSession,
      minutesUntilNextClass: nextSession ? freeDurationMinutes : null,
      clearsAtTime: null,
      clearsInMinutes: null,
      periodTimeline,
      dailyUtilizationPercent,
    };
  } else {
    // Room is currently occupied. Calculate when it actually clears (including consecutive back-to-back classes)
    let clearMins = Math.max(...currentSessions.map((s) => timeToMinutes(s.endTime)));

    // Check if another session starts within <= 10 minutes of clearMins (e.g. across 10m tea break or 0m period change)
    let keepChecking = true;
    while (keepChecking) {
      const consecutive = roomDaySessions.filter((s) => {
        const st = timeToMinutes(s.startTime);
        return st >= clearMins && st <= clearMins + 10;
      });
      if (consecutive.length > 0) {
        const nextEnd = Math.max(...consecutive.map((s) => timeToMinutes(s.endTime)));
        if (nextEnd > clearMins) {
          clearMins = nextEnd;
        } else {
          keepChecking = false;
        }
      } else {
        keepChecking = false;
      }
    }

    const clearsAtTime = minutesToTime24(clearMins);
    const clearsInMinutes = Math.max(0, clearMins - queryMins);

    // Find next session after it clears
    const afterClearSessions = roomDaySessions.filter(
      (s) => timeToMinutes(s.startTime) > clearMins
    );

    return {
      room,
      day,
      queryTime: normalizedQueryTime,
      isCurrentlyEmpty: false,
      statusState: 'occupied',
      freeDurationMinutes: 0,
      freeDurationFormatted: '0m',
      freeUntilTime: normalizedQueryTime,
      freeUntilFormatted: 'Occupied Now',
      isFreeRestOfDay: false,
      currentSessions,
      nextSession: afterClearSessions.length > 0 ? afterClearSessions[0] : null,
      minutesUntilNextClass: 0,
      clearsAtTime,
      clearsInMinutes,
      periodTimeline,
      dailyUtilizationPercent,
    };
  }
}

export function computeAllRoomsStatus(
  day: DayOfWeek,
  time24: string
): RoomAvailabilityStatus[] {
  return ROOMS.map((room) => computeRoomStatus(room, day, time24));
}

export interface FilterCriteria {
  floorId: FloorId | 'all';
  onlyEmpty: boolean;
  onlyAC: boolean;
  minDurationMinutes: number;
  roomType: string; // 'all' or specific
  teamFriendlyOnly: boolean;
  searchQuery: string;
}

export function filterRoomStatuses(
  statuses: RoomAvailabilityStatus[],
  criteria: FilterCriteria
): RoomAvailabilityStatus[] {
  return statuses.filter((item) => {
    if (criteria.floorId !== 'all' && item.room.floorId !== criteria.floorId) {
      return false;
    }
    if (criteria.onlyEmpty && !item.isCurrentlyEmpty) {
      return false;
    }
    if (criteria.onlyAC && !item.room.isAC) {
      return false;
    }
    if (criteria.minDurationMinutes > 0 && item.freeDurationMinutes < criteria.minDurationMinutes) {
      return false;
    }
    if (criteria.roomType !== 'all' && item.room.roomType !== criteria.roomType) {
      return false;
    }
    if (criteria.teamFriendlyOnly && !item.room.teamFriendly) {
      return false;
    }
    if (criteria.searchQuery.trim() !== '') {
      const q = criteria.searchQuery.toLowerCase().trim();
      const hay = [
        item.room.code,
        item.room.name,
        item.room.roomType,
        item.room.wing,
        ...item.room.amenities,
        ...item.room.primarySections,
      ]
        .join(' ')
        .toLowerCase();
      if (!hay.includes(q)) return false;
    }
    return true;
  });
}

export function getFloorSummary(
  statuses: RoomAvailabilityStatus[],
  floorId: FloorId
) {
  const floorRooms = statuses.filter((s) => s.room.floorId === floorId);
  const emptyRooms = floorRooms.filter((s) => s.isCurrentlyEmpty);
  const safeTwoHourRooms = emptyRooms.filter((s) => s.freeDurationMinutes >= 120);
  const emptyACRooms = emptyRooms.filter((s) => s.room.isAC);

  return {
    floor: FLOORS.find((f) => f.id === floorId)!,
    totalCount: floorRooms.length,
    emptyCount: emptyRooms.length,
    safeTwoHourCount: safeTwoHourRooms.length,
    emptyACCount: emptyACRooms.length,
  };
}
import React, { useMemo, useState } from 'react';
import {
  Clock,
  SlidersHorizontal,
  Search,
  RotateCcw,
  Sparkles,
  Snowflake,
  Users,
  CheckCircle2,
  Laptop,
  Box,
  MapPin,
  MessageCircle,
  Star,
} from 'lucide-react';
import {
  DayOfWeek,
  DAYS_OF_WEEK,
  FloorId,
  FLOORS,
  PERIOD_SLOTS,
} from './data/roomsData';
import {
  computeAllRoomsStatus,
  DAY_END_MINUTES,
  DAY_START_MINUTES,
  FilterCriteria,
  filterRoomStatuses,
  formatTime12h,
  getActivePeriodAtTime,
  getFloorSummary,
  minutesToTime24,
  RoomAvailabilityStatus,
  timeToMinutes,
} from './utils/occupancyEngine';
import { AIRoomFinder, ParsedAIIntent } from './components/AIRoomFinder';
import { RoomCard } from './components/RoomCard';
import { RoomDetailModal } from './components/RoomDetailModal';
import { SectionTimetablesView } from './components/SectionTimetablesView';
import { OccupancyMatrixView } from './components/OccupancyMatrixView';
import { Building3DMap } from './components/Building3DMap';
import { SectionGapFinder } from './components/SectionGapFinder';
import { CampusSmartTools } from './components/CampusSmartTools';

type ActiveTab = 'floor-grid' | 'matrix' | 'timetables';

const FLOOR_ACCENTS: Record<
  FloorId,
  { badge: string; border: string; headerBg: string; dot: string }
> = {
  ground: {
    badge: 'bg-indigo-600 text-white',
    border: 'border-indigo-200',
    headerBg: 'from-indigo-50/90 via-white to-white',
    dot: 'bg-indigo-600',
  },
  first: {
    badge: 'bg-teal-600 text-white',
    border: 'border-teal-200',
    headerBg: 'from-teal-50/90 via-white to-white',
    dot: 'bg-teal-600',
  },
  second: {
    badge: 'bg-violet-600 text-white',
    border: 'border-violet-200',
    headerBg: 'from-violet-50/90 via-white to-white',
    dot: 'bg-violet-600',
  },
  third: {
    badge: 'bg-sky-600 text-white',
    border: 'border-sky-200',
    headerBg: 'from-sky-50/90 via-white to-white',
    dot: 'bg-sky-600',
  },
};

export default function App() {
  const [activeTab, setActiveTab] = useState<ActiveTab>('floor-grid');

  // Default to Monday 11:45 AM (Middle of the day, Period 4)
  const [selectedDay, setSelectedDay] = useState<DayOfWeek>('Monday');
  const [selectedTime, setSelectedTime] = useState<string>('11:45');

  // Selected Room on the 3D Map (default to IST-509 so user immediately sees it!)
  const [selected3DRoomId, setSelected3DRoomId] = useState<string>('IST-509');

  // Claimed Room for "Call the Squad"
  const [claimedRoomId, setClaimedRoomId] = useState<string | null>('IST-509');

  // Pinned / Starred Favorite Rooms
  const [favoriteRoomIds, setFavoriteRoomIds] = useState<string[]>([
    'IST-509',
    'TB-106',
    'IST-602',
  ]);
  const [onlyFavorites, setOnlyFavorites] = useState<boolean>(false);

  const handleToggleFavorite = (roomId: string) => {
    setFavoriteRoomIds((prev) =>
      prev.includes(roomId)
        ? prev.filter((id) => id !== roomId)
        : [...prev, roomId]
    );
  };

  // Traditional Filter State
  const [filters, setFilters] = useState<FilterCriteria>({
    floorId: 'all',
    onlyEmpty: true,
    onlyAC: false,
    minDurationMinutes: 0,
    roomType: 'all',
    teamFriendlyOnly: false,
    searchQuery: '',
  });

  // Active Quick Preset ID for user-friendly 1-click filtering
  const [activePreset, setActivePreset] = useState<string>('all-empty');

  // AI Highlighted Room IDs
  const [aiRecommendedIds, setAiRecommendedIds] = useState<string[]>([]);

  // Modal State for Inspecting a Specific Room
  const [inspectedRoom, setInspectedRoom] =
    useState<RoomAvailabilityStatus | null>(null);

  // Compute all 26 rooms' live status for selectedDay + selectedTime
  const allRoomStatuses = useMemo(
    () => computeAllRoomsStatus(selectedDay, selectedTime),
    [selectedDay, selectedTime]
  );

  // Filtered rooms for the Floor Grid
  const filteredStatuses = useMemo(() => {
    const base = filterRoomStatuses(allRoomStatuses, filters);
    if (!onlyFavorites) return base;
    return base.filter((s) => favoriteRoomIds.includes(s.room.id));
  }, [allRoomStatuses, filters, onlyFavorites, favoriteRoomIds]);

  // High-level summary counts
  const metrics = useMemo(() => {
    const emptyNow = allRoomStatuses.filter((s) => s.isCurrentlyEmpty);
    const safe2Hours = emptyNow.filter((s) => s.freeDurationMinutes >= 120);
    const emptyAC = emptyNow.filter((s) => s.room.isAC);
    const kickOutRisk = emptyNow.filter(
      (s) => !s.isFreeRestOfDay && s.freeDurationMinutes < 45
    );
    return {
      totalRooms: allRoomStatuses.length,
      emptyCount: emptyNow.length,
      safe2HoursCount: safe2Hours.length,
      emptyACCount: emptyAC.length,
      kickOutRiskCount: kickOutRisk.length,
    };
  }, [allRoomStatuses]);

  const activePeriodNumber = getActivePeriodAtTime(selectedTime);

  const claimedRoomStatus = useMemo(
    () => allRoomStatuses.find((s) => s.room.id === claimedRoomId) || null,
    [allRoomStatuses, claimedRoomId]
  );

  const handleJumpToLiveClock = () => {
    const now = new Date();
    const dayIdx = now.getDay();
    const mappedDay: DayOfWeek =
      dayIdx >= 1 && dayIdx <= 5 ? DAYS_OF_WEEK[dayIdx - 1] : 'Monday';
    const currentMins = now.getHours() * 60 + now.getMinutes();

    setSelectedDay(mappedDay);
    if (currentMins >= DAY_START_MINUTES && currentMins <= DAY_END_MINUTES) {
      setSelectedTime(minutesToTime24(currentMins));
    } else {
      setSelectedTime('12:35');
    }
  };

  const handleApplyAIFilters = (
    intent: ParsedAIIntent,
    resolvedDay: DayOfWeek,
    resolvedTime: string,
    recommendedIds: string[]
  ) => {
    setSelectedDay(resolvedDay);
    setSelectedTime(resolvedTime);
    setAiRecommendedIds(recommendedIds);
    setActiveTab('floor-grid');
    setActivePreset('ai-custom');

    if (recommendedIds.length > 0) {
      setSelected3DRoomId(recommendedIds[0]);
    }

    setFilters((prev) => ({
      ...prev,
      floorId: intent.floorPreference || 'all',
      onlyEmpty: true,
      onlyAC: Boolean(intent.requiresAC),
      minDurationMinutes:
        intent.minDurationMinutes && intent.minDurationMinutes > 0
          ? intent.minDurationMinutes
          : 0,
      teamFriendlyOnly: Boolean(intent.teamOrGroup),
    }));
  };

  const handleSelectQuickPreset = (presetId: string) => {
    setActivePreset(presetId);
    setAiRecommendedIds([]);
    setOnlyFavorites(presetId === 'favorites');
    switch (presetId) {
      case 'favorites':
        setFilters({
          floorId: 'all',
          onlyEmpty: false,
          onlyAC: false,
          minDurationMinutes: 0,
          roomType: 'all',
          teamFriendlyOnly: false,
          searchQuery: '',
        });
        break;
      case 'all-empty':
        setFilters({
          floorId: 'all',
          onlyEmpty: true,
          onlyAC: false,
          minDurationMinutes: 0,
          roomType: 'all',
          teamFriendlyOnly: false,
          searchQuery: '',
        });
        break;
      case 'ac-cool':
        setFilters({
          floorId: 'all',
          onlyEmpty: true,
          onlyAC: true,
          minDurationMinutes: 60,
          roomType: 'all',
          teamFriendlyOnly: false,
          searchQuery: '',
        });
        break;
      case 'team-2h':
        setFilters({
          floorId: 'all',
          onlyEmpty: true,
          onlyAC: false,
          minDurationMinutes: 120,
          roomType: 'all',
          teamFriendlyOnly: true,
          searchQuery: '',
        });
        break;
      case 'labs':
        setFilters({
          floorId: 'all',
          onlyEmpty: true,
          onlyAC: false,
          minDurationMinutes: 0,
          roomType: 'Computer Lab',
          teamFriendlyOnly: false,
          searchQuery: '',
        });
        break;
      case 'show-all':
        setFilters({
          floorId: 'all',
          onlyEmpty: false,
          onlyAC: false,
          minDurationMinutes: 0,
          roomType: 'all',
          teamFriendlyOnly: false,
          searchQuery: '',
        });
        break;
    }
  };

  const handleResetFilters = () => {
    handleSelectQuickPreset('show-all');
  };

  const floorsToRender =
    filters.floorId === 'all'
      ? FLOORS
      : FLOORS.filter((f) => f.id === filters.floorId);

  return (
    <div className="min-h-screen flex flex-col bg-[#F4F7FB] text-slate-900">
      {/* Top Bar Contract: Zone 1 (Wordmark) — Zone 2 (4 Nav Links) — Zone 3 (Actions) */}
      <header className="sticky top-0 z-30 bg-white/95 backdrop-blur-md border-b border-slate-200/90 px-6 py-3.5 shadow-2xs">
        <div className="max-w-[1380px] mx-auto flex items-center justify-between gap-4">
          <a
            href="#top"
            onClick={(e) => {
              e.preventDefault();
              setActiveTab('floor-grid');
            }}
            className="text-lg font-extrabold tracking-tight bg-gradient-to-r from-indigo-700 via-teal-600 to-emerald-600 bg-clip-text text-transparent whitespace-nowrap"
          >
            SRM RoomPulse
          </a>

          <nav className="hidden md:flex items-center gap-7 text-sm font-semibold text-slate-600">
            <a
              href="#map-3d"
              onClick={() => setActiveTab('floor-grid')}
              className="hover:text-indigo-600 transition-colors whitespace-nowrap"
            >
              3D Map & Squad
            </a>
            <a
              href="#smart-gap-tools"
              onClick={() => setActiveTab('floor-grid')}
              className="hover:text-indigo-600 transition-colors whitespace-nowrap"
            >
              Gap Sync & Relay
            </a>
            <button
              type="button"
              onClick={() => setActiveTab('matrix')}
              className={`hover:text-indigo-600 transition-colors whitespace-nowrap cursor-pointer ${
                activeTab === 'matrix'
                  ? 'text-indigo-600 underline underline-offset-8 decoration-2 decoration-indigo-600'
                  : ''
              }`}
            >
              Occupancy Matrix
            </button>
            <button
              type="button"
              onClick={() => setActiveTab('timetables')}
              className={`hover:text-indigo-600 transition-colors whitespace-nowrap cursor-pointer ${
                activeTab === 'timetables'
                  ? 'text-indigo-600 underline underline-offset-8 decoration-2 decoration-indigo-600'
                  : ''
              }`}
            >
              10 Timetables
            </button>
          </nav>

          <div className="flex items-center gap-2.5">
            {claimedRoomStatus && (
              <a
                href={`https://wa.me/?text=${encodeURIComponent(
                  `📍 Heading to ${claimedRoomStatus.room.code}. It's free until ${
                    claimedRoomStatus.isFreeRestOfDay
                      ? '5:05 PM'
                      : formatTime12h(claimedRoomStatus.freeUntilTime)
                  }. Come fast!`
                )}`}
                target="_blank"
                rel="noopener noreferrer"
                className="hidden sm:inline-flex items-center gap-1.5 px-3 py-1.5 text-xs font-bold text-slate-950 bg-[#25D366] hover:bg-[#20BD5A] rounded-lg transition-colors whitespace-nowrap shadow-2xs"
              >
                <MessageCircle className="w-3.5 h-3.5 fill-slate-950" />
                <span>Squad: {claimedRoomStatus.room.code}</span>
              </a>
            )}
            <button
              type="button"
              onClick={handleJumpToLiveClock}
              className="px-3.5 py-1.5 text-xs font-semibold text-white bg-gradient-to-r from-indigo-600 to-teal-600 hover:from-indigo-700 hover:to-teal-700 rounded-lg transition-all whitespace-nowrap cursor-pointer shadow-2xs"
            >
              Sync Live Clock
            </button>
          </div>
        </div>
      </header>

      {/* Main Content Container */}
      <main className="flex-1 max-w-[1380px] w-full mx-auto px-4 sm:px-6 py-6 space-y-7">
        {/* Vibrant Campus Hero & Interactive Time Control Panel */}
        <section className="rounded-2xl bg-gradient-to-br from-slate-900 via-indigo-950 to-teal-950 text-white p-6 shadow-lg border border-indigo-900/60">
          <div className="flex flex-col lg:flex-row lg:items-center justify-between gap-4 pb-5 border-b border-white/10">
            <div>
              <div className="inline-flex items-center gap-2 text-xs font-semibold text-teal-300 mb-1">
                <span>SRM IST Tiruchirappalli Campus</span>
                <span aria-hidden="true">·</span>
                <span>Faculty of Engineering & Technology</span>
              </div>
              <h1 className="text-2xl sm:text-3xl font-extrabold tracking-tight text-white">
                Find an Empty Classroom, Start the Timer & Call Your Squad
              </h1>
              <p className="text-sm text-slate-300 mt-1">
                Live availability across all 4 floors and 10 department timetables — never get kicked out 10 minutes after sitting down.
              </p>
            </div>

            {/* Day Selector Buttons */}
            <div className="flex items-center gap-1 p-1.5 bg-slate-950/60 border border-white/10 rounded-xl self-start lg:self-auto">
              {DAYS_OF_WEEK.map((day) => (
                <button
                  key={day}
                  type="button"
                  onClick={() => setSelectedDay(day)}
                  className={`px-3.5 py-2 text-xs font-bold rounded-lg transition-all whitespace-nowrap cursor-pointer ${
                    selectedDay === day
                      ? 'bg-gradient-to-r from-teal-400 to-emerald-400 text-slate-950 shadow-sm'
                      : 'text-slate-300 hover:text-white hover:bg-white/5'
                  }`}
                >
                  {day}
                </button>
              ))}
            </div>
          </div>

          {/* Time Scrubber & 9-Period Quick Buttons */}
          <div className="mt-5 grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
            {/* Left: Interactive Time Slider */}
            <div className="lg:col-span-5 bg-white/5 border border-white/10 rounded-xl p-4 space-y-2.5">
              <div className="flex items-center justify-between text-xs">
                <span className="text-teal-300 font-semibold inline-flex items-center gap-1.5">
                  <Clock className="w-4 h-4 text-teal-400" />
                  <span>Checking Time:</span>
                </span>
                <span className="font-mono text-base font-extrabold text-white tabular-nums">
                  {selectedDay} · {formatTime12h(selectedTime)}
                  {activePeriodNumber
                    ? activePeriodNumber === 5
                      ? ' (Lunch)'
                      : ` (Period ${activePeriodNumber})`
                    : ''}
                </span>
              </div>
              <input
                type="range"
                min={DAY_START_MINUTES}
                max={DAY_END_MINUTES - 10}
                step={5}
                value={timeToMinutes(selectedTime)}
                onChange={(e) =>
                  setSelectedTime(minutesToTime24(Number(e.target.value)))
                }
                className="w-full accent-teal-400 cursor-pointer h-2 bg-slate-800 rounded-lg"
                aria-label="Scrub time of day"
              />
              <div className="flex justify-between text-[11px] font-mono text-slate-400 tabular-nums">
                <span>09:00 AM</span>
                <span>11:00 AM</span>
                <span>01:00 PM</span>
                <span>03:00 PM</span>
                <span>05:00 PM</span>
              </div>
            </div>

            {/* Right: 1-Click Period Slot Buttons */}
            <div className="lg:col-span-7">
              <div className="flex items-center justify-between text-xs text-slate-300 mb-2">
                <span className="font-medium">
                  Tap any class period to jump straight to that hour:
                </span>
                <button
                  type="button"
                  onClick={() => {
                    setSelectedDay('Monday');
                    setSelectedTime('11:45');
                  }}
                  className="text-teal-300 hover:text-teal-200 font-semibold underline cursor-pointer"
                >
                  Reset to 11:45 AM Midday
                </button>
              </div>
              <div className="grid grid-cols-3 sm:grid-cols-9 gap-1.5">
                {PERIOD_SLOTS.map((slot) => {
                  const isActive = activePeriodNumber === slot.period;
                  return (
                    <button
                      key={slot.period}
                      type="button"
                      onClick={() => setSelectedTime(slot.start)}
                      className={`py-2 px-2 rounded-xl border text-center transition-all cursor-pointer ${
                        isActive
                          ? 'bg-gradient-to-b from-teal-400 to-emerald-500 border-teal-300 text-slate-950 font-bold shadow-md shadow-teal-500/20 scale-[1.03]'
                          : 'bg-white/5 border-white/10 text-slate-200 hover:bg-white/10'
                      }`}
                    >
                      <div className="font-mono text-xs font-bold tabular-nums">
                        {slot.label}
                      </div>
                      <div
                        className={`font-mono text-[10px] tabular-nums mt-0.5 ${
                          isActive ? 'text-slate-900 font-semibold' : 'text-slate-400'
                        }`}
                      >
                        {slot.start}
                      </div>
                    </button>
                  );
                })}
              </div>
            </div>
          </div>

          {/* 4 Colorful Live Telemetry Summary Strips */}
          <div className="mt-5 pt-5 border-t border-white/10 grid grid-cols-2 lg:grid-cols-4 gap-3.5">
            <div className="rounded-xl bg-emerald-500/15 border border-emerald-400/30 p-3.5">
              <div className="text-xs font-semibold text-emerald-300">
                Empty Rooms Right Now
              </div>
              <div className="mt-1 flex items-baseline gap-2">
                <span className="font-mono text-3xl font-extrabold text-emerald-400 tabular-nums">
                  {metrics.emptyCount}
                </span>
                <span className="text-xs text-emerald-200/80 font-mono tabular-nums">
                  of {metrics.totalRooms} rooms free
                </span>
              </div>
            </div>

            <div className="rounded-xl bg-indigo-500/15 border border-indigo-400/30 p-3.5">
              <div className="text-xs font-semibold text-indigo-300">
                Safe for 2+ Hours
              </div>
              <div className="mt-1 flex items-baseline gap-2">
                <span className="font-mono text-3xl font-extrabold text-white tabular-nums">
                  {metrics.safe2HoursCount}
                </span>
                <span className="text-xs text-indigo-200/80">
                  uninterrupted spots
                </span>
              </div>
            </div>

            <div className="rounded-xl bg-sky-500/15 border border-sky-400/30 p-3.5">
              <div className="text-xs font-semibold text-sky-300">
                Cool AC Rooms Free
              </div>
              <div className="mt-1 flex items-baseline gap-2">
                <span className="font-mono text-3xl font-extrabold text-sky-300 tabular-nums">
                  {metrics.emptyACCount}
                </span>
                <span className="text-xs text-sky-200/80">
                  air-conditioned
                </span>
              </div>
            </div>

            <div className="rounded-xl bg-amber-500/15 border border-amber-400/30 p-3.5">
              <div className="text-xs font-semibold text-amber-300">
                Closing Soon (&lt;45m)
              </div>
              <div className="mt-1 flex items-baseline gap-2">
                <span className="font-mono text-3xl font-extrabold text-amber-400 tabular-nums">
                  {metrics.kickOutRiskCount}
                </span>
                <span className="text-xs text-amber-200/80">
                  next lecture soon
                </span>
              </div>
            </div>
          </div>
        </section>

        {/* Mobile View Switcher */}
        <div className="flex md:hidden items-center gap-1 p-1 bg-slate-200 rounded-xl">
          <button
            type="button"
            onClick={() => setActiveTab('floor-grid')}
            className={`flex-1 py-2 text-xs font-bold rounded-lg ${
              activeTab === 'floor-grid'
                ? 'bg-indigo-600 text-white shadow-xs'
                : 'text-slate-700'
            }`}
          >
            3D Map, AI & Floors
          </button>
          <button
            type="button"
            onClick={() => setActiveTab('matrix')}
            className={`flex-1 py-2 text-xs font-bold rounded-lg ${
              activeTab === 'matrix'
                ? 'bg-indigo-600 text-white shadow-xs'
                : 'text-slate-700'
            }`}
          >
            Matrix
          </button>
          <button
            type="button"
            onClick={() => setActiveTab('timetables')}
            className={`flex-1 py-2 text-xs font-bold rounded-lg ${
              activeTab === 'timetables'
                ? 'bg-indigo-600 text-white shadow-xs'
                : 'text-slate-700'
            }`}
          >
            10 Timetables
          </button>
        </div>

        {activeTab === 'floor-grid' && (
          <>
            {/* 1. THE 3D MAP, LIVE COUNTDOWN TIMER & "CALL THE SQUAD" FEATURE */}
            <Building3DMap
              statuses={allRoomStatuses}
              selectedRoomId={selected3DRoomId}
              onSelectRoomId={(rid) => setSelected3DRoomId(rid)}
              claimedRoomId={claimedRoomId}
              onClaimRoom={(rid) => setClaimedRoomId(rid)}
              aiRecommendedIds={aiRecommendedIds}
              onOpenFullSchedule={(st) => setInspectedRoom(st)}
            />

            {/* 2. THE SMART AI ROOM FINDER */}
            <AIRoomFinder
              currentDay={selectedDay}
              currentTime={selectedTime}
              allStatuses={allRoomStatuses}
              onApplyAIFilters={handleApplyAIFilters}
              onSelectRoom={(st) => {
                setSelected3DRoomId(st.room.id);
                setInspectedRoom(st);
              }}
              onClearAIHighlight={() => handleSelectQuickPreset('all-empty')}
              activeRecommendedIds={aiRecommendedIds}
            />

            {/* 3. NEW FEATURES: SECTION GAP FINDER, TEAM SYNC, ROOM-HOP RELAY & FACULTY RADAR */}
            <div id="smart-gap-tools" className="space-y-6">
              <SectionGapFinder
                selectedDay={selectedDay}
                selectedTime={selectedTime}
                onSelectRoomOnMap={(roomId, time24) => {
                  if (time24) setSelectedTime(time24);
                  setSelected3DRoomId(roomId);
                  const el = document.getElementById('map-3d');
                  if (el) el.scrollIntoView({ behavior: 'smooth' });
                }}
                onClaimRoom={(roomId) => setClaimedRoomId(roomId)}
                onInspectRoom={(st) => setInspectedRoom(st)}
              />

              <CampusSmartTools
                selectedDay={selectedDay}
                selectedTime={selectedTime}
                allStatuses={allRoomStatuses}
                onSelectRoomOnMap={(roomId, time24) => {
                  if (time24) setSelectedTime(time24);
                  setSelected3DRoomId(roomId);
                  const el = document.getElementById('map-3d');
                  if (el) el.scrollIntoView({ behavior: 'smooth' });
                }}
                onClaimRoom={(roomId) => setClaimedRoomId(roomId)}
                onInspectRoom={(st) => setInspectedRoom(st)}
              />
            </div>

            {/* 4. USER-FRIENDLY 1-CLICK FILTER BAR & FLOOR SELECTOR */}
            <section className="bg-white border border-slate-200 rounded-2xl p-5 shadow-xs space-y-4">
              {/* Friendly "What do you need right now?" Quick Filter Buttons */}
              <div className="flex flex-col lg:flex-row lg:items-center justify-between gap-3 pb-4 border-b border-slate-100">
                <div className="flex flex-wrap items-center gap-2">
                  <span className="text-xs font-bold text-slate-700 mr-1">
                    Quick Filter:
                  </span>

                  <button
                    type="button"
                    onClick={() => handleSelectQuickPreset('all-empty')}
                    className={`px-3.5 py-2 rounded-xl text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                      activePreset === 'all-empty'
                        ? 'bg-emerald-600 text-white shadow-xs'
                        : 'bg-emerald-50 text-emerald-800 hover:bg-emerald-100 border border-emerald-200'
                    }`}
                  >
                    <CheckCircle2 className="w-3.5 h-3.5" />
                    <span>All Empty Rooms ({metrics.emptyCount})</span>
                  </button>

                  <button
                    type="button"
                    onClick={() => handleSelectQuickPreset('ac-cool')}
                    className={`px-3.5 py-2 rounded-xl text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                      activePreset === 'ac-cool'
                        ? 'bg-sky-600 text-white shadow-xs'
                        : 'bg-sky-50 text-sky-800 hover:bg-sky-100 border border-sky-200'
                    }`}
                  >
                    <Snowflake className="w-3.5 h-3.5" />
                    <span>Cool AC Rooms (1h+)</span>
                  </button>

                  <button
                    type="button"
                    onClick={() => handleSelectQuickPreset('team-2h')}
                    className={`px-3.5 py-2 rounded-xl text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                      activePreset === 'team-2h'
                        ? 'bg-indigo-600 text-white shadow-xs'
                        : 'bg-indigo-50 text-indigo-800 hover:bg-indigo-100 border border-indigo-200'
                    }`}
                  >
                    <Users className="w-3.5 h-3.5" />
                    <span>Project Team Spots (2h+ Free)</span>
                  </button>

                  <button
                    type="button"
                    onClick={() => handleSelectQuickPreset('labs')}
                    className={`px-3.5 py-2 rounded-xl text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                      activePreset === 'labs'
                        ? 'bg-violet-600 text-white shadow-xs'
                        : 'bg-violet-50 text-violet-800 hover:bg-violet-100 border border-violet-200'
                    }`}
                  >
                    <Laptop className="w-3.5 h-3.5" />
                    <span>Empty Computer Labs</span>
                  </button>

                  <button
                    type="button"
                    onClick={() => handleSelectQuickPreset('favorites')}
                    className={`px-3.5 py-2 rounded-xl text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                      activePreset === 'favorites'
                        ? 'bg-amber-500 text-slate-950 shadow-xs'
                        : 'bg-amber-50 text-amber-900 hover:bg-amber-100 border border-amber-200'
                    }`}
                  >
                    <Star className="w-3.5 h-3.5 fill-amber-400 text-amber-500" />
                    <span>Pinned Favorites ({favoriteRoomIds.length})</span>
                  </button>

                  <button
                    type="button"
                    onClick={() => handleSelectQuickPreset('show-all')}
                    className={`px-3.5 py-2 rounded-xl text-xs font-bold transition-all cursor-pointer flex items-center gap-1.5 ${
                      activePreset === 'show-all'
                        ? 'bg-slate-900 text-white shadow-xs'
                        : 'bg-slate-100 text-slate-700 hover:bg-slate-200'
                    }`}
                  >
                    <Box className="w-3.5 h-3.5" />
                    <span>Show All Rooms (Include Occupied)</span>
                  </button>
                </div>

                {/* Search Input */}
                <div className="relative w-full lg:w-64">
                  <Search className="w-4 h-4 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2 pointer-events-none" />
                  <input
                    type="text"
                    value={filters.searchQuery}
                    onChange={(e) =>
                      setFilters((f) => ({
                        ...f,
                        searchQuery: e.target.value,
                      }))
                    }
                    placeholder="Search room (e.g. IST 509, 602)..."
                    className="w-full pl-9 pr-3 py-2 bg-slate-50 border border-slate-200 rounded-xl text-xs text-slate-900 placeholder:text-slate-400 focus:outline-none focus:bg-white focus:border-indigo-500"
                  />
                </div>
              </div>

              {/* Floor Tabs & Fine-Grained Filter Controls */}
              <div className="flex flex-wrap items-center justify-between gap-3">
                <div className="flex flex-wrap items-center gap-1.5">
                  <span className="text-xs font-semibold text-slate-500 inline-flex items-center gap-1 mr-1">
                    <SlidersHorizontal className="w-3.5 h-3.5" />
                    <span>Floor:</span>
                  </span>
                  <button
                    type="button"
                    onClick={() => setFilters((f) => ({ ...f, floorId: 'all' }))}
                    className={`px-3 py-1.5 text-xs font-bold rounded-lg transition-colors cursor-pointer ${
                      filters.floorId === 'all'
                        ? 'bg-slate-900 text-white'
                        : 'bg-slate-100 text-slate-600 hover:bg-slate-200'
                    }`}
                  >
                    All Floors ({allRoomStatuses.length})
                  </button>
                  {FLOORS.map((fl) => {
                    const summary = getFloorSummary(allRoomStatuses, fl.id);
                    return (
                      <button
                        key={fl.id}
                        type="button"
                        onClick={() =>
                          setFilters((f) => ({ ...f, floorId: fl.id }))
                        }
                        className={`px-3 py-1.5 text-xs font-bold rounded-lg transition-colors cursor-pointer font-mono tabular-nums ${
                          filters.floorId === fl.id
                            ? 'bg-indigo-600 text-white'
                            : 'bg-slate-100 text-slate-700 hover:bg-slate-200'
                        }`}
                      >
                        <span className="font-sans">{fl.shortName}</span> (
                        {summary.emptyCount}/{summary.totalCount} free)
                      </button>
                    );
                  })}
                </div>

                {/* Duration & Climate Toggles */}
                <div className="flex flex-wrap items-center gap-2">
                  <div className="flex items-center gap-1 p-1 bg-slate-100 rounded-lg font-mono text-xs">
                    {[
                      { label: 'Any Time', mins: 0 },
                      { label: '1h+ Free', mins: 60 },
                      { label: '2h+ Free', mins: 120 },
                      { label: '3h+ Free', mins: 180 },
                    ].map((opt) => (
                      <button
                        key={opt.mins}
                        type="button"
                        onClick={() =>
                          setFilters((f) => ({
                            ...f,
                            minDurationMinutes: opt.mins,
                            onlyEmpty: opt.mins > 0 ? true : f.onlyEmpty,
                          }))
                        }
                        className={`px-2.5 py-1 rounded-md font-semibold transition-colors cursor-pointer ${
                          filters.minDurationMinutes === opt.mins
                            ? 'bg-white text-indigo-700 shadow-2xs'
                            : 'text-slate-600 hover:text-slate-900'
                        }`}
                      >
                        {opt.label}
                      </button>
                    ))}
                  </div>

                  <button
                    type="button"
                    onClick={() =>
                      setFilters((f) => ({ ...f, onlyAC: !f.onlyAC }))
                    }
                    className={`px-3 py-1.5 rounded-lg text-xs font-bold border transition-colors cursor-pointer flex items-center gap-1.5 ${
                      filters.onlyAC
                        ? 'bg-sky-600 border-sky-600 text-white'
                        : 'bg-white border-slate-200 text-slate-700 hover:bg-slate-50'
                    }`}
                  >
                    <Snowflake className="w-3.5 h-3.5" />
                    <span>AC Only</span>
                  </button>
                </div>
              </div>
            </section>

            {/* 4. THE FLOOR GRID (Color-Coded Floor-by-Floor Cards) */}
            <div className="space-y-8">
              {floorsToRender.map((floor) => {
                const floorItems = filteredStatuses.filter(
                  (s) => s.room.floorId === floor.id
                );
                const summary = getFloorSummary(allRoomStatuses, floor.id);
                const accent = FLOOR_ACCENTS[floor.id];

                return (
                  <section key={floor.id} className="space-y-4">
                    {/* Colorful Floor Section Banner */}
                    <div
                      className={`rounded-2xl border ${accent.border} bg-gradient-to-r ${accent.headerBg} p-4 sm:px-6 flex flex-col sm:flex-row sm:items-center justify-between gap-3 shadow-2xs`}
                    >
                      <div className="flex items-start sm:items-center gap-3">
                        <span
                          className={`px-3 py-1.5 rounded-xl font-mono text-xs font-extrabold uppercase tracking-wider shadow-2xs shrink-0 ${accent.badge}`}
                        >
                          {floor.shortName}
                        </span>
                        <div>
                          <div className="flex items-center gap-2 flex-wrap">
                            <h2 className="text-lg font-extrabold text-slate-900 tracking-tight">
                              {floor.name}
                            </h2>
                            <span className="text-xs font-mono text-slate-500">
                              · {floor.seriesLabel}
                            </span>
                          </div>
                          <p className="text-xs text-slate-600 mt-0.5">
                            {floor.description}
                          </p>
                        </div>
                      </div>

                      {/* Floor Availability Telemetry */}
                      <div className="flex flex-wrap items-center gap-3 text-xs font-mono tabular-nums shrink-0">
                        <span className="text-emerald-700 font-bold bg-emerald-50 border border-emerald-200 px-3 py-1.5 rounded-lg">
                          {summary.emptyCount} / {summary.totalCount} Empty Now
                        </span>
                        <span className="text-indigo-700 font-semibold bg-indigo-50 border border-indigo-200 px-3 py-1.5 rounded-lg">
                          {summary.safeTwoHourCount} Free 2h+
                        </span>
                        <span className="text-sky-700 font-semibold bg-sky-50 border border-sky-200 px-3 py-1.5 rounded-lg">
                          {summary.emptyACCount} AC Free
                        </span>
                      </div>
                    </div>

                    {/* Room Cards Grid for This Floor */}
                    {floorItems.length > 0 ? (
                      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                        {floorItems.map((roomStatus) => (
                          <RoomCard
                            key={roomStatus.room.id}
                            status={roomStatus}
                            isAIHighlighted={aiRecommendedIds.includes(
                              roomStatus.room.id
                            )}
                            isClaimed={claimedRoomId === roomStatus.room.id}
                            isFavorite={favoriteRoomIds.includes(
                              roomStatus.room.id
                            )}
                            onSelect={(st) => {
                              setSelected3DRoomId(st.room.id);
                              setInspectedRoom(st);
                            }}
                            onClaimRoom={(rid) => {
                              setClaimedRoomId(rid);
                              setSelected3DRoomId(rid);
                            }}
                            onToggleFavorite={handleToggleFavorite}
                          />
                        ))}
                      </div>
                    ) : (
                      <div className="bg-white border border-slate-200 rounded-2xl p-8 text-center">
                        <p className="text-sm font-bold text-slate-800">
                          No rooms on {floor.name} match your active filters at{' '}
                          {formatTime12h(selectedTime)}.
                        </p>
                        <p className="text-xs text-slate-500 mt-1">
                          Try switching to "Show All Rooms" or lowering the minimum free duration.
                        </p>
                        <button
                          type="button"
                          onClick={handleResetFilters}
                          className="mt-3.5 px-4 py-2 bg-indigo-600 text-white text-xs font-bold rounded-xl hover:bg-indigo-700 transition-colors cursor-pointer inline-flex items-center gap-1.5"
                        >
                          <RotateCcw className="w-3.5 h-3.5" />
                          <span>Show All Rooms on Floor</span>
                        </button>
                      </div>
                    )}
                  </section>
                );
              })}
            </div>
          </>
        )}

        {activeTab === 'matrix' && (
          <OccupancyMatrixView
            currentDay={selectedDay}
            statuses={allRoomStatuses}
            onSelectRoom={(st) => {
              setSelected3DRoomId(st.room.id);
              setInspectedRoom(st);
            }}
          />
        )}

        {activeTab === 'timetables' && <SectionTimetablesView />}
      </main>

      {/* Clean Footer */}
      <footer className="mt-12 border-t border-slate-200 bg-white py-5 px-6">
        <div className="max-w-[1380px] mx-auto flex flex-col sm:flex-row items-center justify-between gap-3 text-xs text-slate-500">
          <span>
            SRM Institute of Science and Technology (Tiruchirappalli Campus) — Faculty of Engineering and Technology
          </span>
          <span>
            Powered by 10 Department Timetables · 3D Live Room Tracker & WhatsApp Squad Share
          </span>
        </div>
      </footer>

      {/* Room Detail Schedule & Live Countdown Modal */}
      <RoomDetailModal
        status={inspectedRoom}
        claimedRoomId={claimedRoomId}
        onClaimRoom={(rid) => setClaimedRoomId(rid)}
        onClose={() => setInspectedRoom(null)}
      />
    </div>
  );
}
@import "tailwindcss";

@theme {
  --font-sans: "Plus Jakarta Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-mono: "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
}

@layer base {
  body {
    font-family: var(--font-sans);
    background-color: #F8FAFC;
    color: #0F172A;
  }
}

.tabular-nums {
  font-variant-numeric: tabular-nums;
}

import {StrictMode} from 'react';
import {createRoot} from 'react-dom/client';
import App from './App.tsx';
import './index.css';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>,
);
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>SRM RoomPulse — Free Classroom Tracker & AI Finder</title>
    <meta name="description" content="Real-time empty classroom tracker and AI room finder organized floor-by-floor across 10 engineering department timetables at SRM IST Tiruchirappalli." />
    <meta property="og:title" content="SRM RoomPulse — Free Classroom Tracker & AI Finder" />
    <meta property="og:description" content="Real-time empty classroom tracker and AI room finder organized floor-by-floor across 10 engineering department timetables at SRM IST Tiruchirappalli." />
    <meta property="og:type" content="website" />
    <meta name="twitter:card" content="summary_large_image" />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
  </head>
  <body class="bg-[#F8FAFC] text-slate-900 antialiased selection:bg-teal-600 selection:text-white">
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>

{
  "name": "react-example",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "tsx server.ts",
    "start": "tsx server.ts",
    "build": "vite build",
    "preview": "vite preview",
    "clean": "rm -rf dist server.js",
    "lint": "tsc --noEmit"
  },
  "dependencies": {
    "@google/genai": "^2.4.0",
    "@tailwindcss/vite": "^4.3.3",
    "@vitejs/plugin-react": "^6.1.1",
    "lucide-react": "^0.546.0",
    "react": "^19.0.1",
    "react-dom": "^19.0.1",
    "vite": "^8.3.0",
    "express": "^4.21.2",
    "dotenv": "^17.2.3",
    "motion": "^12.23.24"
  },
  "devDependencies": {
    "@types/node": "^22.14.0",
    "@types/react": "^19.3.0",
    "@types/react-dom": "^19.3.0",
    "autoprefixer": "^10.4.21",
    "esbuild": "^0.25.0",
    "tailwindcss": "^4.3.3",
    "tsx": "^4.21.0",
    "typescript": "^7.0.2",
    "@types/express": "^4.17.21"
  }
}
import dotenv from 'dotenv';
dotenv.config();

import express from 'express';
import path from 'path';
import { fileURLToPath } from 'url';
import { createServer as createViteServer } from 'vite';
import { GoogleGenAI, Type } from '@google/genai';
import { DayOfWeek, DAYS_OF_WEEK, FLOORS, FloorId, ROOMS } from './src/data/roomsData';
import {
  computeAllRoomsStatus,
  formatTime12h,
  RoomAvailabilityStatus,
} from './src/utils/occupancyEngine';

const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);

function getGeminiClient() {
  return new GoogleGenAI({
    apiKey: process.env.GEMINI_API_KEY,
    httpOptions: {
      headers: {
        'User-Agent': 'aistudio-build',
      },
    },
  });
}

// Helper to detect if user query explicitly mentions a day or time
function preResolveDayAndTime(
  query: string,
  fallbackDay: DayOfWeek,
  fallbackTime: string
): { day: DayOfWeek; time24: string } {
  const q = query.toLowerCase();
  let day: DayOfWeek = fallbackDay;
  for (const d of DAYS_OF_WEEK) {
    if (q.includes(d.toLowerCase()) || q.includes(d.slice(0, 3).toLowerCase() + ' ')) {
      day = d;
      break;
    }
  }

  let time24 = fallbackTime;
  const timeMatch = q.match(/\b(\d{1,2})(?::(\d{2}))?\s*(am|pm)\b/i);
  if (timeMatch) {
    let h = parseInt(timeMatch[1], 10);
    const m = timeMatch[2] ? parseInt(timeMatch[2], 10) : 0;
    const meridiem = timeMatch[3].toLowerCase();
    if (meridiem === 'pm' && h < 12) h += 12;
    if (meridiem === 'am' && h === 12) h = 0;
    if (h >= 9 && h <= 17) {
      time24 = `${String(h).padStart(2, '0')}:${String(m).padStart(2, '0')}`;
    }
  }

  return { day, time24 };
}

async function startServer() {
  const app = express();
  const PORT = 3000;

  app.use(express.json());

  app.post('/api/ai-room-finder', async (req, res) => {
    try {
      const { query, currentDay = 'Monday', currentTime = '11:45' } = req.body as {
        query?: string;
        currentDay?: DayOfWeek;
        currentTime?: string;
      };

      if (!query || typeof query !== 'string' || !query.trim()) {
        res.status(400).json({ error: 'Please enter a room search description.' });
        return;
      }

      const { day: resolvedDay, time24: resolvedTime } = preResolveDayAndTime(
        query,
        DAYS_OF_WEEK.includes(currentDay) ? currentDay : 'Monday',
        currentTime || '11:45'
      );

      const allStatuses: RoomAvailabilityStatus[] = computeAllRoomsStatus(
        resolvedDay,
        resolvedTime
      );

      // Build a concise structured timetable context for Gemini
      const roomsDigest = allStatuses.map((st) => ({
        roomId: st.room.id,
        code: st.room.code,
        name: st.room.name,
        floorId: st.room.floorId,
        floorName: FLOORS.find((f) => f.id === st.room.floorId)?.name || st.room.floorId,
        isAC: st.room.isAC,
        capacity: st.room.capacity,
        roomType: st.room.roomType,
        teamFriendly: st.room.teamFriendly,
        quietScore: st.room.quietScore,
        powerOutlets: st.room.powerOutlets,
        isCurrentlyEmpty: st.isCurrentlyEmpty,
        freeDurationMinutes: st.freeDurationMinutes,
        freeDurationFormatted: st.freeDurationFormatted,
        freeUntilFormatted: st.freeUntilFormatted,
        nextClass: st.nextSession
          ? `${st.nextSession.startTime} (${st.nextSession.subjectName} by ${st.nextSession.faculty} for ${st.nextSession.sectionName})`
          : 'No more classes today (Free until 05:05 PM)',
        currentClass:
          st.currentSessions.length > 0
            ? `${st.currentSessions[0].subjectName} (${st.currentSessions[0].sectionName}) until ${st.clearsAtTime}`
            : null,
      }));

      const ai = getGeminiClient();

      const systemInstruction = `You are the AI Room Finder for SRM Institute of Science and Technology (Tiruchirappalli Campus).
Students use you in the middle of the day to find empty classrooms or labs where they or their project teams can sit and work without getting kicked out 10 minutes later by a professor walking in for a scheduled lecture.

Floor Mapping Rules:
- "ground": Ground Floor (100-Series, Tech Block TB-106, IST 107, IST 108, IST 20,21 Workshop, Che Lab)
- "first": First Floor (200 & 300-Series: IST 201, IST 211, IST 225, IST 227, IST 309)
- "second": Second Floor (400 & 500-Series: IST 401, IST 411, IST 416, IST 502, IST 510, IST 518, IST 519, IST 520)
- "third": Third Floor / Upper Wing (600 & 700-Series: IST 602, IST 609, IST 617, IST 618, IST 625, IST 626, IST 702, IST 710)
- "all": No specific floor requested.
(Note: If a student mentions "500 series" or "5th floor", map to "second". If they mention "600/700 series" or "6th/7th floor", map to "third".)

Analyze the student's natural language prompt against the live room availability data at ${resolvedDay}, ${formatTime12h(resolvedTime)} (${resolvedTime}).
1. Extract their exact requirements (floorId, requiresAC, minDurationMinutes, teamOrGroup, quietPreference, roomTypePreference).
2. Select and rank the best matching rooms in recommendedRoomIds that are CURRENTLY EMPTY and stay free for at least their requested duration (or closest available if none strictly meet all criteria).
3. In kickOutWarnings, specifically mention any rooms on the requested floor that are either currently occupied or free for a dangerously short window before a professor walks in.
4. Write a clear, helpful summaryReasoning referencing exact room codes, free durations, and next lecture times.`;

      const response = await ai.models.generateContent({
        model: 'gemini-3.8-flash',
        contents: JSON.stringify({
          studentRequest: query,
          evaluationDay: resolvedDay,
          evaluationTime24: resolvedTime,
          evaluationTime12: formatTime12h(resolvedTime),
          liveRoomsData: roomsDigest,
        }),
        config: {
          systemInstruction,
          responseMimeType: 'application/json',
          responseSchema: {
            type: Type.OBJECT,
            properties: {
              parsedIntent: {
                type: Type.OBJECT,
                properties: {
                  floorPreference: {
                    type: Type.STRING,
                    description: 'One of: ground, first, second, third, all',
                  },
                  requiresAC: {
                    type: Type.BOOLEAN,
                    description: 'True if user asked for AC / air conditioned room',
                  },
                  minDurationMinutes: {
                    type: Type.INTEGER,
                    description: 'Minimum required free duration in minutes (e.g. 120 for 2 hours, 60 for 1 hour)',
                  },
                  teamOrGroup: {
                    type: Type.BOOLEAN,
                    description: 'True if user mentioned team, group, project partners, or friends',
                  },
                  quietPreference: {
                    type: Type.BOOLEAN,
                    description: 'True if user asked for quiet, silent, undisturbed study',
                  },
                  roomTypePreference: {
                    type: Type.STRING,
                    description: 'Classroom, Lab, Seminar Hall, or Any',
                  },
                },
                required: [
                  'floorPreference',
                  'requiresAC',
                  'minDurationMinutes',
                  'teamOrGroup',
                  'quietPreference',
                  'roomTypePreference',
                ],
              },
              summaryReasoning: {
                type: Type.STRING,
                description:
                  'Concise, actionable explanation of the best matching rooms, their unbroken free window, and when the next professor arrives.',
              },
              recommendedRoomIds: {
                type: Type.ARRAY,
                items: { type: Type.STRING },
                description: 'Ordered list of matching roomId values (e.g., TB-106, IST-107, IST-225)',
              },
              kickOutWarnings: {
                type: Type.ARRAY,
                items: { type: Type.STRING },
                description:
                  'Warnings about rooms on the target floor that are occupied or have a lecture starting soon.',
              },
            },
            required: [
              'parsedIntent',
              'summaryReasoning',
              'recommendedRoomIds',
              'kickOutWarnings',
            ],
          },
        },
      });

      const rawText = response.text;
      if (!rawText) {
        throw new Error('Empty response received from Gemini model.');
      }

      const aiResult = JSON.parse(rawText);

      // Normalize floorPreference
      const validFloors = ['ground', 'first', 'second', 'third', 'all'];
      const floorPref: FloorId | 'all' = validFloors.includes(
        aiResult.parsedIntent?.floorPreference
      )
        ? aiResult.parsedIntent.floorPreference
        : 'all';

      // Ensure recommendedRoomIds are valid room IDs
      const validRoomIds = new Set(ROOMS.map((r) => r.id));
      const cleanRecommendedIds: string[] = (aiResult.recommendedRoomIds || []).filter(
        (id: string) => validRoomIds.has(id)
      );

      res.json({
        resolvedDay,
        resolvedTime,
        parsedIntent: {
          ...aiResult.parsedIntent,
          floorPreference: floorPref,
        },
        summaryReasoning: aiResult.summaryReasoning,
        recommendedRoomIds: cleanRecommendedIds,
        kickOutWarnings: aiResult.kickOutWarnings || [],
      });
    } catch (error: any) {
      console.error('AI Room Finder Error (falling back to smart local analyzer):', error);
      // Resilient fallback so students always get instant, accurate timetable results
      const { query = '', currentDay = 'Monday', currentTime = '11:45' } = req.body || {};
      const { day: resolvedDay, time24: resolvedTime } = preResolveDayAndTime(
        String(query),
        DAYS_OF_WEEK.includes(currentDay) ? currentDay : 'Monday',
        currentTime || '11:45'
      );
      const qLower = String(query).toLowerCase();

      let floorPreference: FloorId | 'all' = 'all';
      for (const fl of FLOORS) {
        if (fl.aliases.some((alias) => qLower.includes(alias))) {
          floorPreference = fl.id;
          break;
        }
      }

      const requiresAC =
        /\bac\b|air condition|cool|chilled|climate/i.test(qLower) &&
        !/non-ac|non ac|without ac/i.test(qLower);

      let minDurationMinutes = 60;
      const hrMatch = qLower.match(/(\d+(?:\.\d+)?)\s*(?:hour|hr|hrs|h)\b/i);
      const minMatch = qLower.match(/(\d+)\s*(?:minute|min|mins|m)\b/i);
      if (hrMatch) {
        minDurationMinutes = Math.round(parseFloat(hrMatch[1]) * 60);
      } else if (minMatch) {
        minDurationMinutes = parseInt(minMatch[1], 10);
      } else if (/rest of (the )?day|all afternoon|whole day/i.test(qLower)) {
        minDurationMinutes = 180;
      }

      const teamOrGroup = /team|group|project|friends|partner|us|we/i.test(qLower);
      const quietPreference = /quiet|silent|peaceful|solo|focus|study/i.test(qLower);
      const wantsLab = /lab|computer|pc|workstation/i.test(qLower);

      const allStatuses = computeAllRoomsStatus(resolvedDay, resolvedTime);
      const candidates = allStatuses
        .filter((st) => {
          if (!st.isCurrentlyEmpty) return false;
          if (floorPreference !== 'all' && st.room.floorId !== floorPreference) return false;
          if (requiresAC && !st.room.isAC) return false;
          if (st.freeDurationMinutes < minDurationMinutes) return false;
          if (wantsLab && !st.room.roomType.toLowerCase().includes('lab')) return false;
          return true;
        })
        .sort((a, b) => b.freeDurationMinutes - a.freeDurationMinutes);

      const recommendedRoomIds = candidates.slice(0, 6).map((c) => c.room.id);

      const warnings = allStatuses
        .filter(
          (st) =>
            (floorPreference === 'all' || st.room.floorId === floorPreference) &&
            (!st.isCurrentlyEmpty || (!st.isFreeRestOfDay && st.freeDurationMinutes < 60))
        )
        .slice(0, 3)
        .map((st) =>
          st.isCurrentlyEmpty
            ? `${st.room.code} (${st.room.name}) is only free for ${st.freeDurationFormatted} before ${st.nextSession?.subjectName} starts at ${formatTime12h(st.freeUntilTime)}.`
            : `${st.room.code} (${st.room.name}) is currently occupied by ${st.currentSessions[0]?.sectionName} (${st.currentSessions[0]?.subjectName}) until ${formatTime12h(st.clearsAtTime || '17:05')}.`
        );

      const floorLabel =
        floorPreference === 'all'
          ? 'across all floors'
          : `on the ${FLOORS.find((f) => f.id === floorPreference)?.name}`;

      const topNames = candidates
        .slice(0, 3)
        .map((c) => `${c.room.code} (free for ${c.freeDurationFormatted})`)
        .join(', ');

      res.json({
        resolvedDay,
        resolvedTime,
        parsedIntent: {
          floorPreference,
          requiresAC,
          minDurationMinutes,
          teamOrGroup,
          quietPreference,
          roomTypePreference: wantsLab ? 'Lab' : 'Any',
        },
        summaryReasoning:
          candidates.length > 0
            ? `Found ${candidates.length} empty ${requiresAC ? 'AC ' : ''}room${candidates.length === 1 ? '' : 's'} ${floorLabel} free for at least ${Math.round(minDurationMinutes / 60 * 10) / 10} hours starting at ${formatTime12h(resolvedTime)} on ${resolvedDay}. Best options: ${topNames}.`
            : `No rooms ${floorLabel} strictly matched every filter simultaneously at ${formatTime12h(resolvedTime)}. Try checking adjacent floors or lowering the minimum duration.`,
        recommendedRoomIds,
        kickOutWarnings: warnings,
      });
    }
  });

  if (process.env.NODE_ENV !== 'production') {
    const vite = await createViteServer({
      server: { middlewareMode: true },
      appType: 'spa',
    });
    app.use(vite.middlewares);
  } else {
    const distPath = path.join(__dirname, 'dist');
    app.use(express.static(distPath));
    app.get('*', (_req, res) => {
      res.sendFile(path.join(distPath, 'index.html'));
    });
  }

  app.listen(PORT, '0.0.0.0', () => {
    console.log(`SRM RoomPulse server running on http://localhost:${PORT}`);
  });
}

startServer();


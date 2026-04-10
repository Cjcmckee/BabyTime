<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0,viewport-fit=cover"/>
<title>Baby Time</title>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<meta name="apple-mobile-web-app-title" content="Baby Time"/>
<meta name="theme-color" content="#ffffff"/>
<script>
(function(){
  function babyPNG(size){
    var c=document.createElement('canvas');
    c.width=c.height=size;
    var ctx=c.getContext('2d'),cx=size/2,cy=size/2,r=size*0.41;
    ctx.fillStyle='#fff';ctx.fillRect(0,0,size,size);
    ctx.beginPath();ctx.arc(cx,cy+size*0.04,r,0,Math.PI*2);ctx.fillStyle='#FFCBA4';ctx.fill();
    ctx.beginPath();ctx.arc(cx,cy-r*0.65,r*0.32,Math.PI,0);ctx.fillStyle='#C8A060';ctx.fill();
    ctx.beginPath();ctx.arc(cx-r*0.2,cy-r*0.88,r*0.18,Math.PI,0);ctx.fillStyle='#C8A060';ctx.fill();
    ctx.beginPath();ctx.arc(cx+r*0.2,cy-r*0.88,r*0.18,Math.PI,0);ctx.fillStyle='#C8A060';ctx.fill();
    ctx.beginPath();ctx.arc(cx-r*0.3,cy-r*0.05,r*0.13,0,Math.PI*2);ctx.fillStyle='#4A90D9';ctx.fill();
    ctx.beginPath();ctx.arc(cx-r*0.3,cy-r*0.05,r*0.065,0,Math.PI*2);ctx.fillStyle='#111';ctx.fill();
    ctx.beginPath();ctx.arc(cx-r*0.26,cy-r*0.09,r*0.03,0,Math.PI*2);ctx.fillStyle='#fff';ctx.fill();
    ctx.beginPath();ctx.arc(cx+r*0.3,cy-r*0.05,r*0.13,0,Math.PI*2);ctx.fillStyle='#4A90D9';ctx.fill();
    ctx.beginPath();ctx.arc(cx+r*0.3,cy-r*0.05,r*0.065,0,Math.PI*2);ctx.fillStyle='#111';ctx.fill();
    ctx.beginPath();ctx.arc(cx+r*0.34,cy-r*0.09,r*0.03,0,Math.PI*2);ctx.fillStyle='#fff';ctx.fill();
    ctx.beginPath();ctx.arc(cx-r*0.55,cy+r*0.15,r*0.14,0,Math.PI*2);ctx.fillStyle='rgba(255,140,140,0.35)';ctx.fill();
    ctx.beginPath();ctx.arc(cx+r*0.55,cy+r*0.15,r*0.14,0,Math.PI*2);ctx.fillStyle='rgba(255,140,140,0.35)';ctx.fill();
    ctx.beginPath();ctx.arc(cx,cy+r*0.18,r*0.22,0.25,Math.PI-0.25);ctx.strokeStyle='#c0706a';ctx.lineWidth=r*0.06;ctx.lineCap='round';ctx.stroke();
    return c.toDataURL('image/png');
  }
  var i192=babyPNG(192),i512=babyPNG(512);
  var al=document.createElement('link');al.rel='apple-touch-icon';al.href=i192;document.head.appendChild(al);
  var mb=new Blob([JSON.stringify({name:'Baby Time',short_name:'Baby Time',start_url:'.',display:'standalone',background_color:'#ffffff',theme_color:'#ffffff',icons:[{src:i192,sizes:'192x192',type:'image/png'},{src:i512,sizes:'512x512',type:'image/png'}]})],{type:'application/manifest+json'});
  var ml=document.createElement('link');ml.rel='manifest';ml.href=URL.createObjectURL(mb);document.head.appendChild(ml);
})();
</script>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#fff;--bg2:#f5f5f5;
  --text:#111;--text2:#555;--text3:#999;
  --blue-bg:#e8f0fe;--blue:#1a56db;--blue-br:#93b4f7;
  --green-bg:#dcfce7;--green:#16a34a;--green-br:#86efac;
  --amber-bg:#fef3c7;--amber:#d97706;--amber-br:#fcd34d;
  --red-bg:#fee2e2;--red:#dc2626;--red-br:#fca5a5;
  --purple-bg:#f3e8ff;--purple:#7c3aed;--purple-br:#c4b5fd;
  --pink-bg:#fce7f3;--pink:#db2777;--pink-br:#f9a8d4;
  --border:#e0e0e0;
  --safe-top:env(safe-area-inset-top,0px);
  --safe-bottom:env(safe-area-inset-bottom,0px)
}
@media(prefers-color-scheme:dark){:root{
  --bg:#111;--bg2:#1e1e1e;
  --text:#f0f0f0;--text2:#aaa;--text3:#666;
  --blue-bg:#1a2e4a;--blue:#93b4f7;--blue-br:#2d4f8a;
  --green-bg:#0f2e1a;--green:#86efac;--green-br:#1a5c32;
  --amber-bg:#2e1e00;--amber:#fcd34d;--amber-br:#7a4f00;
  --red-bg:#2e0a0a;--red:#fca5a5;--red-br:#7a1a1a;
  --purple-bg:#2e1a4a;--purple:#c4b5fd;--purple-br:#5b21b6;
  --pink-bg:#3a0a20;--pink:#f9a8d4;--pink-br:#9d174d;
  --border:#333
}}
body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;background:var(--bg);color:var(--text);padding-top:var(--safe-top);padding-bottom:var(--safe-bottom);min-height:100vh;-webkit-tap-highlight-color:transparent}
#root{max-width:480px;margin:0 auto}
button,input{font-family:inherit;-webkit-appearance:none}
input[type="time"]::-webkit-calendar-picker-indicator{display:none}
</style>
</head>
<body>
<div id="root"></div>
<script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
const { useState, useEffect } = React;

const INDICATIONS   = ["Fetal distress / CTG abnormality","Cord prolapse","Placental abruption","Uterine rupture","Failed instrumental delivery","Malpresentation","Maternal haemorrhage","Pre-eclampsia / eclampsia","Failure to progress","Placenta praevia","Previous uterine surgery / scar dehiscence","Other"];
const ANAESTHESIA   = ["Spinal","Epidural top-up","General anaesthesia (GA)","Combined spinal-epidural (CSE)"];
const CATEGORIES    = ["Cat 1 — immediate threat to life","Cat 2 — maternal / fetal compromise","Cat 3 — early delivery needed","Cat 4 — elective timing"];
const PPH_OPTS      = ["No PPH","PPH (>500 ml)","Major PPH (>1000 ml)","Massive PPH (>1500 ml)"];
const SPINAL_LEVELS = ["L1–2","L2–3","L3–4","L4–5"];
const ASA_GRADES    = ["I","II","III","IV","V"];
const MALLAMPATI    = ["I","II","III","IV"];
const CL_GRADES     = ["1","2a","2b","3","4"];
const BLOCK_TYPES   = ["TAP block","Rectus sheath block","QL block"];
const LA_PRIMARY    = ["Bupivacaine (hyperbaric)","Bupivacaine (plain)","Levobupivacaine","Ropivacaine","Lidocaine","Chloroprocaine","Other"];
const LA_BLOCK      = ["Bupivacaine","Levobupivacaine","Ropivacaine","Lidocaine","Other"];
const ADJUVANTS     = ["Diamorphine","Morphine","Fentanyl","Clonidine","Other"];

const STEPS = [
  {key:"tAlerted",        label:"Anaesthetist alerted",          prereqs:[]},
  {key:"tAnaesTheatre",   label:"Anaesthetist in theatre",       prereqs:[]},
  {key:"tPatientTheatre", label:"Patient in theatre",            prereqs:[]},
  {key:"tAnaesStart",     label:"Anaesthesia commenced",         prereqs:[]},
  {key:"tReady",          label:"Anaesthesia ready for surgery", prereqs:["tAnaesStart"]},
  {key:"tSkin",           label:"Knife to skin",                 prereqs:["tReady"]},
  {key:"tBaby",           label:"Baby delivered / cord clamped", prereqs:["tSkin"]},
  {key:"tPlacenta",       label:"Placenta delivered",            prereqs:["tBaby"]},
  {key:"tClosed",         label:"Skin closed",                   prereqs:["tPlacenta"]},
  {key:"tLeft",           label:"Patient leaves theatre",        prereqs:["tClosed"]},
];
const SUMMARY_KEYS = ["tAlerted","tAnaesTheatre","tPatientTheatre","tAnaesStart","tReady","tSkin","tBaby"];

const MEDS_BASE = [
  {key:"tOxytocin",   label:"Oxytocin"},
  {key:"tErgo",       label:"Ergometrine"},
  {key:"tCarboprost", label:"Carboprost"},
  {key:"tTXA",        label:"TXA"},
  {key:"tMisoprostol",label:"Misoprostol"},
];
const MED_SODIUM = {key:"tSodiumCitrate",label:"Sodium citrate"};

const BLANK = {
  category:"",indication:"",anaesType:"",spinalLevel:"",
  age:"",asa:"",
  primaryLAType:"",primaryLAConc:"",primaryLAVol:"",primaryLARoute:"",
  adjuvantType:"",adjuvantConc:"",adjuvantVol:"",adjuvantRoute:"",
  conversion:"",mallampati:"",clGrade:"",
  regionalBlock:"",blockTypes:[],blockUS:"",
  blockLAType:"",blockLAConc:"",blockLAVol:"",
  apgar1:"",apgar5:"",pph:"",ebl:""
};

const CSV_HEAD = [
  "Case No","Date","OOH / In-hours","Category","Indication","Anaesthesia","Spinal level",
  "Age","ASA",
  "Primary LA type","Primary LA conc","Primary LA vol (ml)","Primary LA route",
  "Adjuvant type","Adjuvant conc","Adjuvant vol (ml)","Adjuvant route",
  "Conversion to GA","Mallampati","Cormack-Lehane",
  "Regional block","Block type(s)","Block LA type","Block LA conc","Block LA vol (ml)","Ultrasound",
  ...STEPS.map(s=>s.label),
  ...MEDS_BASE.map(m=>m.label),"Sodium citrate",
  "Apgar 1min","Apgar 5min","PPH","EBL ml",
  "Alert-to-delivery","Alert-to-skin","Induction","Surgical","Total theatre"
];

const fmt     = ts    => ts ? new Date(ts).toLocaleTimeString("en-GB",{hour:"2-digit",minute:"2-digit",second:"2-digit"}) : "—";
const fmtDate = ts    => ts ? new Date(ts).toLocaleDateString("en-GB") : new Date().toLocaleDateString("en-GB");
const secs    = (a,b) => (a&&b) ? Math.round((b-a)/1000) : null;
const mins    = s     => (s===null||s===undefined) ? "—" : `${Math.floor(s/60)}m ${s%60}s`;
const nowStr  = ()    => { const n=new Date(); return `${String(n.getHours()).padStart(2,"0")}:${String(n.getMinutes()).padStart(2,"0")}`; };
const parseT  = val   => { const [h,m]=val.split(":").map(Number); const d=new Date(); d.setHours(h,m,0,0); return d.getTime(); };
const isGA    = t     => !!(t&&t.toLowerCase().includes("general"));
const getOOH  = ts    => { if(!ts)return null; const d=new Date(ts),day=d.getDay(),h=d.getHours(); return(day===0||day===6||h<8||h>=18)?"OOH":"In hours"; };
const catStyle= cat   =>
  cat.startsWith("Cat 1")?{bg:"var(--red-bg)",  fg:"var(--red)",  br:"var(--red-br)"}:
  cat.startsWith("Cat 2")?{bg:"var(--amber-bg)",fg:"var(--amber)",br:"var(--amber-br)"}:
  cat.startsWith("Cat 3")?{bg:"var(--blue-bg)", fg:"var(--blue)", br:"var(--blue-br)"}:
                          {bg:"var(--green-bg)",fg:"var(--green)",br:"var(--green-br)"};

function loadCases()     { try{return JSON.parse(localStorage.getItem("cs_cases")||"[]");}catch(e){return[];} }
function saveCases(c)    { localStorage.setItem("cs_cases",JSON.stringify(c)); }
function nextCaseNo()    { const c=loadCases(); return c.length?Math.max(...c.map(x=>x.caseNo))+1:1; }
function appendCase(d)   { const c=loadCases(); c.push(d); saveCases(c); }

function buildCSV(cases) {
  const rows=[CSV_HEAD,...cases.map(c=>{
    const ddi=secs(c.times.tAlerted,c.times.tBaby),d2s=secs(c.times.tAlerted,c.times.tSkin);
    const ind=secs(c.times.tAnaesStart,c.times.tReady),surg=secs(c.times.tSkin,c.times.tClosed);
    const tot=secs(c.times.tPatientTheatre,c.times.tLeft);
    const e=Object.values(c.times).filter(Boolean).sort()[0];
    const d=c.details;
    return[
      `CS-${String(c.caseNo).padStart(3,"0")}`,fmtDate(e),getOOH(e)||"—",
      d.category||"",d.indication||"",d.anaesType||"",d.spinalLevel||"",
      d.age||"",d.asa||"",
      d.primaryLAType||"",d.primaryLAConc||"",d.primaryLAVol||"",d.primaryLARoute||"",
      d.adjuvantType||"",d.adjuvantConc||"",d.adjuvantVol||"",d.adjuvantRoute||"",
      d.conversion||"",d.mallampati||"",d.clGrade||"",
      d.regionalBlock||"",Array.isArray(d.blockTypes)?d.blockTypes.join("; "):"",
      d.blockLAType||"",d.blockLAConc||"",d.blockLAVol||"",d.blockUS||"",
      ...STEPS.map(s=>fmt(c.times[s.key])),
      ...MEDS_BASE.map(m=>(c.medTimes[m.key]||[]).map(t=>fmt(t)).join("; ")),
      (c.medTimes[MED_SODIUM.key]||[]).map(t=>fmt(t)).join("; ")||"",
      d.apgar1||"",d.apgar5||"",d.pph||"",d.ebl||"",
      mins(ddi),mins(d2s),mins(ind),mins(surg),mins(tot)
    ];
  })];
  return rows.map(r=>r.map(v=>`"${String(v).replace(/"/g,'""')}"`).join(",")).join("\n");
}
function dlCSV(cases,name){
  const b=new Blob([buildCSV(cases)],{type:"text/csv"});
  const u=URL.createObjectURL(b);
  const a=document.createElement("a");a.href=u;a.download=name;a.click();URL.revokeObjectURL(u);
}

const SL=({children})=><p style={{fontSize:11,fontWeight:600,textTransform:"uppercase",letterSpacing:"0.08em",color:"var(--text3)",margin:"0 0 10px"}}>{children}</p>;

function StepCard({step,onRecord}){
  const[mode,setMode]=useState("idle"),[tv,setTv]=useState(""),[leaving,setLeaving]=useState(false);
  function rec(ts){setLeaving(true);setTimeout(()=>onRecord(ts),340);}
  const wrap={transform:leaving?"translateY(-16px)":"translateY(0)",opacity:leaving?0:1,maxHeight:leaving?0:220,marginBottom:leaving?0:12,overflow:"hidden",transition:"transform 0.3s ease,opacity 0.25s ease,max-height 0.38s ease,margin 0.38s ease"};
  if(mode==="entering")return(
    <div style={wrap}>
      <div style={{padding:18,background:"var(--bg2)",border:"0.5px solid var(--border)",borderRadius:16}}>
        <p style={{fontSize:12,color:"var(--text3)",textTransform:"uppercase",letterSpacing:"0.06em",fontWeight:600,marginBottom:4}}>Entering time for</p>
        <p style={{fontSize:18,fontWeight:600,color:"var(--text)",marginBottom:14}}>{step.label}</p>
        <input type="time" value={tv} onChange={e=>setTv(e.target.value)} style={{width:"100%",padding:14,fontSize:26,fontWeight:600,textAlign:"center",borderRadius:10,border:"0.5px solid var(--border)",background:"var(--bg)",color:"var(--text)",marginBottom:12}}/>
        <div style={{display:"flex",gap:8}}>
          <button onClick={()=>{if(tv){rec(parseT(tv));setMode("idle");}}} style={{flex:2,padding:14,fontSize:16,fontWeight:600,background:"var(--blue-bg)",color:"var(--blue)",border:"2px solid var(--blue-br)",borderRadius:10,cursor:"pointer"}}>Confirm</button>
          <button onClick={()=>setMode("idle")} style={{flex:1,padding:14,fontSize:15,background:"transparent",color:"var(--text2)",border:"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>Cancel</button>
        </div>
      </div>
    </div>
  );
  return(
    <div style={wrap}>
      <div style={{border:"2px solid var(--blue-br)",borderRadius:16,overflow:"hidden",background:"var(--bg)"}}>
        <p style={{margin:0,padding:"16px 18px 14px",fontSize:20,fontWeight:600,color:"var(--blue)",lineHeight:1.3}}>{step.label}</p>
        <div style={{display:"flex",borderTop:"1.5px solid var(--blue-br)"}}>
          <button onClick={()=>rec(Date.now())} style={{flex:2,padding:18,fontSize:18,fontWeight:700,background:"var(--blue-bg)",color:"var(--blue)",border:"none",borderRight:"1.5px solid var(--blue-br)",cursor:"pointer"}}>Now</button>
          <button onClick={()=>{setTv(nowStr());setMode("entering");}} style={{flex:1,padding:18,fontSize:14,background:"transparent",color:"var(--blue)",border:"none",cursor:"pointer",opacity:0.8}}>Enter time</button>
        </div>
      </div>
    </div>
  );
}

function MedCard({med,doses,onRecord}){
  const[mode,setMode]=useState("idle"),[tv,setTv]=useState("");
  const given=doses.length>0;
  const col=given?"var(--amber)":"var(--text)",bg=given?"var(--amber-bg)":"var(--bg)",br=given?"var(--amber-br)":"var(--border)";
  if(mode==="entering")return(
    <div style={{background:"var(--bg2)",border:"0.5px solid var(--border)",borderRadius:12,padding:12}}>
      <p style={{fontSize:13,fontWeight:600,color:"var(--text)",marginBottom:8}}>{med.label}</p>
      <input type="time" value={tv} onChange={e=>setTv(e.target.value)} style={{width:"100%",padding:10,fontSize:18,fontWeight:600,textAlign:"center",borderRadius:8,border:"0.5px solid var(--border)",background:"var(--bg)",color:"var(--text)",marginBottom:8}}/>
      <div style={{display:"flex",gap:6}}>
        <button onClick={()=>{if(tv){onRecord(parseT(tv));setMode("idle");}}} style={{flex:1,padding:9,fontSize:13,fontWeight:600,background:"var(--amber-bg)",color:"var(--amber)",border:"1.5px solid var(--amber-br)",borderRadius:8,cursor:"pointer"}}>OK</button>
        <button onClick={()=>setMode("idle")} style={{flex:1,padding:9,fontSize:13,background:"transparent",color:"var(--text2)",border:"0.5px solid var(--border)",borderRadius:8,cursor:"pointer"}}>Cancel</button>
      </div>
    </div>
  );
  return(
    <div style={{border:`${given?"1.5px":"0.5px"} solid ${br}`,borderRadius:12,overflow:"hidden",background:bg}}>
      <button onClick={()=>onRecord(Date.now())} style={{width:"100%",padding:"14px 8px",fontSize:14,fontWeight:600,textAlign:"center",background:"transparent",color:col,border:"none",borderBottom:`0.5px solid ${br}`,cursor:"pointer",lineHeight:1.2}}>{med.label}</button>
      <button onClick={()=>{setTv(nowStr());setMode("entering");}} style={{width:"100%",padding:8,fontSize:11,background:"transparent",color:col,border:"none",cursor:"pointer",opacity:0.85}}>Enter time</button>
      {doses.map((t,i)=><p key={i} style={{margin:0,padding:"2px 8px 6px",fontSize:12,color:col,textAlign:"center",fontWeight:600}}>{fmt(t)}</p>)}
    </div>
  );
}

function LASection({types,typeKey,concKey,volKey,details,upd,inp}){
  const[other,setOther]=useState(false);
  return(
    <>
      <p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Type</p>
      {!other&&(
        <div style={{display:"flex",flexWrap:"wrap",gap:8,marginBottom:12}}>
          {types.filter(t=>t!=="Other").map(t=>{const a=details[typeKey]===t;return<button key={t} onClick={()=>upd(typeKey,a?"":t)} style={{padding:"10px 14px",fontSize:14,fontWeight:a?600:400,background:a?"var(--blue-bg)":"var(--bg)",color:a?"var(--blue)":"var(--text)",border:a?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{t}</button>;})}
          <button onClick={()=>{setOther(true);upd(typeKey,"");}} style={{padding:"10px 14px",fontSize:14,background:"var(--bg)",color:"var(--text)",border:"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>Other</button>
        </div>
      )}
      {other&&<div style={{marginBottom:12}}><input autoFocus value={details[typeKey]} onChange={e=>upd(typeKey,e.target.value)} placeholder="Specify LA…" style={{...inp,marginBottom:8}}/><button onClick={()=>{setOther(false);upd(typeKey,"");}} style={{fontSize:13,color:"var(--text2)",background:"none",border:"none",cursor:"pointer",padding:0}}>Back to list</button></div>}
      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12}}>
        <div><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Concentration (%)</p><input value={details[concKey]} onChange={e=>upd(concKey,e.target.value)} placeholder="e.g. 0.5" style={inp}/></div>
        <div><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Volume (ml)</p><input type="number" min={0} max={100} value={details[volKey]} onChange={e=>upd(volKey,e.target.value)} placeholder="e.g. 2.5" style={inp}/></div>
      </div>
    </>
  );
}

function App(){
  const[view,setView]           =useState("home");
  const[tab,setTab]             =useState("timer");
  const[times,setTimes]         =useState({});
  const[medTimes,setMedTimes]   =useState({});
  const[details,setDetails]     =useState({...BLANK});
  const[clock,setClock]         =useState(new Date());
  const[done,setDone]           =useState(false);
  const[endDone,setEndDone]     =useState(false);
  const[catVisible,setCatVisible]=useState(true);
  const[catLeaving,setCatLeaving]=useState(false);
  const[caseNo]                 =useState(()=>nextCaseNo());

  useEffect(()=>{const t=setInterval(()=>setClock(new Date()),1000);return()=>clearInterval(t);},[]);

  function startCase(){setTimes({tAlerted:Date.now()});setView("tracker");}
  function selectCat(i){setDetails(d=>({...d,category:CATEGORIES[i]}));setCatLeaving(true);setTimeout(()=>setCatVisible(false),320);}
  function buildRec(){return{caseNo,times,medTimes,details,savedAt:Date.now()};}
  function handleEnd(){appendCase(buildRec());setEndDone(true);}
  function handleComplete(){appendCase(buildRec());setDone(true);}
  function resetAll(){
    setTimes({});setMedTimes({});setDetails({...BLANK});
    setDone(false);setEndDone(false);setTab("timer");
    setCatVisible(true);setCatLeaving(false);setView("home");
  }

  const label=`CS-${String(caseNo).padStart(3,"0")}`;
  const cs=details.category?catStyle(details.category):null;

  if(view==="home")   return <HomeView onStart={startCase} onCases={()=>setView("cases")} onAbout={()=>setView("about")} caseLabel={label}/>;
  if(view==="cases")  return <CasesView onBack={()=>setView("home")}/>;
  if(view==="about")  return <AboutView onBack={()=>setView("home")}/>;
  if(endDone)         return <EndSummary times={times} caseNo={caseNo} onHome={resetAll}/>;
  if(done)            return <Summary times={times} medTimes={medTimes} details={details} caseNo={caseNo} onReset={resetAll} onCases={()=>setView("cases")}/>;

  return(
    <div style={{paddingBottom:40}}>
      <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"16px 18px 10px"}}>
        <div style={{display:"flex",alignItems:"center",gap:8}}>
          <button onClick={()=>setView("home")} style={{fontSize:20,background:"transparent",border:"none",cursor:"pointer",padding:"0 4px 0 0",lineHeight:1}}>👶</button>
          <span style={{fontSize:13,fontWeight:700,color:"var(--text3)"}}>{label}</span>
          {!catVisible&&details.category&&<button onClick={()=>{setCatVisible(true);setCatLeaving(false);}} style={{padding:"3px 10px",fontSize:13,fontWeight:600,borderRadius:20,border:"none",cursor:"pointer",background:cs.bg,color:cs.fg}}>{details.category.slice(0,5)}</button>}
        </div>
        <div style={{display:"flex",alignItems:"center",gap:10}}>
          <button onClick={()=>setView("cases")} style={{fontSize:13,fontWeight:600,color:"var(--blue)",background:"transparent",border:"none",cursor:"pointer"}}>All cases</button>
          <span style={{fontSize:20,fontWeight:700,fontVariantNumeric:"tabular-nums",color:"var(--text)"}}>{clock.toLocaleTimeString("en-GB")}</span>
        </div>
      </div>

      {catVisible&&(
        <div style={{display:"flex",gap:8,padding:"0 18px 12px",transform:catLeaving?"translateY(-28px)":"translateY(0)",opacity:catLeaving?0:1,maxHeight:catLeaving?0:80,overflow:"hidden",transition:"transform 0.3s ease,opacity 0.25s ease,max-height 0.3s ease"}}>
          {[["1","red"],["2","amber"],["3","blue"],["4","green"]].map(([n,c])=>{
            const a=details.category.startsWith(`Cat ${n}`);
            const st={red:{bg:"var(--red-bg)",fg:"var(--red)",br:"var(--red-br)"},amber:{bg:"var(--amber-bg)",fg:"var(--amber)",br:"var(--amber-br)"},blue:{bg:"var(--blue-bg)",fg:"var(--blue)",br:"var(--blue-br)"},green:{bg:"var(--green-bg)",fg:"var(--green)",br:"var(--green-br)"}}[c];
            return<button key={n} onClick={()=>selectCat(Number(n)-1)} style={{flex:1,padding:"12px 4px",fontSize:15,fontWeight:a?700:500,background:a?st.bg:"var(--bg2)",color:a?st.fg:"var(--text2)",border:a?`2px solid ${st.br}`:"0.5px solid var(--border)",borderRadius:12,cursor:"pointer"}}>Cat {n}</button>;
          })}
        </div>
      )}

      <div style={{display:"flex",margin:"0 18px 16px",background:"var(--bg2)",borderRadius:10,padding:3}}>
        {[["timer","Timestamps"],["details","Case details"]].map(([id,lbl])=>(
          <button key={id} onClick={()=>setTab(id)} style={{flex:1,padding:11,fontSize:14,fontWeight:tab===id?700:500,background:tab===id?"var(--bg)":"transparent",color:tab===id?"var(--text)":"var(--text2)",border:tab===id?"0.5px solid var(--border)":"none",borderRadius:8,cursor:"pointer"}}>{lbl}</button>
        ))}
      </div>

      {tab==="timer"  &&<TimerTab   times={times} setTimes={setTimes} medTimes={medTimes} setMedTimes={setMedTimes} details={details} setDetails={setDetails} onFinish={handleComplete} onEnd={handleEnd} onCancel={resetAll}/>}
      {tab==="details"&&<DetailsTab details={details} setDetails={setDetails} times={times}/>}
    </div>
  );
}

function TimerTab({times,setTimes,medTimes,setMedTimes,details,setDetails,onFinish,onEnd,onCancel}){
  const skip      =s=>!!(times.tAnaesStart&&s.key==="tPatientTheatre");
  const available =STEPS.filter(s=>!times[s.key]&&!skip(s)&&s.prereqs.every(p=>times[p])).slice(0,3);
  const locked    =STEPS.filter(s=>!times[s.key]&&!skip(s)&&!s.prereqs.every(p=>times[p])).slice(0,2);
  const recorded  =STEPS.filter(s=>times[s.key]).sort((a,b)=>times[a.key]-times[b.key]);
  const allDone   =STEPS.every(s=>times[s.key]||skip(s));
  const ga        =isGA(details.anaesType);
  function recMed(key,ts){setMedTimes(m=>({...m,[key]:[...(m[key]||[]),ts]}));}
  return(
    <div style={{padding:"0 18px 24px"}}>
      <div style={{marginBottom:20}}>
        <SL>Anaesthesia type</SL>
        <div style={{display:"flex",gap:10}}>
          {[{label:"Spinal / Regional",val:"Spinal",col:{bg:"var(--blue-bg)",fg:"var(--blue)",br:"var(--blue-br)"},match:t=>!!(t&&!t.toLowerCase().includes("general"))},{label:"GA",val:"General anaesthesia (GA)",col:{bg:"var(--purple-bg)",fg:"var(--purple)",br:"var(--purple-br)"},match:t=>isGA(t)}].map(o=>{
            const a=o.match(details.anaesType);
            return<button key={o.label} onClick={()=>setDetails(d=>({...d,anaesType:o.val}))} style={{flex:1,padding:"14px 8px",fontSize:16,fontWeight:a?700:500,background:a?o.col.bg:"var(--bg2)",color:a?o.col.fg:"var(--text2)",border:a?`2px solid ${o.col.br}`:"0.5px solid var(--border)",borderRadius:12,cursor:"pointer"}}>{o.label}</button>;
          })}
        </div>
        {details.anaesType&&<p style={{fontSize:12,color:"var(--text3)",marginTop:6,textAlign:"center"}}>{details.anaesType} — refine in Case details</p>}
      </div>

      {!allDone?(
        <div style={{marginBottom:8}}>
          <SL>Tap to record</SL>
          {available.length===0&&<div style={{padding:18,background:"var(--bg2)",borderRadius:12,marginBottom:10,fontSize:15,color:"var(--text2)",textAlign:"center"}}>Waiting for prerequisites…</div>}
          {available.map(s=><StepCard key={s.key} step={s} onRecord={ts=>setTimes(t=>({...t,[s.key]:ts}))}/>)}
          {locked.map(s=>{const b=STEPS.find(x=>s.prereqs.includes(x.key)&&!times[x.key]);return<div key={s.key} style={{display:"flex",justifyContent:"space-between",alignItems:"center",padding:"13px 16px",marginBottom:8,background:"var(--bg2)",borderRadius:10}}><span style={{fontSize:15,color:"var(--text3)"}}>{s.label}</span>{b&&<span style={{fontSize:12,color:"var(--text3)",paddingLeft:8,textAlign:"right"}}>needs: {b.label.toLowerCase()}</span>}</div>;})}
        </div>
      ):(
        <div style={{marginBottom:20,textAlign:"center",padding:"12px 0 20px"}}>
          <p style={{fontSize:16,fontWeight:600,marginBottom:14,color:"var(--text)"}}>All timestamps recorded</p>
          <button onClick={onFinish} style={{width:"100%",padding:20,fontSize:18,fontWeight:700,background:"var(--green-bg)",color:"var(--green)",border:"2px solid var(--green-br)",borderRadius:14,cursor:"pointer"}}>Complete &amp; generate summary</button>
        </div>
      )}

      <div style={{borderTop:"0.5px solid var(--border)",paddingTop:20,marginTop:8}}>
        <SL>Medications{ga?" — GA protocol":""}</SL>
        {ga&&<div style={{marginBottom:10}}><MedCard med={MED_SODIUM} doses={medTimes[MED_SODIUM.key]||[]} onRecord={ts=>recMed(MED_SODIUM.key,ts)}/></div>}
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:10,marginBottom:10}}>
          {MEDS_BASE.slice(0,3).map(m=><MedCard key={m.key} med={m} doses={medTimes[m.key]||[]} onRecord={ts=>recMed(m.key,ts)}/>)}
        </div>
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:10,marginBottom:8}}>
          {MEDS_BASE.slice(3).map(m=><MedCard key={m.key} med={m} doses={medTimes[m.key]||[]} onRecord={ts=>recMed(m.key,ts)}/>)}
        </div>
        <p style={{fontSize:12,color:"var(--text3)",marginTop:4}}>Tap for current time · each dose recorded separately</p>
      </div>

      {recorded.length>0&&(
        <div style={{borderTop:"0.5px solid var(--border)",paddingTop:20,marginTop:20}}>
          <SL>Recorded</SL>
          <div style={{background:"var(--bg2)",borderRadius:12,overflow:"hidden"}}>
            {recorded.map((s,i)=>(
              <div key={s.key} style={{display:"flex",justifyContent:"space-between",alignItems:"center",padding:"14px 16px",borderBottom:i<recorded.length-1?"0.5px solid var(--border)":"none"}}>
                <span style={{fontSize:14,color:"var(--text2)"}}>{s.label}</span>
                <span style={{fontSize:16,fontWeight:700,color:"var(--text)",fontVariantNumeric:"tabular-nums"}}>{fmt(times[s.key])}</span>
              </div>
            ))}
          </div>
        </div>
      )}

      <div style={{borderTop:"0.5px solid var(--border)",paddingTop:20,marginTop:24,display:"flex",flexDirection:"column",gap:10}}>
        <button onClick={onEnd} style={{width:"100%",padding:16,fontSize:16,fontWeight:700,background:"var(--green-bg)",color:"var(--green)",border:"2px solid var(--green-br)",borderRadius:12,cursor:"pointer"}}>End case — save to logbook</button>
        <button onClick={()=>{if(confirm("Cancel this case? No data will be saved."))onCancel();}} style={{width:"100%",padding:14,fontSize:15,fontWeight:600,background:"var(--red-bg)",color:"var(--red)",border:"1.5px solid var(--red-br)",borderRadius:12,cursor:"pointer"}}>Cancel case</button>
      </div>
    </div>
  );
}

function DetailsTab({details,setDetails,times}){
  const upd=(k,v)=>setDetails(d=>({...d,[k]:v}));
  const[otherInd,setOtherInd]=useState(false);
  const ga=isGA(details.anaesType),spinal=details.anaesType&&!ga;
  const earliest=Object.values(times).filter(Boolean).sort()[0];
  const ooh=getOOH(earliest);
  const inp={width:"100%",padding:"13px 16px",fontSize:16,borderRadius:10,border:"0.5px solid var(--border)",background:"var(--bg)",color:"var(--text)"};

  const Sel=({label,active,onClick})=><button onClick={onClick} style={{textAlign:"left",padding:"14px 16px",fontSize:15,fontWeight:active?600:400,width:"100%",background:active?"var(--blue-bg)":"var(--bg)",color:active?"var(--blue)":"var(--text)",border:active?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer",marginBottom:8}}>{label}</button>;
  const YN=({k,yc})=>{
    const cols={blue:{bg:"var(--blue-bg)",fg:"var(--blue)",br:"var(--blue-br)"},amber:{bg:"var(--amber-bg)",fg:"var(--amber)",br:"var(--amber-br)"}};
    return<div style={{display:"flex",gap:10}}>{["Yes","No"].map(v=>{const a=details[k]===v;const c=v==="Yes"?(cols[yc||"blue"]):{bg:"var(--green-bg)",fg:"var(--green)",br:"var(--green-br)"};return<button key={v} onClick={()=>upd(k,a?"":v)} style={{flex:1,padding:"13px",fontSize:15,fontWeight:a?700:500,background:a?c.bg:"var(--bg)",color:a?c.fg:"var(--text)",border:a?`2px solid ${c.br}`:"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{v}</button>;})}</div>;
  };
  const Pills=({opts,k})=><div style={{display:"flex",gap:8,flexWrap:"wrap"}}>{opts.map(o=>{const a=details[k]===o;return<button key={o} onClick={()=>upd(k,a?"":o)} style={{padding:"11px 16px",fontSize:15,fontWeight:a?700:500,background:a?"var(--blue-bg)":"var(--bg)",color:a?"var(--blue)":"var(--text)",border:a?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{o}</button>;})}</div>;
  const Sec=({title,children})=><div style={{marginBottom:26}}><SL>{title}</SL>{children}</div>;
  function togBlock(t){const a=details.blockTypes||[];upd("blockTypes",a.includes(t)?a.filter(x=>x!==t):[...a,t]);}

  return(
    <div style={{padding:"0 18px 24px"}}>
      {ooh&&(
        <div style={{marginBottom:20,display:"flex",alignItems:"center",gap:10}}>
          <span style={{fontSize:14,color:"var(--text2)"}}>Session:</span>
          <span style={{padding:"6px 14px",fontSize:14,fontWeight:700,borderRadius:20,background:ooh==="OOH"?"var(--amber-bg)":"var(--green-bg)",color:ooh==="OOH"?"var(--amber)":"var(--green)",border:`1.5px solid ${ooh==="OOH"?"var(--amber-br)":"var(--green-br)"}`}}>{ooh}</span>
          {earliest&&<span style={{fontSize:13,color:"var(--text3)"}}>{new Date(earliest).toLocaleString("en-GB",{weekday:"short",hour:"2-digit",minute:"2-digit"})}</span>}
        </div>
      )}

      <Sec title="Patient">
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12}}>
          <div><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Age (years)</p><input type="number" min={14} max={60} value={details.age} onChange={e=>upd("age",e.target.value)} placeholder="e.g. 32" style={inp}/></div>
          <div><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>ASA grade</p><div style={{display:"flex",gap:6}}>{ASA_GRADES.map(g=>{const a=details.asa===g;return<button key={g} onClick={()=>upd("asa",a?"":g)} style={{flex:1,padding:"13px 4px",fontSize:15,fontWeight:a?700:500,background:a?"var(--blue-bg)":"var(--bg)",color:a?"var(--blue)":"var(--text)",border:a?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{g}</button>;})}</div></div>
        </div>
      </Sec>

      <Sec title="Category">{CATEGORIES.map(c=><Sel key={c} label={c} active={details.category===c} onClick={()=>upd("category",details.category===c?"":c)}/>)}</Sec>

      <Sec title="Indication">
        {!otherInd&&INDICATIONS.filter(i=>i!=="Other").map(i=><Sel key={i} label={i} active={details.indication===i} onClick={()=>upd("indication",details.indication===i?"":i)}/>)}
        {!otherInd&&<Sel label="Other" active={false} onClick={()=>{setOtherInd(true);upd("indication","");}}/>}
        {otherInd&&<><input autoFocus value={details.indication} onChange={e=>upd("indication",e.target.value)} placeholder="Specify indication…" style={{...inp,marginBottom:10}}/><button onClick={()=>{setOtherInd(false);upd("indication","");}} style={{fontSize:14,color:"var(--text2)",background:"none",border:"none",cursor:"pointer",padding:0}}>Back to list</button></>}
      </Sec>

      <Sec title="Anaesthesia">{ANAESTHESIA.map(a=><Sel key={a} label={a} active={details.anaesType===a} onClick={()=>upd("anaesType",details.anaesType===a?"":a)}/>)}</Sec>

      {spinal&&<Sec title="Spinal needle level"><Pills opts={SPINAL_LEVELS} k="spinalLevel"/></Sec>}

      {spinal&&(
        <Sec title="Local anaesthetic — primary block">
          <LASection types={LA_PRIMARY} typeKey="primaryLAType" concKey="primaryLAConc" volKey="primaryLAVol" details={details} upd={upd} inp={inp}/>
          <p style={{fontSize:13,color:"var(--text2)",margin:"14px 0 8px"}}>Route</p>
          <div style={{display:"flex",gap:10}}>{["Intrathecal","Epidural"].map(v=>{const a=details.primaryLARoute===v;return<button key={v} onClick={()=>upd("primaryLARoute",a?"":v)} style={{flex:1,padding:"13px",fontSize:15,fontWeight:a?700:500,background:a?"var(--blue-bg)":"var(--bg)",color:a?"var(--blue)":"var(--text)",border:a?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{v}</button>;})}</div>
        </Sec>
      )}

      {spinal&&(
        <Sec title="Adjuvant / additive">
          <p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Type</p>
          <div style={{display:"flex",flexWrap:"wrap",gap:8,marginBottom:14}}>{ADJUVANTS.map(t=>{const a=details.adjuvantType===t;return<button key={t} onClick={()=>upd("adjuvantType",a?"":t)} style={{padding:"10px 14px",fontSize:14,fontWeight:a?600:400,background:a?"var(--blue-bg)":"var(--bg)",color:a?"var(--blue)":"var(--text)",border:a?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{t}</button>;})}</div>
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12,marginBottom:14}}>
            <div><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Concentration</p><input value={details.adjuvantConc} onChange={e=>upd("adjuvantConc",e.target.value)} placeholder="e.g. 300mcg" style={inp}/></div>
            <div><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Volume (ml)</p><input type="number" min={0} max={20} value={details.adjuvantVol} onChange={e=>upd("adjuvantVol",e.target.value)} placeholder="e.g. 1" style={inp}/></div>
          </div>
          <p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Route</p>
          <div style={{display:"flex",gap:10}}>{["Intrathecal","Epidural"].map(v=>{const a=details.adjuvantRoute===v;return<button key={v} onClick={()=>upd("adjuvantRoute",a?"":v)} style={{flex:1,padding:"13px",fontSize:15,fontWeight:a?700:500,background:a?"var(--blue-bg)":"var(--bg)",color:a?"var(--blue)":"var(--text)",border:a?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{v}</button>;})}</div>
        </Sec>
      )}

      {ga&&<Sec title="Conversion from regional to GA"><YN k="conversion" yc="amber"/></Sec>}

      {ga&&(
        <Sec title="Airway assessment">
          <p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Mallampati</p><Pills opts={MALLAMPATI} k="mallampati"/>
          <p style={{fontSize:13,color:"var(--text2)",margin:"14px 0 8px"}}>Cormack–Lehane grade</p><Pills opts={CL_GRADES} k="clGrade"/>
        </Sec>
      )}

      {ga&&(
        <Sec title="Regional block (post-op analgesia)">
          <YN k="regionalBlock" yc="blue"/>
          {details.regionalBlock==="Yes"&&(
            <div style={{marginTop:14}}>
              <p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>Block type</p>
              <div style={{display:"flex",flexDirection:"column",gap:8,marginBottom:14}}>{BLOCK_TYPES.map(t=>{const s=(details.blockTypes||[]).includes(t);return<button key={t} onClick={()=>togBlock(t)} style={{textAlign:"left",padding:"13px 16px",fontSize:15,fontWeight:s?600:400,background:s?"var(--blue-bg)":"var(--bg)",color:s?"var(--blue)":"var(--text)",border:s?"2px solid var(--blue-br)":"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>{t}</button>;})}</div>
              <p style={{fontSize:13,color:"var(--text2)",marginBottom:10}}>Local anaesthetic</p>
              <LASection types={LA_BLOCK} typeKey="blockLAType" concKey="blockLAConc" volKey="blockLAVol" details={details} upd={upd} inp={inp}/>
              <p style={{fontSize:13,color:"var(--text2)",margin:"14px 0 8px"}}>Ultrasound guided</p>
              <YN k="blockUS" yc="blue"/>
            </div>
          )}
        </Sec>
      )}

      <Sec title="Apgar scores">
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12}}>
          {[["apgar1","1 minute"],["apgar5","5 minutes"]].map(([k,l])=>(
            <div key={k}><p style={{fontSize:13,color:"var(--text2)",marginBottom:8}}>{l}</p><input type="number" min={0} max={10} value={details[k]} onChange={e=>upd(k,e.target.value)} placeholder="0–10" style={inp}/></div>
          ))}
        </div>
      </Sec>

      <Sec title="PPH classification">{PPH_OPTS.map(p=><Sel key={p} label={p} active={details.pph===p} onClick={()=>upd("pph",details.pph===p?"":p)}/>)}</Sec>
      <Sec title="Estimated blood loss"><input type="number" value={details.ebl} onChange={e=>upd("ebl",e.target.value)} placeholder="ml (e.g. 500)" style={inp}/></Sec>
    </div>
  );
}

function EndSummary({times,caseNo,onHome}){
  const label=`CS-${String(caseNo).padStart(3,"0")}`;
  const earliest=Object.values(times).filter(Boolean).sort()[0];
  const ddi=secs(times.tAlerted,times.tBaby);
  const breach=ddi!==null&&ddi>1800;
  const steps=STEPS.filter(s=>SUMMARY_KEYS.includes(s.key)&&times[s.key]).sort((a,b)=>times[a.key]-times[b.key]);
  return(
    <div style={{padding:"24px 20px 40px"}}>
      <div style={{textAlign:"center",marginBottom:32}}>
        <div style={{fontSize:56,marginBottom:8}}>👶</div>
        <h2 style={{fontSize:22,fontWeight:700,marginBottom:4}}>Case saved</h2>
        <p style={{fontSize:15,color:"var(--text2)"}}>{label} · {fmtDate(earliest)}</p>
      </div>
      {ddi!==null&&(
        <div style={{padding:"16px 20px",borderRadius:14,marginBottom:20,background:breach?"var(--red-bg)":"var(--green-bg)",border:`1.5px solid ${breach?"var(--red-br)":"var(--green-br)"}`}}>
          <p style={{fontSize:13,fontWeight:600,textTransform:"uppercase",letterSpacing:"0.06em",color:breach?"var(--red)":"var(--green)",marginBottom:4}}>Alert to delivery</p>
          <p style={{fontSize:26,fontWeight:700,color:breach?"var(--red)":"var(--green)",fontVariantNumeric:"tabular-nums",margin:0}}>{mins(ddi)}</p>
          {breach&&<p style={{fontSize:13,color:"var(--red)",marginTop:4}}>Exceeds 30-minute Cat 1 target</p>}
        </div>
      )}
      <div style={{background:"var(--bg2)",borderRadius:14,overflow:"hidden",marginBottom:28}}>
        <div style={{padding:"12px 16px 6px"}}><SL>Timeline</SL></div>
        {steps.map((s,i)=>{
          const baby=s.key==="tBaby";
          return(
            <div key={s.key} style={{display:"flex",alignItems:"center",padding:"13px 16px",borderBottom:i<steps.length-1?"0.5px solid var(--border)":"none",background:baby?"var(--pink-bg)":"transparent"}}>
              <div style={{width:8,height:8,borderRadius:"50%",flexShrink:0,marginRight:12,background:baby?"var(--pink)":"var(--blue)"}}/>
              <span style={{flex:1,fontSize:14,fontWeight:baby?600:400,color:baby?"var(--pink)":"var(--text2)"}}>{s.label}</span>
              <span style={{fontSize:15,fontWeight:700,fontVariantNumeric:"tabular-nums",color:baby?"var(--pink)":"var(--text)"}}>{fmt(times[s.key])}</span>
            </div>
          );
        })}
      </div>
      <button onClick={onHome} style={{width:"100%",padding:18,fontSize:17,fontWeight:700,background:"var(--pink-bg)",color:"var(--pink)",border:"2px solid var(--pink-br)",borderRadius:14,cursor:"pointer"}}>Back to home</button>
    </div>
  );
}

function Summary({times,medTimes,details,caseNo,onReset,onCases}){
  const[copied,setCopied]=useState(false);
  const ddi=secs(times.tAlerted,times.tBaby),d2s=secs(times.tAlerted,times.tSkin);
  const ind=secs(times.tAnaesStart,times.tReady),surg=secs(times.tSkin,times.tClosed);
  const tot=secs(times.tPatientTheatre,times.tLeft);
  const isCat1=details.category===CATEGORIES[0],alert=isCat1&&ddi!==null&&ddi>1800;
  const earliest=Object.values(times).filter(Boolean).sort()[0];
  const caseDate=fmtDate(earliest),label=`CS-${String(caseNo).padStart(3,"0")}`;
  const ga=isGA(details.anaesType),ooh=getOOH(earliest);
  const allMeds=ga?[...MEDS_BASE,MED_SODIUM]:[...MEDS_BASE];
  const allRec=[...STEPS.filter(s=>times[s.key]).map(s=>({label:s.label,ts:times[s.key]})),...allMeds.flatMap(m=>(medTimes[m.key]||[]).map((t,i)=>({label:`${m.label}${(medTimes[m.key]||[]).length>1?` (dose ${i+1})`:""}`,ts:t})))].sort((a,b)=>a.ts-b.ts);
  const medLines=allMeds.map(m=>{const ts=medTimes[m.key]||[];return ts.length?`${m.label}: ${ts.map(t=>fmt(t)).join(", ")}`:null;}).filter(Boolean);
  const pLA=details.primaryLAType?`${details.primaryLAType}${details.primaryLAConc?" "+details.primaryLAConc+"%":""}${details.primaryLAVol?" — "+details.primaryLAVol+"ml":""}${details.primaryLARoute?" ("+details.primaryLARoute+")":""}`:null;
  const adj=details.adjuvantType?`${details.adjuvantType}${details.adjuvantConc?" "+details.adjuvantConc:""}${details.adjuvantVol?" — "+details.adjuvantVol+"ml":""}${details.adjuvantRoute?" ("+details.adjuvantRoute+")":""}`:null;
  const bLA=details.blockLAType?`${details.blockLAType}${details.blockLAConc?" "+details.blockLAConc+"%":""}${details.blockLAVol?" — "+details.blockLAVol+"ml":""}`:null;
  const txt=["EMERGENCY CAESAREAN SECTION — PROCEDURE RECORD",`Case: ${label}`,`Date: ${caseDate}`,ooh?`Session: ${ooh}`:null,`Category: ${details.category||"—"}`,`Indication: ${details.indication||"—"}`,`Age: ${details.age||"—"}    ASA: ${details.asa||"—"}`,`Anaesthesia: ${details.anaesType||"—"}`,details.spinalLevel?`Spinal level: ${details.spinalLevel}`:null,pLA?`Primary LA: ${pLA}`:null,adj?`Adjuvant: ${adj}`:null,details.conversion?`Conversion to GA: ${details.conversion}`:null,details.mallampati?`Mallampati: ${details.mallampati}`:null,details.clGrade?`Cormack-Lehane: ${details.clGrade}`:null,details.regionalBlock?`Regional block: ${details.regionalBlock}`:null,details.regionalBlock==="Yes"&&(details.blockTypes||[]).length?`Block type: ${details.blockTypes.join(", ")}`:null,bLA?`Block LA: ${bLA}`:null,details.blockUS?`Ultrasound: ${details.blockUS}`:null,"","TIMESTAMPS (chronological)",...allRec.map(r=>`${r.label.padEnd(42)}${fmt(r.ts)}`),"", ...(medLines.length?["MEDICATIONS",...medLines,""]:[]),`Apgar 1 min: ${details.apgar1||"—"}    Apgar 5 min: ${details.apgar5||"—"}`,`PPH: ${details.pph||"—"}`,`EBL: ${details.ebl?`${details.ebl} ml`:"—"}`,"","KEY INTERVALS",`Alert-to-delivery:            ${mins(ddi)}`,`Alert-to-knife-to-skin:       ${mins(d2s)}`,`Anaesthesia induction time:   ${mins(ind)}`,`Surgical time:                ${mins(surg)}`,`Total theatre time:           ${mins(tot)}`].filter(l=>l!==null).join("\n");
  const Row=({label:l,val})=>(<div style={{display:"flex",justifyContent:"space-between",alignItems:"center",padding:"13px 16px",borderBottom:"0.5px solid var(--border)"}}><span style={{fontSize:14,color:"var(--text2)"}}>{l}</span><span style={{fontSize:14,fontWeight:700,fontVariantNumeric:"tabular-nums",color:val&&val!=="—"?"var(--text)":"var(--text3)"}}>{val||"—"}</span></div>);
  return(
    <div style={{padding:"18px 18px 40px"}}>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-start",marginBottom:22}}>
        <div><h2 style={{fontSize:22,fontWeight:700,marginBottom:2}}>Case complete</h2><div style={{display:"flex",alignItems:"center",gap:8}}><p style={{fontSize:15,color:"var(--text2)"}}>{label} · {caseDate}</p>{ooh&&<span style={{padding:"3px 10px",fontSize:12,fontWeight:700,borderRadius:20,background:ooh==="OOH"?"var(--amber-bg)":"var(--green-bg)",color:ooh==="OOH"?"var(--amber)":"var(--green)"}}>{ooh}</span>}</div></div>
        <button onClick={onCases} style={{fontSize:13,fontWeight:600,color:"var(--blue)",background:"transparent",border:"none",cursor:"pointer",marginTop:4}}>All cases</button>
      </div>
      {alert&&<div style={{padding:"14px 18px",background:"var(--red-bg)",border:"1.5px solid var(--red-br)",borderRadius:12,marginBottom:18}}><p style={{fontSize:15,color:"var(--red)",fontWeight:700,margin:0}}>DDI {mins(ddi)} — exceeds 30-minute target for Cat 1</p></div>}
      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12,marginBottom:20}}>
        {[["DDI",mins(ddi)],["Induction",mins(ind)],["Surgical",mins(surg)],["Total theatre",mins(tot)]].map(([l,v])=>(<div key={l} style={{background:"var(--bg2)",borderRadius:12,padding:"14px 16px"}}><p style={{fontSize:12,color:"var(--text2)",marginBottom:4}}>{l}</p><p style={{fontSize:22,fontWeight:700,fontVariantNumeric:"tabular-nums",margin:0}}>{v}</p></div>))}
      </div>
      <div style={{background:"var(--bg2)",borderRadius:14,overflow:"hidden",marginBottom:14}}>
        <div style={{padding:"12px 16px 4px"}}><SL>Timeline</SL></div>
        {allRec.map((r,i)=><Row key={i} label={r.label} val={fmt(r.ts)}/>)}
      </div>
      <div style={{background:"var(--bg2)",borderRadius:14,overflow:"hidden",marginBottom:24}}>
        <div style={{padding:"12px 16px 4px"}}><SL>Clinical details</SL></div>
        <Row label="Category" val={details.category}/><Row label="Indication" val={details.indication}/><Row label="Age" val={details.age?`${details.age} yrs`:null}/><Row label="ASA" val={details.asa}/><Row label="Anaesthesia" val={details.anaesType}/>
        {details.spinalLevel&&<Row label="Spinal level" val={details.spinalLevel}/>}
        {pLA&&<Row label="Primary LA" val={pLA}/>}
        {adj&&<Row label="Adjuvant" val={adj}/>}
        {details.conversion&&<Row label="Conversion" val={details.conversion}/>}
        {details.mallampati&&<Row label="Mallampati" val={details.mallampati}/>}
        {details.clGrade&&<Row label="Cormack-Lehane" val={details.clGrade}/>}
        {details.regionalBlock&&<Row label="Regional block" val={details.regionalBlock}/>}
        {(details.blockTypes||[]).length>0&&<Row label="Block type" val={details.blockTypes.join(", ")}/>}
        {bLA&&<Row label="Block LA" val={bLA}/>}
        {details.blockUS&&<Row label="Ultrasound" val={details.blockUS}/>}
        <Row label="Apgar 1 / 5 min" val={`${details.apgar1||"—"} / ${details.apgar5||"—"}`}/>
        <Row label="PPH" val={details.pph}/><Row label="EBL" val={details.ebl?`${details.ebl} ml`:null}/>
      </div>
      <div style={{display:"flex",flexDirection:"column",gap:12}}>
        <button onClick={()=>{navigator.clipboard.writeText(txt);setCopied(true);setTimeout(()=>setCopied(false),2500);}} style={{padding:16,fontSize:16,fontWeight:700,background:"var(--blue-bg)",color:"var(--blue)",border:"2px solid var(--blue-br)",borderRadius:12,cursor:"pointer"}}>{copied?"Copied!":"Copy clinical summary"}</button>
        <button onClick={onReset} style={{padding:16,fontSize:16,fontWeight:700,background:"var(--pink-bg)",color:"var(--pink)",border:"2px solid var(--pink-br)",borderRadius:12,cursor:"pointer"}}>Back to home</button>
      </div>
    </div>
  );
}

function HomeView({onStart,onCases,onAbout,caseLabel}){
  const[clock,setClock]=useState(new Date());
  useEffect(()=>{const t=setInterval(()=>setClock(new Date()),1000);return()=>clearInterval(t);},[]);
  const h=clock.getHours();
  const greeting=h<12?"Good morning":h<17?"Good afternoon":"Good evening";
  const ooh=getOOH(Date.now());
  return(
    <div style={{minHeight:"100vh",display:"flex",flexDirection:"column"}}>

      {/* Hero */}
      <div style={{background:"linear-gradient(160deg,#fce7f3 0%,#ede9fe 60%,#dbeafe 100%)",padding:"48px 28px 40px",position:"relative",overflow:"hidden"}}>
        {/* decorative circles */}
        <div style={{position:"absolute",top:-40,right:-40,width:180,height:180,borderRadius:"50%",background:"rgba(219,39,119,0.08)",pointerEvents:"none"}}/>
        <div style={{position:"absolute",bottom:-20,left:-30,width:120,height:120,borderRadius:"50%",background:"rgba(124,58,237,0.07)",pointerEvents:"none"}}/>

        <div style={{position:"relative"}}>
          <p style={{fontSize:14,fontWeight:600,color:"#9d174d",marginBottom:20,letterSpacing:"0.04em"}}>{greeting}</p>
          <div style={{fontSize:72,lineHeight:1,marginBottom:16}}>👶</div>
          <h1 style={{fontSize:36,fontWeight:800,letterSpacing:"-0.03em",color:"#111",marginBottom:6,lineHeight:1.1}}>Baby<br/>Time</h1>
          <p style={{fontSize:15,color:"#6b7280",marginTop:8}}>Emergency CS anaesthetic logbook</p>
        </div>

        <div style={{display:"flex",gap:8,marginTop:24,position:"relative"}}>
          <div style={{padding:"8px 14px",borderRadius:20,background:"rgba(255,255,255,0.7)",backdropFilter:"blur(8px)",display:"inline-flex",alignItems:"center",gap:6}}>
            <span style={{fontSize:13,fontWeight:700,color:"#374151",fontVariantNumeric:"tabular-nums"}}>{clock.toLocaleTimeString("en-GB",{hour:"2-digit",minute:"2-digit"})}</span>
          </div>
          <div style={{padding:"8px 14px",borderRadius:20,background:"rgba(255,255,255,0.7)",backdropFilter:"blur(8px)",display:"inline-flex",alignItems:"center",gap:6}}>
            <span style={{width:7,height:7,borderRadius:"50%",background:ooh==="OOH"?"#d97706":"#16a34a",display:"inline-block"}}/>
            <span style={{fontSize:13,fontWeight:700,color:"#374151"}}>{ooh||"—"}</span>
          </div>
          <div style={{padding:"8px 14px",borderRadius:20,background:"rgba(255,255,255,0.7)",backdropFilter:"blur(8px)",display:"inline-flex",alignItems:"center",gap:6}}>
            <span style={{fontSize:13,fontWeight:700,color:"#374151"}}>{caseLabel}</span>
          </div>
        </div>
      </div>

      {/* Actions */}
      <div style={{padding:"24px 20px",flex:1,display:"flex",flexDirection:"column",gap:14}}>
        <button onClick={onStart} style={{width:"100%",padding:"0",background:"#db2777",border:"none",borderRadius:20,cursor:"pointer",overflow:"hidden",boxShadow:"0 4px 24px rgba(219,39,119,0.25)"}}>
          <div style={{padding:"22px 24px",display:"flex",alignItems:"center",gap:16}}>
            <div style={{width:48,height:48,borderRadius:14,background:"rgba(255,255,255,0.2)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:22,flexShrink:0}}>🚨</div>
            <div style={{textAlign:"left",flex:1}}>
              <p style={{fontSize:18,fontWeight:800,color:"#fff",margin:0,letterSpacing:"-0.01em"}}>Start new case</p>
              <p style={{fontSize:13,color:"rgba(255,255,255,0.75)",margin:"2px 0 0"}}>Records anaesthetist alerted now</p>
            </div>
            <span style={{fontSize:20,color:"rgba(255,255,255,0.6)"}}>→</span>
          </div>
        </button>

        <button onClick={onCases} style={{width:"100%",padding:"0",background:"var(--bg)",border:"1.5px solid var(--border)",borderRadius:20,cursor:"pointer",overflow:"hidden"}}>
          <div style={{padding:"20px 24px",display:"flex",alignItems:"center",gap:16}}>
            <div style={{width:48,height:48,borderRadius:14,background:"var(--blue-bg)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:22,flexShrink:0}}>📋</div>
            <div style={{textAlign:"left",flex:1}}>
              <p style={{fontSize:17,fontWeight:700,color:"var(--text)",margin:0}}>Review cases</p>
              <p style={{fontSize:13,color:"var(--text3)",margin:"2px 0 0"}}>Logbook &amp; CSV export</p>
            </div>
            <span style={{fontSize:18,color:"var(--text3)"}}>→</span>
          </div>
        </button>
      </div>

      {/* Footer */}
      <div style={{padding:"0 20px 36px",textAlign:"center"}}>
        <p style={{fontSize:12,color:"var(--text3)",marginBottom:3}}>Created by Christopher McKee</p>
        <a href="mailto:christopher.mckee8@nhs.net" style={{fontSize:12,color:"var(--blue)",textDecoration:"none",display:"block",marginBottom:10}}>christopher.mckee8@nhs.net</a>
        <button onClick={onAbout} style={{fontSize:12,color:"var(--text3)",background:"transparent",border:"none",cursor:"pointer",textDecoration:"underline"}}>About &amp; disclaimer</button>
      </div>
    </div>
  );
}

function AboutView({onBack}){
  return(
    <div style={{padding:"0 24px 48px"}}>
      <div style={{display:"flex",alignItems:"center",padding:"16px 0 24px"}}>
        <button onClick={onBack} style={{fontSize:15,fontWeight:600,color:"var(--blue)",background:"transparent",border:"none",cursor:"pointer",padding:0}}>← Back</button>
      </div>
      <div style={{textAlign:"center",marginBottom:32}}>
        <div style={{fontSize:64,marginBottom:10,lineHeight:1}}>👶</div>
        <h1 style={{fontSize:24,fontWeight:700,marginBottom:4}}>Baby Time</h1>
        <p style={{fontSize:14,color:"var(--text3)"}}>Emergency CS Anaesthetic Logbook</p>
      </div>
      {[
        {title:"About",bg:"var(--bg2)",border:null,body:"Baby Time is a clinical audit tool for obstetric anaesthetists, designed to capture procedural timestamps and case details during emergency caesarean sections. It records the sequence of events from anaesthetist alert through to patient leaving theatre, calculates key intervals including decision-to-delivery, and exports data for logbook and departmental audit use. No patient-identifiable information is stored. All data remains on your device and is never transmitted to any server."},
        {title:"Created by",bg:"var(--bg2)",border:null,custom:true},
        {title:"Important notice",bg:"var(--amber-bg)",border:"1px solid var(--amber-br)",body:"This app is an audit tool only and does not constitute medical advice or clinical decision support. Timestamps are recorded manually by the user and may not reflect exact clinical events. This app has not been validated as a medical device and should not be used as the primary or sole source of clinical documentation. All cases must be documented through your trust's standard clinical records system. The developer accepts no liability for clinical decisions made on the basis of data recorded within this application."},
        {title:"Data & privacy",bg:"var(--bg2)",border:null,body:"This app stores case data locally on your device using browser storage. No data is transmitted to any external server, cloud service, or third party. No patient-identifiable information is collected or stored. You should not enter patient names, dates of birth, NHS numbers, or any other identifying information into this app. Clearing your browser or app data will permanently delete all saved cases — export your logbook regularly to avoid data loss."},
      ].map(s=>(
        <div key={s.title} style={{marginBottom:24}}>
          <SL>{s.title}</SL>
          <div style={{background:s.bg,border:s.border||"none",borderRadius:14,padding:"18px 20px",fontSize:15,lineHeight:1.7,color:"var(--text2)"}}>
            {s.custom?(
              <>
                <p style={{fontSize:16,fontWeight:600,marginBottom:4,color:"var(--text)"}}>Christopher McKee</p>
                <a href="mailto:christopher.mckee8@nhs.net" style={{fontSize:15,color:"var(--blue)",textDecoration:"none"}}>christopher.mckee8@nhs.net</a>
                <p style={{fontSize:14,color:"var(--text3)",marginTop:8}}>Feedback, suggestions, and bug reports are welcome.</p>
              </>
            ):s.body}
          </div>
        </div>
      ))}
    </div>
  );
}

function CasesView({onBack}){
  const[cases,setCases]           =useState(()=>loadCases().sort((a,b)=>b.caseNo-a.caseNo));
  const[confirmAll,setConfirmAll] =useState(false);

  function doExport(){if(!cases.length){alert("No cases saved yet.");return;}dlCSV(cases,"BabyTime_logbook.csv");}
  function delOne(no){
    if(!confirm(`Delete CS-${String(no).padStart(3,"0")}? This cannot be undone.`))return;
    const u=loadCases().filter(c=>c.caseNo!==no);saveCases(u);setCases(u.sort((a,b)=>b.caseNo-a.caseNo));
  }
  function delAll(){saveCases([]);setCases([]);setConfirmAll(false);}

  const dot=cat=>{if(!cat)return"var(--text3)";if(cat.startsWith("Cat 1"))return"var(--red)";if(cat.startsWith("Cat 2"))return"var(--amber)";if(cat.startsWith("Cat 3"))return"var(--blue)";return"var(--green)";};

  return(
    <div style={{paddingBottom:48}}>
      <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"16px 18px"}}>
        <button onClick={onBack} style={{fontSize:15,fontWeight:600,color:"var(--blue)",background:"transparent",border:"none",cursor:"pointer",padding:0}}>← Home</button>
        <span style={{fontSize:16,fontWeight:700}}>All cases</span>
        <button onClick={doExport} style={{fontSize:14,fontWeight:700,color:"var(--green)",background:"var(--green-bg)",border:"1.5px solid var(--green-br)",borderRadius:8,padding:"7px 14px",cursor:"pointer"}}>Export CSV</button>
      </div>

      {!cases.length?(
        <div style={{padding:"60px 18px",textAlign:"center",color:"var(--text3)"}}>
          <p style={{fontSize:16,marginBottom:8}}>No cases recorded yet</p>
          <p style={{fontSize:14}}>Completed cases will appear here</p>
        </div>
      ):(
        <div style={{padding:"0 18px"}}>
          <p style={{fontSize:13,color:"var(--text3)",marginBottom:14}}>{cases.length} case{cases.length!==1?"s":""} saved · no patient identifiers stored</p>

          {cases.map(c=>{
            const e=Object.values(c.times).filter(Boolean).sort()[0];
            const ddi=secs(c.times.tAlerted,c.times.tBaby);
            const breach=c.details.category===CATEGORIES[0]&&ddi!==null&&ddi>1800;
            const ooh=getOOH(e);
            return(
              <div key={c.caseNo} style={{background:"var(--bg2)",borderRadius:14,marginBottom:12,overflow:"hidden"}}>
                <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"14px 16px 10px"}}>
                  <div style={{display:"flex",alignItems:"center",gap:10,flexWrap:"wrap"}}>
                    <span style={{width:10,height:10,borderRadius:"50%",background:dot(c.details.category),flexShrink:0,display:"inline-block"}}/>
                    <span style={{fontSize:16,fontWeight:700}}>CS-{String(c.caseNo).padStart(3,"0")}</span>
                    <span style={{fontSize:13,color:"var(--text2)"}}>{fmtDate(e)}</span>
                    {ooh&&<span style={{fontSize:11,fontWeight:700,padding:"2px 8px",borderRadius:20,background:ooh==="OOH"?"var(--amber-bg)":"var(--green-bg)",color:ooh==="OOH"?"var(--amber)":"var(--green)"}}>{ooh}</span>}
                  </div>
                  <button onClick={()=>delOne(c.caseNo)} style={{fontSize:12,color:"var(--red)",background:"transparent",border:"none",cursor:"pointer",padding:"2px 6px"}}>Delete</button>
                </div>
                <div style={{padding:"0 16px 14px",display:"grid",gridTemplateColumns:"1fr 1fr",gap:"4px 16px"}}>
                  <p style={{fontSize:13,color:"var(--text2)",margin:0}}>{c.details.category?c.details.category.slice(0,5):"—"}</p>
                  <p style={{fontSize:13,color:"var(--text2)",margin:0}}>{c.details.anaesType||"—"}</p>
                  <p style={{fontSize:13,color:"var(--text2)",margin:0,gridColumn:"1/-1",overflow:"hidden",textOverflow:"ellipsis",whiteSpace:"nowrap"}}>{c.details.indication||"No indication recorded"}</p>
                  <div style={{gridColumn:"1/-1",display:"flex",gap:12,marginTop:6}}>
                    <span style={{fontSize:13,fontWeight:700,color:breach?"var(--red)":"var(--text)"}}>DDI: {mins(ddi)}{breach?" ⚠":""}</span>
                    <span style={{fontSize:13,color:"var(--text2)"}}>Surgical: {mins(secs(c.times.tSkin,c.times.tClosed))}</span>
                  </div>
                </div>
              </div>
            );
          })}

          <div style={{marginTop:8,paddingBottom:8}}>
            {!confirmAll?(
              <button onClick={()=>setConfirmAll(true)} style={{width:"100%",padding:14,fontSize:15,fontWeight:600,background:"transparent",color:"var(--red)",border:"1.5px solid var(--red-br)",borderRadius:12,cursor:"pointer"}}>
                Delete all cases
              </button>
            ):(
              <div style={{background:"var(--red-bg)",border:"1.5px solid var(--red-br)",borderRadius:12,padding:"18px 20px"}}>
                <p style={{fontSize:15,fontWeight:600,color:"var(--red)",marginBottom:4}}>Delete all cases?</p>
                <p style={{fontSize:14,color:"var(--text2)",marginBottom:16}}>This cannot be undone. Export your CSV first if you want to keep the data.</p>
                <div style={{display:"flex",gap:10}}>
                  <button onClick={delAll} style={{flex:1,padding:14,fontSize:15,fontWeight:700,background:"var(--red)",color:"#fff",border:"none",borderRadius:10,cursor:"pointer"}}>Yes, delete all</button>
                  <button onClick={()=>setConfirmAll(false)} style={{flex:1,padding:14,fontSize:15,fontWeight:600,background:"var(--bg)",color:"var(--text)",border:"0.5px solid var(--border)",borderRadius:10,cursor:"pointer"}}>Cancel</button>
                </div>
              </div>
            )}
          </div>
        </div>
      )}
    </div>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App/>);
</script>
</body>
</html>

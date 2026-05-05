!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>EndoEase — Endometriosis Companion</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&display=swap" rel="stylesheet"/>
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --rose:#C94B7B;--rose-light:#FBEAF0;--rose-mid:#F4C0D1;--rose-dark:#4B1528;
  --teal:#1D9E75;--teal-light:#E1F5EE;--teal-dark:#085041;
  --amber:#BA7517;--amber-light:#FAEEDA;
  --purple:#7F77DD;--purple-light:#EEEDFE;
  --blue:#378ADD;--blue-light:#E6F1FB;
  --coral:#D85A30;--coral-light:#FAECE7;
  --green:#3B6D11;--green-light:#EAF3DE;
  --bg:#FAFAF9;--card:#FFFFFF;--border:#E8E4E0;
  --text:#1A1A1A;--text2:#6B6560;--text3:#A09890;
  --shadow:0 1px 3px rgba(0,0,0,0.06),0 4px 16px rgba(0,0,0,0.04);
}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);min-height:100vh}

/* LAYOUT */
.app-shell{display:flex;height:100vh;overflow:hidden}
.sidebar{width:220px;background:var(--card);border-right:1px solid var(--border);display:flex;flex-direction:column;flex-shrink:0}
.main{flex:1;overflow-y:auto}

/* SIDEBAR */
.brand{padding:20px 20px 16px;border-bottom:1px solid var(--border)}
.logo-row{display:flex;align-items:center;gap:10px;margin-bottom:4px}
.logo-mark{width:32px;height:32px;background:var(--rose);border-radius:50%;display:flex;align-items:center;justify-content:center}
.logo-inner{width:13px;height:13px;border:2.5px solid white;border-radius:50%}
.brand-name{font-family:'DM Serif Display',serif;font-size:20px;color:var(--text)}
.brand-name em{font-style:italic;color:var(--rose)}
.brand-sub{font-size:11px;color:var(--text3)}
.nav-list{padding:12px 10px;flex:1}
.nav-item{display:flex;align-items:center;gap:10px;padding:9px 12px;border-radius:8px;cursor:pointer;margin-bottom:2px;font-size:13px;color:var(--text2);transition:all 0.15s;border:none;background:none;width:100%;text-align:left;font-family:'DM Sans',sans-serif}
.nav-item:hover{background:#F5F1EE;color:var(--text)}
.nav-item.active{background:var(--rose-light);color:var(--rose);font-weight:500}
.nav-icon{font-size:16px;width:20px;text-align:center}
.sidebar-footer{padding:14px 16px;border-top:1px solid var(--border);font-size:11px;color:var(--text3);line-height:1.6}
.cycle-badge{background:var(--rose-light);color:var(--rose);padding:4px 10px;border-radius:20px;font-size:12px;font-weight:500;display:inline-block;margin-bottom:6px}

/* MAIN CONTENT */
.page{display:none;padding:28px 32px;max-width:900px}
.page.active{display:block}
.page-header{margin-bottom:24px}
.page-title{font-family:'DM Serif Display',serif;font-size:26px;color:var(--text);margin-bottom:4px}
.page-sub{font-size:14px;color:var(--text2)}

/* CARDS */
.card{background:var(--card);border:1px solid var(--border);border-radius:14px;padding:20px;box-shadow:var(--shadow)}
.card-sm{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:14px}

/* GRID */
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px}
.grid-4{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}

/* TRACKER */
.param-label{font-size:11px;font-weight:600;letter-spacing:0.6px;text-transform:uppercase;color:var(--text3);margin-bottom:10px}
.dot-row{display:flex;gap:6px;flex-wrap:wrap}
.dot{width:34px;height:34px;border-radius:50%;border:1.5px solid var(--border);cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:12px;color:var(--text3);transition:all 0.15s;font-weight:500}
.dot:hover{border-color:var(--rose);color:var(--rose)}
.dot.sel-rose{background:var(--rose);border-color:var(--rose);color:white}
.dot.sel-teal{background:var(--teal);border-color:var(--teal);color:white}
.dot.sel-purple{background:var(--purple);border-color:var(--purple);color:white}
.dot.sel-amber{background:var(--amber);border-color:var(--amber);color:white}
.dot.sel-blue{background:var(--blue);border-color:var(--blue);color:white}

/* SLIDER */
.slider-group{margin-bottom:14px}
.slider-row{display:flex;align-items:center;gap:12px}
.slider-label{font-size:13px;color:var(--text2);min-width:110px}
input[type=range]{flex:1;accent-color:var(--rose);height:4px;border-radius:4px;cursor:pointer}
.slider-val{font-size:14px;font-weight:500;color:var(--text);min-width:20px;text-align:right}

/* BUTTONS */
.btn{padding:10px 20px;border-radius:8px;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:500;cursor:pointer;transition:all 0.15s;border:none}
.btn-primary{background:var(--rose);color:white}
.btn-primary:hover{background:#B5436E}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--text2)}
.btn-outline:hover{border-color:var(--rose);color:var(--rose)}
.btn-full{width:100%}
.btn-sm{padding:6px 12px;font-size:12px}

/* TAGS & BADGES */
.badge{display:inline-flex;align-items:center;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:500}
.badge-rose{background:var(--rose-light);color:var(--rose)}
.badge-teal{background:var(--teal-light);color:var(--teal)}
.badge-amber{background:var(--amber-light);color:var(--amber)}
.badge-blue{background:var(--blue-light);color:var(--blue)}
.badge-coral{background:var(--coral-light);color:var(--coral)}
.badge-purple{background:var(--purple-light);color:var(--purple)}
.badge-green{background:var(--green-light);color:var(--green)}

/* SECTION DIVIDER */
.section-gap{height:20px}
.divider{border:none;border-top:1px solid var(--border);margin:20px 0}

/* TOAST */
.toast{position:fixed;bottom:28px;left:50%;transform:translateX(-50%);background:#1A1A1A;color:white;padding:12px 22px;border-radius:40px;font-size:13px;opacity:0;pointer-events:none;transition:opacity 0.3s;z-index:999}
.toast.show{opacity:1}

/* DISCLAIMER */
.disclaimer{font-size:12px;color:var(--text3);background:#FAFAF9;border:1px solid var(--border);padding:10px 14px;border-radius:8px;line-height:1.6;margin-top:14px}
.disclaimer strong{color:var(--text2)}

/* ===== TRACKER PAGE ===== */
.tracker-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:20px}

/* PAIN MAP */
.body-map-wrap{text-align:center;position:relative;display:inline-block}
.body-svg{width:140px;opacity:0.85}
.pain-point{cursor:pointer;transition:all 0.2s}
.pain-point circle{transition:all 0.2s}
.pain-point.active circle{fill:var(--rose);r:10}
.pain-point text{font-size:8px;fill:white;text-anchor:middle;dominant-baseline:middle;pointer-events:none}

/* CHARTS */
.chart-wrap{position:relative;height:180px;margin:10px 0}
canvas{width:100%!important}

/* MOOD JOURNAL */
.journal-entry{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:14px;margin-bottom:10px}
.journal-date{font-size:11px;color:var(--text3);margin-bottom:4px}
.journal-text{font-size:13px;color:var(--text);line-height:1.6}
.journal-mood-row{display:flex;gap:6px;margin-top:8px}
.mood-emoji{font-size:20px;cursor:pointer;opacity:0.4;transition:opacity 0.15s;filter:grayscale(1)}
.mood-emoji.sel{opacity:1;filter:none}

/* FOOD */
.food-tabs{display:flex;gap:6px;margin-bottom:16px;flex-wrap:wrap}
.food-tab{padding:6px 14px;border-radius:20px;border:1px solid var(--border);font-size:12px;cursor:pointer;background:none;font-family:'DM Sans',sans-serif;color:var(--text2);transition:all 0.15s}
.food-tab.active{background:var(--rose);border-color:var(--rose);color:white}
.meal-card{background:var(--card);border:1px solid var(--border);border-radius:12px;overflow:hidden;margin-bottom:10px}
.meal-head{padding:10px 14px;background:#FAFAF9;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--border)}
.meal-name{font-size:12px;font-weight:600;letter-spacing:0.4px;text-transform:uppercase;color:var(--text2)}
.meal-body{padding:10px 14px}
.food-item{display:flex;align-items:center;gap:8px;padding:5px 0;border-bottom:1px solid #F5F1EE;font-size:13px;color:var(--text)}
.food-item:last-child{border-bottom:none}
.food-dot{width:8px;height:8px;border-radius:50%;background:var(--teal);flex-shrink:0}
.food-dot.red{background:var(--coral)}
.food-dot.amber{background:var(--amber)}
.food-tag-sm{margin-left:auto;font-size:10px;color:var(--text3);background:#F5F1EE;padding:2px 7px;border-radius:10px}

/* EXERCISE */
.week-strip{display:grid;grid-template-columns:repeat(7,1fr);gap:6px;margin-bottom:20px}
.ex-day{text-align:center;padding:8px 4px;border-radius:10px;border:1px solid var(--border);background:var(--card);cursor:pointer;transition:all 0.15s}
.ex-day:hover{border-color:var(--rose)}
.ex-day.today{border-color:var(--rose);background:var(--rose-light)}
.ex-day-lbl{font-size:9px;color:var(--text3);margin-bottom:4px;text-transform:uppercase;letter-spacing:0.3px}
.ex-day-icon{font-size:18px;line-height:1}
.ex-day-type{font-size:9px;color:var(--text3);margin-top:3px}
.ex-card{display:flex;align-items:center;gap:14px;padding:14px 16px;background:var(--card);border:1px solid var(--border);border-radius:12px;margin-bottom:10px}
.ex-icon-box{width:40px;height:40px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.ex-info{flex:1}
.ex-name{font-size:14px;font-weight:500;color:var(--text)}
.ex-meta{font-size:12px;color:var(--text2);margin-top:2px}
.ex-badge{margin-left:auto;flex-shrink:0}

/* MEDS */
.med-row{display:flex;align-items:center;gap:14px;padding:14px 16px;background:var(--card);border:1px solid var(--border);border-radius:12px;margin-bottom:8px;transition:all 0.15s}
.med-row.taken{background:#F7FBF9;border-color:var(--teal-light)}
.med-check{width:22px;height:22px;border-radius:50%;border:2px solid var(--border);cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all 0.15s;flex-shrink:0}
.med-check.done{background:var(--teal);border-color:var(--teal)}
.med-check.done::after{content:'✓';color:white;font-size:12px;font-weight:600}
.med-info{flex:1}
.med-name{font-size:14px;font-weight:500;color:var(--text)}
.med-dose{font-size:12px;color:var(--text2)}
.med-time-tag{font-size:11px;background:#F5F1EE;color:var(--text2);padding:3px 10px;border-radius:6px}
.refill-alert{background:var(--amber-light);border:1px solid #FAC775;border-radius:10px;padding:12px 16px;display:flex;align-items:center;gap:10px;margin-bottom:14px}
.refill-icon{font-size:20px}
.refill-text{font-size:13px;color:var(--amber)}

/* Q&A */
.qa-chips{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:14px}
.chip{padding:6px 12px;border:1px solid var(--border);border-radius:20px;font-size:12px;background:none;cursor:pointer;font-family:'DM Sans',sans-serif;color:var(--text2);transition:all 0.15s}
.chip:hover{border-color:var(--rose);color:var(--rose)}
.qa-input{width:100%;padding:12px 16px;border:1px solid var(--border);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:var(--card);resize:none;outline:none;transition:border-color 0.15s}
.qa-input:focus{border-color:var(--rose)}
.qa-answer-box{background:var(--rose-light);border:1px solid var(--rose-mid);border-radius:10px;padding:16px;margin-top:12px;font-size:14px;color:var(--text);line-height:1.7;display:none}
.qa-typing{font-size:13px;color:var(--rose);display:none;margin-top:8px}

/* FERTILITY */
.fertile-window{background:linear-gradient(135deg,var(--teal-light),#E6F1FB);border:1px solid var(--teal);border-radius:14px;padding:20px;margin-bottom:16px}
.fertile-title{font-size:12px;font-weight:600;color:var(--teal);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:6px}
.fertile-dates{font-family:'DM Serif Display',serif;font-size:28px;color:var(--text);margin-bottom:4px}
.fertile-sub{font-size:13px;color:var(--text2)}
.cycle-vis{display:flex;gap:4px;margin:16px 0;flex-wrap:wrap}
.cycle-day{width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:10px;color:var(--text3);border:1px solid var(--border);font-weight:500}
.cycle-day.menstrual{background:var(--rose-light);border-color:var(--rose-mid);color:var(--rose)}
.cycle-day.follicular{background:#F5F1EE;border-color:var(--border);color:var(--text3)}
.cycle-day.fertile{background:var(--teal-light);border-color:var(--teal);color:var(--teal)}
.cycle-day.ovulation{background:var(--teal);border-color:var(--teal);color:white;font-weight:600}
.cycle-day.luteal{background:var(--purple-light);border-color:var(--purple);color:var(--purple)}
.cycle-day.today-ring{box-shadow:0 0 0 2px var(--rose)}

/* TRENDS */
.stat-card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:16px;text-align:center}
.stat-val{font-family:'DM Serif Display',serif;font-size:28px;color:var(--text)}
.stat-lbl{font-size:12px;color:var(--text3);margin-top:2px}
.stat-delta{font-size:11px;margin-top:4px}
.delta-up{color:var(--coral)}
.delta-down{color:var(--teal)}

/* HEATMAP */
.heatmap-grid{display:grid;grid-template-columns:repeat(28,1fr);gap:2px;margin:10px 0}
.heat-cell{height:16px;border-radius:2px}

/* PAIN MAP SVG */
.body-map-container{display:flex;justify-content:center;margin:10px 0}
.pain-zone{cursor:pointer;transition:all 0.2s}
.pain-zone:hover{opacity:0.8}

/* READINESS */
.readiness-circle{width:120px;height:120px;border-radius:50%;display:flex;flex-direction:column;align-items:center;justify-content:center;margin:0 auto 16px;font-family:'DM Serif Display',serif}
.readiness-num{font-size:36px;line-height:1}
.readiness-lbl{font-size:11px;font-family:'DM Sans',sans-serif;font-weight:500}
.readiness-green{background:var(--green-light);color:var(--green)}
.readiness-amber{background:var(--amber-light);color:var(--amber)}
.readiness-red{background:var(--coral-light);color:var(--coral)}

/* JOURNAL */
.journal-prompt-list{display:flex;flex-direction:column;gap:8px;margin-bottom:14px}
.journal-prompt{padding:10px 14px;border:1px solid var(--border);border-radius:8px;font-size:13px;color:var(--text2);cursor:pointer;transition:all 0.15s;background:var(--card)}
.journal-prompt:hover{border-color:var(--rose);color:var(--rose)}
textarea.journal-input{width:100%;padding:12px;border:1px solid var(--border);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);resize:vertical;min-height:100px;outline:none}
textarea.journal-input:focus{border-color:var(--rose)}

/* TRIGGERS */
.trigger-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:14px}
.trigger-btn{padding:8px 6px;border:1px solid var(--border);border-radius:8px;font-size:12px;color:var(--text2);cursor:pointer;background:var(--card);text-align:center;transition:all 0.15s;font-family:'DM Sans',sans-serif}
.trigger-btn.sel{background:var(--rose-light);border-color:var(--rose);color:var(--rose)}

/* APPOINTMENT REPORT */
.report-section{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:14px;margin-bottom:10px}
.report-section-title{font-size:12px;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px}

/* COPING TOOLKIT */
.toolkit-card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:16px;margin-bottom:10px;cursor:pointer;transition:all 0.15s}
.toolkit-card:hover{border-color:var(--rose)}
.toolkit-header{display:flex;align-items:center;gap:10px}
.toolkit-icon{font-size:22px}
.toolkit-title{font-size:14px;font-weight:500;color:var(--text)}
.toolkit-sub{font-size:12px;color:var(--text2);margin-top:2px}
.toolkit-detail{display:none;margin-top:12px;font-size:13px;color:var(--text2);line-height:1.7;border-top:1px solid var(--border);padding-top:12px}
.toolkit-detail.open{display:block}

/* BREATHING */
.breath-circle{width:100px;height:100px;border-radius:50%;background:var(--rose-light);border:3px solid var(--rose-mid);margin:16px auto;display:flex;align-items:center;justify-content:center;font-size:13px;color:var(--rose);font-weight:500;transition:transform 0.1s}
.breath-text{text-align:center;font-size:13px;color:var(--text2);margin-bottom:8px}

/* DOCTOR DIRECTORY */
.doctor-card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:16px;margin-bottom:10px;display:flex;align-items:center;gap:14px}
.doc-avatar{width:44px;height:44px;border-radius:50%;background:var(--rose-light);color:var(--rose);display:flex;align-items:center;justify-content:center;font-size:16px;font-weight:600;flex-shrink:0}
.doc-info{flex:1}
.doc-name{font-size:14px;font-weight:500;color:var(--text)}
.doc-spec{font-size:12px;color:var(--text2)}
.doc-actions{display:flex;gap:6px}

/* EXPORT */
.export-option{display:flex;align-items:center;gap:14px;padding:14px 16px;background:var(--card);border:1px solid var(--border);border-radius:10px;margin-bottom:8px;cursor:pointer;transition:all 0.15s}
.export-option:hover{border-color:var(--rose)}
.export-icon{font-size:24px}
.export-info{flex:1}
.export-name{font-size:14px;font-weight:500;color:var(--text)}
.export-sub{font-size:12px;color:var(--text2)}

/* ONBOARDING */
.onboarding-overlay{position:fixed;inset:0;background:rgba(0,0,0,0.5);z-index:1000;display:flex;align-items:center;justify-content:center}
.onboarding-card{background:white;border-radius:16px;padding:32px;max-width:460px;width:90%;box-shadow:0 20px 60px rgba(0,0,0,0.15)}
.ob-step{display:none}
.ob-step.active{display:block}
.ob-title{font-family:'DM Serif Display',serif;font-size:22px;color:var(--text);margin-bottom:6px}
.ob-sub{font-size:14px;color:var(--text2);margin-bottom:20px}
.ob-options{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px}
.ob-opt{padding:8px 16px;border:1.5px solid var(--border);border-radius:20px;font-size:13px;cursor:pointer;background:none;font-family:'DM Sans',sans-serif;color:var(--text2);transition:all 0.15s}
.ob-opt.sel{background:var(--rose);border-color:var(--rose);color:white}
.ob-progress{display:flex;gap:6px;margin-bottom:20px}
.ob-pip{height:3px;flex:1;border-radius:3px;background:var(--border)}
.ob-pip.done{background:var(--rose)}
.ob-input{width:100%;padding:10px 14px;border:1px solid var(--border);border-radius:8px;font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);outline:none;margin-bottom:10px}
.ob-input:focus{border-color:var(--rose)}

/* RESPONSIVE SIDEBAR COLLAPSE */
@media(max-width:700px){
  .sidebar{width:60px}
  .nav-label,.brand-sub,.cycle-badge,.brand-name,.sidebar-footer p{display:none}
  .brand-name+em{display:none}
  .sidebar-footer{padding:8px}
  .page{padding:16px}
  .tracker-grid{grid-template-columns:1fr 1fr}
  .grid-3{grid-template-columns:1fr 1fr}
  .grid-4{grid-template-columns:1fr 1fr}
  .trigger-grid{grid-template-columns:repeat(3,1fr)}
}

/* PRINT */
@media print{
  .sidebar,.toast,.btn,.qa-chips,.food-tabs,.onboarding-overlay{display:none!important}
  .main{overflow:visible}
  .page{display:block!important;padding:10px}
  .page-title{font-size:18px}
}

/* SCROLLBAR */
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:10px}
</style>
</head>
<body>

<!-- ONBOARDING OVERLAY -->
<div class="onboarding-overlay" id="onboarding">
  <div class="onboarding-card">
    <div class="ob-progress">
      <div class="ob-pip done" id="pip1"></div>
      <div class="ob-pip" id="pip2"></div>
      <div class="ob-pip" id="pip3"></div>
      <div class="ob-pip" id="pip4"></div>
    </div>

    <div class="ob-step active" id="ob1">
      <p class="ob-title">Welcome to <em style="font-style:italic;color:var(--rose)">EndoEase</em></p>
      <p class="ob-sub">Your endometriosis companion. Let's personalise your experience.</p>
      <p style="font-size:13px;color:var(--text2);margin-bottom:10px">What is your endo stage?</p>
      <div class="ob-options">
        <button class="ob-opt" onclick="obSel(this,'stage')">Stage I (Minimal)</button>
        <button class="ob-opt" onclick="obSel(this,'stage')">Stage II (Mild)</button>
        <button class="ob-opt" onclick="obSel(this,'stage')">Stage III (Moderate)</button>
        <button class="ob-opt" onclick="obSel(this,'stage')">Stage IV (Severe)</button>
        <button class="ob-opt" onclick="obSel(this,'stage')">Not diagnosed yet</button>
        <button class="ob-opt" onclick="obSel(this,'stage')">Prefer not to say</button>
      </div>
      <button class="btn btn-primary" onclick="nextOb(2)">Continue →</button>
    </div>

    <div class="ob-step" id="ob2">
      <p class="ob-title">Your history</p>
      <p class="ob-sub">This helps us personalise your care plan.</p>
      <p style="font-size:13px;color:var(--text2);margin-bottom:8px">Have you had surgery?</p>
      <div class="ob-options" style="margin-bottom:14px">
        <button class="ob-opt" onclick="obSel(this,'surg')">Laparoscopy</button>
        <button class="ob-opt" onclick="obSel(this,'surg')">Laparotomy</button>
        <button class="ob-opt" onclick="obSel(this,'surg')">No surgery</button>
        <button class="ob-opt" onclick="obSel(this,'surg')">Awaiting surgery</button>
      </div>
      <p style="font-size:13px;color:var(--text2);margin-bottom:8px">Current treatment?</p>
      <div class="ob-options">
        <button class="ob-opt" onclick="obSel(this,'tx')">Hormonal therapy</button>
        <button class="ob-opt" onclick="obSel(this,'tx')">Pain medication</button>
        <button class="ob-opt" onclick="obSel(this,'tx')">Diet & lifestyle</button>
        <button class="ob-opt" onclick="obSel(this,'tx')">No treatment</button>
      </div>
      <div style="margin-top:14px;display:flex;gap:8px">
        <button class="btn btn-outline" onclick="nextOb(1)">Back</button>
        <button class="btn btn-primary" onclick="nextOb(3)">Continue →</button>
      </div>
    </div>

    <div class="ob-step" id="ob3">
      <p class="ob-title">Fertility & goals</p>
      <p class="ob-sub">Helps us show the right tracking features.</p>
      <div class="ob-options">
        <button class="ob-opt" onclick="obSel(this,'fert')">Trying to conceive</button>
        <button class="ob-opt" onclick="obSel(this,'fert')">Not trying right now</button>
        <button class="ob-opt" onclick="obSel(this,'fert')">Considering in future</button>
        <button class="ob-opt" onclick="obSel(this,'fert')">Not applicable</button>
      </div>
      <p style="font-size:13px;color:var(--text2);margin:14px 0 8px">Average cycle length</p>
      <input class="ob-input" type="number" placeholder="e.g. 28" min="21" max="45" id="ob-cycle-input"/>
      <div style="margin-top:8px;display:flex;gap:8px">
        <button class="btn btn-outline" onclick="nextOb(2)">Back</button>
        <button class="btn btn-primary" onclick="nextOb(4)">Continue →</button>
      </div>
    </div>

    <div class="ob-step" id="ob4">
      <p class="ob-title">Your name</p>
      <p class="ob-sub">We'll use this to personalise your dashboard.</p>
      <input class="ob-input" id="ob-name-input" placeholder="Your first name" style="margin-bottom:16px"/>
      <p style="font-size:12px;color:var(--text3);margin-bottom:16px">Your data stays on your device. We never share it.</p>
      <div style="display:flex;gap:8px">
        <button class="btn btn-outline" onclick="nextOb(3)">Back</button>
        <button class="btn btn-primary" onclick="finishOnboarding()">Get started →</button>
      </div>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- APP SHELL -->
<div class="app-shell">

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="brand">
      <div class="logo-row">
        <div class="logo-mark"><div class="logo-inner"></div></div>
        <span class="brand-name">endo<em>ease</em></span>
      </div>
      <p class="brand-sub">Endometriosis companion</p>
    </div>
    <nav class="nav-list">
      <button class="nav-item active" onclick="showPage('home',this)"><span class="nav-icon">🏠</span><span class="nav-label">Dashboard</span></button>
      <button class="nav-item" onclick="showPage('tracker',this)"><span class="nav-icon">📊</span><span class="nav-label">Symptom Tracker</span></button>
      <button class="nav-item" onclick="showPage('predict',this)"><span class="nav-icon">🤖</span><span class="nav-label">AI Insights</span></button>
      <button class="nav-item" onclick="showPage('painmap',this)"><span class="nav-icon">🗺️</span><span class="nav-label">Pain Map</span></button>
      <button class="nav-item" onclick="showPage('food',this)"><span class="nav-icon">🥗</span><span class="nav-label">Nutrition Plan</span></button>
      <button class="nav-item" onclick="showPage('exercise',this)"><span class="nav-icon">🏃</span><span class="nav-label">Movement</span></button>
      <button class="nav-item" onclick="showPage('meds',this)"><span class="nav-icon">💊</span><span class="nav-label">Medications</span></button>
      <button class="nav-item" onclick="showPage('qa',this)"><span class="nav-icon">❓</span><span class="nav-label">Medical Q&A</span></button>
      <button class="nav-item" onclick="showPage('fertility',this)"><span class="nav-icon">👶</span><span class="nav-label">Fertility</span></button>
      <button class="nav-item" onclick="showPage('journal',this)"><span class="nav-icon">📖</span><span class="nav-label">Mood Journal</span></button>
      <button class="nav-item" onclick="showPage('triggers',this)"><span class="nav-icon">⚡</span><span class="nav-label">Trigger Diary</span></button>
      <button class="nav-item" onclick="showPage('trends',this)"><span class="nav-icon">📈</span><span class="nav-label">Trends</span></button>
      <button class="nav-item" onclick="showPage('coping',this)"><span class="nav-icon">🧘</span><span class="nav-label">Coping Toolkit</span></button>
      <button class="nav-item" onclick="showPage('doctors',this)"><span class="nav-icon">👩‍⚕️</span><span class="nav-label">My Doctors</span></button>
      <button class="nav-item" onclick="showPage('report',this)"><span class="nav-icon">📋</span><span class="nav-label">Appointment Report</span></button>
      <button class="nav-item" onclick="showPage('export',this)"><span class="nav-icon">📤</span><span class="nav-label">Export Data</span></button>
    </nav>
    <div class="sidebar-footer">
      <span class="cycle-badge" id="sidebar-cycle-badge">Day 14</span>
      <p>Data stored locally.<br>Always consult your doctor.</p>
    </div>
  </aside>

  <!-- MAIN CONTENT -->
  <main class="main">

    <!-- ===== DASHBOARD ===== -->
    <div class="page active" id="page-home">
      <div class="page-header">
        <h1 class="page-title">Good morning, <span id="dash-name">there</span> 👋</h1>
        <p class="page-sub">Here's how you're doing today — Day 14 of your cycle</p>
      </div>

      <!-- Readiness -->
      <div class="grid-2" style="margin-bottom:16px">
        <div class="card" style="text-align:center">
          <p style="font-size:12px;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:12px">Today's readiness</p>
          <div class="readiness-circle readiness-green" id="readiness-circle">
            <span class="readiness-num" id="readiness-num">74</span>
            <span class="readiness-lbl">GOOD</span>
          </div>
          <p style="font-size:12px;color:var(--text2)">Mid-cycle window — lower flare risk today</p>
        </div>
        <div class="card">
          <p style="font-size:12px;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:12px">Flare risk — next 72h</p>
          <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
            <div style="flex:1;background:#F5F1EE;border-radius:6px;height:10px;overflow:hidden">
              <div style="width:28%;height:100%;background:var(--teal);border-radius:6px"></div>
            </div>
            <span class="badge badge-teal">Low</span>
          </div>
          <p style="font-size:12px;color:var(--text2)">Pain typically peaks days 25–28 for you</p>
          <div style="margin-top:14px">
            <p style="font-size:11px;color:var(--text3);margin-bottom:6px">Recent symptoms</p>
            <div style="display:flex;gap:6px;flex-wrap:wrap">
              <span class="badge badge-rose">Pain 3/5</span>
              <span class="badge badge-amber">Bloating 2/5</span>
              <span class="badge badge-purple">Fatigue 2/5</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Quick stats -->
      <div class="grid-4" style="margin-bottom:16px">
        <div class="stat-card">
          <div class="stat-val">28</div>
          <div class="stat-lbl">Avg cycle (days)</div>
          <div class="stat-delta delta-down">↓ Stable</div>
        </div>
        <div class="stat-card">
          <div class="stat-val">3</div>
          <div class="stat-lbl">Avg pain today</div>
          <div class="stat-delta delta-down">↓ vs last week</div>
        </div>
        <div class="stat-card">
          <div class="stat-val">2/4</div>
          <div class="stat-lbl">Meds taken</div>
          <div class="stat-delta" style="color:var(--amber)">2 pending</div>
        </div>
        <div class="stat-card">
          <div class="stat-val">12</div>
          <div class="stat-lbl">Days logged</div>
          <div class="stat-delta delta-down">↑ Great streak!</div>
        </div>
      </div>

      <!-- Today actions -->
      <div class="card">
        <p style="font-size:13px;font-weight:500;color:var(--text);margin-bottom:12px">Today's actions</p>
        <div style="display:flex;flex-direction:column;gap:8px">
          <div style="display:flex;align-items:center;gap:10px;padding:10px;background:var(--rose-light);border-radius:8px">
            <span style="font-size:16px">📊</span>
            <span style="font-size:13px;color:var(--text)">Log today's symptoms</span>
            <button class="btn btn-primary btn-sm" style="margin-left:auto" onclick="showPage('tracker',null)">Log →</button>
          </div>
          <div style="display:flex;align-items:center;gap:10px;padding:10px;background:var(--teal-light);border-radius:8px">
            <span style="font-size:16px">🧘</span>
            <span style="font-size:13px;color:var(--text)">Gentle yin yoga · 30 min recommended</span>
            <button class="btn btn-outline btn-sm" style="margin-left:auto" onclick="showPage('exercise',null)">View →</button>
          </div>
          <div style="display:flex;align-items:center;gap:10px;padding:10px;background:var(--amber-light);border-radius:8px">
            <span style="font-size:16px">💊</span>
            <span style="font-size:13px;color:var(--text)">Dienogest 2mg · due at 8 AM</span>
            <button class="btn btn-outline btn-sm" style="margin-left:auto" onclick="showPage('meds',null)">Mark →</button>
          </div>
        </div>
      </div>
    </div>

    <!-- ===== SYMPTOM TRACKER ===== -->
    <div class="page" id="page-tracker">
      <div class="page-header">
        <h1 class="page-title">Symptom tracker</h1>
        <p class="page-sub">Log how you're feeling across 6 parameters — Day 14</p>
      </div>

      <div class="card" style="margin-bottom:14px">
        <div class="tracker-grid" id="tracker-params">
          <!-- built by JS -->
        </div>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">Pain intensity (sliders)</p>
        <div class="slider-group">
          <div class="slider-row"><span class="slider-label">Pelvic pain</span><input type="range" min="0" max="10" value="3" step="1" oninput="this.nextElementSibling.textContent=this.value"><span class="slider-val">3</span></div>
          <div class="slider-row"><span class="slider-label">Back pain</span><input type="range" min="0" max="10" value="2" step="1" oninput="this.nextElementSibling.textContent=this.value"><span class="slider-val">2</span></div>
          <div class="slider-row"><span class="slider-label">Leg/thigh pain</span><input type="range" min="0" max="10" value="1" step="1" oninput="this.nextElementSibling.textContent=this.value"><span class="slider-val">1</span></div>
          <div class="slider-row"><span class="slider-label">Shoulder pain</span><input type="range" min="0" max="10" value="0" step="1" oninput="this.nextElementSibling.textContent=this.value"><span class="slider-val">0</span></div>
        </div>
        <p class="param-label" style="margin-top:10px">Additional symptoms</p>
        <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:16px">
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Nausea</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Diarrhoea</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Constipation</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Spotting</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Bloating</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Brain fog</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Headache</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Painful sex</button>
        </div>
        <button class="btn btn-primary btn-full" onclick="logToday()">✓ Log today's entry</button>
      </div>

      <!-- 7 day mini chart -->
      <div class="card">
        <p class="param-label">Last 7 days — pain trend</p>
        <div class="chart-wrap"><canvas id="trend-chart"></canvas></div>
      </div>
    </div>

    <!-- ===== AI INSIGHTS ===== -->
    <div class="page" id="page-predict">
      <div class="page-header">
        <h1 class="page-title">AI insights</h1>
        <p class="page-sub">Pattern analysis from your last 3 months of data</p>
      </div>

      <div class="card" style="margin-bottom:14px">
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:10px">
          <p style="font-size:14px;font-weight:500;color:var(--text)">Flare risk — next 3 days</p>
          <span class="badge badge-teal">Low (28%)</span>
        </div>
        <div style="background:#F5F1EE;border-radius:8px;height:12px;overflow:hidden;margin-bottom:8px">
          <div style="width:28%;height:100%;background:var(--teal);border-radius:8px;transition:width 1s ease" id="risk-fill"></div>
        </div>
        <p style="font-size:13px;color:var(--text2)">Mid-cycle follicular phase — hormonal patterns are stable. Inflammation markers suggest a calm window.</p>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p style="font-size:13px;font-weight:500;color:var(--text);margin-bottom:12px">Key patterns detected</p>
        <div style="display:flex;flex-direction:column;gap:10px">
          <div style="display:flex;align-items:flex-start;gap:12px;padding:12px;background:var(--rose-light);border-radius:10px">
            <span style="font-size:18px">📅</span>
            <div><p style="font-size:13px;color:var(--text);margin-bottom:2px">Pain peaks days 25–28</p><p style="font-size:12px;color:var(--text2)">Correlates with luteal phase — consider scheduling lighter days</p></div>
          </div>
          <div style="display:flex;align-items:flex-start;gap:12px;padding:12px;background:var(--purple-light);border-radius:10px">
            <span style="font-size:18px">😴</span>
            <div><p style="font-size:13px;color:var(--text);margin-bottom:2px">Sleep drops 1.8 pts in luteal phase</p><p style="font-size:12px;color:var(--text2)">Try earlier bedtimes & magnesium in the week before your period</p></div>
          </div>
          <div style="display:flex;align-items:flex-start;gap:12px;padding:12px;background:var(--amber-light);border-radius:10px">
            <span style="font-size:18px">🌾</span>
            <div><p style="font-size:13px;color:var(--text);margin-bottom:2px">Bloating correlates with gluten intake</p><p style="font-size:12px;color:var(--text2)">Observed in 3 of your last 4 cycles — consider a gluten-free trial week</p></div>
          </div>
          <div style="display:flex;align-items:flex-start;gap:12px;padding:12px;background:var(--teal-light);border-radius:10px">
            <span style="font-size:18px">🏃</span>
            <div><p style="font-size:13px;color:var(--text);margin-bottom:2px">Exercise reduces pain by avg 1.4 pts</p><p style="font-size:12px;color:var(--text2)">Gentle yoga on high-pain days shows strongest effect</p></div>
          </div>
          <div style="display:flex;align-items:flex-start;gap:12px;padding:12px;background:var(--blue-light);border-radius:10px">
            <span style="font-size:18px">💧</span>
            <div><p style="font-size:13px;color:var(--text);margin-bottom:2px">Hydration linked to fatigue reduction</p><p style="font-size:12px;color:var(--text2)">Days you logged 2L+ water had 30% lower fatigue scores</p></div>
          </div>
        </div>
      </div>

      <div class="card">
        <p style="font-size:13px;font-weight:500;color:var(--text);margin-bottom:12px">Next 14 days forecast</p>
        <div class="chart-wrap"><canvas id="forecast-chart"></canvas></div>
      </div>
    </div>

    <!-- ===== PAIN MAP ===== -->
    <div class="page" id="page-painmap">
      <div class="page-header">
        <h1 class="page-title">Pain body map</h1>
        <p class="page-sub">Tap the zones where you feel pain today</p>
      </div>
      <div class="grid-2">
        <div class="card">
          <div class="body-map-container">
            <svg width="160" height="320" viewBox="0 0 160 320" id="body-svg">
              <!-- Head -->
              <circle cx="80" cy="28" r="24" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <!-- Neck -->
              <rect x="70" y="50" width="20" height="18" rx="4" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <!-- Torso -->
              <rect x="42" y="66" width="76" height="90" rx="12" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <!-- Arms -->
              <rect x="18" y="68" width="26" height="70" rx="10" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <rect x="116" y="68" width="26" height="70" rx="10" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <!-- Pelvis -->
              <rect x="42" y="154" width="76" height="36" rx="8" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <!-- Legs -->
              <rect x="46" y="188" width="32" height="90" rx="10" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <rect x="82" y="188" width="32" height="90" rx="10" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <!-- Feet -->
              <rect x="42" y="276" width="36" height="20" rx="6" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>
              <rect x="82" y="276" width="36" height="20" rx="6" fill="#F5F1EE" stroke="#E0D8D0" stroke-width="1.5"/>

              <!-- Pain zones (clickable overlays) -->
              <g class="pain-zone" id="zone-head" onclick="toggleZone(this,'Head')" title="Head">
                <circle cx="80" cy="28" r="24" fill="transparent" stroke="transparent" stroke-width="2"/>
              </g>
              <g class="pain-zone" id="zone-chest" onclick="toggleZone(this,'Chest/ribcage')" title="Chest">
                <rect x="42" y="66" width="76" height="45" rx="8" fill="transparent"/>
              </g>
              <g class="pain-zone" id="zone-abdomen" onclick="toggleZone(this,'Abdomen')" title="Abdomen">
                <rect x="42" y="109" width="76" height="45" rx="8" fill="transparent"/>
              </g>
              <g class="pain-zone" id="zone-pelvis" onclick="toggleZone(this,'Pelvis/lower abdomen')" title="Pelvis">
                <rect x="42" y="154" width="76" height="36" rx="8" fill="transparent"/>
              </g>
              <g class="pain-zone" id="zone-left-thigh" onclick="toggleZone(this,'Left thigh')" title="L Thigh">
                <rect x="46" y="188" width="32" height="45" rx="6" fill="transparent"/>
              </g>
              <g class="pain-zone" id="zone-right-thigh" onclick="toggleZone(this,'Right thigh')" title="R Thigh">
                <rect x="82" y="188" width="32" height="45" rx="6" fill="transparent"/>
              </g>
              <g class="pain-zone" id="zone-lower-back" onclick="toggleZone(this,'Lower back')" title="Lower back">
                <rect x="42" y="130" width="76" height="24" rx="6" fill="rgba(255,255,255,0.01)"/>
                <text x="80" y="143" font-size="8" fill="var(--text3)" text-anchor="middle">back</text>
              </g>
            </svg>
          </div>
          <p style="font-size:12px;color:var(--text3);text-align:center;margin-top:8px">Tap zones to mark pain</p>
        </div>
        <div>
          <div class="card" style="margin-bottom:12px">
            <p class="param-label">Active pain zones</p>
            <div id="pain-zones-list" style="min-height:60px;font-size:13px;color:var(--text2)">
              None selected yet — tap the body map
            </div>
          </div>
          <div class="card">
            <p class="param-label">Pain intensity per zone</p>
            <div id="pain-intensity-sliders">
              <p style="font-size:13px;color:var(--text3)">Select zones first</p>
            </div>
          </div>
        </div>
      </div>
      <div style="margin-top:14px">
        <button class="btn btn-primary" onclick="logToday()">Save pain map</button>
      </div>
    </div>

    <!-- ===== NUTRITION PLAN ===== -->
    <div class="page" id="page-food">
      <div class="page-header">
        <h1 class="page-title">Nutrition plan</h1>
        <p class="page-sub">Personalised for your follicular phase — anti-inflammatory focus</p>
      </div>

      <div class="food-tabs" id="food-day-tabs">
        <button class="food-tab active" onclick="selFoodDay(this,'mon')">Monday</button>
        <button class="food-tab" onclick="selFoodDay(this,'tue')">Tuesday</button>
        <button class="food-tab" onclick="selFoodDay(this,'wed')">Wednesday</button>
        <button class="food-tab" onclick="selFoodDay(this,'thu')">Thursday</button>
        <button class="food-tab" onclick="selFoodDay(this,'fri')">Friday</button>
        <button class="food-tab" onclick="selFoodDay(this,'sat')">Saturday</button>
        <button class="food-tab" onclick="selFoodDay(this,'sun')">Sunday</button>
      </div>

      <div id="food-content"></div>

      <div class="card" style="margin-top:14px">
        <p class="param-label">Foods to favour this phase</p>
        <div style="display:flex;gap:6px;flex-wrap:wrap">
          <span class="badge badge-teal">Salmon / mackerel</span>
          <span class="badge badge-teal">Leafy greens</span>
          <span class="badge badge-teal">Turmeric</span>
          <span class="badge badge-teal">Ginger</span>
          <span class="badge badge-teal">Berries</span>
          <span class="badge badge-teal">Chia seeds</span>
          <span class="badge badge-teal">Lentils</span>
          <span class="badge badge-teal">Pumpkin seeds</span>
          <span class="badge badge-teal">Extra virgin olive oil</span>
        </div>
        <p class="param-label" style="margin-top:14px">Foods to limit</p>
        <div style="display:flex;gap:6px;flex-wrap:wrap">
          <span class="badge badge-coral">Red meat</span>
          <span class="badge badge-coral">Processed sugar</span>
          <span class="badge badge-coral">Alcohol</span>
          <span class="badge badge-coral">Trans fats</span>
          <span class="badge badge-coral">Gluten (for you)</span>
          <span class="badge badge-coral">Caffeine excess</span>
        </div>
      </div>
    </div>

    <!-- ===== EXERCISE ===== -->
    <div class="page" id="page-exercise">
      <div class="page-header">
        <h1 class="page-title">Movement plan</h1>
        <p class="page-sub">May — adapted to your cycle phases</p>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">This week</p>
        <div class="week-strip">
          <div class="ex-day"><div class="ex-day-lbl">Mon</div><div class="ex-day-icon">🧘</div><div class="ex-day-type">yoga</div></div>
          <div class="ex-day today"><div class="ex-day-lbl">Tue</div><div class="ex-day-icon">🚶</div><div class="ex-day-type">walk</div></div>
          <div class="ex-day"><div class="ex-day-lbl">Wed</div><div class="ex-day-icon">🏊</div><div class="ex-day-type">swim</div></div>
          <div class="ex-day"><div class="ex-day-lbl">Thu</div><div class="ex-day-icon">💤</div><div class="ex-day-type">rest</div></div>
          <div class="ex-day"><div class="ex-day-lbl">Fri</div><div class="ex-day-icon">🤸</div><div class="ex-day-type">pilates</div></div>
          <div class="ex-day"><div class="ex-day-lbl">Sat</div><div class="ex-day-icon">🧘</div><div class="ex-day-type">yoga</div></div>
          <div class="ex-day"><div class="ex-day-lbl">Sun</div><div class="ex-day-icon">💤</div><div class="ex-day-type">rest</div></div>
        </div>
      </div>

      <div class="ex-card">
        <div class="ex-icon-box" style="background:var(--teal-light)">🧘</div>
        <div class="ex-info"><div class="ex-name">Gentle yin yoga</div><div class="ex-meta">30 min · low intensity · reduces pelvic tension and inflammation</div></div>
        <span class="badge badge-rose ex-badge">Today</span>
      </div>
      <div class="ex-card">
        <div class="ex-icon-box" style="background:var(--blue-light)">🚶</div>
        <div class="ex-info"><div class="ex-name">30-minute walk</div><div class="ex-meta">Moderate · supports estrogen balance · improves mood</div></div>
      </div>
      <div class="ex-card">
        <div class="ex-icon-box" style="background:var(--purple-light)">🤸</div>
        <div class="ex-info"><div class="ex-name">Pilates (modified core)</div><div class="ex-meta">45 min · avoid deep twists on high-pain days · great for pelvic floor</div></div>
      </div>
      <div class="ex-card">
        <div class="ex-icon-box" style="background:var(--blue-light)">🏊</div>
        <div class="ex-info"><div class="ex-name">Swimming / pool walking</div><div class="ex-meta">30 min · buoyancy reduces pelvic pressure · anti-inflammatory</div></div>
      </div>
      <div class="ex-card">
        <div class="ex-icon-box" style="background:var(--coral-light)">⚠️</div>
        <div class="ex-info"><div class="ex-name">High-intensity exercise</div><div class="ex-meta">Avoid HIIT, heavy lifting, and running during high-pain or menstrual days</div></div>
        <span class="badge badge-coral ex-badge">Avoid</span>
      </div>

      <div class="card" style="margin-top:14px">
        <p class="param-label">Heat pad timer</p>
        <p style="font-size:13px;color:var(--text2);margin-bottom:12px">Use a heat pad on abdomen/lower back. Set a reminder to avoid burns.</p>
        <div style="display:flex;align-items:center;gap:12px">
          <select style="padding:8px 12px;border:1px solid var(--border);border-radius:8px;font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text)" id="heat-select">
            <option>15 minutes</option><option selected>20 minutes</option><option>30 minutes</option><option>45 minutes</option>
          </select>
          <button class="btn btn-primary" onclick="startHeatTimer()">Start timer 🔥</button>
          <span id="heat-timer-display" style="font-size:14px;font-weight:500;color:var(--rose)"></span>
        </div>
      </div>
    </div>

    <!-- ===== MEDICATIONS ===== -->
    <div class="page" id="page-meds">
      <div class="page-header">
        <h1 class="page-title">Medications</h1>
        <p class="page-sub">Tap to mark as taken — Tuesday 6 May</p>
      </div>

      <div class="refill-alert">
        <span class="refill-icon">⚠️</span>
        <div>
          <p style="font-size:13px;font-weight:500;color:var(--amber)">Refill reminder</p>
          <p style="font-size:12px;color:var(--amber)">Dienogest — 8 days supply remaining. Request prescription soon.</p>
        </div>
      </div>

      <div id="med-list"></div>

      <button class="btn btn-outline" onclick="addMedPrompt()" style="margin-top:4px">+ Add medication</button>

      <div class="disclaimer" style="margin-top:16px">
        <strong>Important:</strong> Always take medications exactly as prescribed by your doctor or gynaecologist. This tracker is a reminder tool only and does not provide medical advice.
      </div>
    </div>

    <!-- ===== MEDICAL Q&A ===== -->
    <div class="page" id="page-qa">
      <div class="page-header">
        <h1 class="page-title">Medical Q&A</h1>
        <p class="page-sub">Evidence-based answers about endometriosis</p>
      </div>

      <div class="qa-chips" id="qa-chips">
        <button class="chip" onclick="fillQ(this)">What is adenomyosis?</button>
        <button class="chip" onclick="fillQ(this)">Can endo affect fertility?</button>
        <button class="chip" onclick="fillQ(this)">What foods reduce inflammation?</button>
        <button class="chip" onclick="fillQ(this)">Is laparoscopy worth it?</button>
        <button class="chip" onclick="fillQ(this)">What is the endo belly?</button>
        <button class="chip" onclick="fillQ(this)">Can endo cause bowel symptoms?</button>
        <button class="chip" onclick="fillQ(this)">What is dienogest?</button>
        <button class="chip" onclick="fillQ(this)">How do I explain endo to my employer?</button>
      </div>

      <div class="card">
        <textarea class="qa-input" id="qa-input" rows="3" placeholder="Type your question about endometriosis..."></textarea>
        <div style="display:flex;gap:8px;margin-top:10px">
          <button class="btn btn-primary" onclick="askQ()">Ask question →</button>
          <button class="btn btn-outline" onclick="clearQ()">Clear</button>
        </div>
        <div class="qa-typing" id="qa-typing">Thinking...</div>
        <div class="qa-answer-box" id="qa-answer"></div>
      </div>

      <div class="disclaimer" style="margin-top:14px">
        <strong>Disclaimer:</strong> Answers are informational and evidence-based but are not a substitute for professional medical advice. Always discuss symptoms and treatment decisions with your gynaecologist or endometriosis specialist.
      </div>
    </div>

    <!-- ===== FERTILITY ===== -->
    <div class="page" id="page-fertility">
      <div class="page-header">
        <h1 class="page-title">Fertility planning</h1>
        <p class="page-sub">Cycle-aware conception support</p>
      </div>

      <div class="fertile-window">
        <p class="fertile-title">Your fertile window this cycle</p>
        <p class="fertile-dates">May 12 – 17</p>
        <p class="fertile-sub">Peak ovulation estimated: May 14 · Based on 28-day average cycle</p>
      </div>

      <div class="grid-4" style="margin-bottom:14px">
        <div class="stat-card"><div class="stat-val">28</div><div class="stat-lbl">Avg cycle</div></div>
        <div class="stat-card"><div class="stat-val">13</div><div class="stat-lbl">Luteal phase</div></div>
        <div class="stat-card"><div class="stat-val">May 28</div><div class="stat-lbl">Next period</div></div>
        <div class="stat-card"><div class="stat-val">Add</div><div class="stat-lbl">AMH result</div></div>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">Cycle visualisation — current cycle</p>
        <div class="cycle-vis" id="cycle-vis"></div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;margin-top:8px">
          <span style="display:flex;align-items:center;gap:4px;font-size:11px;color:var(--text2)"><span style="width:10px;height:10px;border-radius:50%;background:var(--rose-light);border:1px solid var(--rose-mid);display:inline-block"></span>Menstrual</span>
          <span style="display:flex;align-items:center;gap:4px;font-size:11px;color:var(--text2)"><span style="width:10px;height:10px;border-radius:50%;background:var(--teal-light);border:1px solid var(--teal);display:inline-block"></span>Fertile</span>
          <span style="display:flex;align-items:center;gap:4px;font-size:11px;color:var(--text2)"><span style="width:10px;height:10px;border-radius:50%;background:var(--teal);display:inline-block"></span>Ovulation</span>
          <span style="display:flex;align-items:center;gap:4px;font-size:11px;color:var(--text2)"><span style="width:10px;height:10px;border-radius:50%;background:var(--purple-light);border:1px solid var(--purple);display:inline-block"></span>Luteal</span>
        </div>
      </div>

      <div class="card">
        <p class="param-label">Endo & fertility notes</p>
        <div style="display:flex;flex-direction:column;gap:8px">
          <div style="padding:10px 14px;background:var(--rose-light);border-radius:8px;font-size:13px;color:var(--text)">Endometriosis can affect egg quality and ovarian reserve (AMH). Ask your specialist about your ovarian reserve.</div>
          <div style="padding:10px 14px;background:var(--teal-light);border-radius:8px;font-size:13px;color:var(--text)">Many people with endo conceive naturally. Stage of disease doesn't always correlate with fertility outcomes.</div>
          <div style="padding:10px 14px;background:var(--amber-light);border-radius:8px;font-size:13px;color:var(--text)">IVF, IUI, and laparoscopy are all options worth discussing with a reproductive endocrinologist.</div>
        </div>
      </div>

      <div class="disclaimer" style="margin-top:14px">This is a tracking aid only. Please consult a reproductive endocrinologist for personalised fertility planning with endometriosis.</div>
    </div>

    <!-- ===== MOOD JOURNAL ===== -->
    <div class="page" id="page-journal">
      <div class="page-header">
        <h1 class="page-title">Mood journal</h1>
        <p class="page-sub">Guided prompts for endo-related emotions</p>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">How are you feeling today?</p>
        <div class="journal-mood-row" style="margin-bottom:14px" id="mood-emojis">
          <span class="mood-emoji" onclick="selMood(this)" title="Happy">😊</span>
          <span class="mood-emoji" onclick="selMood(this)" title="Okay">😐</span>
          <span class="mood-emoji" onclick="selMood(this)" title="Anxious">😰</span>
          <span class="mood-emoji" onclick="selMood(this)" title="Sad">😢</span>
          <span class="mood-emoji" onclick="selMood(this)" title="Frustrated">😤</span>
          <span class="mood-emoji" onclick="selMood(this)" title="Exhausted">😴</span>
          <span class="mood-emoji" onclick="selMood(this)" title="Hopeful">🌱</span>
        </div>
        <p class="param-label">Journaling prompt</p>
        <div class="journal-prompt-list">
          <div class="journal-prompt" onclick="fillJournal(this)">How has pain affected my plans today?</div>
          <div class="journal-prompt" onclick="fillJournal(this)">What am I grateful for despite how I'm feeling?</div>
          <div class="journal-prompt" onclick="fillJournal(this)">How do I feel about my treatment right now?</div>
          <div class="journal-prompt" onclick="fillJournal(this)">What do I wish others understood about living with endo?</div>
        </div>
        <textarea class="journal-input" id="journal-text" placeholder="Write freely here..."></textarea>
        <button class="btn btn-primary" style="margin-top:10px" onclick="saveJournal()">Save entry</button>
      </div>

      <div class="card">
        <p class="param-label">Previous entries</p>
        <div id="journal-entries">
          <div class="journal-entry">
            <div class="journal-date">May 4, 2026 · 😊 Happy</div>
            <div class="journal-text">Feeling a bit better today. Yoga this morning helped. Pain was manageable at about 3/10. Tried the turmeric golden milk — actually quite nice.</div>
          </div>
          <div class="journal-entry">
            <div class="journal-date">May 3, 2026 · 😤 Frustrated</div>
            <div class="journal-text">Really struggling with the bloating again. Had to cancel lunch with a friend which upset me. Called my sister and felt better. Need to remember to track my food triggers more carefully.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ===== TRIGGER DIARY ===== -->
    <div class="page" id="page-triggers">
      <div class="page-header">
        <h1 class="page-title">Trigger diary</h1>
        <p class="page-sub">Log suspected flare triggers and surface patterns over time</p>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">Today's potential triggers</p>
        <p style="font-size:12px;color:var(--text3);margin-bottom:10px">Select everything that applies today</p>

        <p style="font-size:12px;font-weight:500;color:var(--text2);margin-bottom:6px">Food & drink</p>
        <div class="trigger-grid" style="margin-bottom:14px">
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Gluten</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Dairy</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Alcohol</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Caffeine</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Red meat</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Sugar</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Processed food</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Soy</button>
        </div>

        <p style="font-size:12px;font-weight:500;color:var(--text2);margin-bottom:6px">Lifestyle & environment</p>
        <div class="trigger-grid" style="margin-bottom:14px">
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">High stress</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Poor sleep</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Cold weather</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Travel</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Skipped meal</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Intense exercise</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Dehydration</button>
          <button class="trigger-btn" onclick="this.classList.toggle('sel')">Period coming</button>
        </div>

        <button class="btn btn-primary" onclick="saveTriggers()">Save trigger log</button>
      </div>

      <div class="card">
        <p class="param-label">Pattern analysis — top triggers (last 30 days)</p>
        <div style="display:flex;flex-direction:column;gap:8px;margin-top:8px">
          <div style="display:flex;align-items:center;gap:10px"><span style="font-size:13px;color:var(--text);min-width:120px">Gluten</span><div style="flex:1;background:#F5F1EE;border-radius:4px;height:8px"><div style="width:80%;height:100%;background:var(--rose);border-radius:4px"></div></div><span style="font-size:12px;color:var(--text3)">10/14 days</span></div>
          <div style="display:flex;align-items:center;gap:10px"><span style="font-size:13px;color:var(--text);min-width:120px">High stress</span><div style="flex:1;background:#F5F1EE;border-radius:4px;height:8px"><div style="width:65%;height:100%;background:var(--amber);border-radius:4px"></div></div><span style="font-size:12px;color:var(--text3)">8/14 days</span></div>
          <div style="display:flex;align-items:center;gap:10px"><span style="font-size:13px;color:var(--text);min-width:120px">Poor sleep</span><div style="flex:1;background:#F5F1EE;border-radius:4px;height:8px"><div style="width:55%;height:100%;background:var(--purple);border-radius:4px"></div></div><span style="font-size:12px;color:var(--text3)">7/14 days</span></div>
          <div style="display:flex;align-items:center;gap:10px"><span style="font-size:13px;color:var(--text);min-width:120px">Alcohol</span><div style="flex:1;background:#F5F1EE;border-radius:4px;height:8px"><div style="width:35%;height:100%;background:var(--coral);border-radius:4px"></div></div><span style="font-size:12px;color:var(--text3)">4/14 days</span></div>
          <div style="display:flex;align-items:center;gap:10px"><span style="font-size:13px;color:var(--text);min-width:120px">Dairy</span><div style="flex:1;background:#F5F1EE;border-radius:4px;height:8px"><div style="width:25%;height:100%;background:var(--blue);border-radius:4px"></div></div><span style="font-size:12px;color:var(--text3)">3/14 days</span></div>
        </div>
      </div>
    </div>

    <!-- ===== TRENDS ===== -->
    <div class="page" id="page-trends">
      <div class="page-header">
        <h1 class="page-title">Trends & data</h1>
        <p class="page-sub">3-month symptom overview and cycle analysis</p>
      </div>

      <div class="grid-4" style="margin-bottom:14px">
        <div class="stat-card"><div class="stat-val">3.1</div><div class="stat-lbl">Avg daily pain</div><div class="stat-delta delta-down">↓ 0.4 vs last month</div></div>
        <div class="stat-card"><div class="stat-val">27.8</div><div class="stat-lbl">Avg cycle length</div><div class="stat-delta delta-down">↓ Stable</div></div>
        <div class="stat-card"><div class="stat-val">6.4</div><div class="stat-lbl">Avg sleep score</div><div class="stat-delta delta-up">↑ 0.2 vs last month</div></div>
        <div class="stat-card"><div class="stat-val">84%</div><div class="stat-lbl">Med adherence</div><div class="stat-delta delta-down">↑ Great</div></div>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">3-month pain heatmap</p>
        <div class="heatmap-grid" id="heatmap"></div>
        <div style="display:flex;align-items:center;gap:8px;margin-top:8px">
          <span style="font-size:11px;color:var(--text3)">Low</span>
          <div style="display:flex;gap:2px">
            <div style="width:16px;height:10px;border-radius:2px;background:#F5F1EE"></div>
            <div style="width:16px;height:10px;border-radius:2px;background:#F4C0D1"></div>
            <div style="width:16px;height:10px;border-radius:2px;background:#ED93B1"></div>
            <div style="width:16px;height:10px;border-radius:2px;background:var(--rose)"></div>
            <div style="width:16px;height:10px;border-radius:2px;background:var(--rose-dark)"></div>
          </div>
          <span style="font-size:11px;color:var(--text3)">High</span>
        </div>
      </div>

      <div class="card" style="margin-bottom:14px">
        <p class="param-label">Pain over 12 weeks</p>
        <div class="chart-wrap"><canvas id="trends-chart"></canvas></div>
      </div>

      <div class="card">
        <p class="param-label">Symptom correlation matrix</p>
        <div style="overflow-x:auto">
          <table style="width:100%;font-size:12px;border-collapse:collapse">
            <thead><tr><th style="text-align:left;padding:8px;color:var(--text2);font-weight:500">Symptom</th><th style="padding:8px;color:var(--text2);font-weight:500">Pain</th><th style="padding:8px;color:var(--text2);font-weight:500">Bloating</th><th style="padding:8px;color:var(--text2);font-weight:500">Fatigue</th><th style="padding:8px;color:var(--text2);font-weight:500">Sleep</th></tr></thead>
            <tbody>
              <tr><td style="padding:8px;color:var(--text)">Gluten intake</td><td style="padding:8px;text-align:center"><span class="badge badge-rose">0.72</span></td><td style="padding:8px;text-align:center"><span class="badge badge-rose">0.68</span></td><td style="padding:8px;text-align:center"><span class="badge badge-amber">0.41</span></td><td style="padding:8px;text-align:center"><span class="badge badge-teal">0.18</span></td></tr>
              <tr><td style="padding:8px;color:var(--text)">Stress level</td><td style="padding:8px;text-align:center"><span class="badge badge-rose">0.65</span></td><td style="padding:8px;text-align:center"><span class="badge badge-amber">0.44</span></td><td style="padding:8px;text-align:center"><span class="badge badge-rose">0.70</span></td><td style="padding:8px;text-align:center"><span class="badge badge-rose">0.61</span></td></tr>
              <tr><td style="padding:8px;color:var(--text)">Exercise done</td><td style="padding:8px;text-align:center"><span class="badge badge-teal">-0.52</span></td><td style="padding:8px;text-align:center"><span class="badge badge-teal">-0.38</span></td><td style="padding:8px;text-align:center"><span class="badge badge-teal">-0.45</span></td><td style="padding:8px;text-align:center"><span class="badge badge-teal">-0.40</span></td></tr>
            </tbody>
          </table>
        </div>
        <p style="font-size:11px;color:var(--text3);margin-top:8px">Positive = increases symptom. Negative = reduces symptom. Based on Pearson correlation of your logged data.</p>
      </div>
    </div>

    <!-- ===== COPING TOOLKIT ===== -->
    <div class="page" id="page-coping">
      <div class="page-header">
        <h1 class="page-title">Coping toolkit</h1>
        <p class="page-sub">Evidence-based tools for pain management and emotional wellbeing</p>
      </div>

      <div class="toolkit-card" onclick="toggleToolkit(this)">
        <div class="toolkit-header">
          <span class="toolkit-icon">🌬️</span>
          <div><div class="toolkit-title">Box breathing (4-4-4-4)</div><div class="toolkit-sub">Calms the nervous system · reduces pain perception · 5 minutes</div></div>
        </div>
        <div class="toolkit-detail" id="breath-detail">
          <div class="breath-text" id="breath-instruction">Press start to begin</div>
          <div class="breath-circle" id="breath-circle">Start</div>
          <div style="display:flex;gap:8px;justify-content:center">
            <button class="btn btn-primary btn-sm" onclick="event.stopPropagation();startBreath()">Start</button>
            <button class="btn btn-outline btn-sm" onclick="event.stopPropagation();stopBreath()">Stop</button>
          </div>
        </div>
      </div>

      <div class="toolkit-card" onclick="toggleToolkit(this)">
        <div class="toolkit-header">
          <span class="toolkit-icon">🔥</span>
          <div><div class="toolkit-title">Heat therapy guide</div><div class="toolkit-sub">Proven to reduce pelvic pain · application tips</div></div>
        </div>
        <div class="toolkit-detail">
          Apply a heat pad or hot water bottle to your lower abdomen or back at 40–45°C. Use for 15–30 minutes at a time. Always place a cloth between the heat source and skin. Heat increases blood flow and relaxes smooth muscle — clinically shown to reduce endo-related cramping. Do not use on open wounds or after surgery until healed.
        </div>
      </div>

      <div class="toolkit-card" onclick="toggleToolkit(this)">
        <div class="toolkit-header">
          <span class="toolkit-icon">🧠</span>
          <div><div class="toolkit-title">Pain reframing — mindfulness</div><div class="toolkit-sub">CBT-based technique · separate pain sensation from suffering</div></div>
        </div>
        <div class="toolkit-detail">
          Notice the pain without judgement. Describe it neutrally: "There is a sensation of pressure in my lower abdomen." Avoid catastrophising language ("this is unbearable") and replace with observational language. Research shows this reduces the emotional amplification of chronic pain over time. Pair with slow diaphragmatic breathing.
        </div>
      </div>

      <div class="toolkit-card" onclick="toggleToolkit(this)">
        <div class="toolkit-header">
          <span class="toolkit-icon">💬</span>
          <div><div class="toolkit-title">How to talk to your employer</div><div class="toolkit-sub">Template script for accommodation conversations</div></div>
        </div>
        <div class="toolkit-detail">
          "I have a chronic condition called endometriosis which occasionally affects my ability to work at full capacity, particularly around my menstrual cycle. I would like to discuss reasonable adjustments such as flexible start times, the option to work from home on high-symptom days, and clarity around sick leave policies for chronic conditions. I have a letter from my gynaecologist if helpful."<br><br>
          <button class="btn btn-outline btn-sm" onclick="event.stopPropagation();printSection('employer-letter')">Download template →</button>
        </div>
      </div>

      <div class="toolkit-card" onclick="toggleToolkit(this)">
        <div class="toolkit-header">
          <span class="toolkit-icon">🤝</span>
          <div><div class="toolkit-title">Community & support resources</div><div class="toolkit-sub">You are not alone — endo affects ~190 million worldwide</div></div>
        </div>
        <div class="toolkit-detail">
          <strong>UK:</strong> Endometriosis UK (endometriosis-uk.org) · helpline 0808 808 2227<br>
          <strong>US:</strong> Endometriosis Foundation of America (endofound.org)<br>
          <strong>India:</strong> Endometriosis Society of India (endometriosisindia.com)<br>
          <strong>Global:</strong> World Endometriosis Society (endometriosis.ca)<br>
          <strong>Mental health:</strong> Endo and mental health are closely linked — please reach out to a therapist if you are struggling emotionally.
        </div>
      </div>

      <div class="toolkit-card" onclick="toggleToolkit(this)">
        <div class="toolkit-header">
          <span class="toolkit-icon">🧊</span>
          <div><div class="toolkit-title">Emergency flare kit checklist</div><div class="toolkit-sub">Be prepared for unexpected high-pain days</div></div>
        </div>
        <div class="toolkit-detail">
          ☑ Heat pad or hot water bottle<br>
          ☑ PRN pain medication (Ibuprofen / Naproxen)<br>
          ☑ TENS machine (if you use one)<br>
          ☑ Comfortable loose clothing<br>
          ☑ Herbal teas (ginger, chamomile)<br>
          ☑ Phone charger (you may be resting for hours)<br>
          ☑ Emergency contacts list (doctor, trusted person)<br>
          ☑ Pre-written message to cancel plans if needed
        </div>
      </div>
    </div>

    <!-- ===== DOCTORS ===== -->
    <div class="page" id="page-doctors">
      <div class="page-header">
        <h1 class="page-title">My medical team</h1>
        <p class="page-sub">Your specialists and contacts in one place</p>
      </div>

      <div class="doctor-card">
        <div class="doc-avatar">SK</div>
        <div class="doc-info">
          <div class="doc-name">Dr. Sunita Kapoor</div>
          <div class="doc-spec">Gynaecologist · Endometriosis specialist</div>
          <div style="font-size:12px;color:var(--text3);margin-top:2px">Apollo Hospital, Delhi · Next appt: June 12</div>
        </div>
        <div class="doc-actions">
          <button class="btn btn-outline btn-sm" onclick="showToast('Calling Dr. Kapoor...')">📞</button>
          <button class="btn btn-outline btn-sm" onclick="showToast('Opening appointment notes...')">📋</button>
        </div>
      </div>

      <div class="doctor-card">
        <div class="doc-avatar" style="background:var(--blue-light);color:var(--blue)">RG</div>
        <div class="doc-info">
          <div class="doc-name">Dr. Rohan Gupta</div>
          <div class="doc-spec">Reproductive Endocrinologist</div>
          <div style="font-size:12px;color:var(--text3);margin-top:2px">Max Fertility Centre · Fertility consultation</div>
        </div>
        <div class="doc-actions">
          <button class="btn btn-outline btn-sm" onclick="showToast('Calling Dr. Gupta...')">📞</button>
          <button class="btn btn-outline btn-sm" onclick="showToast('Opening notes...')">📋</button>
        </div>
      </div>

      <div class="doctor-card">
        <div class="doc-avatar" style="background:var(--purple-light);color:var(--purple)">AM</div>
        <div class="doc-info">
          <div class="doc-name">Ananya Menon</div>
          <div class="doc-spec">Pelvic physiotherapist</div>
          <div style="font-size:12px;color:var(--text3);margin-top:2px">Physio First Clinic · Monthly sessions</div>
        </div>
        <div class="doc-actions">
          <button class="btn btn-outline btn-sm" onclick="showToast('Calling Ananya...')">📞</button>
          <button class="btn btn-outline btn-sm" onclick="showToast('Opening notes...')">📋</button>
        </div>
      </div>

      <button class="btn btn-outline" style="margin-top:8px;width:100%" onclick="showToast('Add doctor feature — coming in full version')">+ Add doctor or specialist</button>
    </div>

    <!-- ===== APPOINTMENT REPORT ===== -->
    <div class="page" id="page-report">
      <div class="page-header">
        <h1 class="page-title">Appointment report</h1>
        <p class="page-sub">Auto-generated 1-page summary to bring to your gynaecologist</p>
      </div>

      <div id="report-content">
        <div class="report-section">
          <div class="report-section-title">Patient summary</div>
          <div style="font-size:13px;color:var(--text);line-height:1.8">
            <strong>Name:</strong> <span id="report-name">User</span><br>
            <strong>Report period:</strong> April 6 – May 5, 2026<br>
            <strong>Cycle length:</strong> 28 days (average)<br>
            <strong>Days logged:</strong> 24 of 30
          </div>
        </div>

        <div class="report-section">
          <div class="report-section-title">Symptom summary</div>
          <div style="font-size:13px;color:var(--text);line-height:1.8">
            <strong>Average daily pain:</strong> 3.1/10<br>
            <strong>Peak pain:</strong> 7/10 (April 26 — day 25 of cycle)<br>
            <strong>Most common symptoms:</strong> Pelvic pain, bloating, fatigue<br>
            <strong>Pain locations:</strong> Pelvis, lower back (primary); left thigh (occasional)
          </div>
        </div>

        <div class="report-section">
          <div class="report-section-title">Medications taken</div>
          <div style="font-size:13px;color:var(--text);line-height:1.8">
            Dienogest 2mg — 84% adherence<br>
            Ibuprofen 400mg — used 8 days (PRN)<br>
            Vitamin D3 2000IU — daily<br>
            Magnesium 300mg — most evenings
          </div>
        </div>

        <div class="report-section">
          <div class="report-section-title">Suspected triggers identified</div>
          <div style="font-size:13px;color:var(--text)">Gluten (correlation 0.72 with pain flares), stress (0.65), poor sleep (0.61)</div>
        </div>

        <div class="report-section">
          <div class="report-section-title">Questions for my doctor</div>
          <textarea style="width:100%;padding:10px;border:1px solid var(--border);border-radius:8px;font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text);min-height:80px;resize:vertical;outline:none" placeholder="Add questions you want to ask at your appointment...">1. Should I consider changing from Dienogest to a different hormonal treatment?
2. Is my AMH level worth testing given my symptoms?
3. Would a repeat laparoscopy be beneficial?</textarea>
        </div>
      </div>

      <div style="display:flex;gap:8px;margin-top:14px">
        <button class="btn btn-primary" onclick="showToast('Generating PDF report...')">📄 Download PDF</button>
        <button class="btn btn-outline" onclick="window.print()">🖨️ Print report</button>
      </div>
    </div>

    <!-- ===== EXPORT ===== -->
    <div class="page" id="page-export">
      <div class="page-header">
        <h1 class="page-title">Export data</h1>
        <p class="page-sub">Download your health data in different formats</p>
      </div>

      <div class="export-option" onclick="exportCSV()">
        <span class="export-icon">📊</span>
        <div class="export-info">
          <div class="export-name">Export as CSV</div>
          <div class="export-sub">All symptom data, pain scores, and medication logs — spreadsheet compatible</div>
        </div>
        <button class="btn btn-outline btn-sm">Download</button>
      </div>

      <div class="export-option" onclick="showToast('PDF export — generating...')">
        <span class="export-icon">📄</span>
        <div class="export-info">
          <div class="export-name">Monthly report PDF</div>
          <div class="export-sub">Formatted summary for your doctor — includes trends, meds, and triggers</div>
        </div>
        <button class="btn btn-outline btn-sm">Download</button>
      </div>

      <div class="export-option" onclick="showToast('Apple Health integration — configure in Settings')">
        <span class="export-icon">🍎</span>
        <div class="export-info">
          <div class="export-name">Sync with Apple Health</div>
          <div class="export-sub">Share pain scores and cycle data with your Health app</div>
        </div>
        <button class="btn btn-outline btn-sm">Connect</button>
      </div>

      <div class="export-option" onclick="showToast('Google Fit integration — configure in Settings')">
        <span class="export-icon">🏃</span>
        <div class="export-info">
          <div class="export-name">Sync with Google Fit</div>
          <div class="export-sub">Exercise, sleep, and heart rate data integration</div>
        </div>
        <button class="btn btn-outline btn-sm">Connect</button>
      </div>

      <div class="disclaimer" style="margin-top:14px">Your data is stored locally in your browser. No data is sent to any server. You own your health data.</div>
    </div>

  </main>
</div>

<!-- Chart.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>

<script>
// ===== STATE =====
let userName = '';
let activeZones = [];
let breathTimer = null;
let heatTimerInterval = null;
let breathPhase = 0;
let breathRunning = false;
let journalEntries = [];
const medData = [
  {name:'Dienogest 2mg', dose:'Hormonal therapy · once daily', time:'8:00 AM', taken:false},
  {name:'Ibuprofen 400mg', dose:'Pain relief · as needed', time:'PRN', taken:false},
  {name:'Vitamin D3 2000IU', dose:'Supplement · with breakfast', time:'8:00 AM', taken:true},
  {name:'Magnesium 300mg', dose:'Supplement · evening', time:'9:00 PM', taken:false}
];

const trackerParams = [
  {id:'pain', label:'Pain level', max:5, color:'sel-rose'},
  {id:'bloat', label:'Bloating', max:5, color:'sel-amber'},
  {id:'fatigue', label:'Fatigue', max:5, color:'sel-purple'},
  {id:'flow', label:'Flow', max:4, color:'sel-rose'},
  {id:'mood', label:'Mood', max:5, color:'sel-teal'},
  {id:'sleep', label:'Sleep quality', max:5, color:'sel-blue'},
];

const qaAnswers = {
  'What is adenomyosis?': 'Adenomyosis occurs when endometrial-like tissue grows into the muscular wall of the uterus (the myometrium). It is distinct from endometriosis but frequently co-exists with it. Symptoms include heavy, painful periods, pelvic pressure, and an enlarged uterus. Diagnosis is typically via MRI or ultrasound. Treatments range from hormonal therapy to hysterectomy in severe cases.',
  'Can endo affect fertility?': 'Yes — endometriosis can affect fertility through pelvic inflammation, scar tissue (adhesions), distorted anatomy, reduced egg quality, and impact on ovarian reserve. However, many people with endometriosis do conceive naturally, and the stage of disease does not always correlate with fertility outcomes. Options include expectant management, IUI, IVF, and surgical intervention. A reproductive endocrinologist can assess your specific situation.',
  'What foods reduce inflammation?': 'Anti-inflammatory foods beneficial in endometriosis include: oily fish rich in omega-3 (salmon, mackerel, sardines), leafy green vegetables (spinach, kale), berries, turmeric and ginger, flaxseeds, walnuts, and extra-virgin olive oil. Many people find reducing gluten, dairy, red meat, alcohol, and refined sugar also helps symptom load. Individual responses vary — a food diary can help identify personal triggers.',
  'Is laparoscopy worth it?': 'Laparoscopy is the gold standard for both diagnosing and surgically treating endometriosis. For many people it significantly reduces pain, improves quality of life, and can improve fertility. Benefits depend on the surgeon\'s expertise (an excision specialist is preferable to ablation), the stage of disease, and your goals. Risks include anaesthesia, infection, and organ injury — all rare with experienced surgeons. Discuss this carefully with your specialist.',
  'What is the endo belly?': 'Endo belly refers to severe abdominal bloating that many endometriosis patients experience, often dramatically — some describe going from flat to looking visibly pregnant within hours. It is thought to be caused by gastrointestinal inflammation, bowel adhesions, and gut-hormone interactions related to endo. It can be triggered by certain foods, stress, or the menstrual cycle. Dietary changes (low-FODMAP, gluten-free) and treating the underlying endo can help.',
  'Can endo cause bowel symptoms?': 'Yes — bowel endometriosis is common. Symptoms include painful bowel movements, diarrhoea or constipation (often cyclical), bloating, rectal bleeding during menstruation, and pain during defecation. Deep infiltrating endometriosis (DIE) on the bowel can be severe. Diagnosis requires specialist MRI. Treatment options include hormonal therapy, dietary changes, and in severe cases bowel surgery. Always discuss these symptoms with your gynaecologist.',
  'What is dienogest?': 'Dienogest is a synthetic progestogen (progesterone-like hormone) specifically licensed for treating endometriosis in many countries. It is taken orally once daily and works by reducing estrogen levels locally, causing endometrial tissue to atrophy (shrink). It is generally well-tolerated, though side effects can include irregular bleeding, mood changes, and headaches. It is not a contraceptive. Research supports its effectiveness in reducing endometriosis-related pain.',
  'How do I explain endo to my employer?': 'Key points to communicate: Endometriosis is a recognised chronic condition affecting approximately 1 in 10 people with a uterus. It causes cyclical and sometimes constant pain, fatigue, and other debilitating symptoms. It is not "bad periods" — it is a systemic disease. You may need flexibility around high-symptom days, remote working options, or adjustments to sick leave policies. A letter from your gynaecologist can support your case. In many countries, endo may qualify as a disability for workplace accommodation purposes.'
};

const foodPlan = {
  mon:{meals:[{name:'Breakfast',phase:'Anti-inflammatory',items:[{t:'Overnight oats with chia seeds',tag:'omega-3'},{t:'Wild blueberries + walnuts',tag:'antioxidant'},{t:'Turmeric golden milk',tag:'anti-inflam'}]},{name:'Lunch',phase:'Iron-rich',items:[{t:'Lentil soup with spinach',tag:'iron'},{t:'Pumpkin seeds',tag:'zinc'},{t:'Gluten-free bread',tag:'gut-friendly',avoid:false}]},{name:'Dinner',phase:'Hormone support',items:[{t:'Baked salmon, broccoli, quinoa',tag:'DHA'},{t:'Olive oil & garlic dressing',tag:'anti-inflam'},{t:'Ginger green tea',tag:'digestion'}]}]},
  tue:{meals:[{name:'Breakfast',phase:'Gut-friendly',items:[{t:'Smoothie: banana, spinach, flaxseed',tag:'fibre'},{t:'Ginger + lemon water',tag:'anti-inflam'},{t:'Handful of walnuts',tag:'omega-3'}]},{name:'Lunch',phase:'Anti-inflammatory',items:[{t:'Grilled sardines on salad',tag:'omega-3'},{t:'Cherry tomatoes, cucumber, olive oil',tag:'lycopene'},{t:'Avoid: wheat crackers',tag:'gluten',avoid:true}]},{name:'Dinner',phase:'Iron-rich',items:[{t:'Chickpea & sweet potato curry',tag:'iron'},{t:'Brown rice',tag:'complex carb'},{t:'Mint & coriander raita (coconut yogurt)',tag:'probiotic'}]}]},
  wed:{meals:[{name:'Breakfast',phase:'Energy',items:[{t:'Scrambled eggs, avocado, GF toast',tag:'protein'},{t:'Orange juice (small)',tag:'vitamin C'}]},{name:'Lunch',phase:'Anti-inflammatory',items:[{t:'Miso soup with tofu & seaweed',tag:'phytoestrogen'},{t:'Brown rice bowl with edamame',tag:'protein'},{t:'Ginger dressing',tag:'anti-inflam'}]},{name:'Dinner',phase:'Hormone support',items:[{t:'Roast chicken with turmeric rub',tag:'protein'},{t:'Roasted cauliflower, broccoli',tag:'cruciferous'},{t:'Bone broth gravy',tag:'gut-healing'}]}]},
  thu:{meals:[{name:'Breakfast',phase:'Antioxidant',items:[{t:'Acai bowl with berries, coconut',tag:'antioxidant'},{t:'Chia seeds, hemp seeds',tag:'omega-3'}]},{name:'Lunch',phase:'Iron-rich',items:[{t:'Black bean tacos (corn tortilla)',tag:'iron'},{t:'Guacamole, pico de gallo',tag:'anti-inflam'},{t:'Lime water',tag:'alkaline'}]},{name:'Dinner',phase:'Anti-inflammatory',items:[{t:'Baked mackerel with fennel',tag:'omega-3'},{t:'Asparagus, roasted beets',tag:'folate'},{t:'Lemon tahini dressing',tag:'calcium'}]}]},
  fri:{meals:[{name:'Breakfast',phase:'Gut-friendly',items:[{t:'Kefir (coconut) with berries',tag:'probiotic'},{t:'Gluten-free granola',tag:'fibre'}]},{name:'Lunch',phase:'Protein',items:[{t:'Quinoa & roasted vegetable salad',tag:'complete protein'},{t:'Pumpkin seeds, feta (or vegan alt)',tag:'zinc'},{t:'Avoid: croutons',tag:'gluten',avoid:true}]},{name:'Dinner',phase:'Hormone support',items:[{t:'Stir-fry: tofu, bok choy, ginger',tag:'phytoestrogen'},{t:'Brown rice noodles',tag:'GF'},{t:'Tamari soy sauce (GF)',tag:'umami'}]}]},
  sat:{meals:[{name:'Breakfast',phase:'Indulgent & healing',items:[{t:'GF pancakes, blueberries, maple syrup',tag:'treat'},{t:'Matcha latte with oat milk',tag:'antioxidant'}]},{name:'Lunch',phase:'Anti-inflammatory',items:[{t:'Avocado toast on GF bread',tag:'healthy fats'},{t:'Smoked salmon, capers',tag:'omega-3'},{t:'Tomato, red onion, dill',tag:'anti-inflam'}]},{name:'Dinner',phase:'Relaxing',items:[{t:'Lamb tagine (lean, with turmeric)',tag:'iron'},{t:'Couscous (GF: cauliflower rice)',tag:'option'},{t:'Herbal chamomile tea',tag:'calming'}]}]},
  sun:{meals:[{name:'Breakfast',phase:'Prep day',items:[{t:'Poached eggs on wilted spinach',tag:'iron + protein'},{t:'Sliced avocado',tag:'healthy fats'},{t:'Freshly squeezed juice',tag:'vitamin C'}]},{name:'Lunch',phase:'Batch cook',items:[{t:'Big pot of lentil dal',tag:'meal prep'},{t:'Roasted vegetables (tray)',tag:'batch'},{t:'Brown rice (batch cook)',tag:'energy'}]},{name:'Dinner',phase:'Light & easy',items:[{t:'Vegetable soup (homemade)',tag:'anti-inflam'},{t:'GF bread with olive oil',tag:'simple'},{t:'Early night prep',tag:'self-care'}]}]}
};

// ===== INIT =====
window.onload = function(){
  buildTrackerParams();
  buildMedList();
  buildCycleVis();
  buildHeatmap();
  buildFoodDay('mon');
  setTimeout(buildCharts, 300);
};

// ===== ONBOARDING =====
let obStep = 1;
function nextOb(n){
  document.getElementById('ob'+obStep).classList.remove('active');
  obStep = n;
  document.getElementById('ob'+n).classList.add('active');
  for(let i=1;i<=4;i++){
    document.getElementById('pip'+i).classList.toggle('done', i<=n);
  }
}
function obSel(el, group){
  el.closest('.ob-options').querySelectorAll('.ob-opt').forEach(b=>b.classList.remove('sel'));
  el.classList.add('sel');
}
function finishOnboarding(){
  userName = document.getElementById('ob-name-input').value || 'there';
  document.getElementById('dash-name').textContent = userName;
  document.getElementById('report-name').textContent = userName;
  document.getElementById('onboarding').style.display = 'none';
}

// ===== NAVIGATION =====
function showPage(id, btn){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(b=>b.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  if(btn) btn.classList.add('active');
  else {
    document.querySelectorAll('.nav-item').forEach(b=>{
      if(b.getAttribute('onclick') && b.getAttribute('onclick').includes("'"+id+"'")) b.classList.add('active');
    });
  }
}

// ===== TRACKER =====
function buildTrackerParams(){
  const grid = document.getElementById('tracker-params');
  grid.innerHTML = '';
  trackerParams.forEach(p=>{
    const card = document.createElement('div');
    card.className = 'card-sm';
    card.innerHTML = `<p class="param-label">${p.label}</p><div class="dot-row" id="dots-${p.id}"></div>`;
    grid.appendChild(card);
    const row = document.getElementById('dots-'+p.id);
    for(let i=1;i<=p.max;i++){
      const d = document.createElement('div');
      d.className = 'dot';
      d.textContent = i;
      d.onclick = function(){
        row.querySelectorAll('.dot').forEach(x=>x.className='dot');
        d.className = 'dot '+p.color;
      };
      row.appendChild(d);
    }
  });
}

function logToday(){
  showToast('Entry saved — great job tracking!');
  updateReadiness();
}

function updateReadiness(){
  const score = Math.floor(Math.random()*30)+60;
  document.getElementById('readiness-num').textContent = score;
  const el = document.getElementById('readiness-circle');
  el.className = 'readiness-circle ' + (score>70?'readiness-green':score>50?'readiness-amber':'readiness-red');
}

// ===== PAIN MAP =====
function toggleZone(el, name){
  const idx = activeZones.indexOf(name);
  const shapes = el.querySelectorAll('circle,rect');
  if(idx === -1){
    activeZones.push(name);
    shapes.forEach(s=>{
      s.style.fill = 'rgba(201,75,123,0.25)';
      s.style.stroke = 'var(--rose)';
      s.style.strokeWidth = '2';
    });
  } else {
    activeZones.splice(idx,1);
    shapes.forEach(s=>{
      s.style.fill = 'transparent';
      s.style.stroke = 'transparent';
    });
  }
  updateZonesList();
}

function updateZonesList(){
  const list = document.getElementById('pain-zones-list');
  const sliders = document.getElementById('pain-intensity-sliders');
  if(activeZones.length===0){
    list.textContent = 'None selected — tap the body map';
    sliders.innerHTML = '<p style="font-size:13px;color:var(--text3)">Select zones first</p>';
    return;
  }
  list.innerHTML = activeZones.map(z=>`<span class="badge badge-rose" style="margin:3px">${z}</span>`).join('');
  sliders.innerHTML = activeZones.map(z=>`
    <div class="slider-row" style="margin-bottom:10px">
      <span class="slider-label" style="font-size:12px">${z}</span>
      <input type="range" min="0" max="10" value="3" step="1" oninput="this.nextElementSibling.textContent=this.value">
      <span class="slider-val">3</span>
    </div>
  `).join('');
}

// ===== FOOD =====
function selFoodDay(btn, day){
  document.querySelectorAll('.food-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  buildFoodDay(day);
}
function buildFoodDay(day){
  const plan = foodPlan[day] || foodPlan['mon'];
  const el = document.getElementById('food-content');
  el.innerHTML = plan.meals.map(m=>`
    <div class="meal-card">
      <div class="meal-head">
        <span class="meal-name">${m.name}</span>
        <span class="badge badge-teal">${m.phase}</span>
      </div>
      <div class="meal-body">
        ${m.items.map(i=>`
          <div class="food-item">
            <span class="food-dot ${i.avoid?'red':i.amber?'amber':''}"></span>
            ${i.t}
            <span class="food-tag-sm">${i.tag}</span>
          </div>
        `).join('')}
      </div>
    </div>
  `).join('');
}

// ===== MEDS =====
function buildMedList(){
  const list = document.getElementById('med-list');
  list.innerHTML = medData.map((m,i)=>`
    <div class="med-row ${m.taken?'taken':''}" id="med-row-${i}">
      <div class="med-check ${m.taken?'done':''}" id="med-check-${i}" onclick="toggleMed(${i})"></div>
      <div class="med-info">
        <div class="med-name">${m.name}</div>
        <div class="med-dose">${m.dose}</div>
      </div>
      <span class="med-time-tag">${m.time}</span>
    </div>
  `).join('');
}
function toggleMed(i){
  medData[i].taken = !medData[i].taken;
  buildMedList();
  showToast(medData[i].taken ? `${medData[i].name} marked as taken ✓` : `${medData[i].name} unmarked`);
}
function addMedPrompt(){showToast('Add medication feature — enter details in full app');}

// ===== Q&A =====
function fillQ(btn){
  document.getElementById('qa-input').value = btn.textContent;
}
function askQ(){
  const q = document.getElementById('qa-input').value.trim();
  if(!q) return;
  const typing = document.getElementById('qa-typing');
  const ans = document.getElementById('qa-answer');
  ans.style.display = 'none';
  typing.style.display = 'block';
  setTimeout(()=>{
    typing.style.display = 'none';
    ans.style.display = 'block';
    ans.textContent = qaAnswers[q] || 'Endometriosis is a complex, highly individual condition. For this specific question, we recommend consulting your gynaecologist or endometriosis specialist who can review your full clinical history and provide personalised, evidence-based guidance.';
  }, 1200);
}
function clearQ(){
  document.getElementById('qa-input').value = '';
  document.getElementById('qa-answer').style.display = 'none';
  document.getElementById('qa-typing').style.display = 'none';
}

// ===== FERTILITY CYCLE VIS =====
function buildCycleVis(){
  const vis = document.getElementById('cycle-vis');
  const classes = Array(28).fill('follicular');
  [0,1,2,3,4].forEach(i=>classes[i]='menstrual');
  [11,12,13,14,15].forEach(i=>classes[i]='fertile');
  classes[13]='ovulation';
  [15,16,17,18,19,20,21,22,23,24,25,26,27].forEach(i=>classes[i]='luteal');
  vis.innerHTML = classes.map((c,i)=>`
    <div class="cycle-day ${c} ${i===13?'today-ring':''}">${i+1}</div>
  `).join('');
}

// ===== JOURNAL =====
function selMood(el){
  document.querySelectorAll('.mood-emoji').forEach(e=>e.classList.remove('sel'));
  el.classList.add('sel');
}
function fillJournal(el){
  document.getElementById('journal-text').value = el.textContent + '\n\n';
  document.getElementById('journal-text').focus();
}
function saveJournal(){
  const text = document.getElementById('journal-text').value.trim();
  if(!text) return;
  const mood = document.querySelector('.mood-emoji.sel');
  const entry = document.createElement('div');
  entry.className = 'journal-entry';
  entry.innerHTML = `<div class="journal-date">Today · ${mood?mood.textContent:''}</div><div class="journal-text">${text}</div>`;
  document.getElementById('journal-entries').prepend(entry);
  document.getElementById('journal-text').value = '';
  document.querySelectorAll('.mood-emoji').forEach(e=>e.classList.remove('sel'));
  showToast('Journal entry saved');
}

// ===== TRIGGERS =====
function saveTriggers(){
  const sel = Array.from(document.querySelectorAll('#page-triggers .trigger-btn.sel')).map(b=>b.textContent);
  showToast(sel.length>0 ? `${sel.length} triggers logged: ${sel.join(', ')}` : 'No triggers logged today');
}

// ===== HEATMAP =====
function buildHeatmap(){
  const hm = document.getElementById('heatmap');
  const colors = ['#F5F1EE','#F4C0D1','#ED93B1','var(--rose)','#4B1528'];
  const pain = [1,2,1,3,2,4,5,4,3,2,1,2,3,4,6,7,5,4,3,2,1,2,3,4,5,4,3,2];
  hm.innerHTML = pain.map(p=>{
    const ci = Math.min(Math.floor(p/2), 4);
    return `<div class="heat-cell" style="background:${colors[ci]}" title="Pain: ${p}"></div>`;
  }).join('');
}

// ===== CHARTS =====
function buildCharts(){
  // Trend chart (tracker page)
  const tc = document.getElementById('trend-chart');
  if(tc) new Chart(tc, {
    type:'line',
    data:{
      labels:['Apr 29','Apr 30','May 1','May 2','May 3','May 4','May 5'],
      datasets:[{
        label:'Pain', data:[4,5,3,2,3,4,3],
        borderColor:'var(--rose)', backgroundColor:'rgba(201,75,123,0.08)',
        tension:0.4, fill:true, pointBackgroundColor:'var(--rose)'
      },{
        label:'Fatigue', data:[3,4,3,2,2,3,2],
        borderColor:'var(--purple)', backgroundColor:'rgba(127,119,221,0.06)',
        tension:0.4, fill:true, pointBackgroundColor:'var(--purple)'
      }]
    },
    options:{responsive:true, maintainAspectRatio:false, plugins:{legend:{labels:{font:{family:"'DM Sans',sans-serif",size:11},color:'#6B6560'}}}, scales:{y:{min:0,max:10,ticks:{color:'#A09890',font:{family:"'DM Sans',sans-serif",size:10}},grid:{color:'#F5F1EE'}},x:{ticks:{color:'#A09890',font:{family:"'DM Sans',sans-serif",size:10}},grid:{display:false}}}}
  });

  // Forecast chart (predict page)
  const fc = document.getElementById('forecast-chart');
  if(fc) new Chart(fc, {
    type:'bar',
    data:{
      labels:['May 6','May 7','May 8','May 9','May 10','May 11','May 12','May 13','May 14','May 15','May 16','May 17','May 18','May 19'],
      datasets:[{
        label:'Predicted pain',
        data:[3,2,2,3,3,4,4,5,5,6,6,7,5,4],
        backgroundColor: Array(14).fill('').map((_,i)=>i<6?'rgba(29,158,117,0.4)':i<8?'rgba(186,117,23,0.4)':'rgba(201,75,123,0.4)'),
        borderRadius:4
      }]
    },
    options:{responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}}, scales:{y:{min:0,max:10,ticks:{color:'#A09890',font:{family:"'DM Sans',sans-serif",size:10}},grid:{color:'#F5F1EE'}},x:{ticks:{color:'#A09890',font:{family:"'DM Sans',sans-serif",size:9}},grid:{display:false}}}}
  });

  // Trends 12-week chart
  const tnc = document.getElementById('trends-chart');
  if(tnc) new Chart(tnc, {
    type:'line',
    data:{
      labels:['Feb W1','Feb W2','Feb W3','Feb W4','Mar W1','Mar W2','Mar W3','Mar W4','Apr W1','Apr W2','Apr W3','Apr W4'],
      datasets:[{
        label:'Avg pain', data:[4.2,3.8,5.1,6.2,3.9,3.5,4.8,5.9,3.7,3.2,4.4,5.6],
        borderColor:'var(--rose)', backgroundColor:'rgba(201,75,123,0.08)',
        tension:0.4, fill:true
      },{
        label:'Avg fatigue', data:[3.5,3.2,4.2,5.0,3.3,3.0,4.0,4.8,3.1,2.8,3.8,4.6],
        borderColor:'var(--purple)', backgroundColor:'rgba(127,119,221,0.06)',
        tension:0.4, fill:true
      }]
    },
    options:{responsive:true, maintainAspectRatio:false, plugins:{legend:{labels:{font:{family:"'DM Sans',sans-serif",size:11},color:'#6B6560'}}}, scales:{y:{min:0,max:10,ticks:{color:'#A09890',font:{family:"'DM Sans',sans-serif",size:10}},grid:{color:'#F5F1EE'}},x:{ticks:{color:'#A09890',font:{family:"'DM Sans',sans-serif",size:9}},grid:{display:false}}}}
  });
}

// ===== COPING TOOLKIT =====
function toggleToolkit(card){
  const detail = card.querySelector('.toolkit-detail');
  detail.classList.toggle('open');
}

// Box breathing
const phases = ['Inhale...','Hold...','Exhale...','Hold...'];
const phaseColors = ['var(--teal-light)','var(--purple-light)','var(--rose-light)','var(--amber-light)'];
const phaseBorder = ['var(--teal)','var(--purple)','var(--rose)','var(--amber)'];
let breathCount = 0;
function startBreath(){
  if(breathRunning) return;
  breathRunning = true;
  runBreath();
}
function runBreath(){
  if(!breathRunning) return;
  const circle = document.getElementById('breath-circle');
  const instr = document.getElementById('breath-instruction');
  const idx = breathCount % 4;
  circle.textContent = phases[idx];
  circle.style.background = phaseColors[idx];
  circle.style.borderColor = phaseBorder[idx];
  instr.textContent = `${phases[idx]} for 4 seconds (round ${Math.floor(breathCount/4)+1})`;
  const scale = idx===0||idx===3?'scale(1)':idx===1?'scale(1.15)':'scale(0.9)';
  circle.style.transform = scale;
  breathCount++;
  breathTimer = setTimeout(runBreath, 4000);
}
function stopBreath(){
  breathRunning = false;
  clearTimeout(breathTimer);
  breathCount = 0;
  const circle = document.getElementById('breath-circle');
  circle.textContent = 'Start';
  circle.style.background = 'var(--rose-light)';
  circle.style.borderColor = 'var(--rose-mid)';
  circle.style.transform = 'scale(1)';
  document.getElementById('breath-instruction').textContent = 'Press start to begin';
}

// Heat timer
function startHeatTimer(){
  if(heatTimerInterval) clearInterval(heatTimerInterval);
  const sel = document.getElementById('heat-select');
  let seconds = parseInt(sel.value) * 60;
  const display = document.getElementById('heat-timer-display');
  display.textContent = formatTime(seconds);
  heatTimerInterval = setInterval(()=>{
    seconds--;
    display.textContent = formatTime(seconds);
    if(seconds<=0){
      clearInterval(heatTimerInterval);
      display.textContent = '';
      showToast('🔥 Heat pad timer complete! Remove heat source now.');
    }
  }, 1000);
  showToast('Heat pad timer started');
}
function formatTime(s){
  return `${Math.floor(s/60)}:${String(s%60).padStart(2,'0')}`;
}

// ===== EXPORT =====
function exportCSV(){
  const rows = [
    ['Date','Pain','Bloating','Fatigue','Flow','Mood','Sleep'],
    ['2026-04-29','4','3','3','2','3','4'],
    ['2026-04-30','5','4','4','3','2','3'],
    ['2026-05-01','3','2','3','1','4','5'],
    ['2026-05-02','2','2','2','1','4','6'],
    ['2026-05-03','3','3','3','2','3','5'],
    ['2026-05-04','4','3','3','2','3','4'],
    ['2026-05-05','3','2','2','0','4','5'],
  ];
  const csv = rows.map(r=>r.join(',')).join('\n');
  const blob = new Blob([csv], {type:'text/csv'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url; a.download = 'endoease-data.csv'; a.click();
  URL.revokeObjectURL(url);
  showToast('CSV downloaded');
}

// ===== TOAST =====
function showToast(msg){
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'), 2800);
}
</script>
</body>
</html>


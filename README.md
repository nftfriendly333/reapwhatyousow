<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>REAP WHAT YOU SOW — $PvE</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Bebas+Neue&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#0a0a06;--s1:#111108;--s2:#1a1a10;
  --gold:#d4a843;--goldb:#f0c84a;--goldd:#8a6c25;
  --green:#4caf6e;--red:#c0392b;--purple:#c084fc;
  --text:#e8e0c8;--dim:#8a8068;--bdr:#2a2818;--bdr2:#3d3820;
}
*{box-sizing:border-box;margin:0;padding:0;}
html{-webkit-text-size-adjust:100%;}
body{background:var(--bg);color:var(--text);font-family:'Space Mono',monospace;font-size:14px;min-height:100vh;overflow-x:hidden;}
::-webkit-scrollbar{width:4px;height:4px;}
::-webkit-scrollbar-track{background:var(--s1);}
::-webkit-scrollbar-thumb{background:var(--bdr2);border-radius:2px;}
input,select,button,textarea{font-family:'Space Mono',monospace;-webkit-appearance:none;appearance:none;}
input[type=number]::-webkit-inner-spin-button{opacity:0;}
button{touch-action:manipulation;cursor:pointer;}
.hidden{display:none!important;}

/* ── LAYOUT ── */
.container{width:100%;padding:0 14px;}
.page-header{border-bottom:1px solid var(--bdr);padding:12px 14px;}
.hdr-row{display:flex;flex-direction:column;gap:10px;}
.hdr-title{font-family:'Bebas Neue',sans-serif;font-size:36px;color:var(--gold);letter-spacing:.04em;line-height:.9;text-shadow:0 0 30px rgba(212,168,67,.3);}
.hdr-sub{font-size:9px;letter-spacing:.18em;text-transform:uppercase;color:var(--dim);margin-top:4px;}
.hdr-actions{display:flex;flex-wrap:wrap;gap:6px;align-items:center;}
.session-badge{background:rgba(212,168,67,.08);border:1px solid rgba(212,168,67,.2);padding:7px 12px;border-radius:2px;font-size:11px;color:var(--gold);letter-spacing:.06em;}
.supply-chip{text-align:right;}
.supply-chip .sc-lbl{font-size:8px;color:var(--dim);text-transform:uppercase;letter-spacing:.12em;}
.supply-chip .sc-val{font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--goldb);line-height:1;}
.supply-chip .sc-unit{font-size:8px;color:var(--goldd);}

/* ── BUTTONS ── */
.btn-gold{width:100%;background:var(--gold);color:#0a0a06;border:none;font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:.13em;padding:14px;border-radius:2px;transition:background .15s;}
.btn-gold:hover,.btn-gold:active{background:var(--goldb);}
.btn-gold:disabled{background:var(--goldd);opacity:.5;}
.btn-outline{background:transparent;border:1px solid var(--bdr2);color:var(--dim);font-family:'Bebas Neue',sans-serif;font-size:12px;letter-spacing:.1em;padding:8px 12px;border-radius:2px;}
.btn-sm{background:transparent;border:1px solid var(--bdr);color:var(--dim);font-size:10px;padding:5px 9px;border-radius:2px;}
.btn-pause{font-size:10px;padding:4px 8px;border-radius:2px;border:none;min-width:36px;min-height:30px;}
.btn-wd{width:100%;background:transparent;font-family:'Bebas Neue',sans-serif;font-size:13px;letter-spacing:.1em;padding:10px;border-radius:2px;margin-top:10px;border:1px solid var(--bdr);color:var(--dim);opacity:.5;}
.btn-wd.ready{border-color:var(--green);color:var(--green);opacity:1;box-shadow:0 0 10px rgba(76,175,110,.2);}

/* ── INPUTS ── */
.field{margin-bottom:14px;}
.field label{display:block;font-size:9px;letter-spacing:.18em;text-transform:uppercase;color:var(--dim);margin-bottom:5px;}
.inp{width:100%;background:var(--s2);border:1px solid var(--bdr2);color:var(--text);font-size:14px;padding:12px 14px;border-radius:2px;outline:none;min-height:44px;}
.inp:focus{border-color:var(--goldd);}
.inp-sm{background:var(--s2);border:1px solid var(--bdr2);color:var(--text);font-size:13px;padding:10px 12px;border-radius:2px;outline:none;width:100%;min-height:44px;}

/* ── PANELS ── */
.panel{background:var(--s1);border:1px solid var(--bdr);border-radius:2px;overflow:hidden;margin-bottom:12px;}
.panel-hdr{padding:11px 14px;border-bottom:1px solid var(--bdr);background:var(--s2);display:flex;align-items:center;gap:8px;flex-wrap:wrap;}
.phdr-dot{width:6px;height:6px;border-radius:50%;flex-shrink:0;}
.phdr-title{font-size:9px;letter-spacing:.18em;text-transform:uppercase;color:var(--dim);}
.phdr-extra{margin-left:auto;font-size:9px;}
.panel-body{padding:14px;}

/* ── STATS ── */
.stats-bar{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--bdr);border:1px solid var(--bdr);margin:10px 0;border-radius:2px;overflow:hidden;}
.stat{background:var(--s1);padding:10px 12px;}
.s-lbl{font-size:9px;letter-spacing:.14em;text-transform:uppercase;color:var(--dim);margin-bottom:2px;}
.s-val{font-family:'Bebas Neue',sans-serif;font-size:20px;color:var(--text);letter-spacing:.04em;line-height:1;}

/* ── HUD ── */
.hud{background:#0d0d09;border:1px solid var(--gold);border-radius:2px;margin-bottom:10px;overflow:hidden;}
.hud-hdr{background:linear-gradient(90deg,rgba(212,168,67,.18),rgba(212,168,67,.06));border-bottom:1px solid rgba(212,168,67,.25);padding:10px 14px;}
.hud-hdr-top{display:flex;align-items:center;gap:8px;margin-bottom:3px;}
.hud-dot{width:7px;height:7px;border-radius:50%;background:var(--gold);box-shadow:0 0 8px var(--gold);flex-shrink:0;}
.hud-hdr-title{font-size:10px;letter-spacing:.18em;text-transform:uppercase;color:var(--gold);}
.hud-hdr-note{font-size:9px;color:var(--dim);font-style:italic;}
.hud-body{padding:14px;}
.hud-balances{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:14px;}
.hud-bal-item .hbl{font-size:8px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);margin-bottom:3px;}
.hud-num{font-family:'Bebas Neue',sans-serif;font-size:32px;line-height:1;letter-spacing:.02em;}
.hud-sub{font-size:9px;color:var(--goldd);margin-top:1px;}
.hud-wallet-info{margin-bottom:12px;}
.hud-name{font-family:'DM Serif Display',serif;font-size:17px;color:var(--goldb);margin-bottom:2px;}
.hud-addr{font-size:9px;color:var(--dim);word-break:break-all;}
.eth-bar-section .eth-lbl{font-size:8px;letter-spacing:.14em;text-transform:uppercase;color:var(--dim);margin-bottom:5px;}
.eth-bar{height:6px;background:#1a1a10;border-radius:3px;overflow:hidden;margin-bottom:4px;}
.eth-fill{height:100%;border-radius:3px;transition:width .5s;}
.eth-status{font-size:10px;}

/* ── COUNTDOWN ── */
.cdown{background:linear-gradient(135deg,#0e0d08,#1a180a,#0e0d08);border:1px solid var(--goldd);border-left:3px solid var(--goldb);border-radius:2px;padding:14px;margin-bottom:10px;}
.cdown-label{font-size:8px;letter-spacing:.2em;text-transform:uppercase;color:var(--goldd);margin-bottom:2px;}
.cdown-title{font-family:'DM Serif Display',serif;font-size:16px;color:var(--goldb);margin-bottom:1px;}
.cdown-sub{font-size:9px;color:var(--dim);margin-bottom:12px;}
.cd-digits{display:flex;gap:4px;align-items:flex-end;margin-bottom:10px;}
.cd-unit{text-align:center;}
.cd-val{font-family:'Bebas Neue',sans-serif;font-size:30px;color:var(--text);letter-spacing:.04em;line-height:1;min-width:36px;display:block;}
.cd-lbl{font-size:7px;letter-spacing:.14em;text-transform:uppercase;color:var(--dim);margin-top:2px;}
.cd-sep{font-family:'Bebas Neue',sans-serif;font-size:26px;color:var(--goldd);padding-bottom:12px;opacity:.5;}
.drip-live{font-family:'Bebas Neue',sans-serif;font-size:20px;color:var(--green);letter-spacing:.1em;animation:pulse 1s infinite;margin:8px 0;}
.cdown-info{font-size:10px;color:var(--dim);line-height:1.9;}

/* ── TABS ── */
.tabs{display:flex;border-bottom:1px solid var(--bdr);overflow-x:auto;-webkit-overflow-scrolling:touch;margin-bottom:10px;}
.tabs::-webkit-scrollbar{display:none;}
.tab{background:transparent;border:none;color:var(--dim);font-size:11px;letter-spacing:.12em;text-transform:uppercase;padding:12px 14px;border-bottom:2px solid transparent;transition:all .15s;white-space:nowrap;min-height:44px;}
.tab.on{color:var(--gold);border-bottom-color:var(--gold);}

/* ── WALLET CARDS ── */
.wgrid{display:grid;grid-template-columns:1fr;gap:10px;}
.wcard{background:var(--s2);border:1px solid var(--bdr);border-radius:2px;padding:14px;position:relative;overflow:hidden;}
.wcard.mine{background:#1e1d10;border-color:var(--gold);}
.wcard.mine::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--goldd),transparent);}
.wcard.paused{opacity:.75;border-color:rgba(192,57,43,.3);}
.wcard-header{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:4px;gap:8px;}
.wcard-name{font-family:'DM Serif Display',serif;font-size:16px;color:var(--goldb);line-height:1.2;flex:1;}
.wcard-addr{font-size:9px;color:var(--dim);margin-bottom:8px;word-break:break-all;}
.wcard-balrow{display:flex;gap:16px;align-items:flex-end;margin-bottom:6px;}
.wcard-bal{font-family:'Bebas Neue',sans-serif;font-size:24px;color:var(--text);}
.wcard-eth{font-size:10px;color:var(--purple);}
.wtags{display:flex;gap:4px;margin-top:6px;flex-wrap:wrap;align-items:center;}
.tag{font-size:8px;padding:3px 6px;border:1px solid var(--bdr2);color:var(--dim);}
.tag.user{color:#7fb3f5;border-color:rgba(127,179,245,.3);}
.tag.you{color:var(--gold);border-color:rgba(212,168,67,.3);}
.tag.paused-t{color:var(--red);border-color:rgba(192,57,43,.3);}

/* ── LEDGER ── */
.ltbl{width:100%;border-collapse:collapse;font-size:11px;min-width:520px;}
.ltbl th{padding:0 10px 10px;text-align:left;font-size:9px;letter-spacing:.13em;text-transform:uppercase;color:var(--dim);font-weight:400;white-space:nowrap;}
.ltbl th.fee-col{color:var(--purple);}
.ltbl td{padding:10px;border-bottom:1px solid var(--bdr);vertical-align:middle;}
.tx-badge{font-size:9px;letter-spacing:.08em;padding:3px 6px;border-radius:2px;white-space:nowrap;}
.bnum{font-family:'Bebas Neue',sans-serif;font-size:14px;color:var(--dim);}
.thash{font-size:9px;color:var(--goldd);font-family:monospace;}
.ledger-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch;max-height:55vh;overflow-y:auto;}

/* ── AUTOMATION ── */
.auto-form{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:14px;}
.auto-form-full{grid-column:1/-1;}
.rule-row{background:var(--s2);border:1px solid var(--bdr);border-radius:2px;padding:12px;margin-bottom:8px;}
.rule-info{margin-bottom:8px;}
.rule-name{font-family:'DM Serif Display',serif;font-size:14px;margin-bottom:3px;}
.rule-detail{font-size:10px;color:var(--dim);line-height:1.6;}
.rule-actions{display:flex;gap:6px;}

/* ── LOGIN ── */
.login-wrap{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:16px;}
.login-card{width:100%;max-width:420px;}
.login-logo{text-align:center;margin-bottom:24px;}
.login-logo-title{font-family:'Bebas Neue',sans-serif;font-size:44px;color:var(--gold);letter-spacing:.04em;line-height:.9;text-shadow:0 0 30px rgba(212,168,67,.3);}
.ltabs{display:grid;grid-template-columns:1fr 1fr;border-bottom:1px solid var(--bdr);}
.ltab{background:transparent;border:none;border-bottom:2px solid transparent;color:var(--dim);font-size:10px;letter-spacing:.18em;text-transform:uppercase;padding:14px;transition:all .15s;min-height:44px;}
.ltab.on{background:var(--s2);border-bottom-color:var(--gold);color:var(--gold);}
.login-form{padding:20px;}

/* ── MODAL ── */
.modal-bg{position:fixed;inset:0;background:rgba(0,0,0,.8);display:flex;align-items:flex-end;justify-content:center;z-index:500;padding:0;}
.modal{background:var(--s1);border:1px solid var(--bdr2);border-radius:2px 2px 0 0;padding:20px;width:100%;max-width:500px;max-height:90vh;overflow-y:auto;}
.modal-title{font-family:'DM Serif Display',serif;font-size:20px;color:var(--gold);margin-bottom:6px;}
.modal-btns{display:flex;gap:8px;margin-top:4px;}
.modal-btns .btn-add{flex:1;background:var(--gold);color:#0a0a06;border:none;font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:.12em;padding:13px;border-radius:2px;}
.modal-btns .btn-cancel{background:transparent;border:1px solid var(--bdr2);color:var(--dim);font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:.12em;padding:13px 16px;border-radius:2px;}

/* ── TOAST ── */
.toast{position:fixed;bottom:16px;left:12px;right:12px;background:var(--s2);border:1px solid var(--goldd);border-radius:2px;padding:12px 16px;font-size:12px;color:var(--text);z-index:999;max-width:500px;margin:0 auto;box-shadow:0 8px 28px rgba(0,0,0,.5);line-height:1.5;opacity:0;transform:translateY(10px);transition:all .3s;pointer-events:none;}
.toast.show{opacity:1;transform:translateY(0);pointer-events:auto;}
.toast-title{font-family:'DM Serif Display',serif;font-size:14px;color:var(--gold);margin-bottom:2px;}

/* ── MISC ── */
.err-msg{font-size:11px;color:var(--red);background:rgba(192,57,43,.08);border:1px solid rgba(192,57,43,.2);border-radius:2px;padding:10px 12px;margin-bottom:14px;}
.info-box{background:rgba(212,168,67,.06);border:1px solid rgba(212,168,67,.15);border-radius:2px;padding:10px 14px;margin-bottom:16px;font-size:11px;color:var(--dim);line-height:1.7;}
.ldot{width:5px;height:5px;border-radius:50%;background:var(--green);box-shadow:0 0 6px var(--green);display:inline-block;animation:pulse 1.5s infinite;}
.sup-bar{height:3px;background:var(--bdr);border-radius:2px;margin-bottom:10px;overflow:hidden;}
.sup-fill{height:100%;background:linear-gradient(90deg,var(--goldd),var(--goldb));border-radius:2px;transition:width .4s;}
footer{border-top:1px solid var(--bdr);padding:12px 0;margin-top:6px;display:flex;justify-content:space-between;flex-wrap:wrap;gap:4px;}
footer span{font-size:9px;letter-spacing:.08em;text-transform:uppercase;color:var(--dim);}

@keyframes flash{0%{background:rgba(212,168,67,.15);}100%{background:transparent;}}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:.4;}}
.nr{animation:flash .8s ease-out;}

/* ── TABLET+ ── */
@media(min-width:600px){
  .container{padding:0 20px;}
  .hdr-title{font-size:52px;}
  .hdr-row{flex-direction:row;align-items:flex-end;justify-content:space-between;}
  .stats-bar{grid-template-columns:repeat(5,1fr);}
  .wgrid{grid-template-columns:repeat(auto-fill,minmax(200px,1fr));}
  .auto-form{grid-template-columns:repeat(4,1fr) auto;}
  .auto-form-full{grid-column:auto;}
  .modal-bg{align-items:center;padding:16px;}
  .modal{border-radius:2px;max-width:420px;}
  .toast{left:auto;right:16px;max-width:300px;}
  .hud-balances{grid-template-columns:1fr 1fr 1fr;}
  .hud-num{font-size:38px;}
  .rule-row{display:grid;grid-template-columns:1fr auto;align-items:center;gap:10px;}
  .rule-info{margin-bottom:0;}
}
</style>
</head>
<body>

<!-- LOGIN -->
<div id="screen-login" class="login-wrap">
  <div class="login-card">
    <div class="login-logo">
      <div class="login-logo-title">REAP WHAT<br><span style="color:var(--text);opacity:.2;">//</span> YOU SOW</div>
      <div style="font-size:9px;letter-spacing:.2em;text-transform:uppercase;color:var(--dim);margin-top:8px;">$PvE Token · Internal Shared Ledger</div>
    </div>
    <div class="panel">
      <div class="ltabs">
        <button class="ltab on" id="ltab-login" onclick="setMode('login')">Sign In</button>
        <button class="ltab" id="ltab-register" onclick="setMode('register')">Register</button>
      </div>
      <div class="login-form">
        <div class="info-box hidden" id="reg-info">New accounts start with <span style="color:var(--gold);">1000 $PvE locked 🔒</span>. Unstake anytime with a 25% fee to the Team Treasury.</div>
        <div class="field"><label>Username</label><input class="inp" id="l-user" placeholder="e.g. alice" onkeydown="if(event.key==='Enter')doLogin()"></div>
        <div class="field"><label>Password</label><input class="inp" type="password" id="l-pass" placeholder="min 4 characters" onkeydown="if(event.key==='Enter')doLogin()"></div>
        <div id="reg-fields" class="hidden">
          <div class="field"><label>Display Name (optional)</label><input class="inp" id="l-name" placeholder="e.g. Alice's Vault"></div>
          <div class="field">
            <label>Wallet Address (optional)</label>
            <input class="inp" id="l-addr" placeholder="0x..." oninput="checkAddrDupe(this.value)">
            <div id="addr-dupe-msg" style="display:none;font-size:9px;color:var(--red);margin-top:4px;">⚠ This address is already registered to another account.</div>
          </div>
        </div>
        <div class="err-msg hidden" id="l-err"></div>
        <button class="btn-gold" id="l-btn" onclick="doLogin()">SIGN IN</button>
        <div style="text-align:center;margin-top:14px;font-size:9px;color:var(--dim);">All users share the same live ledger · Prototype</div>
      </div>
    </div>
  </div>
</div>

<!-- APP -->
<div id="screen-app" class="hidden">
  <div class="page-header">
    <div class="container">
      <div class="hdr-row">
        <div>
          <div class="hdr-title">REAP WHAT <span style="color:var(--text);opacity:.2;">//</span> YOU SOW</div>
          <div class="hdr-sub">$PvE Token · Internal Shared Ledger</div>
        </div>
        <div class="hdr-actions">
          <div id="session-badge" class="session-badge"></div>
          <button class="btn-outline" id="add-wallet-btn" onclick="openAddWallet()">+ ADD WALLET</button>
          <button class="btn-outline" onclick="doSignOut()">SIGN OUT</button>
          <div class="supply-chip">
            <div class="sc-lbl">Supply</div>
            <div class="sc-val" id="hdr-supply"></div>
            <div class="sc-unit">$PvE</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="container">
    <!-- STATS -->
    <div class="stats-bar">
      <div class="stat"><div class="s-lbl">Transactions</div><div class="s-val" id="st-tx">0</div></div>
      <div class="stat"><div class="s-lbl">Volume</div><div class="s-val" id="st-vol">0</div></div>
      <div class="stat"><div class="s-lbl">Rewards</div><div class="s-val" id="st-rew">0</div></div>
      <div class="stat"><div class="s-lbl">Wallets</div><div class="s-val" id="st-wals">0</div></div>
      <div class="stat"><div class="s-lbl">Block</div><div class="s-val" id="st-blk">0</div></div>
    </div>

    <!-- HUD -->
    <div class="hud">
      <div class="hud-hdr">
        <div class="hud-hdr-top">
          <div class="hud-dot"></div>
          <span class="hud-hdr-title">Your In-App Wallet — <span id="hud-uname"></span></span>
        </div>
        <div class="hud-hdr-note">balances are internal · not connected to mainnet</div>
      </div>
      <div id="hud-body" class="hud-body">
        <div style="display:flex;align-items:center;gap:10px;">
          <div style="width:8px;height:8px;border-radius:50%;background:var(--gold);animation:pulse 1s infinite;flex-shrink:0;"></div>
          <span style="font-size:12px;color:var(--dim);">Loading your in-app balances...</span>
        </div>
      </div>
    </div>

    <!-- COUNTDOWN -->
    <div class="cdown">
      <div class="cdown-label">Next $ETH Drip</div>
      <div class="cdown-title">Tuesday Drop</div>
      <div class="cdown-sub">Every Tuesday · 8:00 AM Eastern</div>
      <div class="cd-digits" id="cd-digits">
        <div class="cd-unit"><span class="cd-val" id="cd-d">--</span><div class="cd-lbl">Days</div></div>
        <div class="cd-sep">:</div>
        <div class="cd-unit"><span class="cd-val" id="cd-h">--</span><div class="cd-lbl">Hrs</div></div>
        <div class="cd-sep">:</div>
        <div class="cd-unit"><span class="cd-val" id="cd-m">--</span><div class="cd-lbl">Mins</div></div>
        <div class="cd-sep">:</div>
        <div class="cd-unit"><span class="cd-val" id="cd-s">--</span><div class="cd-lbl">Secs</div></div>
      </div>
      <div class="cdown-info">
        <span style="color:var(--gold);">+0.000005 $ETH</span> drip per wallet<br><span style="color:var(--gold);">0.000000015 $ETH</span> burned / tx<br><span style="color:var(--goldb);">1000 $PvE locked · unstake with 25% fee</span>
      </div>
    </div>

    <!-- TABS -->
    <div class="tabs">
      <button class="tab on" data-tab="automation" onclick="switchTab('automation')">⏱ Automate</button>
      <button class="tab" data-tab="registry" onclick="switchTab('registry')">⊞ Wallets</button>
      <button class="tab" data-tab="ledger" onclick="switchTab('ledger')">≡ Ledger</button>
    </div>

    <!-- AUTOMATION TAB -->
    <div id="tab-automation" class="hidden">
      <div class="panel">
        <div class="panel-hdr">
          <div class="phdr-dot" style="background:var(--purple);box-shadow:0 0 8px var(--purple);"></div>
          <span class="phdr-title">Automation — Auto-Sends</span>
          <span class="phdr-extra" style="color:var(--purple);">0.002 $ETH / tx</span>
        </div>
        <div class="panel-body">
          <div class="auto-form">
            <div><label style="display:block;font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">From Wallet</label><select class="inp-sm" id="auto-wallet"></select></div>
            <div><label style="display:block;font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">Every (sec)</label><input type="number" class="inp-sm" id="auto-sec" min="5" value="10"></div>
            <div><label style="display:block;font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">Amount / Wallet</label><input type="number" class="inp-sm" id="auto-amt" min="0.01" step="0.01" value="1"></div>
            <div><label style="display:block;font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">Max Recipients</label><input type="number" class="inp-sm" id="auto-max" min="1" max="5" value="1"></div>
            <div class="auto-form-full"><button onclick="createRule()" style="width:100%;background:var(--purple);color:#0a0a06;border:none;font-family:'Bebas Neue',sans-serif;font-size:15px;letter-spacing:.1em;padding:13px;border-radius:2px;">+ ADD RULE</button></div>
          </div>
          <div id="rules-list"><div style="text-align:center;padding:20px;font-size:11px;color:var(--dim);font-style:italic;">No rules yet.</div></div>
        </div>
      </div>
    </div>

    <!-- REGISTRY TAB -->
    <div id="tab-registry" class="hidden">
      <div class="panel">
        <div class="panel-hdr">
          <div class="phdr-dot" style="background:var(--gold);box-shadow:0 0 8px var(--gold);"></div>
          <span class="phdr-title">Wallet Registry</span>
          <span class="phdr-extra" style="display:flex;align-items:center;gap:5px;color:var(--green);"><span class="ldot"></span>LIVE</span>
        </div>
        <div class="panel-body"><div class="wgrid" id="registry-grid"></div></div>
      </div>
    </div>

    <!-- LEDGER TAB -->
    <div id="tab-ledger" class="hidden">
      <div class="panel">
        <div class="panel-hdr">
          <div class="phdr-dot" style="background:var(--goldb);box-shadow:0 0 8px var(--goldb);"></div>
          <span class="phdr-title">Global Ledger</span>
          <span class="phdr-extra" style="color:var(--dim);">Internal · Real-time</span>
        </div>
        <div class="ledger-wrap">
          <table class="ltbl">
            <thead><tr style="border-bottom:1px solid var(--bdr);">
              <th>Block</th><th>Type</th><th>From → To</th><th>Amount</th><th class="fee-col">Fee</th><th>Time</th>
            </tr></thead>
            <tbody id="ledger-body"><tr><td colspan="6" style="text-align:center;padding:36px;color:var(--dim);font-size:11px;font-style:italic;">No transactions yet.</td></tr></tbody>
          </table>
        </div>
      </div>
    </div>

    <footer>
      <span>$PvE · Reap What You Sow · <span id="ft-wals">0</span> Wallets</span>
      <span id="ft-time"></span>
    </footer>
  </div>
</div>

<!-- ADD WALLET MODAL -->
<div class="modal-bg hidden" id="modal-add">
  <div class="modal">
    <div class="modal-title">Add New Wallet</div>
    <div style="font-size:11px;color:var(--dim);margin-bottom:14px;line-height:1.7;">Register a wallet as recipient. They start with <span style="color:var(--gold);">1000 $PvE locked 🔒</span>. Unstake anytime with a 25% fee.</div>
    <div style="background:var(--s2);border:1px solid var(--bdr2);border-radius:2px;padding:12px;margin-bottom:16px;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">
        <span style="font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);">Wallet Slots</span>
        <span id="slot-label" style="font-size:11px;color:var(--green);">3 slots remaining</span>
      </div>
      <div style="height:6px;background:var(--bdr);border-radius:3px;overflow:hidden;">
        <div id="slot-bar-fill" style="height:100%;width:0%;background:var(--green);border-radius:3px;transition:width .4s,background .3s;"></div>
      </div>
      <div style="display:flex;justify-content:space-between;margin-top:5px;font-size:9px;color:var(--dim);">
        <span id="slot-used-label">0 used</span><span>3 max</span>
      </div>
    </div>
    <div class="field">
      <label>Wallet Address</label>
      <input class="inp" id="add-addr" placeholder="0x..." onkeydown="if(event.key==='Enter')submitAdd()" oninput="checkAddAddrDupe(this.value)">
      <div id="add-addr-dupe-msg" style="display:none;font-size:10px;color:var(--red);margin-top:4px;">⚠ This address is already in the registry.</div>
    </div>
    <div class="field"><label>Display Name <span style="color:var(--gold);">*</span></label><input class="inp" id="add-name" placeholder="e.g. Alice's Vault" onkeydown="if(event.key==='Enter')submitAdd()"></div>
    <div class="modal-btns">
      <button class="btn-add" onclick="submitAdd()">ADD TO REGISTRY</button>
      <button class="btn-cancel" onclick="closeAdd()">CANCEL</button>
    </div>
  </div>
</div>

<!-- LIMIT MODAL -->
<div class="modal-bg hidden" id="modal-limit">
  <div class="modal" style="text-align:center;">
    <div style="font-size:40px;margin-bottom:12px;">⛔</div>
    <div style="font-family:'DM Serif Display',serif;font-size:22px;color:var(--red);margin-bottom:8px;">Wallet Limit Reached</div>
    <div style="font-size:12px;color:var(--dim);line-height:1.8;margin-bottom:20px;">You have used all <span style="color:var(--gold);">3 wallet slots</span>.<br>No additional wallets can be added.</div>
    <div style="height:6px;background:var(--bdr);border-radius:3px;overflow:hidden;margin-bottom:20px;"><div style="height:100%;width:100%;background:var(--red);border-radius:3px;"></div></div>
    <button onclick="hide('modal-limit')" style="background:var(--red);color:#fff;border:none;font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:.14em;padding:13px 32px;border-radius:2px;">CLOSE</button>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast">
  <div class="toast-title" id="toast-t"></div>
  <div id="toast-m"></div>
</div>

<script>
// ════════════════════════════════════
// CONSTANTS & STATE
// ════════════════════════════════════
const FEE=0.000000015,ETH_DRIP=0.000005,UNSTAKE_FEE=0.25,BLOCK_START=1;
const TEAM_WALLET_ID='team-treasury';
const TEAM_WALLET={id:TEAM_WALLET_ID,name:'Team Treasury',addr:'0xTEAM...VAULT',balance:0,locked:0,eth:0.1,paused:false,pending:0,tag:'Team Wallet',color:'#e879f9',isUser:false};
const PALETTE=['#d4a843','#e07b7b','#7bade0','#7be09a','#c07be0','#e0c37b','#e08c7b','#7be0d4','#b07be0','#e0d47b'];
const TX_STYLE={
  send:{bg:'rgba(192,57,43,0.12)',c:'#c0392b',b:'rgba(192,57,43,0.2)',l:'SEND'},
  reward:{bg:'rgba(212,168,67,0.1)',c:'#d4a843',b:'rgba(212,168,67,0.2)',l:'REWARD'},
  mint:{bg:'rgba(100,149,237,0.1)',c:'#7fb3f5',b:'rgba(100,149,237,0.2)',l:'MINT'},
  auto:{bg:'rgba(192,132,252,0.1)',c:'#c084fc',b:'rgba(192,132,252,0.2)',l:'AUTO'},
  withdraw:{bg:'rgba(76,175,110,0.1)',c:'#4caf6e',b:'rgba(76,175,110,0.25)',l:'WITHDRAW'},
  register:{bg:'rgba(127,179,245,0.08)',c:'#7fb3f5',b:'rgba(127,179,245,0.2)',l:'JOINED'},
  unlock:{bg:'rgba(76,175,110,0.1)',c:'#4caf6e',b:'rgba(76,175,110,0.25)',l:'UNLOCK'},
  unstake:{bg:'rgba(192,57,43,0.12)',c:'#c0392b',b:'rgba(192,57,43,0.2)',l:'UNSTAKE'},
};
const SEEDS=[];

let ST={wallets:[JSON.parse(JSON.stringify(TEAM_WALLET)),...JSON.parse(JSON.stringify(SEEDS))],ledger:[],blockNum:BLOCK_START,totalVol:0,totalRewards:0,totalWithdrawn:0};
let session=null,dripReady=false,saveTimer=null,pollTimer=null,cdTimer=null;
let rules=[],ruleId=1,currentTab='automation',loginMode='login';

// ════════════════════════════════════
// UTILS
// ════════════════════════════════════
const r4=n=>parseFloat(parseFloat(n).toFixed(4));
const fmt=(n,d=2)=>parseFloat(n).toLocaleString(undefined,{maximumFractionDigits:d});
const $=id=>document.getElementById(id);
const show=id=>$(id).classList.remove('hidden');
const hide=id=>$(id).classList.add('hidden');
function genHash(){const h='0123456789abcdef';let r='0x';for(let i=0;i<8;i++)r+=h[~~(Math.random()*16)];r+='...';for(let i=0;i<4;i++)r+=h[~~(Math.random()*16)];return r;}
function hashPw(p){let h=0;for(let i=0;i<p.length;i++){h=((h<<5)-h)+p.charCodeAt(i);h|=0;}return h.toString(36);}
function msTillDrip(){const now=new Date(),et=new Date(now.toLocaleString('en-US',{timeZone:'America/New_York'}));const day=et.getDay(),ms=(et.getHours()*3600+et.getMinutes()*60+et.getSeconds())*1000+et.getMilliseconds(),target=8*3600*1000;let days=(2-day+7)%7;if(days===0&&ms>=target)days=7;return Math.max(0,days*86400000+target-ms);}
function toast(t,m,d=4000){$('toast-t').textContent=t;$('toast-m').textContent=m;$('toast').classList.add('show');setTimeout(()=>$('toast').classList.remove('show'),d);}

// ════════════════════════════════════
// STORAGE
// ════════════════════════════════════
async function loadS(k){if(!window.storage)return null;try{const r=await window.storage.get(k,true);return r?JSON.parse(r.value):null;}catch{return null;}}
async function saveS(k,v){if(!window.storage)return;try{await window.storage.set(k,JSON.stringify(v),true);}catch{/* storage unavailable */}}
function scheduleSave(){if(saveTimer)clearTimeout(saveTimer);saveTimer=setTimeout(async()=>{await saveS('rwys-state',{wallets:ST.wallets,blockNum:ST.blockNum,totalVol:ST.totalVol,totalRewards:ST.totalRewards,totalWithdrawn:ST.totalWithdrawn});await saveS('rwys-ledger',ST.ledger.slice(0,200));},800);}
async function loadAll(){const st=await loadS('rwys-state'),ld=await loadS('rwys-ledger');if(st&&!st.wallets?.find(w=>w.id===TEAM_WALLET_ID)){if(st.wallets)st.wallets.unshift(JSON.parse(JSON.stringify(TEAM_WALLET)));}if(st?.wallets?.length){ST.wallets=st.wallets;ST.blockNum=st.blockNum||BLOCK_START;ST.totalVol=st.totalVol||0;ST.totalRewards=st.totalRewards||0;ST.totalWithdrawn=st.totalWithdrawn||0;}if(ld?.length)ST.ledger=ld;}
function startPoll(){pollTimer=setInterval(async()=>{const st=await loadS('rwys-state'),ld=await loadS('rwys-ledger');if(st?.wallets){ST.wallets=st.wallets;ST.blockNum=st.blockNum||BLOCK_START;ST.totalVol=st.totalVol||0;ST.totalRewards=st.totalRewards||0;ST.totalWithdrawn=st.totalWithdrawn||0;}if(ld)ST.ledger=ld;renderAll();},3000);}

// ════════════════════════════════════
// LOGIN
// ════════════════════════════════════
function setMode(m){
  loginMode=m;
  $('ltab-login').classList.toggle('on',m==='login');
  $('ltab-register').classList.toggle('on',m==='register');
  $('reg-info').classList.toggle('hidden',m==='login');
  $('reg-fields').classList.toggle('hidden',m==='login');
  $('l-btn').textContent=m==='login'?'SIGN IN':'CREATE ACCOUNT';
  hide('l-err');
}
async function doLogin(){
  const u=$('l-user').value.trim().toLowerCase(),p=$('l-pass').value.trim();
  hide('l-err');
  if(!u||!p){showErr('Username and password required.');return;}
  if(p.length<4){showErr('Password must be 4+ characters.');return;}
  $('l-btn').textContent='PLEASE WAIT...';$('l-btn').disabled=true;
  const users=(await loadS('rwys-users'))||{};
  if(loginMode==='login'){
    if(!users[u]){showErr('Account not found — register first.');return;}
    if(users[u].ph!==hashPw(p)){showErr('Incorrect password.');return;}
    session={username:u,walletId:users[u].wid};
    await loadAll();startApp();
  }else{
    if(users[u]){showErr('Username taken — choose another.');return;}
    const dn=$('l-name').value.trim()||u;
    const wa=$('l-addr').value.trim()||`0x${u.padEnd(6,'0').slice(0,6)}...${hashPw(p).slice(0,4)}`;
    await loadAll();
    // Check for duplicate wallet address (only if user provided a real one)
    const addrEntered = $('l-addr').value.trim();
    if(addrEntered && ST.wallets.find(w=>w.addr.toLowerCase()===addrEntered.toLowerCase())){
      showErr('Wallet address already registered to another account.');return;
    }
    const wid='wu'+Date.now();
    const nw={id:wid,name:dn,addr:wa,balance:0,locked:1000,eth:0.1,paused:false,pending:0,tag:'Registered User',color:PALETTE[ST.wallets.length%PALETTE.length],isUser:true};
    ST.blockNum++;ST.wallets.push(nw);
    ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'mint',from:'PROTOCOL',to:dn,amount:100,time:new Date().toISOString()});
    if(ST.ledger.length>200)ST.ledger.length=200;
    users[u]={ph:hashPw(p),wid,walletsAdded:0};
    await saveS('rwys-users',users);
    await saveS('rwys-state',{wallets:ST.wallets,blockNum:ST.blockNum,totalVol:ST.totalVol,totalRewards:ST.totalRewards,totalWithdrawn:ST.totalWithdrawn});
    await saveS('rwys-ledger',ST.ledger.slice(0,200));
    session={username:u,walletId:wid};startApp();
  }
}
function checkAddAddrDupe(val){
  const v=val.trim();
  const msg=$('add-addr-dupe-msg');
  if(!msg) return;
  if(v && ST.wallets.find(w=>w.addr.toLowerCase()===v.toLowerCase())){
    msg.style.display='block';
  } else {
    msg.style.display='none';
  }
}
function checkAddrDupe(val){
  const v=val.trim();
  const msg=$('addr-dupe-msg');
  if(!msg) return;
  if(v && ST.wallets.find(w=>w.addr.toLowerCase()===v.toLowerCase())){
    msg.style.display='block';
  } else {
    msg.style.display='none';
  }
}
function showErr(msg){$('l-err').textContent=msg;show('l-err');$('l-btn').textContent=loginMode==='login'?'SIGN IN':'CREATE ACCOUNT';$('l-btn').disabled=false;}
function doSignOut(){session=null;if(pollTimer)clearInterval(pollTimer);if(cdTimer)clearInterval(cdTimer);rules.forEach(r=>{if(r.tid)clearInterval(r.tid);});rules=[];hide('screen-app');show('screen-login');$('l-user').value='';$('l-pass').value='';$('l-name').value='';$('l-addr').value='';hide('l-err');$('l-btn').textContent='SIGN IN';$('l-btn').disabled=false;}

// ════════════════════════════════════
// APP INIT
// ════════════════════════════════════
function startApp(){
  hide('screen-login');show('screen-app');
  $('hud-uname').textContent=session.username;
  startPoll();startCountdown();renderAll();
  setInterval(()=>{$('ft-time').textContent=new Date().toUTCString();},1000);
  // Refresh slot counter in header
  walletsAdded().then(n=>updateSlotCounter(n));
}
const myW=()=>ST.wallets.find(w=>w.id===session?.walletId)||null;

// ════════════════════════════════════
// TUESDAY DRIP
// ════════════════════════════════════
let lastDripDate = null;
function fireTuesdayDrip(){
  const today = new Date().toDateString();
  if(lastDripDate === today) return; // only fire once per day
  lastDripDate = today;
  let anyChange = false;
  ST.wallets.forEach((w,i)=>{
    // ETH drip only — locked $PvE stays locked until unstake
    const newEth = Math.min(0.1, r4((ST.wallets[i].eth||0) + ETH_DRIP));
    if(newEth !== ST.wallets[i].eth){ ST.wallets[i] = {...ST.wallets[i], eth: newEth}; anyChange = true; }
  });
  if(ST.ledger.length>200) ST.ledger.length=200;
  if(anyChange){ scheduleSave(); renderAll(); toast('Tuesday Drip','+0.000005 $ETH dripped to all wallets'); }
}

// ════════════════════════════════════
// COUNTDOWN
// ════════════════════════════════════
function startCountdown(){
  const tick=()=>{
    const ms=msTillDrip();
    if(ms<1000){if(!dripReady)fireTuesdayDrip();dripReady=true;$('cd-digits').innerHTML='<div class="drip-live">DRIP LIVE — WITHDRAW NOW</div>';renderHUD();renderRegistry();return;}
    const s=~~(ms/1000);
    $('cd-d').textContent=String(~~(s/86400)).padStart(2,'0');
    $('cd-h').textContent=String(~~((s%86400)/3600)).padStart(2,'0');
    $('cd-m').textContent=String(~~((s%3600)/60)).padStart(2,'0');
    $('cd-s').textContent=String(s%60).padStart(2,'0');
  };
  tick();cdTimer=setInterval(tick,1000);
}

// ════════════════════════════════════
// TABS
// ════════════════════════════════════
function switchTab(t){
  currentTab=t;
  document.querySelectorAll('.tab').forEach(b=>b.classList.toggle('on',b.dataset.tab===t));
  ['automation','registry','ledger'].forEach(id=>{
    const el=$('tab-'+id);if(el)el.classList.toggle('hidden',id!==t);
  });
  if(t==='automation')renderAutoDropdown();
  if(t==='registry')renderRegistry();
  if(t==='ledger')renderLedger();
}

// ════════════════════════════════════
// RENDER ALL
// ════════════════════════════════════
function renderAll(){
  renderStats();renderHUD();
  if(currentTab==='registry')renderRegistry();
  if(currentTab==='ledger')renderLedger();
  $('hdr-supply').textContent=fmt(ST.wallets.reduce((s,w)=>s+w.balance,0),0);
  $('ft-wals').textContent=ST.wallets.length;
  // Refresh slot counter if modal is open
  walletsAdded().then(added=>updateSlotCounter(added));
}

// ════════════════════════════════════
// STATS
// ════════════════════════════════════
function renderStats(){
  $('st-tx').textContent=ST.ledger.filter(x=>x.type==='send'||x.type==='auto').length;
  $('st-vol').textContent=fmt(ST.totalVol,0);
  $('st-rew').textContent=ST.totalRewards;
  $('st-wals').textContent=ST.wallets.length;
  $('st-blk').textContent=ST.blockNum.toLocaleString();
}

// ════════════════════════════════════
// HUD
// ════════════════════════════════════
function wdHTML(id,pending,small){
  const rdy=dripReady&&pending>0;
  const lbl=rdy?`⬆ WITHDRAW${small?'':' '+pending.toFixed(4)} $PvE`:'⏳ NO PENDING WITHDRAWAL';
  return `<button class="btn-wd${rdy?' ready':''}" ${rdy?`onclick="event.stopPropagation();doWithdraw('${id}')"`:' disabled'}>${lbl}</button>`;
}
function renderHUD(){
  const w=myW();
  const sb=$('session-badge');
  if(!w){sb.textContent='◈ '+(session?.username||'');return;}
  sb.innerHTML=`◈ ${session.username}<span style="color:var(--dim);margin-left:6px;">${fmt(w.balance,2)} $PvE</span>`;
  const pct=Math.min(100,w.eth/0.1*100);
  const ec=w.eth<0.02?'#c0392b':w.eth<0.05?'#f59e0b':'var(--purple)';
  const emsg=w.eth<0.02?'⚠ Critical — sends will fail':w.eth<0.05?'△ Low — drips back on Tuesday':'✓ Ready to send';
  const locked = w.locked||0;
  $('hud-body').innerHTML=`
    <div class="hud-wallet-info">
      <div class="hud-name">${w.name}</div>
      <div class="hud-addr">${w.addr}</div>
      <div class="wtags" style="margin-top:6px;">
        <span class="tag">${w.tag}</span>${w.paused?'<span class="tag paused-t">TX PAUSED</span>':''}
      </div>
    </div>
    <div class="hud-balances">
      <div class="hud-bal-item">
        <div class="hbl">$PvE Unlocked</div>
        <div class="hud-num" style="color:var(--goldb);">${fmt(w.balance,4)}</div>
        <div class="hud-sub">available</div>
      </div>
      <div class="hud-bal-item">
        <div class="hbl">$PvE Locked 🔒</div>
        <div class="hud-num" style="color:var(--dim);">${fmt(locked,4)}</div>
        <div class="hud-sub">unlocks Tuesday</div>
      </div>
      <div class="hud-bal-item">
        <div class="hbl">$ETH (gas)</div>
        <div class="hud-num" style="color:var(--purple);">${w.eth.toFixed(6)}</div>
        <div class="hud-sub">max 0.1</div>
      </div>
      ${w.pending>0?`<div class="hud-bal-item"><div class="hbl">Pending</div><div class="hud-num" style="color:var(--green);">${w.pending.toFixed(4)}</div><div class="hud-sub">$PvE queued</div></div>`:''}
    </div>
    <div class="eth-bar-section">
      <div class="eth-lbl">$ETH Gas Level</div>
      <div class="eth-bar"><div class="eth-fill" style="width:${pct}%;background:linear-gradient(90deg,${ec},#e879f9);"></div></div>
      <div class="eth-status" style="color:${ec};">${emsg}</div>
      ${wdHTML(w.id,w.pending,false)}
    </div>
    <div style="margin-top:10px;padding:10px 12px;background:rgba(192,57,43,.06);border:1px solid rgba(192,57,43,.2);border-radius:2px;">
      <div style="font-size:9px;color:var(--red);letter-spacing:.12em;text-transform:uppercase;margin-bottom:5px;">Early Unstake</div>
      <div style="font-size:10px;color:var(--dim);margin-bottom:8px;line-height:1.6;">Withdraw all $PvE now — 25% fee goes to Team Treasury. You receive <b style="color:var(--text);">${fmt(r4((w.balance+locked)*0.75),4)} $PvE</b> and <b style="color:var(--red);">${fmt(r4((w.balance+locked)*0.25),4)} $PvE</b> → Team Treasury.</div>
      <button onclick="confirmUnstake('${w.id}')" style="width:100%;background:transparent;border:1px solid rgba(192,57,43,.4);color:var(--red);font-family:'Bebas Neue',sans-serif;font-size:13px;letter-spacing:.1em;padding:9px;border-radius:2px;"">⚠ UNSTAKE EARLY (−25%)</button>
    </div>`;
}

// ════════════════════════════════════
// SEND
// ════════════════════════════════════

// ════════════════════════════════════
// INSPECTOR
// ════════════════════════════════════

// ════════════════════════════════════
// REGISTRY
// ════════════════════════════════════
function renderRegistry(){
  const g=$('registry-grid');if(!g)return;
  g.innerHTML=ST.wallets.map(w=>{
    const me=w.id===session?.walletId;
    return `<div class="wcard${me?' mine':''}${w.paused?' paused':''}">
      <div class="wcard-header">
        <div class="wcard-name">${w.name}</div>
        <button class="btn-pause" style="background:${w.paused?'rgba(76,175,110,.15)':'rgba(192,57,43,.12)'};color:${w.paused?'#4caf6e':'#c0392b'};border:1px solid ${w.paused?'rgba(76,175,110,.3)':'rgba(192,57,43,.25)'};" onclick="event.stopPropagation();togglePause('${w.id}')">${w.paused?'▶':'⏸'}</button>
      </div>
      <div class="wcard-addr">${w.addr}</div>
      <div class="wcard-balrow">
        <div>
          <div style="font-size:9px;color:var(--dim);margin-bottom:2px;">$PvE</div>
          <div class="wcard-bal" style="opacity:${w.paused?.45:1};">${fmt(w.balance,2)}</div>
          ${(w.locked||0)>0?`<div style="font-size:9px;color:var(--dim);">🔒 ${fmt(w.locked,2)} locked</div>`:''}
        </div>
        <div>
          <div style="font-size:9px;color:var(--dim);margin-bottom:2px;">$ETH</div>
          <div class="wcard-eth" style="opacity:${w.paused?.45:1};font-size:18px;font-family:'Bebas Neue',sans-serif;">${w.eth.toFixed(6)}</div>
        </div>
      </div>
      ${w.pending>0?`<div style="font-size:10px;color:var(--green);margin-top:4px;">⬆ ${w.pending.toFixed(4)} pending</div>`:''}
      <div class="wtags">
        <span class="tag">${w.tag}</span>
        ${w.paused?'<span class="tag paused-t">PAUSED</span>':''}
        ${w.isUser?'<span class="tag user">USER</span>':''}
        ${me?'<span class="tag you">YOU</span>':''}
      </div>
      ${wdHTML(w.id,w.pending,true)}
    </div>`;
  }).join('');
}

// ════════════════════════════════════
// UNSTAKE (early withdrawal with 25% fee)
// ════════════════════════════════════
function confirmUnstake(id){
  const w = ST.wallets.find(x=>x.id===id);
  if(!w) return;
  const total = r4((w.balance||0)+(w.locked||0));
  const fee = r4(total*0.25);
  const gets = r4(total-fee);
  if(confirm(`Unstake early?\n\nYou will receive: ${gets.toFixed(4)} $PvE\nBurned (25% fee): ${fee.toFixed(4)} $PvE\n\nThis cannot be undone.`)){
    doUnstake(id);
  }
}
function doUnstake(id){
  const i = ST.wallets.findIndex(w=>w.id===id);
  if(i<0) return;
  const w = ST.wallets[i];
  const total = r4((w.balance||0) + (w.locked||0));
  if(total <= 0){ toast('Nothing to Unstake','No $PvE balance'); return; }
  const fee = r4(total * UNSTAKE_FEE);
  const received = r4(total - fee);
  // Deduct from user
  ST.wallets[i] = {...w, balance: 0, locked: 0, pending: 0};
  // Send fee to team treasury
  const ti = ST.wallets.findIndex(x=>x.id===TEAM_WALLET_ID);
  if(ti>=0) ST.wallets[ti] = {...ST.wallets[ti], balance: r4((ST.wallets[ti].balance||0)+fee)};
  ST.blockNum++;
  ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'unstake',from:w.name,to:'Team Treasury',amount:fee,time:new Date().toISOString()});
  ST.blockNum++;
  ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'withdraw',from:w.name,to:'WITHDRAWN',amount:received,time:new Date().toISOString()});
  if(ST.ledger.length>200) ST.ledger.length=200;
  ST.totalWithdrawn = r4(ST.totalWithdrawn + received);
  scheduleSave(); renderAll();
  toast('Unstaked Early',`${received.toFixed(4)} $PvE withdrawn · ${fee.toFixed(4)} $PvE → Team Treasury`);
}

// ════════════════════════════════════
// WITHDRAW
// ════════════════════════════════════
function doWithdraw(id){
  if(!dripReady)return;
  const i=ST.wallets.findIndex(w=>w.id===id);
  if(i<0||ST.wallets[i].pending<=0){toast('Nothing to Withdraw','No pending balance');return;}
  const amount=ST.wallets[i].pending;
  ST.wallets[i]={...ST.wallets[i],pending:0};
  ST.blockNum++;
  ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'withdraw',from:ST.wallets[i].name,to:'WITHDRAWN',amount,time:new Date().toISOString()});
  if(ST.ledger.length>200)ST.ledger.length=200;
  ST.totalWithdrawn=r4(ST.totalWithdrawn+amount);
  scheduleSave();renderAll();
  toast('Withdrawal Initiated',`${fmt(amount,4)} $PvE withdrawn`);
}

// ════════════════════════════════════
// PAUSE
// ════════════════════════════════════
function togglePause(id){
  const i=ST.wallets.findIndex(w=>w.id===id);if(i<0)return;
  ST.wallets[i]={...ST.wallets[i],paused:!ST.wallets[i].paused};
  const w=ST.wallets[i];scheduleSave();renderAll();
  toast(w.paused?'Wallet Paused':'Wallet Resumed',`${w.name} ${w.paused?'paused':'active'}`);
}

// ════════════════════════════════════
// LEDGER
// ════════════════════════════════════
function renderLedger(){
  const tb=$('ledger-body');if(!tb)return;
  if(!ST.ledger.length){tb.innerHTML='<tr><td colspan="6" style="text-align:center;padding:36px;color:var(--dim);font-size:11px;font-style:italic;">No transactions yet.</td></tr>';return;}
  tb.innerHTML=ST.ledger.map((tx,i)=>{
    const s=TX_STYLE[tx.type]||TX_STYLE.send;
    const ac=tx.type==='reward'||tx.type==='withdraw'?'#4caf6e':tx.type==='send'||tx.type==='auto'?'#c0392b':'var(--text)';
    const pf=tx.type==='send'||tx.type==='auto'?'−':'+';
    const tm=tx.time?new Date(tx.time).toLocaleTimeString('en-US',{hour:'2-digit',minute:'2-digit',second:'2-digit'}):'—';
    return `<tr${i===0?' class="nr"':''}>
      <td><span class="bnum">#${tx.block}</span></td>
      <td><span class="tx-badge" style="background:${s.bg};color:${s.c};border:1px solid ${s.b};">${s.l}</span></td>
      <td><div style="font-size:11px;color:var(--text);white-space:nowrap;">${tx.from}</div><div style="font-size:10px;color:var(--dim);white-space:nowrap;">→ ${tx.to}</div></td>
      <td style="white-space:nowrap;"><span style="color:${ac};">${pf}${fmt(tx.amount||0,4)} $PvE</span></td>
      <td>${tx.fee?`<span style="font-size:10px;color:var(--purple);white-space:nowrap;">−${tx.fee}</span>`:'<span style="color:var(--dim);font-size:10px;">—</span>'}</td>
      <td><span style="font-size:10px;color:var(--dim);white-space:nowrap;">${tm}</span></td>
    </tr>`;
  }).join('');
}

// ════════════════════════════════════
// ADD WALLET
// ════════════════════════════════════
const MAX_WALLETS = 3;

async function walletsAdded() {
  const users = (await loadS('rwys-users')) || {};
  const u = session?.username;
  if (!u || !users[u]) return 0;
  return users[u].walletsAdded || 0;
}

async function openAddWallet() {
  const added = await walletsAdded();
  const remaining = MAX_WALLETS - added;
  if (remaining <= 0) {
    showLimitModal();
    return;
  }
  // Update modal slot counter before showing
  updateSlotCounter(added);
  show('modal-add');
  $('add-addr').focus();
}

function updateSlotCounter(added) {
  const remaining = MAX_WALLETS - added;
  const bar = $('slot-bar-fill');
  const label = $('slot-label');
  const usedLbl = $('slot-used-label');
  const color = remaining === 0 ? 'var(--red)' : remaining === 1 ? '#f59e0b' : 'var(--green)';
  const pct = (added / MAX_WALLETS) * 100;
  if (bar) { bar.style.width = pct + '%'; bar.style.background = color; }
  if (label) {
    label.textContent = remaining === 0 ? 'No slots remaining' : remaining === 1 ? '1 slot remaining' : remaining + ' slots remaining';
    label.style.color = color;
  }
  if (usedLbl) { usedLbl.textContent = added + ' used'; }
  // Update header button
  const btn = $('add-wallet-btn');
  if (btn) {
    btn.textContent = remaining === 0 ? '⛔ WALLET LIMIT REACHED' : `+ ADD WALLET (${remaining} left)`;
    btn.style.color = remaining === 0 ? 'var(--red)' : 'var(--dim)';
    btn.style.borderColor = remaining === 0 ? 'rgba(192,57,43,.4)' : 'var(--bdr2)';
  }
}

function showLimitModal() {
  show('modal-limit');
}
function closeAdd(){hide('modal-add');$('add-addr').value='';$('add-name').value='';const m=$('add-addr-dupe-msg');if(m)m.style.display='none';}
async function submitAdd(){
  const a=$('add-addr').value.trim(),n=$('add-name').value.trim();
  if(!n){toast('Name Required','Enter a display name for this wallet');return;}
  if(!a||a.length<4){toast('Invalid','Enter a valid address');return;}
  if(ST.wallets.find(w=>w.addr.toLowerCase()===a.toLowerCase())){toast('Address Already Registered','This wallet address is already in the registry.');return;}
  // Check limit
  const users=(await loadS('rwys-users'))||{};
  const u=session?.username;
  const added=(users[u]?.walletsAdded||0);
  if(added>=MAX_WALLETS){closeAdd();showLimitModal();return;}
  // Add wallet
  const id='wa'+Date.now();
  ST.wallets.push({id,name:n,addr:a,balance:0,locked:1000,eth:0.1,paused:false,pending:0,tag:'Added Wallet',color:PALETTE[ST.wallets.length%PALETTE.length],isUser:true});
  ST.blockNum++;
  ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'mint',from:'PROTOCOL',to:n,amount:100,time:new Date().toISOString()});
  if(ST.ledger.length>200)ST.ledger.length=200;
  // Persist incremented counter
  users[u]={...users[u],walletsAdded:(added+1)};
  await saveS('rwys-users',users);
  closeAdd();scheduleSave();renderAll();
  const newRemaining=MAX_WALLETS-(added+1);
  toast('Wallet Added',`${n} · 100 $PvE · ${newRemaining} slot${newRemaining===1?'':'s'} remaining`);
}

// ════════════════════════════════════
// AUTOMATION
// ════════════════════════════════════
function renderAutoDropdown(){
  const sel=$('auto-wallet');if(!sel)return;
  const cur=sel.value;
  sel.innerHTML=ST.wallets.map(w=>`<option value="${w.id}">${w.name}</option>`).join('');
  if(cur)sel.value=cur;
}
function createRule(){
  const wid=$('auto-wallet').value,sec=Math.max(5,parseFloat($('auto-sec').value)||10),amt=parseFloat($('auto-amt').value)||1,max=Math.min(5,Math.max(1,parseInt($('auto-max').value)||1));
  const w=ST.wallets.find(x=>x.id===wid);if(!w){toast('Error','Pick a wallet');return;}
  const rule={id:ruleId++,wid,sec,amt,max,on:true,tid:null};
  rule.tid=setInterval(()=>fireRule(rule),rule.sec*1000);
  rules.push(rule);renderRules();
  toast('Rule Created',`${w.name} · every ${rule.sec}s`);
}
function fireRule(rule){
  const si=ST.wallets.findIndex(x=>x.id===rule.wid);if(si<0||!rule.on||ST.wallets[si].paused)return;
  const sender=ST.wallets[si],others=ST.wallets.filter(x=>x.id!==rule.wid&&!x.paused);
  const targets=[...others].sort(()=>Math.random()-.5).slice(0,rule.max);
  const fee=parseFloat((targets.length*FEE).toFixed(6));
  if(sender.eth<fee){rule.on=false;renderRules();toast(sender.name+' out of $ETH','Automation paused');return;}
  if(sender.balance<targets.length*rule.amt+0.01)return;
  targets.forEach(rec=>{
    const ri=ST.wallets.findIndex(x=>x.id===rec.id);if(ri<0)return;
    ST.wallets[si]={...ST.wallets[si],balance:r4(ST.wallets[si].balance-rule.amt+1),eth:r4(ST.wallets[si].eth-FEE)};
    ST.wallets[ri]={...ST.wallets[ri],balance:r4(ST.wallets[ri].balance+rule.amt)};
    ST.blockNum++;
    ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'auto',from:sender.name,to:rec.name,amount:rule.amt,fee:FEE,time:new Date().toISOString()});
    ST.blockNum++;
    ST.ledger.unshift({block:ST.blockNum,hash:genHash(),type:'reward',from:'PROTOCOL',to:sender.name,amount:1,time:new Date().toISOString()});
    ST.totalVol=r4(ST.totalVol+rule.amt);ST.totalRewards++;
  });
  if(ST.ledger.length>200)ST.ledger.length=200;
  scheduleSave();renderAll();
}
function toggleRule(id){
  const r=rules.find(x=>x.id===id);if(!r)return;r.on=!r.on;
  if(r.on&&!r.tid)r.tid=setInterval(()=>fireRule(r),r.sec*1000);
  if(!r.on&&r.tid){clearInterval(r.tid);r.tid=null;}
  renderRules();
}
function deleteRule(id){
  const r=rules.find(x=>x.id===id);if(r?.tid)clearInterval(r.tid);
  rules=rules.filter(x=>x.id!==id);renderRules();
}
function renderRules(){
  const c=$('rules-list');if(!c)return;
  if(!rules.length){c.innerHTML='<div style="text-align:center;padding:18px;font-size:10px;color:var(--dim);font-style:italic;">No rules yet.</div>';return;}
  c.innerHTML=rules.map(r=>{
    const w=ST.wallets.find(x=>x.id===r.wid),low=w&&w.eth<0.05,sc=r.on?(low?'#f59e0b':'var(--purple)'):'var(--red)';
    return `<div class="rule-row" style="border-color:${r.on?'rgba(192,132,252,.25)':'var(--bdr)'};">
      <div class="rule-info">
        <div class="rule-name" style="color:${sc};">
          ${w?.name||'?'}
          <span style="font-size:9px;letter-spacing:.1em;padding:2px 6px;border:1px solid ${sc};border-radius:2px;margin-left:6px;">${r.on?(low?'LOW $ETH':'ACTIVE'):'PAUSED'}</span>
        </div>
        <div class="rule-detail">Every <b style="color:var(--text);">${r.sec}s</b> · <b style="color:var(--text);">${r.amt} $PvE</b> × <b style="color:var(--text);">${r.max}</b> wallets · <span style="color:var(--purple);">${(r.max*FEE).toFixed(3)} $ETH/fire</span> · $ETH left: <span style="color:${low?'#f59e0b':'var(--purple)'};">${w?w.eth.toFixed(3):'?'}</span></div>
      </div>
      <div class="rule-actions">
        <button onclick="toggleRule(${r.id})" style="background:${r.on?'rgba(192,57,43,.15)':'rgba(76,175,110,.15)'};color:${r.on?'var(--red)':'var(--green)'};border:1px solid ${r.on?'rgba(192,57,43,.3)':'rgba(76,175,110,.3)'};font-family:'Space Mono',monospace;font-size:10px;padding:8px 14px;border-radius:2px;white-space:nowrap;">${r.on?'PAUSE':'RESUME'}</button>
        <button class="btn-sm" onclick="deleteRule(${r.id})">✕</button>
      </div>
    </div>`;
  }).join('');
}

// ════════════════════════════════════
// BOOT
// ════════════════════════════════════
setMode('login');
setInterval(()=>{ const t=$('ft-time');if(t)t.textContent=new Date().toUTCString(); },1000);
</script>
</body>
</html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>REAP WHAT YOU SOW — $TRIAL</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Bebas+Neue&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a06;
    --surface: #111108;
    --surface2: #1a1a10;
    --gold: #d4a843;
    --gold-bright: #f0c84a;
    --gold-dim: #8a6c25;
    --green: #4caf6e;
    --red: #c0392b;
    --text: #e8e0c8;
    --text-dim: #8a8068;
    --border: #2a2818;
    --border-bright: #3d3820;
    --grain: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: var(--grain);
    pointer-events: none;
    z-index: 1000;
    opacity: 0.5;
  }

  /* Radial glow */
  body::after {
    content: '';
    position: fixed;
    top: -20%;
    left: 50%;
    transform: translateX(-50%);
    width: 800px;
    height: 400px;
    background: radial-gradient(ellipse, rgba(212,168,67,0.07) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 24px;
    position: relative;
    z-index: 1;
  }

  /* HEADER */
  header {
    padding: 40px 0 24px;
    border-bottom: 1px solid var(--border);
    position: relative;
  }

  .header-inner {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    gap: 24px;
    flex-wrap: wrap;
  }

  .logo-block h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(42px, 7vw, 80px);
    letter-spacing: 0.04em;
    line-height: 0.9;
    color: var(--gold);
    text-shadow: 0 0 60px rgba(212,168,67,0.3);
  }

  .logo-block h1 span {
    color: var(--text);
    opacity: 0.3;
  }

  .logo-block .subtitle {
    font-size: 10px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-top: 6px;
  }

  .supply-ticker {
    text-align: right;
  }

  .supply-ticker .label {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 4px;
  }

  .supply-ticker .value {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 40px;
    color: var(--gold-bright);
    letter-spacing: 0.05em;
    line-height: 1;
    text-shadow: 0 0 30px rgba(240,200,74,0.4);
  }

  .supply-ticker .unit {
    font-size: 10px;
    color: var(--gold-dim);
    letter-spacing: 0.15em;
  }

  .inflation-notice {
    display: none;
    margin-top: 4px;
    font-size: 10px;
    letter-spacing: 0.12em;
    color: var(--green);
    animation: pulse-text 1s ease-in-out infinite;
  }

  .inflation-notice.active { display: block; }

  @keyframes pulse-text {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.4; }
  }

  /* MAIN GRID */
  .main-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin: 28px 0;
  }

  @media (max-width: 700px) {
    .main-grid { grid-template-columns: 1fr; }
  }

  /* PANELS */
  .panel {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 2px;
    overflow: hidden;
  }

  .panel-header {
    padding: 14px 20px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 10px;
    background: var(--surface2);
  }

  .panel-header .dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--gold);
    box-shadow: 0 0 8px var(--gold);
  }

  .panel-header h2 {
    font-size: 10px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--text-dim);
    font-weight: 400;
  }

  .panel-body { padding: 20px; }

  /* WALLET CARDS */
  .wallets-panel { grid-column: 1 / -1; }

  .wallets-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }

  .wallet-card {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 16px;
    cursor: pointer;
    transition: border-color 0.15s, background 0.15s;
    position: relative;
    overflow: hidden;
  }

  .wallet-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-dim), transparent);
    opacity: 0;
    transition: opacity 0.2s;
  }

  .wallet-card:hover, .wallet-card.selected {
    border-color: var(--gold-dim);
    background: #1e1d10;
  }

  .wallet-card:hover::before, .wallet-card.selected::before { opacity: 1; }

  .wallet-card.selected { border-color: var(--gold); }
  .wallet-card.wallet-paused { opacity: 0.7; border-color: rgba(192,57,43,0.3) !important; }
  .wallet-card.wallet-paused::before { background: linear-gradient(90deg, transparent, rgba(192,57,43,0.4), transparent) !important; }

  .wallet-name {
    font-family: 'DM Serif Display', serif;
    font-size: 16px;
    color: var(--gold-bright);
    margin-bottom: 4px;
  }

  .wallet-addr {
    font-size: 10px;
    color: var(--text-dim);
    letter-spacing: 0.05em;
    margin-bottom: 10px;
    word-break: break-all;
  }

  .wallet-balance {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 30px;
    color: var(--text);
    letter-spacing: 0.05em;
  }

  .wallet-balance span {
    font-size: 10px;
    color: var(--gold-dim);
    letter-spacing: 0.1em;
    font-family: 'Space Mono', monospace;
  }

  .wallet-tag {
    display: inline-block;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    padding: 2px 6px;
    border: 1px solid var(--border-bright);
    color: var(--text-dim);
    margin-top: 8px;
  }

  /* SEND PANEL */
  .form-group {
    margin-bottom: 16px;
  }

  label {
    display: block;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 6px;
  }

  select, input[type="number"] {
    width: 100%;
    background: var(--surface2);
    border: 1px solid var(--border-bright);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 10px 12px;
    border-radius: 2px;
    outline: none;
    transition: border-color 0.15s;
    appearance: none;
    -webkit-appearance: none;
  }

  select {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M0 0l5 6 5-6z' fill='%238a6c25'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 12px center;
    padding-right: 30px;
  }

  select:focus, input[type="number"]:focus {
    border-color: var(--gold-dim);
  }

  input[type="number"]::-webkit-inner-spin-button { opacity: 0; }

  .recipient-row {
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: center;
    gap: 8px;
    padding: 8px 10px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 2px;
    margin-bottom: 6px;
    transition: border-color 0.15s;
  }

  .recipient-row:focus-within {
    border-color: var(--gold-dim);
  }

  .recipient-row.has-amount {
    border-color: var(--gold-dim);
    background: #1e1d10;
  }

  .recipient-row .r-name {
    font-family: 'DM Serif Display', serif;
    font-size: 10px;
    color: var(--gold-bright);
    line-height: 1.1;
  }

  .recipient-row .r-bal {
    font-size: 10px;
    color: var(--text-dim);
    letter-spacing: 0.08em;
    margin-top: 1px;
  }

  .recipient-row .r-input-wrap {
    position: relative;
    width: 100px;
  }

  .recipient-row .r-prefix {
    position: absolute;
    left: 8px; top: 50%;
    transform: translateY(-50%);
    font-size: 10px;
    color: var(--gold-dim);
    pointer-events: none;
    letter-spacing: 0.08em;
  }

  .recipient-row input[type="number"] {
    width: 100%;
    background: var(--bg);
    border: 1px solid var(--border-bright);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 7px 8px 7px 42px;
    border-radius: 2px;
    outline: none;
    transition: border-color 0.15s;
    text-align: right;
    padding-right: 8px;
    padding-left: 42px;
  }

  .recipient-row input[type="number"]:focus {
    border-color: var(--gold-dim);
  }

  .recipient-row input[type="number"]::-webkit-inner-spin-button { opacity: 0; }

  .send-btn {
    width: 100%;
    background: var(--gold);
    color: #0a0a06;
    border: none;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 10px;
    letter-spacing: 0.15em;
    padding: 14px;
    border-radius: 2px;
    cursor: pointer;
    transition: background 0.15s, transform 0.1s;
    margin-top: 4px;
  }

  .send-btn:hover { background: var(--gold-bright); }
  .send-btn:active { transform: scale(0.99); }
  .send-btn:disabled { background: var(--gold-dim); cursor: not-allowed; opacity: 0.5; }

  .tx-feedback {
    margin-top: 12px;
    padding: 10px 14px;
    font-size: 10px;
    letter-spacing: 0.1em;
    border-radius: 2px;
    display: none;
    line-height: 1.6;
  }

  .tx-feedback.success {
    display: block;
    background: rgba(76,175,110,0.08);
    border: 1px solid rgba(76,175,110,0.3);
    color: var(--green);
  }

  .tx-feedback.error {
    display: block;
    background: rgba(192,57,43,0.08);
    border: 1px solid rgba(192,57,43,0.3);
    color: var(--red);
  }

  .selected-wallet-info {
    background: var(--surface2);
    border: 1px solid var(--border);
    padding: 12px 14px;
    margin-bottom: 16px;
    border-radius: 2px;
    font-size: 10px;
    color: var(--text-dim);
  }

  .selected-wallet-info .name {
    font-family: 'DM Serif Display', serif;
    font-size: 10px;
    color: var(--gold);
    margin-bottom: 2px;
  }

  .selected-wallet-info .bal {
    font-size: 10px;
    color: var(--text);
  }

  .no-wallet-msg {
    text-align: center;
    padding: 30px;
    color: var(--text-dim);
    font-size: 10px;
    letter-spacing: 0.1em;
    font-style: italic;
  }

  /* LEDGER */
  .ledger-panel { grid-column: 1 / -1; }

  .ledger-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 10px;
  }

  .ledger-table th {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text-dim);
    font-weight: 400;
    padding: 0 14px 12px;
    text-align: left;
    border-bottom: 1px solid var(--border);
  }

  .ledger-table td {
    padding: 12px 14px;
    border-bottom: 1px solid var(--border);
    vertical-align: top;
    line-height: 1.5;
  }

  .ledger-table tr:last-child td { border-bottom: none; }

  .ledger-table tr {
    transition: background 0.1s;
  }

  .ledger-table tbody tr:hover {
    background: rgba(212,168,67,0.03);
  }

  .ledger-table tr.new-tx {
    animation: flash-row 0.8s ease-out;
  }

  @keyframes flash-row {
    0% { background: rgba(212,168,67,0.15); }
    100% { background: transparent; }
  }

  .tx-hash {
    font-size: 10px;
    color: var(--gold-dim);
    letter-spacing: 0.05em;
    font-family: 'Space Mono', monospace;
  }

  .tx-type {
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 2px 6px;
    border-radius: 2px;
    display: inline-block;
  }

  .tx-type.send { background: rgba(192,57,43,0.12); color: var(--red); border: 1px solid rgba(192,57,43,0.2); }
  .tx-type.receive { background: rgba(76,175,110,0.1); color: var(--green); border: 1px solid rgba(76,175,110,0.2); }
  .tx-type.reward { background: rgba(212,168,67,0.1); color: var(--gold); border: 1px solid rgba(212,168,67,0.2); }
  .tx-type.mint { background: rgba(100,149,237,0.1); color: #7fb3f5; border: 1px solid rgba(100,149,237,0.2); }
  .tx-type.auto { background: rgba(192,132,252,0.1); color: #c084fc; border: 1px solid rgba(192,132,252,0.2); }
  .tx-type.errnearn { background: rgba(192,132,252,0.18); color: #e879f9; border: 1px solid rgba(232,121,249,0.35); }
  .tx-amount-err { color: #e879f9; }

  .tx-amount-pos { color: var(--green); }
  .tx-amount-neg { color: var(--red); }
  .tx-amount-gold { color: var(--gold); }

  .from-to {
    color: var(--text);
    font-size: 10px;
  }

  .addr-short { color: var(--text-dim); font-size: 10px; }

  .timestamp { color: var(--text-dim); font-size: 10px; }

  .block-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 10px;
    color: var(--text-dim);
    letter-spacing: 0.05em;
  }

  /* STATS BAR */
  .stats-bar {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    margin-bottom: 20px;
    border-radius: 2px;
    overflow: hidden;
  }

  .stat-item {
    background: var(--surface);
    padding: 14px 18px;
  }

  .stat-item .s-label {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 4px;
  }

  .stat-item .s-value {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 24px;
    color: var(--text);
    letter-spacing: 0.05em;
    line-height: 1;
  }

  .stat-item .s-value.gold { color: var(--gold-bright); }

  /* SCROLLABLE LEDGER */
  .ledger-scroll {
    max-height: 420px;
    overflow-y: auto;
  }

  .ledger-scroll::-webkit-scrollbar { width: 4px; }
  .ledger-scroll::-webkit-scrollbar-track { background: var(--surface); }
  .ledger-scroll::-webkit-scrollbar-thumb { background: var(--border-bright); border-radius: 2px; }

  .empty-ledger {
    text-align: center;
    padding: 48px;
    color: var(--text-dim);
    font-size: 10px;
    letter-spacing: 0.15em;
    font-style: italic;
  }

  /* LIVE INDICATOR */
  .live-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--green);
    text-transform: uppercase;
  }

  .live-dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--green);
    box-shadow: 0 0 6px var(--green);
    animation: blink 1.5s ease-in-out infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.2; }
  }

  /* RULE BANNER */
  .rules-banner {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-left: 3px solid var(--gold-dim);
    padding: 14px 18px;
    margin-bottom: 20px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 8px 24px;
    font-size: 10px;
    color: var(--text-dim);
    line-height: 1.7;
    border-radius: 2px;
  }

  .rules-banner strong { color: var(--gold); font-weight: 400; }

  .inflation-bar {
    grid-column: 1 / -1;
    height: 3px;
    background: var(--border);
    border-radius: 2px;
    overflow: hidden;
    margin-top: 4px;
  }

  .inflation-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--gold-dim), var(--gold-bright));
    transition: width 0.5s ease;
    border-radius: 2px;
  }

  .inflation-countdown {
    font-size: 10px;
    color: var(--text-dim);
    margin-top: 6px;
    letter-spacing: 0.1em;
  }

  .inflation-countdown.active { color: var(--green); }

  footer {
    border-top: 1px solid var(--border);
    padding: 20px 0;
    margin-top: 8px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 10px;
  }

  footer p {
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--text-dim);
  }

  /* Toast */
  .toast {
    position: fixed;
    bottom: 30px;
    right: 30px;
    background: var(--surface2);
    border: 1px solid var(--gold-dim);
    padding: 14px 20px;
    border-radius: 2px;
    font-size: 10px;
    color: var(--text);
    letter-spacing: 0.05em;
    z-index: 999;
    transform: translateY(20px);
    opacity: 0;
    transition: all 0.3s ease;
    max-width: 300px;
    line-height: 1.5;
    box-shadow: 0 8px 32px rgba(0,0,0,0.5);
  }

  .toast.show { transform: translateY(0); opacity: 1; }
  .toast .toast-title { font-family: 'DM Serif Display', serif; color: var(--gold); margin-bottom: 4px; font-size: 10px; }
</style>
</head>
<body>

<div class="container">
  <header>
    <div class="header-inner">
      <div class="logo-block">
        <h1>REAP WHAT<br><span>//</span> YOU SOW</h1>
        <p class="subtitle">Transparent Ledger · $TRIAL Token Experiment</p>
      </div>
      <div class="supply-ticker">
        <div class="label">Circulating Supply</div>
        <div class="value" id="total-supply">1,000</div>
        <div class="unit">$TRIAL IN EXISTENCE</div>
        <div class="inflation-notice" id="inflation-notice">⬆ INFLATION ACTIVE — +500 $TRIAL/min</div>
      </div>
    </div>
  </header>

  <div style="margin-top: 20px;">
    <div class="stats-bar">
      <div class="stat-item">
        <div class="s-label">Total Transactions</div>
        <div class="s-value" id="stat-tx">0</div>
      </div>
      <div class="stat-item">
        <div class="s-label">Total Volume</div>
        <div class="s-value gold" id="stat-vol">0</div>
      </div>
      <div class="stat-item">
        <div class="s-label">Rewards Issued</div>
        <div class="s-value" id="stat-rewards">0</div>
      </div>
      <div class="stat-item">
        <div class="s-label">Active Wallets</div>
        <div class="s-value" id="stat-wallets">6</div>
      </div>
      <div class="stat-item">
        <div class="s-label">Current Block</div>
        <div class="s-value" id="stat-block">0</div>
      </div>
    </div>

    <div class="rules-banner">
      <div><strong>SEND REWARD:</strong> Sender receives <strong>+1 $TRIAL</strong> back for every transaction</div>
      <div><strong>INFLATION TRIGGER:</strong> When any wallet holds &lt;2,500 $TRIAL, <strong>+500 $TRIAL/min</strong> minted</div>
      <div><strong>TRANSPARENCY:</strong> All transactions visible on ledger below — no hidden moves</div>
      <div><strong>FIXED SUPPLY:</strong> Started at <strong>10,000 $TRIAL</strong> — every coin accounted for</div>
      <div><strong>$ETH ECONOMY:</strong> Fee: <strong>−0.002/tx</strong> · Drip: <strong>+0.007 $ETH</strong> every 30s · Cap: <strong>0.1 $ETH</strong> per wallet</div>
      <div style="grid-column: 1 / -1;">
        <div style="font-size:10px; letter-spacing:0.15em; text-transform:uppercase; color:var(--text-dim); margin-bottom:6px;">SUPPLY HEALTH — Inflation triggers below 2,500 $TRIAL in any wallet</div>
        <div class="inflation-bar"><div class="inflation-bar-fill" id="inflation-bar-fill" style="width:100%"></div></div>
        <div class="inflation-countdown" id="inflation-countdown">All wallets healthy</div>
      </div>
    </div>

    <div class="main-grid">
      <!-- SEND -->
      <div class="panel">
        <div class="panel-header">
          <div class="dot" style="background:var(--green); box-shadow: 0 0 8px var(--green);"></div>
          <h2>Multi-Send $TRIAL</h2>
        </div>
        <div class="panel-body" id="send-panel-body">
          <div class="no-wallet-msg" id="no-wallet-msg">← Select a wallet to send from</div>
          <div id="send-form" style="display:none;">
            <div class="selected-wallet-info" id="selected-info">
              <div class="name" id="sel-name">—</div>
              <div class="bal" id="sel-bal">—</div>
            </div>

            <div style="font-size:10px; letter-spacing:0.2em; text-transform:uppercase; color:var(--text-dim); margin-bottom:10px;">Recipients — set amount per wallet (0 = skip)</div>

            <div id="multi-recipients"></div>

            <div style="background:var(--surface2); border:1px solid var(--border); border-radius:2px; padding:10px 14px; margin: 14px 0; display:flex; justify-content:space-between; align-items:center;">
              <span style="font-size:10px; letter-spacing:0.15em; text-transform:uppercase; color:var(--text-dim);">Total to Send</span>
              <span style="font-family:'Bebas Neue',sans-serif; font-size:24px; color:var(--gold-bright);" id="send-total-display">0 <span style="font-size:10px; color:var(--gold-dim);">$TRIAL</span></span>
            </div>

            <button class="send-btn" id="send-btn" onclick="executeSend()">BROADCAST ALL TRANSACTIONS</button>
            <div class="tx-feedback" id="tx-feedback"></div>
          </div>
        </div>
      </div>

      <!-- BLOCK EXPLORER -->
      <div class="panel">
        <div class="panel-header">
          <div class="dot" style="background:#7fb3f5; box-shadow: 0 0 8px #7fb3f5;"></div>
          <h2>Wallet Inspector</h2>
        </div>
        <div class="panel-body" id="inspector-panel">
          <div class="no-wallet-msg">Select a wallet below to inspect</div>
        </div>
      </div>

      <!-- AUTOMATION -->
      <div class="panel wallets-panel" id="automation-panel-wrap">
        <div class="panel-header">
          <div class="dot" style="background:#c084fc; box-shadow: 0 0 8px #c084fc;"></div>
          <h2>Automation — Schedule Auto-Sends</h2>
          <div style="margin-left:auto; font-size:10px; color:#c084fc; letter-spacing:0.15em;">0.002 $ETH fee / tx</div>
        </div>
        <div class="panel-body">
          <div style="display:grid; grid-template-columns: 1fr 1fr 1fr 1fr auto; gap:10px; align-items:end; margin-bottom:16px; flex-wrap:wrap;">
            <div>
              <label>From Wallet</label>
              <select id="auto-wallet" style="font-size:10px; padding:8px 10px;"></select>
            </div>
            <div>
              <label>Every (seconds)</label>
              <input type="number" id="auto-interval" min="5" step="1" value="10" style="font-size:10px; padding:8px 10px;">
            </div>
            <div>
              <label>Amount / Recipient</label>
              <input type="number" id="auto-amount" min="0.01" step="0.01" value="1" style="font-size:10px; padding:8px 10px;">
            </div>
            <div>
              <label>Max Recipients</label>
              <input type="number" id="auto-max-recv" min="1" max="5" step="1" value="1" style="font-size:10px; padding:8px 10px;">
            </div>
            <div>
              <button onclick="createAutomation()" style="background:#c084fc; color:#0a0a06; border:none; font-family:'Bebas Neue',sans-serif; font-size:16px; letter-spacing:0.1em; padding:9px 18px; border-radius:2px; cursor:pointer; white-space:nowrap;">+ ADD RULE</button>
            </div>
          </div>
          <div id="automations-list" style="display:flex; flex-direction:column; gap:8px;">
            <div style="text-align:center; padding:20px; font-size:10px; color:var(--text-dim); font-style:italic; letter-spacing:0.1em;">No automation rules yet. Add one above.</div>
          </div>
        </div>
      </div>

      <!-- WALLETS -->
      <div class="panel wallets-panel">
        <div class="panel-header">
          <div class="dot"></div>
          <h2>Wallet Registry — Click to Switch Sender</h2>
          <div style="margin-left:auto;"><div class="live-badge"><div class="live-dot"></div>Live</div></div>
        </div>
        <div class="panel-body">
          <div class="wallets-grid" id="wallets-grid"></div>
        </div>
      </div>

      <!-- LEDGER -->
      <div class="panel ledger-panel">
        <div class="panel-header">
          <div class="dot" style="background:var(--gold-bright); box-shadow: 0 0 8px var(--gold-bright);"></div>
          <h2>Global Ledger — All Transactions</h2>
          <div style="margin-left:auto; font-size:10px; color:var(--text-dim); letter-spacing:0.1em;">Block Explorer · OP Mainnet · 2s blocks</div>
        </div>
        <div class="ledger-scroll">
          <table class="ledger-table">
            <thead>
              <tr>
                <th>Block</th>
                <th>Tx Hash</th>
                <th>Type</th>
                <th>From → To</th>
                <th>Amount</th>
                <th style="color:#c084fc;">$ETH Fee</th>
                <th>Time</th>
              </tr>
            </thead>
            <tbody id="ledger-body">
              <tr><td colspan="7"><div class="empty-ledger">No transactions yet. Send $TRIAL to begin.</div></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>

  <footer>
    <p>$TRIAL · Reap What You Sow · Experimental Ledger System</p>
    <p id="footer-time">—</p>
  </footer>
</div>

<div class="toast" id="toast">
  <div class="toast-title" id="toast-title"></div>
  <div id="toast-msg"></div>
</div>

<script>
// ===================== STATE =====================
// ── Full OP Mainnet wallet pool — wallets are drawn from here into the active set ──
const WALLET_POOL = [
  { name: 'Optimism Foundation',    addr: '0x2501c477...8b3f0', tag: 'OP Foundation Multisig' },
  { name: 'Velodrome Finance',      addr: '0xF4c67CdA...2bD87', tag: 'DEX · OP Mainnet' },
  { name: 'Uniswap V3 Router',     addr: '0xE592427A...5932D', tag: 'Swap Router · OP' },
  { name: 'Aave V3 Pool',          addr: '0x794a6135...14aD',  tag: 'Lending Protocol · OP' },
  { name: 'Synthetix Treasury',    addr: '0x99f4176e...A92',   tag: 'Protocol Treasury' },
  { name: 'OP Token Contract',     addr: '0x42000000...0042',  tag: 'Native OP Token · ERC-20' },
  { name: 'Coinbase Bridge',       addr: '0x3154Cf16...5026',  tag: 'L1→L2 Bridge · Coinbase' },
  { name: 'Kwenta Staking',        addr: '0x1f5Ea53e...b3F1',  tag: 'Perps DEX · OP' },
  { name: 'Beethoven X',           addr: '0xBA12222...1111',   tag: 'Balancer Fork · OP' },
  { name: 'Exactly Protocol',      addr: '0x3d76e86...cF3A',   tag: 'Fixed-Rate Lending' },
  { name: 'PoolTogether V5',       addr: '0xF35fE10...d7B2',   tag: 'Prize Savings · OP' },
  { name: 'Stargate Finance',      addr: '0xB0D502e...8A41',   tag: 'Cross-Chain Bridge' },
  { name: 'Hop Protocol',          addr: '0x83f6244...Ca12',   tag: 'L2 Bridge Aggregator' },
  { name: 'Socket Bridge',         addr: '0x3a23F943...891C',  tag: 'Bridge Aggregator' },
  { name: 'Perpetual Protocol',    addr: '0xAD7b4C1...3390',   tag: 'Perps Protocol · OP' },
  { name: 'dHEDGE Pool',          addr: '0x90263779...FF41',   tag: 'Asset Manager · OP' },
  { name: 'Lyra Finance',          addr: '0x59D0d4A...90A1',   tag: 'Options Protocol · OP' },
  { name: 'Curve Finance OP',      addr: '0x445FE580...bF44',  tag: 'Stableswap DEX' },
  { name: 'Sonne Finance',         addr: '0x60CF091...C1D3',   tag: 'Lending Market · OP' },
  { name: 'WePiggy Protocol',      addr: '0x0D8F841...2EA1',   tag: 'Money Market · OP' },
  { name: 'Beefy Finance',         addr: '0x4710fc9...A501',   tag: 'Yield Optimizer' },
  { name: 'Clipper DEX',           addr: '0x655bFe2...9F31',   tag: 'Stablecoin DEX · OP' },
  { name: 'Rubicon Market',        addr: '0x7B5B3e5...CC01',   tag: 'Orderbook DEX · OP' },
  { name: 'Tarot Finance',         addr: '0x35A0DD1...8811',   tag: 'Leveraged LP · OP' },
  { name: 'Granary Finance',       addr: '0xB702CE1...E9D2',   tag: 'Lending Fork · OP' },
  { name: 'Overnight Finance',     addr: '0xE80772E...B3A1',   tag: 'Stablecoin Yield · OP' },
  { name: 'Pika Protocol',         addr: '0xD5A8f23...7741',   tag: 'Perps Exchange · OP' },
  { name: 'Optimism Multisig 2',   addr: '0x9BA6e03...0f91',   tag: 'OP Core Multisig' },
  { name: 'Alchemix Finance',      addr: '0x76a7bA4...1102',   tag: 'Self-Repaying Loans' },
  { name: 'WETH Gateway',          addr: '0xe9e157...8D1',     tag: 'Wrapped ETH · OP' },
];

const PALETTE = ['#d4a843','#e07b7b','#7bade0','#7be09a','#c07be0','#e0c37b','#e08c7b','#7be0d4','#b07be0','#e0d47b','#7bb8e0','#e07bb8','#a8e07b','#e0a87b','#7be0a8'];
let walletIdCounter = 7;

function makeWallet(poolEntry) {
  const id = 'w' + (walletIdCounter++);
  const color = PALETTE[wallets.length % PALETTE.length];
  const startBal = parseFloat((Math.random() * 800 + 200).toFixed(2));
  return { id, name: poolEntry.name, addr: poolEntry.addr, balance: startBal, error: 0.1, paused: false, tag: poolEntry.tag, color };
}

const wallets = WALLET_POOL.slice(0, 6).map((p, i) => ({
  id: 'w' + (i + 1),
  name: p.name, addr: p.addr, tag: p.tag,
  balance: [2500, 1500, 2000, 1750, 1250, 1000][i],
  error: 0.1, paused: false,
  color: PALETTE[i]
}));

// Track which pool entries are already active
const usedPoolNames = new Set(wallets.map(w => w.name));

// Periodically pull a new wallet from the pool into the active set
function startWalletGrowth() {
  const remaining = WALLET_POOL.filter(p => !usedPoolNames.has(p.name));
  if (remaining.length === 0) return;
  setInterval(() => {
    const pool = WALLET_POOL.filter(p => !usedPoolNames.has(p.name));
    if (pool.length === 0) return;
    const entry = pool[Math.floor(Math.random() * pool.length)];
    usedPoolNames.add(entry.name);
    const w = makeWallet(entry);
    wallets.push(w);
    renderWallets();
    updateStats();
    updateSupplyDisplay();
    // Replenish supply: new wallet gets fresh $TRIAL from protocol
    blockNum++;
    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'mint', from: 'PROTOCOL', to: w.name, amount: w.balance, time: new Date() });
    showToast('New Wallet Joined', w.name + ' · ' + w.tag);
    // Update automation dropdown
    const aw = document.getElementById('auto-wallet');
    if (aw) aw.innerHTML = wallets.map(w => '<option value="' + w.id + '">' + w.name + '</option>').join('');
  }, 8000); // new wallet every 8 seconds
}

// Automation rules
const automations = [];
let autoIdCounter = 1;
const ERROR_FEE = 0.002;
const ERROR_EARN = 0.007;   // earned per qualifying event
const ERROR_CAP  = 0.1;     // wallets cap at 0.1 $ETH
const ERROR_FAUCET_SEC = 30; // passive drip every N seconds per wallet

let ledger = [];
let selectedWalletId = null;
let blockNum = 149165000; // OP Mainnet approximate current block height
let totalTxVol = 0;
let totalRewards = 0;
let inflationInterval = null;

// ===================== INIT =====================
function init() {
  selectedWalletId = 'w6'; // Default: Dev Reserve
  // Populate automation wallet dropdown
  const aw = document.getElementById('auto-wallet');
  if (aw) aw.innerHTML = wallets.map(w => `<option value="${w.id}">${w.name}</option>`).join('');
  renderWallets();
  renderSendForm();
  renderInspector();
  updateStats();
  updateSupplyDisplay();
  checkInflation();
  setInterval(updateFooterTime, 1000);
  updateFooterTime();
  startFaucet();
  startWalletGrowth();
}

function totalSupply() {
  return wallets.reduce((s, w) => s + w.balance, 0);
}

function minWalletBalance() {
  return Math.min(...wallets.map(w => w.balance));
}

// ===================== WALLETS =====================
function renderWallets() {
  const grid = document.getElementById('wallets-grid');
  grid.innerHTML = wallets.map(w => `
    <div class="wallet-card ${selectedWalletId === w.id ? 'selected' : ''} ${w.paused ? 'wallet-paused' : ''}" onclick="selectWallet('${w.id}')">
      <div style="display:flex; justify-content:space-between; align-items:flex-start;">
        <div class="wallet-name">${w.name}</div>
        <button onclick="event.stopPropagation(); toggleWalletPause('${w.id}')" style="background:${w.paused ? 'rgba(76,175,110,0.15)' : 'rgba(192,57,43,0.12)'}; color:${w.paused ? 'var(--green)' : 'var(--red)'}; border:1px solid ${w.paused ? 'rgba(76,175,110,0.3)' : 'rgba(192,57,43,0.25)'}; font-family:'Space Mono',monospace; font-size:10px; letter-spacing:0.12em; padding:3px 7px; border-radius:2px; cursor:pointer; white-space:nowrap;">${w.paused ? '▶ RESUME' : '⏸ PAUSE'}</button>
      </div>
      <div class="wallet-addr">${w.addr}</div>
      <div class="wallet-balance" style="opacity:${w.paused ? 0.45 : 1}">${w.balance.toLocaleString(undefined,{maximumFractionDigits:4})} <span>$TRIAL</span></div>
      <div style="font-size:10px; color:#c084fc; letter-spacing:0.08em; margin-top:2px; opacity:${w.paused ? 0.45 : 1}">${w.error.toFixed(3)} <span style="font-size:10px; opacity:0.7;">$ETH</span></div>
      <div style="display:flex; align-items:center; gap:6px; margin-top:6px;">
        <div class="wallet-tag">${w.tag}</div>
        ${w.paused ? '<span style="font-size:10px; letter-spacing:0.12em; color:var(--red); border:1px solid rgba(192,57,43,0.3); padding:2px 5px;">TX PAUSED</span>' : ''}
      </div>
    </div>
  `).join('');
}

function toggleWalletPause(id) {
  const w = getWallet(id);
  if (!w) return;
  w.paused = !w.paused;
  renderWallets();
  renderInspector();
  showToast(w.paused ? 'Wallet Paused' : 'Wallet Resumed', `${w.name} transactions are now ${w.paused ? 'paused' : 'active'}`);
}

function selectWallet(id) {
  selectedWalletId = id;
  renderWallets();
  renderSendForm();
  renderInspector();
}

function getWallet(id) {
  return wallets.find(w => w.id === id);
}

// ===================== SEND FORM =====================
function renderSendForm() {
  const wallet = getWallet(selectedWalletId);
  if (!wallet) return;

  document.getElementById('no-wallet-msg').style.display = 'none';
  document.getElementById('send-form').style.display = 'block';
  document.getElementById('sel-name').textContent = wallet.name;
  document.getElementById('sel-bal').textContent = `${wallet.balance.toLocaleString(undefined,{maximumFractionDigits:4})} $TRIAL  ·  ${wallet.error.toFixed(3)} $ETH`;

  const container = document.getElementById('multi-recipients');
  container.innerHTML = wallets
    .filter(w => w.id !== selectedWalletId)
    .map(w => `
      <div class="recipient-row" id="rrow-${w.id}">
        <div>
          <div class="r-name">${w.name}</div>
          <div class="r-bal">${w.balance.toLocaleString(undefined, {maximumFractionDigits: 4})} $TRIAL · ${w.addr}</div>
        </div>
        <div class="r-input-wrap">
          <span class="r-prefix">$TRIAL</span>
          <input type="number" min="0" step="0.01" value="0" id="amt-${w.id}"
            oninput="onAmountChange('${w.id}')"
            onfocus="this.select()"
          >
        </div>
      </div>
    `).join('');

  document.getElementById('tx-feedback').style.display = 'none';
  updateSendTotal();
}

function onAmountChange(wid) {
  const input = document.getElementById(`amt-${wid}`);
  const row = document.getElementById(`rrow-${wid}`);
  const val = parseInt(input.value) || 0;
  row.classList.toggle('has-amount', val > 0);
  updateSendTotal();
}

function updateSendTotal() {
  const sender = getWallet(selectedWalletId);
  if (!sender) return;
  const total = getMultiSendTargets().reduce((s, t) => s + t.amount, 0);
  document.getElementById('send-total-display').innerHTML =
    `${total.toLocaleString()} <span style="font-size:10px; color:var(--gold-dim);">$TRIAL</span>`;
}

function getMultiSendTargets() {
  return wallets
    .filter(w => w.id !== selectedWalletId)
    .map(w => ({ wallet: w, amount: parseFloat(document.getElementById(`amt-${w.id}`)?.value) || 0 }))
    .filter(t => t.amount > 0);
}

// ===================== EXECUTE SEND =====================
function executeSend() {
  const sender = getWallet(selectedWalletId);
  const targets = getMultiSendTargets();
  const feedback = document.getElementById('tx-feedback');
  feedback.className = 'tx-feedback';
  feedback.style.display = 'none';

  if (!sender) { showFeedback('error', 'No sender selected.'); return; }
  if (sender.paused) { showFeedback('error', `${sender.name} is paused. Resume it to send transactions.`); return; }
  if (targets.length === 0) { showFeedback('error', 'Enter an amount for at least one recipient.'); return; }

  const totalOut = targets.reduce((s, t) => s + t.amount, 0);
  if (totalOut > sender.balance) {
    showFeedback('error', `Insufficient balance. Need ${totalOut} $TRIAL but ${sender.name} only holds ${sender.balance} $TRIAL.`);
    return;
  }

  // Validate each amount
  for (const t of targets) {
    if (t.amount <= 0) { showFeedback('error', `All amounts must be greater than 0.`); return; }
  }

  const ts = new Date();
  const summaryLines = [];

  const feeTotal = parseFloat((targets.length * ERROR_FEE).toFixed(6));
  if (sender.error < feeTotal) {
    showFeedback('error', `Insufficient $ETH. Need ${feeTotal} $ETH for ${targets.length} tx but only have ${sender.error.toFixed(3)} $ETH.`);
    return;
  }

  for (const { wallet: recipient, amount } of targets) {
    sender.balance = parseFloat((sender.balance - amount).toFixed(6));
    recipient.balance = parseFloat((recipient.balance + amount).toFixed(6));
    sender.balance = parseFloat((sender.balance + 1).toFixed(6));
    sender.error = parseFloat((sender.error - ERROR_FEE).toFixed(6));
    totalRewards += 1;

    blockNum++;
    const txHash = generateHash();

    addLedgerEntry({ block: blockNum, hash: txHash, type: 'send', from: sender.name, to: recipient.name, amount, fee: ERROR_FEE, time: ts });
    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'reward', from: 'PROTOCOL', to: sender.name, amount: 1, time: ts });

    totalTxVol += amount;
    summaryLines.push(`${amount} $TRIAL → ${recipient.name} (−${ERROR_FEE} $ETH)`);
  }

  const rewardTotal = targets.length;
  showFeedback('success',
    `✓ Broadcast ${targets.length} transaction${targets.length > 1 ? 's' : ''}:\n` +
    summaryLines.join('\n') +
    `\n\n+${rewardTotal} $TRIAL rewarded back to ${sender.name}\n−${feeTotal} $ETH burned as fees`
  );
  showToast('Multi-Send Confirmed', `${targets.length} tx · ${totalOut} $TRIAL sent · −${feeTotal} $ETH burned`);

  renderWallets();
  renderSendForm();
  renderInspector();
  updateStats();
  updateSupplyDisplay();
  checkInflation();
}

function showFeedback(type, msg) {
  const el = document.getElementById('tx-feedback');
  el.className = `tx-feedback ${type}`;
  el.textContent = msg;
  el.style.display = 'block';
}

// ===================== LEDGER =====================
function addLedgerEntry(entry) {
  ledger.unshift(entry);
  renderLedger();
}

function renderLedger() {
  const tbody = document.getElementById('ledger-body');
  if (ledger.length === 0) {
    tbody.innerHTML = '<tr><td colspan="7"><div class="empty-ledger">No transactions yet. Send $TRIAL to begin.</div></td></tr>';
    return;
  }

  tbody.innerHTML = ledger.map((tx, i) => {
    let typeLabel, amountClass, amountPrefix;
    switch (tx.type) {
      case 'send':   typeLabel = '<span class="tx-type send">SEND</span>';    amountClass = 'tx-amount-neg'; amountPrefix = '−'; break;
      case 'receive': typeLabel = '<span class="tx-type receive">RECV</span>'; amountClass = 'tx-amount-pos'; amountPrefix = '+'; break;
      case 'reward': typeLabel = '<span class="tx-type reward">REWARD</span>'; amountClass = 'tx-amount-gold'; amountPrefix = '+'; break;
      case 'mint':   typeLabel = '<span class="tx-type mint">MINT</span>';    amountClass = 'tx-amount-pos'; amountPrefix = '+'; break;
      case 'auto':   typeLabel = '<span class="tx-type auto">AUTO</span>';    amountClass = 'tx-amount-neg'; amountPrefix = '−'; break;
      case 'errnearn': typeLabel = '<span class="tx-type errnearn">$ERR+</span>'; amountClass = 'tx-amount-err'; amountPrefix = '+'; break;
    }
    const feeCell = tx.fee ? `<span style="font-size:10px; color:#c084fc;">−${tx.fee} $ETH</span>` : tx.type === 'errnearn' ? `<span style="font-size:10px; color:#e879f9;">+earned $ETH</span>` : `<span style="color:var(--text-dim); font-size:10px;">—</span>`;
    const amountDisplay = tx.currency === 'ERROR' ? `${amountPrefix}${tx.amount} $ETH` : `${amountPrefix}${tx.amount.toLocaleString(undefined,{maximumFractionDigits:4})} $TRIAL`;
    const noteTag = tx.note ? `<div style="font-size:10px; color:var(--text-dim); margin-top:1px; letter-spacing:0.05em;">${tx.note}</div>` : '';
    return `
      <tr class="${i === 0 ? 'new-tx' : ''}">
        <td><div class="block-num">#${tx.block}</div></td>
        <td><div class="tx-hash">${tx.hash}</div></td>
        <td>${typeLabel}</td>
        <td>
          <div class="from-to">${tx.from}</div>
          <div class="addr-short">→ ${tx.to}</div>
        </td>
        <td><span class="${amountClass}">${amountDisplay}</span>${noteTag}</td>
        <td>${feeCell}</td>
        <td><div class="timestamp">${formatTime(tx.time)}</div></td>
      </tr>`;
  }).join('');
}

// ===================== INSPECTOR =====================
function renderInspector() {
  const panel = document.getElementById('inspector-panel');
  const wallet = getWallet(selectedWalletId);
  if (!wallet) {
    panel.innerHTML = '<div class="no-wallet-msg">← Select a wallet to inspect</div>';
    return;
  }

  const walletTxs = ledger.filter(tx => tx.from === wallet.name || tx.to === wallet.name);
  const sent = walletTxs.filter(t => t.type === 'send').reduce((s, t) => s + t.amount, 0);
  const received = walletTxs.filter(t => t.type === 'receive' || (t.type !== 'send' && t.to === wallet.name)).reduce((s, t) => s + t.amount, 0);
  const pct = ((wallet.balance / totalSupply()) * 100).toFixed(1);

  panel.innerHTML = `
    <div style="margin-bottom:16px;">
      <div style="font-family:'DM Serif Display',serif; font-size:24px; color:var(--gold); margin-bottom:4px;">${wallet.name}</div>
      <div style="font-size:10px; color:var(--text-dim); letter-spacing:0.08em; margin-bottom:12px;">${wallet.addr}</div>
      <div style="font-family:'Bebas Neue',sans-serif; font-size:42px; color:var(--text); letter-spacing:0.05em; line-height:1;">${wallet.balance.toLocaleString()}</div>
      <div style="font-size:10px; color:var(--gold-dim); letter-spacing:0.1em; margin-bottom:12px;">$TRIAL · ${pct}% of supply</div>
      <div style="height:3px; background:var(--border); border-radius:2px; margin-bottom:16px; overflow:hidden;">
        <div style="height:100%; width:${pct}%; background:linear-gradient(90deg, var(--gold-dim), var(--gold-bright)); border-radius:2px; transition:width 0.4s ease;"></div>
      </div>
    </div>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:8px; margin-bottom:16px;">
      <div style="background:var(--surface2); border:1px solid var(--border); padding:10px 12px; border-radius:2px;">
        <div style="font-size:10px; letter-spacing:0.15em; text-transform:uppercase; color:var(--text-dim); margin-bottom:4px;">Total Sent</div>
        <div style="font-family:'Bebas Neue',sans-serif; font-size:24px; color:var(--red);">${sent.toLocaleString()}</div>
      </div>
      <div style="background:var(--surface2); border:1px solid var(--border); padding:10px 12px; border-radius:2px;">
        <div style="font-size:10px; letter-spacing:0.15em; text-transform:uppercase; color:var(--text-dim); margin-bottom:4px;">Total Received</div>
        <div style="font-family:'Bebas Neue',sans-serif; font-size:24px; color:var(--green);">${received.toLocaleString()}</div>
      </div>
    </div>
    <div style="font-size:10px; letter-spacing:0.2em; text-transform:uppercase; color:var(--text-dim); margin-bottom:8px;">Recent Activity (${Math.min(walletTxs.length, 5)} of ${walletTxs.length})</div>
    ${walletTxs.length === 0
      ? `<div style="font-size:10px; color:var(--text-dim); font-style:italic; text-align:center; padding:20px;">No activity yet</div>`
      : walletTxs.slice(0, 5).map(tx => {
          const dir = tx.to === wallet.name ? '+' : '−';
          const col = tx.to === wallet.name ? 'var(--green)' : 'var(--red)';
          if (tx.type === 'reward' || tx.type === 'mint') return `
            <div style="display:flex; justify-content:space-between; align-items:center; padding:8px 0; border-bottom:1px solid var(--border); font-size:10px;">
              <span style="color:var(--gold);">${tx.type === 'reward' ? '⬆ REWARD' : '⬆ MINT'}</span>
              <span style="color:var(--gold);">+${tx.amount} $TRIAL</span>
            </div>`;
          return `
            <div style="display:flex; justify-content:space-between; align-items:center; padding:8px 0; border-bottom:1px solid var(--border); font-size:10px;">
              <span style="color:var(--text-dim);">${tx.from} → ${tx.to}</span>
              <span style="color:${col};">${dir}${tx.amount} $TRIAL</span>
            </div>`;
        }).join('')
    }
  `;
}

// ===================== INFLATION =====================
let inflationTimer = null;
let inflationSecondsLeft = 60;

function checkInflation() {
  const minBal = minWalletBalance();
  const notice = document.getElementById('inflation-notice');
  const countdown = document.getElementById('inflation-countdown');
  const fill = document.getElementById('inflation-bar-fill');

  // Bar shows min wallet health
  const pct = Math.min(100, (minBal / 2500) * 100);
  fill.style.width = `${pct}%`;

  if (minBal < 250) {
    notice.classList.add('active');
    countdown.classList.add('active');

    if (!inflationTimer) {
      inflationSecondsLeft = 60;
      inflationTimer = setInterval(inflationTick, 1000);
    }
  } else {
    notice.classList.remove('active');
    countdown.classList.remove('active');
    countdown.textContent = 'All wallets healthy';

    if (inflationTimer) {
      clearInterval(inflationTimer);
      inflationTimer = null;
    }
  }
}

function inflationTick() {
  inflationSecondsLeft--;
  const countdown = document.getElementById('inflation-countdown');

  if (inflationSecondsLeft <= 0) {
    // Mint 50 to the lowest wallet
    const minBal = minWalletBalance();
    const poorWallets = wallets.filter(w => w.balance < 2500);

    poorWallets.forEach(w => {
      w.balance += 500;
      blockNum++;
      addLedgerEntry({
        block: blockNum,
        hash: generateHash(),
        type: 'mint',
        from: 'INFLATION PROTOCOL',
        to: w.name,
        amount: 50,
        time: new Date(),
      });
    });

    showToast('Inflation Event', `+500 $TRIAL minted to ${poorWallets.length} wallet(s) below 2500 $TRIAL threshold`);
    renderWallets();
    renderInspector();
    updateStats();
    updateSupplyDisplay();

    inflationSecondsLeft = 60;
    checkInflation();
  } else {
    if (minWalletBalance() < 250) {
      countdown.textContent = `Next mint in ${inflationSecondsLeft}s — wallets below 2500 $TRIAL threshold`;
    }
  }
}

// ===================== STATS & DISPLAY =====================
function updateStats() {
  document.getElementById('stat-wallets').textContent = wallets.length;
  document.getElementById('stat-tx').textContent = ledger.filter(tx => tx.type === 'send').length;
  document.getElementById('stat-vol').textContent = totalTxVol.toLocaleString();
  document.getElementById('stat-rewards').textContent = totalRewards;
  document.getElementById('stat-block').textContent = blockNum.toLocaleString();
}

function updateSupplyDisplay() {
  const supply = totalSupply();
  document.getElementById('total-supply').textContent = supply.toLocaleString();
}

function formatTime(date) {
  return date.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
}

function updateFooterTime() {
  document.getElementById('footer-time').textContent = new Date().toUTCString();
}

function generateHash() {
  const chars = '0123456789abcdef';
  let hash = '0x';
  for (let i = 0; i < 8; i++) hash += chars[Math.floor(Math.random() * 16)];
  hash += '...';
  for (let i = 0; i < 4; i++) hash += chars[Math.floor(Math.random() * 16)];
  return hash;
}

// ===================== TOAST =====================
function showToast(title, msg) {
  const toast = document.getElementById('toast');
  document.getElementById('toast-title').textContent = title;
  document.getElementById('toast-msg').textContent = msg;
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 4000);
}


// ===================== $ETH EARNING =====================
function earnError(wallet, reason) {
  if (!wallet) return;
  const before = wallet.error;
  wallet.error = Math.min(ERROR_CAP, parseFloat((wallet.error + ERROR_EARN).toFixed(6)));
  const gained = parseFloat((wallet.error - before).toFixed(6));
  if (gained > 0) {
    blockNum++;
    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'errnearn', from: 'PROTOCOL', to: wallet.name, amount: gained, currency: 'ERROR', note: reason, time: new Date() });
  }
}

function startFaucet() {
  setInterval(() => {
    wallets.forEach(w => {
      if (w.error < ERROR_CAP) {
        earnError(w, 'passive drip');
      }
    });
    renderWallets();
    renderInspector();
    renderAutomations();
  }, ERROR_FAUCET_SEC * 1000);
}

// ===================== AUTOMATION ENGINE =====================
function createAutomation() {
  const walletId = document.getElementById('auto-wallet').value;
  const intervalSec = Math.max(5, parseFloat(document.getElementById('auto-interval').value) || 10);
  const amount = parseFloat(document.getElementById('auto-amount').value) || 1;
  const maxRecipients = Math.min(5, Math.max(1, parseInt(document.getElementById('auto-max-recv').value) || 1));
  const wallet = getWallet(walletId);
  if (!wallet) return;

  const rule = { id: autoIdCounter++, walletId, intervalSec, amount, maxRecipients, active: true, timerId: null };
  automations.push(rule);
  scheduleAutomation(rule);
  renderAutomations();
  showToast('Automation Created', `${wallet.name} → ${maxRecipients} wallet(s) · ${amount} $TRIAL · every ${intervalSec}s`);
}

function scheduleAutomation(rule) {
  if (rule.timerId) clearInterval(rule.timerId);
  if (!rule.active) return;
  rule.timerId = setInterval(() => fireAutomation(rule), rule.intervalSec * 1000);
}

function fireAutomation(rule) {
  if (!rule.active) return;
  const sender = getWallet(rule.walletId);
  if (!sender) return;
  if (sender.paused) return; // wallet paused

  // Build recipients
  const others = wallets.filter(w => w.id !== sender.id && !w.paused);
  const shuffled = others.sort(() => Math.random() - 0.5).slice(0, rule.maxRecipients);
  const totalNeeded = shuffled.length * rule.amount;
  const feeNeeded = parseFloat((shuffled.length * ERROR_FEE).toFixed(6));

  if (sender.error < feeNeeded) {
    // Pause automation — out of $ETH
    rule.active = false;
    if (rule.timerId) { clearInterval(rule.timerId); rule.timerId = null; }
    renderAutomations();
    showToast('Automation Paused', `${sender.name} ran out of $ETH — rule #${rule.id} paused`);
    return;
  }
  if (sender.balance < totalNeeded + 0.001) return; // skip tick if too broke

  const ts = new Date();
  for (const recipient of shuffled) {
    sender.balance = parseFloat((sender.balance - rule.amount).toFixed(6));
    recipient.balance = parseFloat((recipient.balance + rule.amount).toFixed(6));
    sender.balance = parseFloat((sender.balance + 1).toFixed(6));
    sender.error = parseFloat((sender.error - ERROR_FEE).toFixed(6));
    totalRewards += 1;
    blockNum++;
    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'auto', from: sender.name, to: recipient.name, amount: rule.amount, fee: ERROR_FEE, time: ts });
    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'reward', from: 'PROTOCOL', to: sender.name, amount: 1, time: ts });
    totalTxVol = parseFloat((totalTxVol + rule.amount).toFixed(6));
  }

  renderWallets();
  if (sender.id === selectedWalletId) renderSendForm();
  renderInspector();
  updateStats();
  updateSupplyDisplay();
  checkInflation();
  renderAutomations();
}

function toggleAutomation(id) {
  const rule = automations.find(r => r.id === id);
  if (!rule) return;
  rule.active = !rule.active;
  scheduleAutomation(rule);
  renderAutomations();
}

function deleteAutomation(id) {
  const idx = automations.findIndex(r => r.id === id);
  if (idx === -1) return;
  if (automations[idx].timerId) clearInterval(automations[idx].timerId);
  automations.splice(idx, 1);
  renderAutomations();
}

function renderAutomations() {
  const el = document.getElementById('automations-list');
  if (!el) return;
  if (automations.length === 0) {
    el.innerHTML = '<div style="text-align:center; padding:20px; font-size:10px; color:var(--text-dim); font-style:italic; letter-spacing:0.1em;">No automation rules yet. Add one above.</div>';
    return;
  }
  el.innerHTML = automations.map(rule => {
    const wallet = getWallet(rule.walletId);
    const outOfError = wallet && wallet.error <= 0;
    const statusColor = !rule.active ? 'var(--red)' : outOfError ? '#f59e0b' : '#c084fc';
    const statusLabel = !rule.active ? 'PAUSED' : outOfError ? 'LOW $ETH' : 'ACTIVE';
    return `
      <div style="display:grid; grid-template-columns:1fr auto; align-items:center; gap:10px; background:var(--surface2); border:1px solid ${rule.active ? 'rgba(192,132,252,0.25)' : 'var(--border)'}; border-radius:2px; padding:10px 14px;">
        <div>
          <div style="display:flex; align-items:center; gap:8px; margin-bottom:3px;">
            <span style="font-family:'DM Serif Display',serif; font-size:10px; color:${statusColor};">${wallet ? wallet.name : '?'}</span>
            <span style="font-size:10px; letter-spacing:0.15em; padding:1px 5px; border:1px solid ${statusColor}; color:${statusColor}; border-radius:2px;">${statusLabel}</span>
          </div>
          <div style="font-size:10px; color:var(--text-dim); letter-spacing:0.06em;">
            Every <strong style="color:var(--text)">${rule.intervalSec}s</strong> · 
            <strong style="color:var(--text)">${rule.amount} $TRIAL</strong> × <strong style="color:var(--text)">${rule.maxRecipients}</strong> wallet(s) ·
            <span style="color:#c084fc;">${(rule.maxRecipients * ERROR_FEE).toFixed(3)} $ETH/fire</span>
            · $ETH left: <span style="color:${wallet && wallet.error < 0.05 ? '#f59e0b' : '#c084fc'}">${wallet ? wallet.error.toFixed(3) : '?'}</span>
          </div>
        </div>
        <div style="display:flex; gap:6px;">
          <button onclick="toggleAutomation(${rule.id})" style="background:${rule.active ? 'rgba(192,57,43,0.15)' : 'rgba(76,175,110,0.15)'}; color:${rule.active ? 'var(--red)' : 'var(--green)'}; border:1px solid ${rule.active ? 'rgba(192,57,43,0.3)' : 'rgba(76,175,110,0.3)'}; font-family:'Space Mono',monospace; font-size:10px; letter-spacing:0.1em; padding:5px 10px; border-radius:2px; cursor:pointer; white-space:nowrap;">${rule.active ? 'PAUSE' : 'RESUME'}</button>
          <button onclick="deleteAutomation(${rule.id})" style="background:transparent; color:var(--text-dim); border:1px solid var(--border); font-family:'Space Mono',monospace; font-size:10px; padding:5px 8px; border-radius:2px; cursor:pointer;">✕</button>
        </div>
      </div>`;
  }).join('');
}

// ===================== AUTO SIMULATION =====================
let simRunning = true;

function randomBetween(min, max, decimals = 2) {
  const val = Math.random() * (max - min) + min;
  return parseFloat(val.toFixed(decimals));
}

function runSimTick() {
  if (!simRunning) return;

  // Pick a random sender that has enough balance and is not paused
  const eligible = wallets.filter(w => w.balance > 0.01 && !w.paused);
  if (eligible.length < 2) return;

  const sender = eligible[Math.floor(Math.random() * eligible.length)];

  // Pick 1–3 random recipients (not the sender)
  const others = wallets.filter(w => w.id !== sender.id && !w.paused);
  const numRecipients = Math.floor(Math.random() * Math.min(3, others.length)) + 1;
  const shuffled = others.sort(() => Math.random() - 0.5).slice(0, numRecipients);

  // Generate amounts — small fractional amounts for speed
  const targets = [];
  let remaining = sender.balance;
  for (const recipient of shuffled) {
    const maxSend = Math.min(remaining * 0.4, remaining - 0.01);
    if (maxSend <= 0.01) break;
    const amount = randomBetween(0.01, Math.min(maxSend, 20), 2);
    targets.push({ wallet: recipient, amount });
    remaining -= amount;
  }

  if (targets.length === 0) return;

  const totalOut = targets.reduce((s, t) => s + t.amount, 0);
  if (totalOut > sender.balance) return;

  const ts = new Date();

  // Check $ETH for sim
  const simFeeTotal = parseFloat((targets.length * ERROR_FEE).toFixed(6));
  if (sender.error < simFeeTotal) return; // skip if out of $ETH

  for (const { wallet: recipient, amount } of targets) {
    sender.balance = parseFloat((sender.balance - amount).toFixed(6));
    recipient.balance = parseFloat((recipient.balance + amount).toFixed(6));
    sender.balance = parseFloat((sender.balance + 1).toFixed(6));
    sender.error = parseFloat((sender.error - ERROR_FEE).toFixed(6));
    totalRewards += 1;
    blockNum++;

    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'send', from: sender.name, to: recipient.name, amount, fee: ERROR_FEE, time: ts });
    addLedgerEntry({ block: blockNum, hash: generateHash(), type: 'reward', from: 'PROTOCOL', to: sender.name, amount: 1, time: ts });
    totalTxVol = parseFloat((totalTxVol + amount).toFixed(6));
  }

  renderWallets();
  // Only re-render send form if selected wallet was involved
  if (targets.some(t => t.wallet.id === selectedWalletId) || sender.id === selectedWalletId) {
    renderSendForm();
  }
  renderInspector();
  updateStats();
  updateSupplyDisplay();
  checkInflation();

  // Schedule next tick — OP Mainnet block time: 2 seconds
  setTimeout(runSimTick, 2000);
}

// ===================== START =====================
init();
// Kick off simulation after a short delay
setTimeout(runSimTick, 2000);</script>
</body>
</html>

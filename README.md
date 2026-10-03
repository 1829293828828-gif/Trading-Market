<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Market Arcade</title>

<style>
*{box-sizing:border-box}
body{
  margin:0;
  font-family:Arial,Helvetica,sans-serif;
  background:#071018;
  color:#e8eef5;
}
button,input{
  font:inherit;
}
button{
  cursor:pointer;
}
.hidden{
  display:none!important;
}

/* LOGIN */
#loginScreen{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:20px;
  background:
    radial-gradient(circle at top,#102536 0,#071018 48%,#04080c 100%);
}
.loginBox{
  width:100%;
  max-width:430px;
  background:#0d1822;
  border:1px solid #223545;
  border-radius:18px;
  padding:30px;
  box-shadow:0 20px 70px #0008;
}
.logo{
  font-size:30px;
  font-weight:800;
  letter-spacing:-1px;
}
.logo span{
  color:#27d17f;
}
.subtitle{
  color:#8295a7;
  margin:8px 0 25px;
}
.tabs{
  display:flex;
  gap:6px;
  margin-bottom:18px;
}
.tab{
  flex:1;
  padding:11px;
  border:0;
  border-radius:9px;
  background:#142431;
  color:#91a4b5;
}
.tab.active{
  background:#1c9d65;
  color:white;
}
.field{
  margin-bottom:13px;
}
.field label{
  display:block;
  color:#91a4b5;
  font-size:13px;
  margin-bottom:6px;
}
input{
  width:100%;
  padding:13px;
  border-radius:9px;
  border:1px solid #2a3d4d;
  background:#08121a;
  color:white;
  outline:none;
}
input:focus{
  border-color:#27d17f;
}
.primary{
  width:100%;
  border:0;
  padding:13px;
  border-radius:9px;
  background:#20b873;
  color:white;
  font-weight:700;
}
.primary:hover{
  background:#28ca82;
}
.message{
  min-height:20px;
  margin-top:12px;
  color:#ff7272;
  font-size:13px;
}

/* APP */
#app{
  min-height:100vh;
}
.topbar{
  height:64px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 18px;
  background:#0b151e;
  border-bottom:1px solid #1d2d3a;
  position:sticky;
  top:0;
  z-index:20;
}
.brand{
  font-weight:800;
  font-size:20px;
}
.brand span{
  color:#28d17e;
}
.topRight{
  display:flex;
  align-items:center;
  gap:15px;
}
.cashTop{
  color:#52dfa0;
  font-weight:700;
}
.logout{
  background:#182630;
  border:1px solid #293c4b;
  color:#b8c6d1;
  padding:8px 12px;
  border-radius:8px;
}
.layout{
  display:grid;
  grid-template-columns:220px 1fr;
  min-height:calc(100vh - 64px);
}
.sidebar{
  background:#09131b;
  border-right:1px solid #1d2d3a;
  padding:15px 10px;
}
.navBtn{
  width:100%;
  text-align:left;
  padding:12px 13px;
  margin-bottom:5px;
  border:0;
  border-radius:8px;
  background:transparent;
  color:#879aaa;
}
.navBtn:hover,.navBtn.active{
  background:#142530;
  color:white;
}
.main{
  padding:22px;
  max-width:1450px;
  width:100%;
  margin:auto;
}
.pageTitle{
  font-size:27px;
  font-weight:800;
  margin-bottom:4px;
}
.pageSub{
  color:#718596;
  margin-bottom:20px;
}

/* CARDS */
.cards{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:12px;
  margin-bottom:20px;
}
.card{
  background:#0d1922;
  border:1px solid #203340;
  border-radius:12px;
  padding:17px;
}
.cardLabel{
  color:#758999;
  font-size:12px;
  text-transform:uppercase;
  letter-spacing:.5px;
}
.cardValue{
  margin-top:8px;
  font-size:22px;
  font-weight:800;
}
.green{
  color:#43d991;
}
.red{
  color:#ff6666;
}

/* TABLE */
.panel{
  background:#0d1922;
  border:1px solid #203340;
  border-radius:12px;
  overflow:hidden;
  margin-bottom:18px;
}
.panelHead{
  padding:16px 18px;
  border-bottom:1px solid #203340;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
.panelTitle{
  font-weight:800;
}
table{
  width:100%;
  border-collapse:collapse;
}
th{
  text-align:left;
  color:#6f8292;
  font-size:12px;
  font-weight:600;
  padding:12px 15px;
  border-bottom:1px solid #203340;
}
td{
  padding:13px 15px;
  border-bottom:1px solid #172732;
}
tr:last-child td{
  border-bottom:0;
}
.stockName{
  font-weight:700;
}
.ticker{
  color:#718697;
  font-size:12px;
}
.stockButton{
  background:transparent;
  border:0;
  color:inherit;
  text-align:left;
  padding:0;
}
.tradeBtn{
  border:0;
  border-radius:7px;
  padding:7px 11px;
  margin-left:4px;
  font-weight:700;
}
.buy{
  background:#164d36;
  color:#55e5a2;
}
.sell{
  background:#552329;
  color:#ff8585;
}

/* MARKET */
.marketGrid{
  display:grid;
  grid-template-columns:1fr 380px;
  gap:16px;
}
.chartBox{
  padding:18px;
}
.chartTitle{
  display:flex;
  justify-content:space-between;
  margin-bottom:10px;
}
.chartCanvas{
  width:100%;
  height:320px;
  background:#08121a;
  border:1px solid #1d2e3b;
  border-radius:10px;
}
.tradeBox{
  padding:18px;
}
.priceBig{
  font-size:30px;
  font-weight:800;
  margin:8px 0 20px;
}
.buySell{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:8px;
}
.buyBig,.sellBig{
  border:0;
  padding:13px;
  border-radius:8px;
  font-weight:800;
}
.buyBig{
  background:#1c9b63;
  color:white;
}
.sellBig{
  background:#a9434d;
  color:white;
}
.small{
  color:#718697;
  font-size:12px;
}

/* FRIENDS / OPERATOR */
.formRow{
  display:flex;
  gap:8px;
}
.formRow input{
  flex:1;
}
.formRow button{
  width:auto;
  padding:0 17px;
}
.action{
  border:0;
  padding:9px 13px;
  border-radius:8px;
  background:#1d8f5d;
  color:white;
  font-weight:700;
}
.danger{
  background:#9d3e48;
}
.secondary{
  background:#172733;
  color:#c4d0d9;
}

/* MODAL */
.modal{
  position:fixed;
  inset:0;
  background:#000b;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:20px;
  z-index:100;
}
.modalBox{
  width:100%;
  max-width:470px;
  background:#0d1922;
  border:1px solid #2a3d4d;
  border-radius:15px;
  padding:22px;
}
.modalActions{
  display:flex;
  gap:8px;
  margin-top:18px;
}
.modalActions button{
  flex:1;
}

/* MOBILE */
@media(max-width:900px){
  .layout{
    grid-template-columns:1fr;
  }
  .sidebar{
    display:flex;
    overflow-x:auto;
    border-right:0;
    border-bottom:1px solid #1d2d3a;
    padding:7px;
  }
  .navBtn{
    white-space:nowrap;
    width:auto;
    margin:0 3px;
  }
  .cards{
    grid-template-columns:repeat(2,1fr);
  }
  .marketGrid{
    grid-template-columns:1fr;
  }
}
@media(max-width:600px){
  .main{
    padding:13px;
  }
  .cards{
    grid-template-columns:1fr 1fr;
  }
  .cards .card{
    padding:13px;
  }
  .topbar{
    padding:0 12px;
  }
  .cashTop{
    display:none;
  }
  th,td{
    padding:10px 8px;
  }
}
</style>
</head>

<body>

<!-- LOGIN -->
<div id="loginScreen">
  <div class="loginBox">
    <div class="logo">MARKET <span>ARCADE</span></div>
    <div class="subtitle">The fictional stock market game.</div>

    <div class="tabs">
      <button class="tab active" id="loginTab" onclick="showLogin()">Login</button>
      <button class="tab" id="signupTab" onclick="showSignup()">Create account</button>
    </div>

    <div id="loginForm">
      <div class="field">
        <label>Username</label>
        <input id="loginUsername" type="text" autocomplete="username">
      </div>

      <div class="field">
        <label>Password</label>
        <input id="loginPassword" type="password" autocomplete="current-password">
      </div>

      <button class="primary" onclick="login()">Login</button>
    </div>

    <div id="signupForm" class="hidden">
      <div class="field">
        <label>Username</label>
        <input id="signupUsername" type="text" autocomplete="username">
      </div>

      <div class="field">
        <label>Password</label>
        <input id="signupPassword" type="password" autocomplete="new-password">
      </div>

      <div class="field">
        <label>Confirm password</label>
        <input id="signupConfirm" type="password">
      </div>

      <button class="primary" onclick="signup()">Create account</button>
    </div>

    <div id="authMessage" class="message"></div>
  </div>
</div>

<!-- APP -->
<div id="app" class="hidden">

  <div class="topbar">
    <div class="brand">MARKET <span>ARCADE</span></div>
    <div class="topRight">
      <div class="cashTop" id="topCash">$100.00</div>
      <div id="topUser">Player</div>
      <button class="logout" onclick="logout()">Logout</button>
    </div>
  </div>

  <div class="layout">

    <aside class="sidebar">
      <button class="navBtn active" onclick="page('dashboard',this)">📊 Dashboard</button>
      <button class="navBtn" onclick="page('market',this)">📈 Market</button>
      <button class="navBtn" onclick="page('portfolio',this)">💼 Portfolio</button>
      <button class="navBtn" onclick="page('friends',this)">👥 Friends</button>
      <button class="navBtn" onclick="page('leaderboard',this)">🏆 Leaderboard</button>
      <button class="navBtn" onclick="page('create',this)">🏢 Create Stock</button>
      <button class="navBtn" onclick="operatorLogin()">🛡️ Operator</button>
    </aside>

    <main class="main">

      <!-- DASHBOARD -->
      <section id="dashboardPage">
        <div class="pageTitle">Dashboard</div>
        <div class="pageSub">Welcome back, <span id="dashUser">Player</span>.</div>

        <div class="cards">
          <div class="card">
            <div class="cardLabel">Cash</div>
            <div class="cardValue green" id="dashCash">$100.00</div>
          </div>

          <div class="card">
            <div class="cardLabel">Portfolio</div>
            <div class="cardValue" id="dashPortfolio">$0.00</div>
          </div>

          <div class="card">
            <div class="cardLabel">Total value</div>
            <div class="cardValue" id="dashTotal">$100.00</div>
          </div>

          <div class="card">
            <div class="cardLabel">P/L</div>
            <div class="cardValue" id="dashPL">$0.00</div>
          </div>
        </div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Market overview</div>
            <button class="action" onclick="page('market')">Open market</button>
          </div>

          <table>
            <thead>
              <tr>
                <th>Company</th>
                <th>Price</th>
                <th>24h</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody id="dashboardStocks"></tbody>
          </table>
        </div>
      </section>

      <!-- MARKET -->
      <section id="marketPage" class="hidden">
        <div class="pageTitle">Market</div>
        <div class="pageSub">Trade fictional stocks using virtual money.</div>

        <div class="marketGrid">

          <div class="panel">
            <div class="chartBox">
              <div class="chartTitle">
                <div>
                  <div class="panelTitle" id="selectedName">Select a stock</div>
                  <div class="ticker" id="selectedTicker">---</div>
                </div>
                <div>
                  <div class="priceBig" id="selectedPrice">$0.00</div>
                  <div id="selectedChange">0.00%</div>
                </div>
              </div>
              <canvas id="chart" class="chartCanvas"></canvas>
            </div>
          </div>

          <div class="panel">
            <div class="tradeBox">
              <div class="panelTitle">Trade</div>
              <p class="small" id="tradeHint">Select a stock from the list.</p>

              <div class="field">
                <label>Shares</label>
                <input id="tradeShares" type="number" min="1" step="1" value="1">
              </div>

              <div class="card">
                <div class="cardLabel">Estimated total</div>
                <div class="cardValue" id="tradeTotal">$0.00</div>
              </div>

              <br>

              <div class="buySell">
                <button class="buyBig" onclick="trade('buy')">BUY</button>
                <button class="sellBig" onclick="trade('sell')">SELL</button>
              </div>
            </div>
          </div>

        </div>

        <br>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Stocks</div>
          </div>

          <table>
            <thead>
              <tr>
                <th>Company</th>
                <th>Price</th>
                <th>24h</th>
                <th>Owner</th>
                <th></th>
              </tr>
            </thead>
            <tbody id="marketStocks"></tbody>
          </table>
        </div>
      </section>

      <!-- PORTFOLIO -->
      <section id="portfolioPage" class="hidden">
        <div class="pageTitle">Portfolio</div>
        <div class="pageSub">Your current holdings.</div>

        <div class="cards">
          <div class="card">
            <div class="cardLabel">Cash</div>
            <div class="cardValue green" id="portCash">$100.00</div>
          </div>
          <div class="card">
            <div class="cardLabel">Holdings</div>
            <div class="cardValue" id="portHoldings">$0.00</div>
          </div>
          <div class="card">
            <div class="cardLabel">Total</div>
            <div class="cardValue" id="portTotal">$100.00</div>
          </div>
        </div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Holdings</div>
          </div>

          <table>
            <thead>
              <tr>
                <th>Stock</th>
                <th>Shares</th>
                <th>Price</th>
                <th>Value</th>
                <th></th>
              </tr>
            </thead>
            <tbody id="portfolioRows"></tbody>
          </table>
        </div>
      </section>

      <!-- FRIENDS -->
      <section id="friendsPage" class="hidden">
        <div class="pageTitle">Friends</div>
        <div class="pageSub">Add other players by username.</div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Add friend</div>
          </div>
          <div style="padding:18px">
            <div class="formRow">
              <input id="friendInput" placeholder="Username">
              <button class="action" onclick="addFriend()">Add</button>
            </div>
            <div id="friendMessage" class="message"></div>
          </div>
        </div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Your friends</div>
          </div>
          <div id="friendList" style="padding:18px"></div>
        </div>
      </section>

      <!-- LEADERBOARD -->
      <section id="leaderboardPage" class="hidden">
        <div class="pageTitle">Leaderboard</div>
        <div class="pageSub">Players ranked by total virtual wealth.</div>

        <div class="panel">
          <table>
            <thead>
              <tr>
                <th>#</th>
                <th>Player</th>
                <th>Cash</th>
                <th>Portfolio</th>
                <th>Total</th>
              </tr>
            </thead>
            <tbody id="leaderRows"></tbody>
          </table>
        </div>
      </section>

      <!-- CREATE STOCK -->
      <section id="createPage" class="hidden">
        <div class="pageTitle">Create a Stock</div>
        <div class="pageSub">Launch your own fictional company.</div>

        <div class="panel">
          <div style="padding:20px">
            <div class="card" style="margin-bottom:18px">
              <div class="cardLabel">Current creation fee</div>
              <div class="cardValue" id="creationFee">$100,000,000.00</div>
              <div class="small">Only one stock may be created per real-world day.</div>
            </div>

            <div class="field">
              <label>Company name</label>
              <input id="stockCompany" placeholder="Example: Future Systems">
            </div>

            <div class="field">
              <label>Ticker</label>
              <input id="stockTicker" maxlength="5" placeholder="FUTR">
            </div>

            <div class="field">
              <label>Starting price</label>
              <input id="stockStartingPrice" type="number" min=".01" step=".01" placeholder="10">
            </div>

            <button class="action" onclick="createStock()">Create stock</button>
            <div id="createMessage" class="message"></div>
          </div>
        </div>
      </section>

      <!-- OPERATOR -->
      <section id="operatorPage" class="hidden">
        <div class="pageTitle">Operator Panel</div>
        <div class="pageSub">Local beta administration tools.</div>

        <div class="cards">
          <div class="card">
            <div class="cardLabel">Players</div>
            <div class="cardValue" id="opPlayers">0</div>
          </div>
          <div class="card">
            <div class="cardLabel">Stocks</div>
            <div class="cardValue" id="opStocks">0</div>
          </div>
        </div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Market settings</div>
          </div>

          <div style="padding:18px">
            <div class="field">
              <label>Stock creation fee</label>
              <input id="opFee" type="number" min="0" step="100">
            </div>

            <button class="action" onclick="saveOperatorSettings()">Save settings</button>
            <button class="action secondary" onclick="resetDemo()" style="margin-left:6px">Reset demo data</button>
          </div>
        </div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Players</div>
          </div>

          <table>
            <thead>
              <tr>
                <th>Username</th>
                <th>Cash</th>
                <th>Status</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody id="operatorPlayers"></tbody>
          </table>
        </div>

        <div class="panel">
          <div class="panelHead">
            <div class="panelTitle">Stocks</div>
          </div>

          <table>
            <thead>
              <tr>
                <th>Company</th>
                <th>Ticker</th>
                <th>Price</th>
                <th>Owner</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody id="operatorStocks"></tbody>
          </table>
        </div>
      </section>

    </main>
  </div>
</div>

<!-- TRADE MODAL -->
<div id="tradeModal" class="modal hidden">
  <div class="modalBox">
    <div class="panelTitle" id="modalTitle">Trade</div>
    <p id="modalText"></p>

    <div class="field">
      <label>Shares</label>
      <input id="modalShares" type="number" min="1" value="1">
    </div>

    <div class="card">
      <div class="cardLabel">Estimated total</div>
      <div class="cardValue" id="modalTotal">$0.00</div>
    </div>

    <div class="modalActions">
      <button class="action secondary" onclick="closeModal()">Cancel</button>
      <button class="action" id="modalConfirm">Confirm</button>
    </div>
  </div>
</div>

<script>
/*
  MARKET ARCADE
  Single-file browser beta.

  IMPORTANT:
  This version uses localStorage.
  It is NOT a real multiplayer backend.
*/

const DATA_KEY = "MARKET_ARCADE_COMPLETE_DATA";
const SESSION_KEY = "MARKET_ARCADE_COMPLETE_SESSION";

/*
  Change this before giving the site to anyone.
  This operator password is only a local beta password.
  It is NOT secure against someone inspecting the HTML.
*/
const OPERATOR_PASSWORD = "MA-ADMIN-2026";

let db = loadDatabase();
let selectedStock = null;
let currentTradeType = null;
let tickTimer = null;

/* ---------------- DATABASE ---------------- */

function defaultDatabase(){
  return {
    settings:{
      creationFee:100000000
    },

    users:[],

    stocks:[
      makeStock(
        "Nova Technologies",
        "NOVA",
        10,
        "Market Arcade"
      ),
      makeStock(
        "Pixel Works",
        "PIXL",
        4.50,
        "Market Arcade"
      ),
      makeStock(
        "Orbit Industries",
        "ORBT",
        23.75,
        "Market Arcade"
      )
    ]
  };
}

function makeStock(name,ticker,price,owner){
  return {
    id:"stock_"+Date.now()+"_"+Math.random().toString(36).slice(2),
    name:name,
    ticker:ticker.toUpperCase(),
    price:Number(price),
    previousPrice:Number(price),
    owner:owner,
    createdAt:Date.now(),
    suspended:false,
    rugged:false,
    candles:makeCandles(Number(price),40),
    history:[Number(price)]
  };
}

function makeCandles(price,count){
  let arr=[];
  let p=price;

  for(let i=0;i<count;i++){
    let open=p;
    let movement=p*(Math.random()*.08-.04);
    let close=Math.max(.01,p+movement);
    let high=Math.max(open,close)*(1+Math.random()*.025);
    let low=Math.max(.01,Math.min(open,close)*(1-Math.random()*.025));

    arr.push({
      open:open,
      high:high,
      low:low,
      close:close
    });

    p=close;
  }

  return arr;
}

function loadDatabase(){
  try{
    const saved=localStorage.getItem(DATA_KEY);

    if(!saved){
      return defaultDatabase();
    }

    const parsed=JSON.parse(saved);

    if(!parsed.settings) parsed.settings={creationFee:100000000};
    if(!parsed.users) parsed.users=[];
    if(!parsed.stocks) parsed.stocks=[];

    parsed.users.forEach(normalizeUser);
    parsed.stocks.forEach(normalizeStock);

    return parsed;
  }catch(e){
    return defaultDatabase();
  }
}

function saveDatabase(){
  localStorage.setItem(DATA_KEY,JSON.stringify(db));
}

function normalizeUser(u){
  if(!u.holdings) u.holdings={};
  if(!u.friends) u.friends=[];
  if(typeof u.cash!=="number") u.cash=100;
  if(typeof u.banned!=="boolean") u.banned=false;
}

function normalizeStock(s){
  if(!Array.isArray(s.candles)){
    s.candles=makeCandles(Number(s.price)||1,40);
  }

  if(!Array.isArray(s.history)){
    s.history=[Number(s.price)||1];
  }

  if(typeof s.suspended!=="boolean") s.suspended=false;
  if(typeof s.rugged!=="boolean") s.rugged=false;
}

/* ---------------- AUTH ---------------- */

function currentUser(){
  const id=localStorage.getItem(SESSION_KEY);

  if(!id) return null;

  const u=db.users.find(x=>x.id===id);

  if(u){
    normalizeUser(u);
  }

  return u||null;
}

function showLogin(){
  document.getElementById("loginForm").classList.remove("hidden");
  document.getElementById("signupForm").classList.add("hidden");

  document.getElementById("loginTab").classList.add("active");
  document.getElementById("signupTab").classList.remove("active");

  document.getElementById("authMessage").textContent="";
}

function showSignup(){
  document.getElementById("loginForm").classList.add("hidden");
  document.getElementById("signupForm").classList.remove("hidden");

  document.getElementById("loginTab").classList.remove("active");
  document.getElementById("signupTab").classList.add("active");

  document.getElementById("authMessage").textContent="";
}

function signup(){
  const username=document.getElementById("signupUsername").value.trim();
  const password=document.getElementById("signupPassword").value;
  const confirm=document.getElementById("signupConfirm").value;
  const message=document.getElementById("authMessage");

  if(username.length<3){
    message.textContent="Username must be at least 3 characters.";
    return;
  }

  if(password.length<4){
    message.textContent="Password must be at least 4 characters.";
    return;
  }

  if(password!==confirm){
    message.textContent="Passwords do not match.";
    return;
  }

  if(db.users.some(u=>u.username.toLowerCase()===username.toLowerCase())){
    message.textContent="That username already exists.";
    return;
  }

  const user={
    id:"user_"+Date.now()+"_"+Math.random().toString(36).slice(2),
    username:username,
    password:password,
    cash:100,
    holdings:{},
    friends:[],
    createdAt:Date.now(),
    banned:false
  };

  db.users.push(user);
  saveDatabase();

  localStorage.setItem(SESSION_KEY,user.id);

  startGame();
}

function login(){
  const username=document.getElementById("loginUsername").value.trim();
  const password=document.getElementById("loginPassword").value;
  const message=document.getElementById("authMessage");

  const user=db.users.find(
    u=>u.username.toLowerCase()===username.toLowerCase()
    && u.password===password
  );

  if(!user){
    message.textContent="Incorrect username or password.";
    return;
  }

  if(user.banned){
    message.textContent="This account is banned.";
    return;
  }

  normalizeUser(user);

  localStorage.setItem(SESSION_KEY,user.id);

  startGame();
}

function logout(){
  localStorage.removeItem(SESSION_KEY);

  if(tickTimer){
    clearInterval(tickTimer);
    tickTimer=null;
  }

  document.getElementById("app").classList.add("hidden");
  document.getElementById("loginScreen").classList.remove("hidden");
  showLogin();
}

function startGame(){
  document.getElementById("loginScreen").classList.add("hidden");
  document.getElementById("app").classList.remove("hidden");

  updateAll();
  page("dashboard");

  if(tickTimer) clearInterval(tickTimer);

  tickTimer=setInterval(marketTick,5000);
}

/* ---------------- NAVIGATION ---------------- */

function page(name,button){
  const pages=[
    "dashboard",
    "market",
    "portfolio",
    "friends",
    "leaderboard",
    "create",
    "operator"
  ];

  pages.forEach(p=>{
    const el=document.getElementById(p+"Page");

    if(el){
      el.classList.toggle("hidden",p!==name);
    }
  });

  document.querySelectorAll(".navBtn").forEach(b=>{
    b.classList.remove("active");
  });

  if(button){
    button.classList.add("active");
  }

  if(name==="market"){
    renderMarket();
    drawChart();
  }

  if(name==="portfolio"){
    renderPortfolio();
  }

  if(name==="friends"){
    renderFriends();
  }

  if(name==="leaderboard"){
    renderLeaderboard();
  }

  if(name==="create"){
    document.getElementById("creationFee").textContent=
      money(db.settings.creationFee);
  }

  if(name==="operator"){
    renderOperator();
  }
}

/* ---------------- MONEY ---------------- */

function money(n){
  return "$"+Number(n||0).toLocaleString("en-US",{
    minimumFractionDigits:2,
    maximumFractionDigits:2
  });
}

function portfolioValue(user){
  let total=0;

  for(const id in user.holdings){
    const shares=Number(user.holdings[id])||0;
    const stock=db.stocks.find(s=>s.id===id);

    if(stock){
      total+=shares*stock.price;
    }
  }

  return total;
}

function totalWealth(user){
  return user.cash+portfolioValue(user);
}

/* ---------------- DASHBOARD ---------------- */

function renderDashboard(){
  const user=currentUser();

  if(!user) return;

  const port=portfolioValue(user);
  const total=user.cash+port;
  const pl=total-100;

  document.getElementById("topUser").textContent=user.username;
  document.getElementById("dashUser").textContent=user.username;

  document.getElementById("topCash").textContent=money(user.cash);
  document.getElementById("dashCash").textContent=money(user.cash);
  document.getElementById("dashPortfolio").textContent=money(port);
  document.getElementById("dashTotal").textContent=money(total);

  const plEl=document.getElementById("dashPL");
  plEl.textContent=(pl>=0?"+":"")+money(pl);
  plEl.className="cardValue "+(pl>=0?"green":"red");

  const body=document.getElementById("dashboardStocks");
  body.innerHTML="";

  db.stocks.forEach(stock=>{
    const change=percentChange(stock);

    body.innerHTML+=`
      <tr>
        <td>
          <button class="stockButton" onclick="selectAndMarket('${stock.id}')">
            <div class="stockName">${escapeHtml(stock.name)}</div>
            <div class="ticker">${escapeHtml(stock.ticker)}</div>
          </button>
        </td>
        <td>${money(stock.price)}</td>
        <td class="${change>=0?'green':'red'}">${change>=0?"+":""}${change.toFixed(2)}%</td>
        <td>
          <button class="tradeBtn buy" onclick="quickTrade('${stock.id}','buy')">Buy</button>
          <button class="tradeBtn sell" onclick="quickTrade('${stock.id}','sell')">Sell</button>
        </td>
      </tr>
    `;
  });
}

/* ---------------- MARKET ---------------- */

function renderMarket(){
  const body=document.getElementById("marketStocks");
  body.innerHTML="";

  db.stocks.forEach(stock=>{
    const change=percentChange(stock);

    body.innerHTML+=`
      <tr>
        <td>
          <button class="stockButton" onclick="selectStock('${stock.id}')">
            <div class="stockName">${escapeHtml(stock.name)}</div>
            <div class="ticker">${escapeHtml(stock.ticker)}</div>
          </button>
        </td>
        <td>${money(stock.price)}</td>
        <td class="${change>=0?'green':'red'}">
          ${change>=0?"+":""}${change.toFixed(2)}%
        </td>
        <td>${escapeHtml(stock.owner)}</td>
        <td>
          <button class="tradeBtn buy" onclick="quickTrade('${stock.id}','buy')">Buy</button>
          <button class="tradeBtn sell" onclick="quickTrade('${stock.id}','sell')">Sell</button>
        </td>
      </tr>
    `;
  });

  if(!selectedStock && db.stocks.length){
    selectStock(db.stocks[0].id);
  }
}

function selectAndMarket(id){
  page("market");

  setTimeout(()=>{
    selectStock(id);
  },20);
}

function selectStock(id){
  selectedStock=db.stocks.find(s=>s.id===id)||null;

  if(!selectedStock) return;

  document.getElementById("selectedName").textContent=selectedStock.name;
  document.getElementById("selectedTicker").textContent=selectedStock.ticker;
  document.getElementById("selectedPrice").textContent=money(selectedStock.price);

  const change=percentChange(selectedStock);
  const changeEl=document.getElementById("selectedChange");

  changeEl.textContent=(change>=0?"+":"")+change.toFixed(2)+"%";
  changeEl.className=change>=0?"green":"red";

  document.getElementById("tradeHint").textContent=
    selectedStock.suspended
      ?"This stock is suspended."
      :"Trading "+selectedStock.ticker;

  updateTradeTotal();
  drawChart();
}

function percentChange(stock){
  if(!stock.candles || stock.candles.length<2) return 0;

  const first=stock.candles[0].open;

  if(!first) return 0;

  return ((stock.price-first)/first)*100;
}

function updateTradeTotal(){
  const shares=Number(document.getElementById("tradeShares").value)||0;

  if(selectedStock){
    document.getElementById("tradeTotal").textContent=
      money(shares*selectedStock.price);
  }
}

document.getElementById("tradeShares").addEventListener(
  "input",
  updateTradeTotal
);

/* ---------------- TRADING ---------------- */

function quickTrade(id,type){
  selectAndMarket(id);

  currentTradeType=type;

  const stock=db.stocks.find(s=>s.id===id);

  if(!stock) return;

  document.getElementById("modalTitle").textContent=
    type==="buy"?"Buy "+stock.ticker:"Sell "+stock.ticker;

  document.getElementById("modalText").textContent=
    stock.name+" is currently "+money(stock.price)+" per share.";

  document.getElementById("modalShares").value=1;
  updateModalTotal();

  document.getElementById("tradeModal").classList.remove("hidden");

  document.getElementById("modalConfirm").onclick=function(){
    executeTrade(id,type);
  };
}

document.getElementById("modalShares").addEventListener(
  "input",
  updateModalTotal
);

function updateModalTotal(){
  const shares=Number(document.getElementById("modalShares").value)||0;

  if(selectedStock){
    document.getElementById("modalTotal").textContent=
      money(shares*selectedStock.price);
  }
}

function closeModal(){
  document.getElementById("tradeModal").classList.add("hidden");
}

function trade(type){
  if(!selectedStock){
    alert("Select a stock first.");
    return;
  }

  quickTrade(selectedStock.id,type);
}

function executeTrade(id,type){
  const user=currentUser();
  const stock=db.stocks.find(s=>s.id===id);

  if(!user || !stock) return;

  if(stock.suspended){
    alert("This stock is suspended.");
    return;
  }

  const shares=Math.floor(
    Number(document.getElementById("modalShares").value)
  );

  if(!shares || shares<1){
    alert("Enter at least 1 share.");
    return;
  }

  const total=shares*stock.price;

  if(type==="buy"){
    if(user.cash<total){
      alert("You don't have enough virtual cash.");
      return;
    }

    user.cash-=total;
    user.holdings[stock.id]=(user.holdings[stock.id]||0)+shares;

  }else{
    const owned=user.holdings[stock.id]||0;

    if(owned<shares){
      alert("You don't own enough shares.");
      return;
    }

    user.cash+=total;
    user.holdings[stock.id]-=shares;

    if(user.holdings[stock.id]<=0){
      delete user.holdings[stock.id];
    }
  }

  saveDatabase();
  closeModal();
  updateAll();
}

/* ---------------- CHART ---------------- */

function drawChart(){
  const canvas=document.getElementById("chart");

  if(!canvas || !selectedStock) return;

  const rect=canvas.getBoundingClientRect();

  const dpr=window.devicePixelRatio||1;

  canvas.width=Math.max(1,rect.width*dpr);
  canvas.height=Math.max(1,rect.height*dpr);

  const ctx=canvas.getContext("2d");

  ctx.scale(dpr,dpr);

  const w=rect.width;
  const h=rect.height;

  ctx.clearRect(0,0,w,h);

  const candles=selectedStock.candles.slice(-45);

  if(!candles.length) return;

  let min=Infinity;
  let max=-Infinity;

  candles.forEach(c=>{
    min=Math.min(min,c.low);
    max=Math.max(max,c.high);
  });

  const padding={
    left:45,
    right:15,
    top:15,
    bottom:25
  };

  const cw=w-padding.left-padding.right;
  const ch=h-padding.top-padding.bottom;

  if(max===min){
    max+=1;
    min-=1;
  }

  function y(value){
    return padding.top+(max-value)/(max-min)*ch;
  }

  /* grid */
  ctx.strokeStyle="#1c2d39";
  ctx.lineWidth=1;

  for(let i=0;i<5;i++){
    const yy=padding.top+(ch/4)*i;

    ctx.beginPath();
    ctx.moveTo(padding.left,yy);
    ctx.lineTo(w-padding.right,yy);
    ctx.stroke();

    const value=max-(max-min)*(i/4);

    ctx.fillStyle="#657887";
    ctx.font="11px Arial";
    ctx.fillText(money(value),5,yy+4);
  }

  const gap=cw/candles.length;
  const candleWidth=Math.max(3,gap*.55);

  candles.forEach((c,i)=>{
    const x=padding.left+i*gap+gap/2;

    const openY=y(c.open);
    const closeY=y(c.close);
    const highY=y(c.high);
    const lowY=y(c.low);

    const up=c.close>=c.open;

    ctx.strokeStyle=up?"#38d68d":"#ff626d";
    ctx.fillStyle=ctx.strokeStyle;

    ctx.beginPath();
    ctx.moveTo(x,highY);
    ctx.lineTo(x,lowY);
    ctx.stroke();

    const top=Math.min(openY,closeY);
    const height=Math.max(2,Math.abs(openY-closeY));

    ctx.fillRect(
      x-candleWidth/2,
      top,
      candleWidth,
      height
    );
  });
}

/* ---------------- MARKET TICK ---------------- */

function marketTick(){
  db.stocks.forEach(stock=>{
    if(stock.suspended) return;

    const old=stock.price;

    /*
      Arcade-style volatility.
      The movement is intentionally exaggerated compared
      with a real stock market.
    */
    const percent=(Math.random()*.08)-.04;

    let next=old*(1+percent);

    if(next<.01) next=.01;

    stock.previousPrice=old;
    stock.price=Number(next.toFixed(2));

    if(!Array.isArray(stock.candles)){
      stock.candles=[];
    }

    let last=stock.candles[stock.candles.length-1];

    if(!last){
      last={
        open:old,
        high:old,
        low:old,
        close:old
      };
      stock.candles.push(last);
    }

    last.close=stock.price;
    last.high=Math.max(last.high,stock.price);
    last.low=Math.min(last.low,stock.price);

    if(Math.random()<.45){
      stock.candles.push({
        open:stock.price,
        high:stock.price,
        low:stock.price,
        close:stock.price
      });
    }

    if(stock.candles.length>80){
      stock.candles.shift();
    }

    stock.history.push(stock.price);

    if(stock.history.length>200){
      stock.history.shift();
    }
  });

  saveDatabase();
  updateAll();
}

/* ---------------- PORTFOLIO ---------------- */

function renderPortfolio(){
  const user=currentUser();

  if(!user) return;

  const holdings=portfolioValue(user);

  document.getElementById("portCash").textContent=money(user.cash);
  document.getElementById("portHoldings").textContent=money(holdings);
  document.getElementById("portTotal").textContent=
    money(user.cash+holdings);

  const body=document.getElementById("portfolioRows");
  body.innerHTML="";

  let count=0;

  for(const id in user.holdings){
    const shares=Number(user.holdings[id]);

    if(shares<=0) continue;

    const stock=db.stocks.find(s=>s.id===id);

    if(!stock) continue;

    count++;

    body.innerHTML+=`
      <tr>
        <td>
          <div class="stockName">${escapeHtml(stock.name)}</div>
          <div class="ticker">${escapeHtml(stock.ticker)}</div>
        </td>
        <td>${shares}</td>
        <td>${money(stock.price)}</td>
        <td>${money(shares*stock.price)}</td>
        <td>
          <button class="tradeBtn sell" onclick="quickTrade('${stock.id}','sell')">Sell</button>
        </td>
      </tr>
    `;
  }

  if(count===0){
    body.innerHTML=`
      <tr>
        <td colspan="5" class="small">
          You don't own any stocks yet.
        </td>
      </tr>
    `;
  }
}

/* ---------------- FRIENDS ---------------- */

function addFriend(){
  const user=currentUser();
  const input=document.getElementById("friendInput");
  const message=document.getElementById("friendMessage");

  const name=input.value.trim();

  if(!name){
    message.textContent="Enter a username.";
    return;
  }

  const friend=db.users.find(
    u=>u.username.toLowerCase()===name.toLowerCase()
  );

  if(!friend){
    message.textContent="Player not found.";
    return;
  }

  if(friend.id===user.id){
    message.textContent="You can't add yourself.";
    return;
  }

  if(user.friends.includes(friend.id)){
    message.textContent="Already added.";
    return;
  }

  user.friends.push(friend.id);

  saveDatabase();

  input.value="";
  message.textContent="Friend added.";
  renderFriends();
}

function renderFriends(){
  const user=currentUser();
  const box=document.getElementById("friendList");

  box.innerHTML="";

  if(!user || !user.friends.length){
    box.innerHTML='<div class="small">No friends added yet.</div>';
    return;
  }

  user.friends.forEach(id=>{
    const friend=db.users.find(u=>u.id===id);

    if(!friend) return;

    box.innerHTML+=`
      <div class="card" style="margin-bottom:8px">
        <div class="stockName">${escapeHtml(friend.username)}</div>
        <div class="small">
          Total wealth: ${money(totalWealth(friend))}
        </div>
      </div>
    `;
  });
}

/* ---------------- LEADERBOARD ---------------- */

function renderLeaderboard(){
  const rows=db.users
    .slice()
    .sort((a,b)=>totalWealth(b)-totalWealth(a));

  const body=document.getElementById("leaderRows");

  body.innerHTML="";

  rows.forEach((u,index)=>{
    body.innerHTML+=`
      <tr>
        <td>${index+1}</td>
        <td class="stockName">${escapeHtml(u.username)}</td>
        <td>${money(u.cash)}</td>
        <td>${money(portfolioValue(u))}</td>
        <td class="green">${money(totalWealth(u))}</td>
      </tr>
    `;
  });
}

/* ---------------- STOCK CREATION ---------------- */

function createStock(){
  const user=currentUser();

  const name=document.getElementById("stockCompany").value.trim();
  const ticker=document.getElementById("stockTicker").value.trim().toUpperCase();
  const price=Number(document.getElementById("stockStartingPrice").value);
  const message=document.getElementById("createMessage");

  if(!name){
    message.textContent="Enter a company name.";
    return;
  }

  if(!/^[A-Z0-9]{2,5}$/.test(ticker)){
    message.textContent="Ticker must be 2-5 letters/numbers.";
    return;
  }

  if(!price || price<=0){
    message.textContent="Enter a valid starting price.";
    return;
  }

  if(user.cash<db.settings.creationFee){
    message.textContent=
      "You need "+money(db.settings.creationFee)+" to create a stock.";
    return;
  }

  const today=new Date().toISOString().slice(0,10);

  if(user.createdToday===today){
    message.textContent=
      "Only one stock can be created per player per day.";
    return;
  }

  if(db.stocks.some(s=>s.ticker===ticker)){
    message.textContent="That ticker already exists.";
    return;
  }

  user.cash-=db.settings.creationFee;
  user.createdToday=today;

  db.stocks.push(
    makeStock(name,ticker,price,user.username)
  );

  saveDatabase();

  document.getElementById("stockCompany").value="";
  document.getElementById("stockTicker").value="";
  document.getElementById("stockStartingPrice").value="";

  message.className="message green";
  message.textContent="Stock created successfully.";

  updateAll();
}

/* ---------------- RUG PULL ---------------- */

function rugPull(stockId){
  const user=currentUser();
  const stock=db.stocks.find(s=>s.id===stockId);

  if(!user || !stock) return;

  if(stock.owner!==user.username){
    alert("Only the stock creator can rug pull.");
    return;
  }

  if(stock.rugged){
    alert("This stock has already been rugged.");
    return;
  }

  let creatorProfit=0;
  let victims=0;

  db.users.forEach(investor=>{
    const shares=Number(investor.holdings[stock.id])||0;

    if(shares<=0) return;

    const value=shares*stock.price;
    const refund=value*.50;
    const creatorCut=value*.50;

    investor.cash+=refund;
    delete investor.holdings[stock.id];

    creatorProfit+=creatorCut;
    victims++;
  });

  user.cash+=creatorProfit;

  stock.rugged=true;
  stock.suspended=true;
  stock.ruggedAt=Date.now();
  stock.ruggedBy=user.username;

  /*
    Set chart price to zero after the rug pull.
    The historical candles remain so the event is visible.
  */
  stock.previousPrice=stock.price;
  stock.price=.01;

  stock.candles.push({
    open:stock.previousPrice,
    high:stock.previousPrice,
    low:.01,
    close:.01
  });

  saveDatabase();

  alert(
    "Rug pull completed.\n\n"+
    victims+" investor(s) affected.\n"+
    "Creator received "+money(creatorProfit)+".\n"+
    "Investors received 50% back."
  );

  updateAll();
}

/* ---------------- OPERATOR ---------------- */

function operatorLogin(){
  const password=prompt("Operator password:");

  if(password!==OPERATOR_PASSWORD){
    if(password!==null){
      alert("Incorrect operator password.");
    }
    return;
  }

  page("operator");

  document.querySelectorAll(".navBtn").forEach(b=>{
    b.classList.remove("active");
  });
}

function renderOperator(){
  document.getElementById("opPlayers").textContent=db.users.length;
  document.getElementById("opStocks").textContent=db.stocks.length;

  document.getElementById("opFee").value=db.settings.creationFee;

  const playerBody=document.getElementById("operatorPlayers");
  playerBody.innerHTML="";

  db.users.forEach(u=>{
    playerBody.innerHTML+=`
      <tr>
        <td>${escapeHtml(u.username)}</td>
        <td>${money(u.cash)}</td>
        <td class="${u.banned?'red':'green'}">
          ${u.banned?'Banned':'Active'}
        </td>
        <td>
          <button
            class="tradeBtn ${u.banned?'buy':'danger'}"
            onclick="toggleBan('${u.id}')">
            ${u.banned?'Unban':'Ban'}
          </button>
        </td>
      </tr>
    `;
  });

  const stockBody=document.getElementById("operatorStocks");
  stockBody.innerHTML="";

  db.stocks.forEach(stock=>{
    stockBody.innerHTML+=`
      <tr>
        <td>${escapeHtml(stock.name)}</td>
        <td>${escapeHtml(stock.ticker)}</td>
        <td>${money(stock.price)}</td>
        <td>${escapeHtml(stock.owner)}</td>
        <td>
          ${
            stock.suspended
              ? '<span class="small">Suspended</span>'
              : `<button class="tradeBtn danger" onclick="operatorSuspend('${stock.id}')">Suspend</button>`
          }
        </td>
      </tr>
    `;
  });
}

function saveOperatorSettings(){
  const fee=Number(document.getElementById("opFee").value);

  if(!Number.isFinite(fee)||fee<0){
    alert("Enter a valid fee.");
    return;
  }

  db.settings.creationFee=fee;
  saveDatabase();

  alert("Settings saved.");
  updateAll();
}

function toggleBan(id){
  const user=db.users.find(u=>u.id===id);

  if(!user) return;

  user.banned=!user.banned;

  saveDatabase();
  renderOperator();

  const active=currentUser();

  if(active && active.id===id && user.banned){
    alert("This account has been banned.");
    logout();
  }
}

function operatorSuspend(id){
  const stock=db.stocks.find(s=>s.id===id);

  if(!stock) return;

  stock.suspended=true;

  saveDatabase();
  renderOperator();
  updateAll();
}

function resetDemo(){
  if(!confirm(
    "This will erase local accounts, stocks and game progress. Continue?"
  )){
    return;
  }

  localStorage.removeItem(DATA_KEY);
  localStorage.removeItem(SESSION_KEY);

  db=defaultDatabase();

  location.reload();
}

/* ---------------- UPDATE ---------------- */

function updateAll(){
  const user=currentUser();

  if(!user) return;

  renderDashboard();
  renderMarket();
  renderPortfolio();
  renderFriends();
  renderLeaderboard();

  if(!document.getElementById("operatorPage").classList.contains("hidden")){
    renderOperator();
  }

  if(selectedStock){
    const fresh=db.stocks.find(s=>s.id===selectedStock.id);

    if(fresh){
      selectedStock=fresh;
      document.getElementById("selectedPrice").textContent=
        money(fresh.price);

      const change=percentChange(fresh);
      const changeEl=document.getElementById("selectedChange");

      changeEl.textContent=
        (change>=0?"+":"")+change.toFixed(2)+"%";

      changeEl.className=change>=0?"green":"red";
    }
  }

  drawChart();
}

/* ---------------- UTILITY ---------------- */

function escapeHtml(value){
  return String(value)
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");
}

window.addEventListener("resize",drawChart);

/* Start existing session if available */
(function boot(){
  const user=currentUser();

  if(user && !user.banned){
    startGame();
  }
})();
</script>

</body>
</html>
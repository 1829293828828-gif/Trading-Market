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
  background:#061018;
  color:#eaf2f8;
}
button,input{font:inherit}
button{cursor:pointer}
.hidden{display:none!important}

:root{
  --panel:#0d1a24;
  --panel2:#101f2b;
  --line:#203541;
  --muted:#7f94a5;
  --green:#35df91;
  --red:#ff626d;
  --blue:#55aaff;
}

/* LOGIN */
#loginScreen{
  min-height:100vh;
  display:grid;
  place-items:center;
  padding:20px;
  background:
    radial-gradient(circle at 50% -10%,#17364b,#061018 55%,#03070a);
}
.loginBox{
  width:min(430px,100%);
  background:#0c1821;
  border:1px solid #274050;
  border-radius:20px;
  padding:30px;
  box-shadow:0 25px 90px #0009;
}
.logo{
  font-size:30px;
  font-weight:900;
  letter-spacing:-1px;
}
.logo span,.brand span{color:var(--green)}
.subtitle{
  color:var(--muted);
  margin:7px 0 24px;
}
.tabs{
  display:flex;
  gap:6px;
  margin-bottom:18px;
}
.tab{
  flex:1;
  border:0;
  border-radius:9px;
  padding:11px;
  background:#142530;
  color:#91a5b4;
}
.tab.active{
  background:#1e9f68;
  color:white;
}
.field{
  margin:0 0 13px;
}
.field label{
  display:block;
  color:#91a5b4;
  font-size:13px;
  margin-bottom:6px;
}
input{
  width:100%;
  padding:12px;
  border-radius:9px;
  border:1px solid #29404f;
  background:#07121a;
  color:#fff;
  outline:none;
}
input:focus{
  border-color:var(--green);
}
.primary,.action{
  border:0;
  border-radius:9px;
  padding:12px 15px;
  font-weight:800;
}
.primary{
  width:100%;
  background:#20b873;
  color:#fff;
}
.action{
  background:#1d9863;
  color:#fff;
}
.secondary{
  background:#172733;
  color:#c6d2da;
}
.danger{
  background:#963c47;
  color:#fff;
}
.message{
  min-height:20px;
  margin-top:11px;
  font-size:13px;
  color:#ff7b82;
}

/* TOP */
.topbar{
  height:66px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 20px;
  background:#0a151e;
  border-bottom:1px solid var(--line);
  position:sticky;
  top:0;
  z-index:20;
}
.brand{
  font-size:21px;
  font-weight:900;
}
.topRight{
  display:flex;
  align-items:center;
  gap:14px;
}
.cashTop{
  color:var(--green);
  font-weight:800;
}
.logout{
  background:#172630;
  border:1px solid #2a3e4c;
  color:#c2ced7;
  padding:8px 12px;
  border-radius:8px;
}

/* LAYOUT */
.layout{
  display:grid;
  grid-template-columns:225px 1fr;
  min-height:calc(100vh - 66px);
}
.sidebar{
  background:#08131b;
  border-right:1px solid var(--line);
  padding:14px 10px;
}
.navBtn{
  width:100%;
  text-align:left;
  border:0;
  border-radius:9px;
  background:transparent;
  color:#8296a6;
  padding:12px 13px;
  margin-bottom:5px;
}
.navBtn:hover,
.navBtn.active{
  background:#142733;
  color:#fff;
}
.main{
  padding:24px;
  max-width:1500px;
  width:100%;
  margin:auto;
}
.pageTitle{
  font-size:29px;
  font-weight:900;
}
.pageSub{
  color:var(--muted);
  margin:5px 0 20px;
}

/* CARDS */
.cards{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:12px;
  margin-bottom:18px;
}
.card,
.panel{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:13px;
}
.card{
  padding:17px;
}
.cardLabel{
  color:#738999;
  font-size:11px;
  text-transform:uppercase;
  letter-spacing:.6px;
}
.cardValue{
  margin-top:7px;
  font-size:23px;
  font-weight:900;
}
.green{color:var(--green)}
.red{color:var(--red)}
.blue{color:var(--blue)}

/* TABLE */
.panel{
  overflow:hidden;
  margin-bottom:18px;
}
.panelHead{
  padding:16px 18px;
  border-bottom:1px solid var(--line);
  display:flex;
  align-items:center;
  justify-content:space-between;
}
.panelTitle{
  font-weight:850;
}
table{
  width:100%;
  border-collapse:collapse;
}
th{
  padding:11px 15px;
  text-align:left;
  color:#718493;
  font-size:11px;
  text-transform:uppercase;
  border-bottom:1px solid var(--line);
}
td{
  padding:13px 15px;
  border-bottom:1px solid #172934;
}
tr:last-child td{
  border-bottom:0;
}
.stockButton{
  background:transparent;
  border:0;
  color:inherit;
  text-align:left;
  padding:0;
}
.stockName{
  font-weight:800;
}
.ticker{
  color:#708595;
  font-size:12px;
  margin-top:2px;
}
.tradeBtn{
  border:0;
  border-radius:7px;
  padding:7px 10px;
  margin-left:4px;
  font-weight:800;
}
.buy{
  background:#154c35;
  color:#5ee8a8;
}
.sell{
  background:#55232a;
  color:#ff858c;
}

/* MARKET */
.marketGrid{
  display:grid;
  grid-template-columns:minmax(0,1fr) 350px;
  gap:16px;
}
.chartBox{
  padding:18px;
}
.chartWrap{
  height:390px;
}
.chartCanvas{
  width:100%;
  height:100%;
}
.priceBig{
  font-size:32px;
  font-weight:900;
}
.chartTitle{
  display:flex;
  justify-content:space-between;
  align-items:flex-start;
  margin-bottom:8px;
}
.statStrip{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:9px;
  margin:12px 0;
}
.mini{
  background:#0a141c;
  border:1px solid #1d303d;
  border-radius:10px;
  padding:11px;
}
.mini b{
  display:block;
  margin-top:4px;
}
.tradeBox{
  padding:18px;
}
.small{
  color:var(--muted);
  font-size:12px;
}
.buySell{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:8px;
}
.buyBig,
.sellBig{
  border:0;
  border-radius:9px;
  padding:13px;
  font-weight:900;
}
.buyBig{
  background:#1d9e66;
  color:#fff;
}
.sellBig{
  background:#a8444e;
  color:#fff;
}

/* FRIENDS */
.formRow{
  display:flex;
  gap:8px;
}
.formRow input{
  flex:1;
}
.formRow button{
  width:auto;
}

/* MODAL */
.modal{
  position:fixed;
  inset:0;
  background:#000b;
  display:grid;
  place-items:center;
  padding:20px;
  z-index:100;
}
.modalBox{
  width:min(470px,100%);
  background:#0d1922;
  border:1px solid #2a4050;
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

/* BADGES */
.badge{
  display:inline-block;
  padding:4px 7px;
  border-radius:999px;
  font-size:11px;
  background:#173041;
  color:#9cb0be;
}
.badge.green{
  background:#123c2c;
  color:#62e5a8;
}
.badge.red{
  background:#45232a;
  color:#ff838c;
}

/* MOBILE */
@media(max-width:900px){
  .layout{
    grid-template-columns:1fr;
  }

  .sidebar{
    display:flex;
    overflow:auto;
    border-right:0;
    border-bottom:1px solid var(--line);
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

  .chartWrap{
    height:320px;
  }
}

@media(max-width:600px){
  .main{
    padding:13px;
  }

  .cards{
    gap:8px;
  }

  .card{
    padding:13px;
  }

  .topbar{
    padding:0 12px;
  }

  .cashTop{
    display:none;
  }

  th,td{
    padding:9px 7px;
  }

  .statStrip{
    grid-template-columns:1fr 1fr;
  }
}
</style>
</head>

<body>

<!-- LOGIN -->
<div id="loginScreen">
  <div class="loginBox">

    <div class="logo">
      MARKET <span>ARCADE</span>
    </div>

    <div class="subtitle">
      A fictional stock-market game with virtual money.
    </div>

    <div class="tabs">
      <button class="tab active" id="loginTab" onclick="showLogin()">
        Login
      </button>

      <button class="tab" id="signupTab" onclick="showSignup()">
        Create account
      </button>
    </div>

    <div id="loginForm">

      <div class="field">
        <label>Username</label>
        <input id="loginUsername" autocomplete="username">
      </div>

      <div class="field">
        <label>Password</label>
        <input
          id="loginPassword"
          type="password"
          autocomplete="current-password"
        >
      </div>

      <button class="primary" onclick="login()">
        Login
      </button>

    </div>

    <div id="signupForm" class="hidden">

      <div class="field">
        <label>Username</label>
        <input id="signupUsername" autocomplete="username">
      </div>

      <div class="field">
        <label>Password</label>
        <input
          id="signupPassword"
          type="password"
          autocomplete="new-password"
        >
      </div>

      <div class="field">
        <label>Confirm password</label>
        <input id="signupConfirm" type="password">
      </div>

      <button class="primary" onclick="signup()">
        Create account
      </button>

    </div>

    <div id="authMessage" class="message"></div>

  </div>
</div>


<!-- APP -->
<div id="app" class="hidden">

  <div class="topbar">

    <div class="brand">
      MARKET <span>ARCADE</span>
    </div>

    <div class="topRight">
      <div class="cashTop" id="topCash">$100.00</div>

      <div id="topUser">
        Player
      </div>

      <button class="logout" onclick="logout()">
        Logout
      </button>
    </div>

  </div>


  <div class="layout">

    <aside class="sidebar">

      <button
        class="navBtn active"
        onclick="page('dashboard',this)"
      >
        📊 Dashboard
      </button>

      <button
        class="navBtn"
        onclick="page('market',this)"
      >
        📈 Market
      </button>

      <button
        class="navBtn"
        onclick="page('portfolio',this)"
      >
        💼 Portfolio
      </button>

      <button
        class="navBtn"
        onclick="page('friends',this)"
      >
        👥 Friends
      </button>

      <button
        class="navBtn"
        onclick="page('leaderboard',this)"
      >
        🏆 Leaderboard
      </button>

      <button
        class="navBtn"
        onclick="page('create',this)"
      >
        🏢 Create Stock
      </button>

      <button
        class="navBtn"
        onclick="operatorLogin()"
      >
        🛡️ Operator
      </button>

    </aside>


    <main class="main">

      <!-- DASHBOARD -->

      <section id="dashboardPage">

        <div class="pageTitle">
          Dashboard
        </div>

        <div class="pageSub">
          Welcome back, <span id="dashUser">Player</span>.
        </div>


        <div class="cards">

          <div class="card">
            <div class="cardLabel">
              Cash
            </div>

            <div
              class="cardValue green"
              id="dashCash"
            >
              $100.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Portfolio
            </div>

            <div
              class="cardValue"
              id="dashPortfolio"
            >
              $0.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Total value
            </div>

            <div
              class="cardValue"
              id="dashTotal"
            >
              $100.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Profit / Loss
            </div>

            <div
              class="cardValue"
              id="dashPL"
            >
              $0.00
            </div>
          </div>

        </div>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              Market overview
            </div>

            <button
              class="action"
              onclick="page('market')"
            >
              Open market
            </button>

          </div>


          <table>

            <thead>
              <tr>
                <th>Company</th>
                <th>Price</th>
                <th>24h</th>
                <th>Market value</th>
                <th>Shareholders</th>
              </tr>
            </thead>

            <tbody id="dashboardStocks"></tbody>

          </table>

        </div>

      </section>


      <!-- MARKET -->

      <section id="marketPage" class="hidden">

        <div class="pageTitle">
          Market
        </div>

        <div class="pageSub">
          Prices can move dramatically, while the long-term market trend
          is designed to reward patience.
        </div>


        <div class="marketGrid">


          <div class="panel">

            <div class="chartBox">

              <div class="chartTitle">

                <div>

                  <div
                    class="panelTitle"
                    id="selectedName"
                  >
                    Select a stock
                  </div>

                  <div
                    class="ticker"
                    id="selectedTicker"
                  >
                    ---
                  </div>

                </div>


                <div>

                  <div
                    class="priceBig"
                    id="selectedPrice"
                  >
                    $0.00
                  </div>

                  <div id="selectedChange">
                    0.00%
                  </div>

                </div>

              </div>


              <div class="statStrip">

                <div class="mini">
                  <span class="small">
                    Market value
                  </span>

                  <b id="selectedMarketCap">
                    $0.00
                  </b>
                </div>


                <div class="mini">
                  <span class="small">
                    Shareholders
                  </span>

                  <b id="selectedHolders">
                    0
                  </b>
                </div>


                <div class="mini">
                  <span class="small">
                    Shares owned
                  </span>

                  <b id="selectedShares">
                    0
                  </b>
                </div>


                <div class="mini">
                  <span class="small">
                    Status
                  </span>

                  <b id="selectedStatus">
                    Trading
                  </b>
                </div>

              </div>


              <div class="chartWrap">
                <canvas
                  id="chart"
                  class="chartCanvas"
                ></canvas>
              </div>

            </div>

          </div>


          <div class="panel">

            <div class="tradeBox">

              <div class="panelTitle">
                Trade
              </div>

              <p
                class="small"
                id="tradeHint"
              >
                Select a stock.
              </p>


              <div class="field">

                <label>
                  Shares
                </label>

                <input
                  id="tradeShares"
                  type="number"
                  min="1"
                  step="1"
                  value="1"
                >

              </div>


              <div class="card">

                <div class="cardLabel">
                  Estimated total
                </div>

                <div
                  class="cardValue"
                  id="tradeTotal"
                >
                  $0.00
                </div>

              </div>


              <br>


              <div class="buySell">

                <button
                  class="buyBig"
                  onclick="trade('buy')"
                >
                  BUY
                </button>

                <button
                  class="sellBig"
                  onclick="trade('sell')"
                >
                  SELL
                </button>

              </div>

            </div>

          </div>

        </div>


        <br>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              All stocks
            </div>

          </div>


          <table>

            <thead>
              <tr>
                <th>Company</th>
                <th>Price</th>
                <th>24h</th>
                <th>Market value</th>
                <th>Shareholders</th>
                <th></th>
              </tr>
            </thead>

            <tbody id="marketStocks"></tbody>

          </table>

        </div>

      </section>


      <!-- PORTFOLIO -->

      <section id="portfolioPage" class="hidden">

        <div class="pageTitle">
          Portfolio
        </div>

        <div class="pageSub">
          Track your virtual investments.
        </div>


        <div class="cards">

          <div class="card">
            <div class="cardLabel">
              Cash
            </div>

            <div
              class="cardValue green"
              id="portCash"
            >
              $100.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Holdings
            </div>

            <div
              class="cardValue"
              id="portHoldings"
            >
              $0.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Total
            </div>

            <div
              class="cardValue"
              id="portTotal"
            >
              $100.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Positions
            </div>

            <div
              class="cardValue"
              id="portPositions"
            >
              0
            </div>
          </div>

        </div>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              Holdings
            </div>

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

        <div class="pageTitle">
          Friends
        </div>

        <div class="pageSub">
          Compare your virtual market journey with other players.
        </div>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              Add friend
            </div>

          </div>


          <div style="padding:18px">

            <div class="formRow">

              <input
                id="friendInput"
                placeholder="Username"
              >

              <button
                class="action"
                onclick="addFriend()"
              >
                Add
              </button>

            </div>

            <div
              id="friendMessage"
              class="message"
            ></div>

          </div>

        </div>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              Your friends
            </div>

          </div>

          <div
            id="friendList"
            style="padding:18px"
          ></div>

        </div>

      </section>


      <!-- LEADERBOARD -->

      <section id="leaderboardPage" class="hidden">

        <div class="pageTitle">
          Leaderboard
        </div>

        <div class="pageSub">
          Ranked by total virtual wealth.
        </div>


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

        <div class="pageTitle">
          Create a Stock
        </div>

        <div class="pageSub">
          Players can launch new fictional companies as the market grows.
        </div>


        <div class="panel">

          <div style="padding:20px">

            <div
              class="card"
              style="margin-bottom:18px"
            >

              <div class="cardLabel">
                Current creation fee
              </div>

              <div
                class="cardValue"
                id="creationFee"
              >
                $100,000,000.00
              </div>

              <div class="small">
                Only one stock may be created per player per real-world day.
              </div>

            </div>


            <div class="field">

              <label>
                Company name
              </label>

              <input
                id="stockCompany"
                placeholder="Example: Future Systems"
              >

            </div>


            <div class="field">

              <label>
                Ticker
              </label>

              <input
                id="stockTicker"
                maxlength="5"
                placeholder="FUTR"
              >

            </div>


            <div class="field">

              <label>
                Starting price
              </label>

              <input
                id="stockStartingPrice"
                type="number"
                min=".01"
                step=".01"
                placeholder="10"
              >

            </div>


            <button
              class="action"
              onclick="createStock()"
            >
              Create stock
            </button>


            <div
              id="createMessage"
              class="message"
            ></div>

          </div>

        </div>

      </section>


      <!-- OPERATOR -->

      <section id="operatorPage" class="hidden">

        <div class="pageTitle">
          Operator Panel
        </div>

        <div class="pageSub">
          Local beta administration tools.
        </div>


        <div class="cards">

          <div class="card">
            <div class="cardLabel">
              Players
            </div>

            <div
              class="cardValue"
              id="opPlayers"
            >
              0
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Stocks
            </div>

            <div
              class="cardValue"
              id="opStocks"
            >
              0
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              Market value
            </div>

            <div
              class="cardValue"
              id="opMarketValue"
            >
              $0.00
            </div>
          </div>


          <div class="card">
            <div class="cardLabel">
              COOL price
            </div>

            <div
              class="cardValue"
              id="opCoolPrice"
            >
              $0.00
            </div>
          </div>

        </div>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              Market settings
            </div>

          </div>


          <div style="padding:18px">

            <div class="field">

              <label>
                Stock creation fee
              </label>

              <input
                id="opFee"
                type="number"
                min="0"
                step="100"
              >

            </div>


            <button
              class="action"
              onclick="saveOperatorSettings()"
            >
              Save settings
            </button>


            <button
              class="action secondary"
              onclick="resetDemo()"
              style="margin-left:6px"
            >
              Reset demo data
            </button>

          </div>

        </div>


        <div class="panel">

          <div class="panelHead">

            <div class="panelTitle">
              Players
            </div>

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

            <div class="panelTitle">
              Stocks
            </div>

          </div>


          <table>

            <thead>

              <tr>
                <th>Company</th>
                <th>Ticker</th>
                <th>Price</th>
                <th>Market value</th>
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

<div
  id="tradeModal"
  class="modal hidden"
>

  <div class="modalBox">

    <div
      class="panelTitle"
      id="modalTitle"
    >
      Trade
    </div>

    <p
      id="modalText"
      class="small"
    ></p>


    <div class="field">

      <label>
        Shares
      </label>

      <input
        id="modalShares"
        type="number"
        min="1"
        value="1"
      >

    </div>


    <div class="card">

      <div class="cardLabel">
        Estimated total
      </div>

      <div
        class="cardValue"
        id="modalTotal"
      >
        $0.00
      </div>

    </div>


    <div class="modalActions">

      <button
        class="action secondary"
        onclick="closeModal()"
      >
        Cancel
      </button>

      <button
        class="action"
        id="modalConfirm"
      >
        Confirm
      </button>

    </div>

  </div>

</div>


<script>

const DATA_KEY = "MARKET_ARCADE_POLISHED_DATA";
const SESSION_KEY = "MARKET_ARCADE_POLISHED_SESSION";

/*
  LOCAL BETA OPERATOR PASSWORD
  Change this before sharing the site.
*/
const OPERATOR_PASSWORD = "MA-ADMIN-2026";

let db = loadDatabase();
let selectedStock = null;
let tickTimer = null;


/* DATABASE */

function makeStock(
  name,
  ticker,
  price,
  owner = "Market Arcade"
){

  const p = Number(price) || 1;

  return {
    id:
      "stock_" +
      Date.now() +
      "_" +
      Math.random().toString(36).slice(2),

    name:name,

    ticker:ticker.toUpperCase(),

    price:p,

    previousPrice:p,

    owner:owner,

    /*
      This is the number of virtual shares
      that exist for market-value calculations.
    */
    sharesOutstanding:1000000,

    createdAt:Date.now(),

    suspended:false,

    rugged:false,

    candles:makeCandles(p,55),

    history:[p]
  };
}


function makeCandles(price,count){

  let candles = [];

  let p = price;

  for(let i=0;i<count;i++){

    const open = p;

    /*
      Starting chart movement.
    */
    const close =
      Math.max(
        0.01,
        p * (1 + (Math.random() - 0.47) * 0.08)
      );

    const high =
      Math.max(open,close) *
      (1 + Math.random() * 0.03);

    const low =
      Math.max(
        0.01,
        Math.min(open,close) *
        (1 - Math.random() * 0.03)
      );

    candles.push({
      open:open,
      high:high,
      low:low,
      close:close
    });

    p = close;
  }

  return candles;
}


function defaultDatabase(){

  return {

    settings:{
      creationFee:100000000
    },

    users:[],

    /*
      COOL is the only starting stock.
    */
    stocks:[
      makeStock(
        "Cool Holdings",
        "COOL",
        10
      )
    ]

  };
}


function loadDatabase(){

  try{

    const saved =
      localStorage.getItem(DATA_KEY);

    if(!saved){
      return defaultDatabase();
    }

    const data =
      JSON.parse(saved);

    if(!data.settings){
      data.settings={
        creationFee:100000000
      };
    }

    if(!data.users){
      data.users=[];
    }

    if(!data.stocks){
      data.stocks=[];
    }

    data.users.forEach(normalizeUser);
    data.stocks.forEach(normalizeStock);

    /*
      Make sure COOL exists.
    */
    if(
      !data.stocks.some(
        stock => stock.ticker === "COOL"
      )
    ){

      data.stocks.unshift(
        makeStock(
          "Cool Holdings",
          "COOL",
          10
        )
      );

    }

    return data;

  }catch(error){

    return defaultDatabase();

  }

}


function normalizeUser(user){

  if(!user.holdings){
    user.holdings={};
  }

  if(!user.friends){
    user.friends=[];
  }

  if(typeof user.cash !== "number"){
    user.cash=100;
  }

  if(typeof user.banned !== "boolean"){
    user.banned=false;
  }

}


function normalizeStock(stock){

  if(!stock.sharesOutstanding){
    stock.sharesOutstanding=1000000;
  }

  if(!Array.isArray(stock.candles)){
    stock.candles=
      makeCandles(
        Number(stock.price) || 1,
        55
      );
  }

  if(!Array.isArray(stock.history)){
    stock.history=[
      Number(stock.price) || 1
    ];
  }

  if(typeof stock.suspended !== "boolean"){
    stock.suspended=false;
  }

  if(typeof stock.rugged !== "boolean"){
    stock.rugged=false;
  }

}


function saveDatabase(){

  localStorage.setItem(
    DATA_KEY,
    JSON.stringify(db)
  );

}


function currentUser(){

  const id =
    localStorage.getItem(SESSION_KEY);

  if(!id){
    return null;
  }

  const user =
    db.users.find(
      u => u.id === id
    );

  if(user){
    normalizeUser(user);
  }

  return user || null;
}


/* MONEY / MARKET HELPERS */

function money(number){

  return "$" +
    Number(number || 0)
    .toLocaleString(
      "en-US",
      {
        minimumFractionDigits:2,
        maximumFractionDigits:2
      }
    );

}


function portfolioValue(user){

  let total=0;

  for(
    const stockId in user.holdings
  ){

    const shares =
      Number(user.holdings[stockId]) || 0;

    const stock =
      db.stocks.find(
        s => s.id === stockId
      );

    if(stock){
      total +=
        shares * stock.price;
    }

  }

  return total;

}


function totalWealth(user){

  return (
    user.cash +
    portfolioValue(user)
  );

}


function marketCap(stock){

  return (
    stock.price *
    (stock.sharesOutstanding || 1000000)
  );

}


function shareholders(stock){

  return db.users.filter(
    user =>
      (Number(
        user.holdings[stock.id]
      ) || 0) > 0
  ).length;

}


function totalSharesOwned(stock){

  return db.users.reduce(
    (total,user) =>
      total +
      (Number(
        user.holdings[stock.id]
      ) || 0),
    0
  );

}


function percentChange(stock){

  if(
    !stock.candles ||
    stock.candles.length < 2
  ){
    return 0;
  }

  const first =
    stock.candles[0].open;

  if(!first){
    return 0;
  }

  return (
    (stock.price-first) /
    first
  ) * 100;

}


function escapeHtml(value){

  return String(value)
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");

}


/* AUTH */

function showLogin(){

  loginForm.classList.remove("hidden");

  signupForm.classList.add("hidden");

  loginTab.classList.add("active");

  signupTab.classList.remove("active");

  authMessage.textContent="";

}


function showSignup(){

  loginForm.classList.add("hidden");

  signupForm.classList.remove("hidden");

  loginTab.classList.remove("active");

  signupTab.classList.add("active");

  authMessage.textContent="";

}


function signup(){

  const username =
    signupUsername.value.trim();

  const password =
    signupPassword.value;

  if(username.length < 3){

    authMessage.textContent =
      "Username must be at least 3 characters.";

    return;

  }

  if(password.length < 4){

    authMessage.textContent =
      "Password must be at least 4 characters.";

    return;

  }

  if(
    password !==
    signupConfirm.value
  ){

    authMessage.textContent =
      "Passwords do not match.";

    return;

  }

  if(
    db.users.some(
      user =>
        user.username.toLowerCase() ===
        username.toLowerCase()
    )
  ){

    authMessage.textContent =
      "That username already exists.";

    return;

  }

  const user={

    id:
      "user_" +
      Date.now() +
      "_" +
      Math.random()
      .toString(36)
      .slice(2),

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

  localStorage.setItem(
    SESSION_KEY,
    user.id
  );

  startGame();

}


function login(){

  const username =
    loginUsername.value
      .trim()
      .toLowerCase();

  const password =
    loginPassword.value;

  const user =
    db.users.find(
      u =>
        u.username.toLowerCase() === username &&
        u.password === password
    );

  if(!user){

    authMessage.textContent =
      "Incorrect username or password.";

    return;

  }

  if(user.banned){

    authMessage.textContent =
      "This account is banned.";

    return;

  }

  localStorage.setItem(
    SESSION_KEY,
    user.id
  );

  startGame();

}


function logout(){

  localStorage.removeItem(
    SESSION_KEY
  );

  clearInterval(tickTimer);

  app.classList.add("hidden");

  loginScreen.classList.remove(
    "hidden"
  );

  showLogin();

}


/* GAME START */

function startGame(){

  loginScreen.classList.add(
    "hidden"
  );

  app.classList.remove(
    "hidden"
  );

  updateAll();

  page("dashboard");

  clearInterval(tickTimer);

  /*
    Every five seconds the market changes.
  */
  tickTimer =
    setInterval(
      marketTick,
      5000
    );

}


/* NAVIGATION */

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

  pages.forEach(
    pageName => {

      const element =
        document.getElementById(
          pageName + "Page"
        );

      if(element){

        element.classList.toggle(
          "hidden",
          pageName !== name
        );

      }

    }
  );

  document
    .querySelectorAll(".navBtn")
    .forEach(
      b => b.classList.remove("active")
    );

  if(button){
    button.classList.add("active");
  }

  if(name === "market"){

    renderMarket();

    if(
      !selectedStock &&
      db.stocks.length
    ){
      selectStock(
        db.stocks[0].id
      );
    }

    drawChart();

  }

  if(name === "portfolio"){
    renderPortfolio();
  }

  if(name === "friends"){
    renderFriends();
  }

  if(name === "leaderboard"){
    renderLeaderboard();
  }

  if(name === "create"){

    creationFee.textContent =
      money(
        db.settings.creationFee
      );

  }

  if(name === "operator"){
    renderOperator();
  }

}


/* DASHBOARD */

function renderDashboard(){

  const user =
    currentUser();

  if(!user){
    return;
  }

  const portfolio =
    portfolioValue(user);

  const total =
    totalWealth(user);

  const profit =
    total - 100;

  topUser.textContent =
    user.username;

  dashUser.textContent =
    user.username;

  topCash.textContent =
    money(user.cash);

  dashCash.textContent =
    money(user.cash);

  dashPortfolio.textContent =
    money(portfolio);

  dashTotal.textContent =
    money(total);

  dashPL.textContent =
    (profit >= 0 ? "+" : "") +
    money(profit);

  dashPL.className =
    "cardValue " +
    (profit >= 0
      ? "green"
      : "red");

  dashboardStocks.innerHTML =
    db.stocks.map(
      stock => {

        const change =
          percentChange(stock);

        return `
          <tr>

            <td>

              <button
                class="stockButton"
                onclick="selectAndMarket('${stock.id}')"
              >

                <div class="stockName">
                  ${escapeHtml(stock.name)}
                </div>

                <div class="ticker">
                  ${escapeHtml(stock.ticker)}
                </div>

              </button>

            </td>

            <td>
              ${money(stock.price)}
            </td>

            <td class="${change >= 0 ? "green" : "red"}">
              ${change >= 0 ? "+" : ""}
              ${change.toFixed(2)}%
            </td>

            <td>
              ${money(marketCap(stock))}
            </td>

            <td>
              ${shareholders(stock).toLocaleString()}
            </td>

          </tr>
        `;

      }
    )
    .join("");

}


/* MARKET */

function renderMarket(){

  marketStocks.innerHTML =
    db.stocks.map(
      stock => {

        const change =
          percentChange(stock);

        return `
          <tr>

            <td>

              <button
                class="stockButton"
                onclick="selectStock('${stock.id}')"
              >

                <div class="stockName">
                  ${escapeHtml(stock.name)}
                </div>

                <div class="ticker">
                  ${escapeHtml(stock.ticker)}
                </div>

              </button>

            </td>

            <td>
              ${money(stock.price)}
            </td>

            <td class="${change >= 0 ? "green" : "red"}">

              ${change >= 0 ? "+" : ""}
              ${change.toFixed(2)}%

            </td>

            <td>
              ${money(marketCap(stock))}
            </td>

            <td>
              ${shareholders(stock).toLocaleString()}
            </td>

            <td>

              <button
                class="tradeBtn buy"
                onclick="quickTrade('${stock.id}','buy')"
              >
                Buy
              </button>

              <button
                class="tradeBtn sell"
                onclick="quickTrade('${stock.id}','sell')"
              >
                Sell
              </button>

            </td>

          </tr>
        `;

      }
    )
    .join("");

}


function selectAndMarket(id){

  page("market");

  setTimeout(
    () => selectStock(id),
    20
  );

}


function selectStock(id){

  selectedStock =
    db.stocks.find(
      stock => stock.id === id
    ) || null;

  if(!selectedStock){
    return;
  }

  selectedName.textContent =
    selectedStock.name;

  selectedTicker.textContent =
    selectedStock.ticker;

  selectedPrice.textContent =
    money(selectedStock.price);

  const change =
    percentChange(selectedStock);

  selectedChange.textContent =
    (change >= 0 ? "+" : "") +
    change.toFixed(2) +
    "%";

  selectedChange.className =
    change >= 0
      ? "green"
      : "red";

  selectedMarketCap.textContent =
    money(
      marketCap(selectedStock)
    );

  selectedHolders.textContent =
    shareholders(
      selectedStock
    ).toLocaleString();

  selectedShares.textContent =
    totalSharesOwned(
      selectedStock
    ).toLocaleString();

  selectedStatus.textContent =
    selectedStock.suspended
      ? "Suspended"
      : "Trading";

  tradeHint.textContent =
    selectedStock.suspended
      ? "This stock is suspended."
      : "Trading " +
        selectedStock.ticker;

  updateTradeTotal();

  drawChart();

}


tradeShares.addEventListener(
  "input",
  updateTradeTotal
);


function updateTradeTotal(){

  const shares =
    Number(tradeShares.value) || 0;

  tradeTotal.textContent =
    money(
      shares *
      (selectedStock
        ? selectedStock.price
        : 0)
    );

}


/* TRADING */

function quickTrade(id,type){

  selectStock(id);

  const stock =
    db.stocks.find(
      s => s.id === id
    );

  if(!stock){
    return;
  }

  modalTitle.textContent =
    type === "buy"
      ? "Buy " + stock.ticker
      : "Sell " + stock.ticker;

  modalText.textContent =
    stock.name +
    " is currently " +
    money(stock.price) +
    " per share.";

  modalShares.value = 1;

  updateModalTotal();

  tradeModal.classList.remove(
    "hidden"
  );

  modalConfirm.onclick =
    function(){

      executeTrade(
        id,
        type
      );

    };

}


modalShares.addEventListener(
  "input",
  updateModalTotal
);


function updateModalTotal(){

  const shares =
    Number(modalShares.value) || 0;

  modalTotal.textContent =
    money(
      shares *
      (selectedStock
        ? selectedStock.price
        : 0)
    );

}


function closeModal(){

  tradeModal.classList.add(
    "hidden"
  );

}


function trade(type){

  if(!selectedStock){

    alert(
      "Select a stock first."
    );

    return;

  }

  quickTrade(
    selectedStock.id,
    type
  );

}


function executeTrade(
  id,
  type
){

  const user =
    currentUser();

  const stock =
    db.stocks.find(
      s => s.id === id
    );

  if(!user || !stock){
    return;
  }

  if(stock.suspended){

    alert(
      "This stock is suspended."
    );

    return;

  }

  const shares =
    Math.floor(
      Number(
        modalShares.value
      )
    );

  if(
    !shares ||
    shares < 1
  ){

    alert(
      "Enter at least 1 share."
    );

    return;

  }

  const total =
    shares *
    stock.price;

  if(type === "buy"){

    if(user.cash < total){

      alert(
        "You don't have enough virtual cash."
      );

      return;

    }

    user.cash -= total;

    user.holdings[stock.id] =
      (user.holdings[stock.id] || 0) +
      shares;

  }else{

    const owned =
      user.holdings[stock.id] || 0;

    if(owned < shares){

      alert(
        "You don't own enough shares."
      );

      return;

    }

    user.cash += total;

    user.holdings[stock.id] -=
      shares;

    if(
      user.holdings[stock.id] <= 0
    ){

      delete user.holdings[
        stock.id
      ];

    }

  }

  saveDatabase();

  closeModal();

  updateAll();

}


/* CANDLESTICK CHART */

function drawChart(){

  const canvas =
    document.getElementById(
      "chart"
    );

  if(
    !canvas ||
    !selectedStock
  ){
    return;
  }

  const rect =
    canvas.getBoundingClientRect();

  const dpr =
    window.devicePixelRatio || 1;

  canvas.width =
    Math.max(
      1,
      rect.width * dpr
    );

  canvas.height =
    Math.max(
      1,
      rect.height * dpr
    );

  const ctx =
    canvas.getContext("2d");

  ctx.scale(
    dpr,
    dpr
  );

  const width =
    rect.width;

  const height =
    rect.height;

  const candles =
    selectedStock.candles.slice(
      -50
    );

  if(!candles.length){
    return;
  }

  let min = Infinity;
  let max = -Infinity;

  candles.forEach(
    candle => {

      min =
        Math.min(
          min,
          candle.low
        );

      max =
        Math.max(
          max,
          candle.high
        );

    }
  );

  if(max === min){

    max += 1;
    min -= 1;

  }

  const padding={
    left:55,
    right:15,
    top:15,
    bottom:25
  };

  const chartWidth =
    width -
    padding.left -
    padding.right;

  const chartHeight =
    height -
    padding.top -
    padding.bottom;

  function y(value){

    return (
      padding.top +
      (
        (max-value) /
        (max-min)
      ) *
      chartHeight
    );

  }

  ctx.clearRect(
    0,
    0,
    width,
    height
  );

  ctx.strokeStyle =
    "#1d303c";

  ctx.fillStyle =
    "#667b8b";

  ctx.font =
    "11px Arial";

  for(
    let i=0;
    i<5;
    i++
  ){

    const yy =
      padding.top +
      chartHeight *
      i /
      4;

    ctx.beginPath();

    ctx.moveTo(
      padding.left,
      yy
    );

    ctx.lineTo(
      width -
      padding.right,
      yy
    );

    ctx.stroke();

    const value =
      max -
      (
        (max-min) *
        i /
        4
      );

    ctx.fillText(
      money(value),
      5,
      yy+4
    );

  }

  const gap =
    chartWidth /
    candles.length;

  const candleWidth =
    Math.max(
      3,
      gap * .55
    );

  candles.forEach(
    (candle,index) => {

      const x =
        padding.left +
        index *
        gap +
        gap /
        2;

      const openY =
        y(candle.open);

      const closeY =
        y(candle.close);

      const highY =
        y(candle.high);

      const lowY =
        y(candle.low);

      const up =
        candle.close >=
        candle.open;

      ctx.strokeStyle =
        up
          ? "#35df91"
          : "#ff626d";

      ctx.fillStyle =
        ctx.strokeStyle;

      ctx.beginPath();

      ctx.moveTo(
        x,
        highY
      );

      ctx.lineTo(
        x,
        lowY
      );

      ctx.stroke();

      const top =
        Math.min(
          openY,
          closeY
        );

      const bodyHeight =
        Math.max(
          2,
          Math.abs(
            openY -
            closeY
          )
        );

      ctx.fillRect(
        x -
        candleWidth /
        2,

        top,

        candleWidth,

        bodyHeight
      );

    }
  );

}


/* MARKET MOVEMENT */

function marketTick(){

  db.stocks.forEach(
    stock => {

      if(stock.suspended){
        return;
      }

      const old =
        stock.price;

      /*
        Dramatic movement:

        +0.9% average drift
        with approximately +/-7%
        random movement.

        This means the price can fall
        significantly in the short term,
        while the long-term expectation
        is upward.
      */

      const drift =
        0.009;

      const swing =
        (Math.random() - 0.5) *
        0.14;

      let next =
        old *
        (
          1 +
          drift +
          swing
        );

      if(next < 0.01){
        next=0.01;
      }

      stock.previousPrice =
        old;

      stock.price =
        Number(
          next.toFixed(2)
        );

      let last =
        stock.candles[
          stock.candles.length - 1
        ];

      if(!last){

        last={
          open:old,
          high:old,
          low:old,
          close:old
        };

        stock.candles.push(
          last
        );

      }

      last.close =
        stock.price;

      last.high =
        Math.max(
          last.high,
          stock.price
        );

      last.low =
        Math.min(
          last.low,
          stock.price
        );

      /*
        More frequent new candles
        make the market feel alive.
      */

      if(
        Math.random() <
        0.65
      ){

        stock.candles.push({
          open:stock.price,
          high:stock.price,
          low:stock.price,
          close:stock.price
        });

      }

      if(
        stock.candles.length >
        90
      ){

        stock.candles.shift();

      }

      stock.history.push(
        stock.price
      );

      if(
        stock.history.length >
        250
      ){

        stock.history.shift();

      }

    }
  );

  saveDatabase();

  updateAll();

}


/* PORTFOLIO */

function renderPortfolio(){

  const user =
    currentUser();

  if(!user){
    return;
  }

  const holdings =
    portfolioValue(user);

  portCash.textContent =
    money(user.cash);

  portHoldings.textContent =
    money(holdings);

  portTotal.textContent =
    money(
      user.cash +
      holdings
    );

  const ids =
    Object.keys(
      user.holdings
    ).filter(
      id =>
        (Number(
          user.holdings[id]
        ) || 0) > 0
    );

  portPositions.textContent =
    ids.length;

  if(!ids.length){

    portfolioRows.innerHTML=`
      <tr>
        <td
          colspan="5"
          class="small"
        >
          You don't own any stocks yet.
        </td>
      </tr>
    `;

    return;

  }

  portfolioRows.innerHTML =
    ids.map(
      id => {

        const stock =
          db.stocks.find(
            s => s.id === id
          );

        const shares =
          Number(
            user.holdings[id]
          );

        if(!stock){
          return "";
        }

        return `
          <tr>

            <td>

              <div class="stockName">
                ${escapeHtml(stock.name)}
              </div>

              <div class="ticker">
                ${stock.ticker}
              </div>

            </td>

            <td>
              ${shares.toLocaleString()}
            </td>

            <td>
              ${money(stock.price)}
            </td>

            <td>
              ${money(
                shares *
                stock.price
              )}
            </td>

            <td>

              <button
                class="tradeBtn sell"
                onclick="quickTrade('${stock.id}','sell')"
              >
                Sell
              </button>

            </td>

          </tr>
        `;

      }
    )
    .join("");

}


/* FRIENDS */

function addFriend(){

  const user =
    currentUser();

  const name =
    friendInput.value.trim();

  if(!name){

    friendMessage.textContent =
      "Enter a username.";

    return;

  }

  const friend =
    db.users.find(
      u =>
        u.username.toLowerCase() ===
        name.toLowerCase()
    );

  if(!friend){

    friendMessage.textContent =
      "Player not found.";

    return;

  }

  if(
    friend.id ===
    user.id
  ){

    friendMessage.textContent =
      "You can't add yourself.";

    return;

  }

  if(
    user.friends.includes(
      friend.id
    )
  ){

    friendMessage.textContent =
      "Already added.";

    return;

  }

  user.friends.push(
    friend.id
  );

  saveDatabase();

  friendInput.value="";

  friendMessage.textContent =
    "Friend added.";

  renderFriends();

}


function renderFriends(){

  const user =
    currentUser();

  friendList.innerHTML="";

  if(
    !user ||
    !user.friends.length
  ){

    friendList.innerHTML =
      '<div class="small">No friends added yet.</div>';

    return;

  }

  user.friends.forEach(
    id => {

      const friend =
        db.users.find(
          u => u.id === id
        );

      if(!friend){
        return;
      }

      friendList.innerHTML += `
        <div
          class="card"
          style="margin-bottom:8px"
        >

          <div class="stockName">
            ${escapeHtml(
              friend.username
            )}
          </div>

          <div class="small">
            Total wealth:
            ${money(
              totalWealth(friend)
            )}
          </div>

        </div>
      `;

    }
  );

}


/* LEADERBOARD */

function renderLeaderboard(){

  const rows =
    db.users
      .slice()
      .sort(
        (a,b) =>
          totalWealth(b) -
          totalWealth(a)
      );

  leaderRows.innerHTML =
    rows.map(
      (user,index) => {

        return `
          <tr>

            <td>
              ${index+1}
            </td>

            <td class="stockName">
              ${escapeHtml(
                user.username
              )}
            </td>

            <td>
              ${money(user.cash)}
            </td>

            <td>
              ${money(
                portfolioValue(user)
              )}
            </td>

            <td class="green">
              ${money(
                totalWealth(user)
              )}
            </td>

          </tr>
        `;

      }
    )
    .join("");

}


/* STOCK CREATION */

function createStock(){

  const user =
    currentUser();

  const name =
    stockCompany.value.trim();

  const ticker =
    stockTicker.value
      .trim()
      .toUpperCase();

  const price =
    Number(
      stockStartingPrice.value
    );

  if(!name){

    createMessage.textContent =
      "Enter a company name.";

    return;

  }

  if(
    !/^[A-Z0-9]{2,5}$/.test(
      ticker
    )
  ){

    createMessage.textContent =
      "Ticker must be 2-5 letters/numbers.";

    return;

  }

  if(
    !price ||
    price <= 0
  ){

    createMessage.textContent =
      "Enter a valid starting price.";

    return;

  }

  if(
    user.cash <
    db.settings.creationFee
  ){

    createMessage.textContent =
      "You need " +
      money(
        db.settings.creationFee
      ) +
      " to create a stock.";

    return;

  }

  const today =
    new Date()
      .toISOString()
      .slice(0,10);

  if(
    user.createdToday ===
    today
  ){

    createMessage.textContent =
      "Only one stock can be created per player per day.";

    return;

  }

  if(
    db.stocks.some(
      stock =>
        stock.ticker ===
        ticker
    )
  ){

    createMessage.textContent =
      "That ticker already exists.";

    return;

  }

  user.cash -=
    db.settings.creationFee;

  user.createdToday =
    today;

  db.stocks.push(
    makeStock(
      name,
      ticker,
      price,
      user.username
    )
  );

  saveDatabase();

  stockCompany.value="";
  stockTicker.value="";
  stockStartingPrice.value="";

  createMessage.className =
    "message green";

  createMessage.textContent =
    "Stock created successfully.";

  updateAll();

}


/* OPERATOR */

function operatorLogin(){

  const password =
    prompt(
      "Operator password:"
    );

  if(
    password !==
    OPERATOR_PASSWORD
  ){

    if(password !== null){

      alert(
        "Incorrect operator password."
      );

    }

    return;

  }

  page("operator");

  document
    .querySelectorAll(".navBtn")
    .forEach(
      button =>
        button.classList.remove(
          "active"
        )
    );

}


function renderOperator(){

  opPlayers.textContent =
    db.users.length;

  opStocks.textContent =
    db.stocks.length;

  opMarketValue.textContent =
    money(
      db.stocks.reduce(
        (total,stock) =>
          total +
          marketCap(stock),
        0
      )
    );

  const cool =
    db.stocks.find(
      stock =>
        stock.ticker ===
        "COOL"
    );

  opCoolPrice.textContent =
    money(
      cool
        ? cool.price
        : 0
    );

  opFee.value =
    db.settings.creationFee;


  operatorPlayers.innerHTML =
    db.users.map(
      user => {

        return `
          <tr>

            <td>
              ${escapeHtml(
                user.username
              )}
            </td>

            <td>
              ${money(
                user.cash
              )}
            </td>

            <td class="${
              user.banned
                ? "red"
                : "green"
            }">

              ${
                user.banned
                  ? "Banned"
                  : "Active"
              }

            </td>

            <td>

              <button
                class="tradeBtn ${
                  user.banned
                    ? "buy"
                    : "danger"
                }"
                onclick="toggleBan('${user.id}')"
              >

                ${
                  user.banned
                    ? "Unban"
                    : "Ban"
                }

              </button>

            </td>

          </tr>
        `;

      }
    )
    .join("");


  operatorStocks.innerHTML =
    db.stocks.map(
      stock => {

        return `
          <tr>

            <td>
              ${escapeHtml(
                stock.name
              )}
            </td>

            <td>
              ${escapeHtml(
                stock.ticker
              )}
            </td>

            <td>
              ${money(
                stock.price
              )}
            </td>

            <td>
              ${money(
                marketCap(stock)
              )}
            </td>

            <td>
              ${escapeHtml(
                stock.owner
              )}
            </td>

            <td>

              ${
                stock.suspended

                ? `
                  <span class="badge red">
                    Suspended
                  </span>
                `

                : `
                  <button
                    class="tradeBtn danger"
                    onclick="operatorSuspend('${stock.id}')"
                  >
                    Suspend
                  </button>
                `
              }

            </td>

          </tr>
        `;

      }
    )
    .join("");

}


function saveOperatorSettings(){

  const fee =
    Number(
      opFee.value
    );

  if(
    !Number.isFinite(fee) ||
    fee < 0
  ){

    alert(
      "Enter a valid fee."
    );

    return;

  }

  db.settings.creationFee =
    fee;

  saveDatabase();

  alert(
    "Settings saved."
  );

  updateAll();

}


function toggleBan(id){

  const user =
    db.users.find(
      u => u.id === id
    );

  if(!user){
    return;
  }

  user.banned =
    !user.banned;

  saveDatabase();

  renderOperator();

  const active =
    currentUser();

  if(
    active &&
    active.id === id &&
    user.banned
  ){

    alert(
      "This account has been banned."
    );

    logout();

  }

}


function operatorSuspend(id){

  const stock =
    db.stocks.find(
      s => s.id === id
    );

  if(!stock){
    return;
  }

  stock.suspended=true;

  saveDatabase();

  renderOperator();

  updateAll();

}


function resetDemo(){

  if(
    !confirm(
      "Erase all local accounts, stocks and progress?"
    )
  ){

    return;

  }

  localStorage.removeItem(
    DATA_KEY
  );

  localStorage.removeItem(
    SESSION_KEY
  );

  location.reload();

}


/* GLOBAL UPDATE */

function updateAll(){

  const user =
    currentUser();

  if(!user){
    return;
  }

  renderDashboard();

  renderMarket();

  renderPortfolio();

  renderFriends();

  renderLeaderboard();

  if(
    !operatorPage
      .classList
      .contains("hidden")
  ){

    renderOperator();

  }


  if(selectedStock){

    const fresh =
      db.stocks.find(
        stock =>
          stock.id ===
          selectedStock.id
      );

    if(fresh){

      selectedStock =
        fresh;

      selectedPrice.textContent =
        money(
          fresh.price
        );

      const change =
        percentChange(fresh);

      selectedChange.textContent =
        (change >= 0
          ? "+"
          : "") +
        change.toFixed(2) +
        "%";

      selectedChange.className =
        change >= 0
          ? "green"
          : "red";

      selectedMarketCap.textContent =
        money(
          marketCap(fresh)
        );

      selectedHolders.textContent =
        shareholders(
          fresh
        ).toLocaleString();

      selectedShares.textContent =
        totalSharesOwned(
          fresh
        ).toLocaleString();

      selectedStatus.textContent =
        fresh.suspended
          ? "Suspended"
          : "Trading";

    }

  }

  drawChart();

}


window.addEventListener(
  "resize",
  drawChart
);


/* BOOT */

(function(){

  const user =
    currentUser();

  if(
    user &&
    !user.banned
  ){

    startGame();

  }

})();

</script>

</body>
</html>

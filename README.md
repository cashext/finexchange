<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>DemoPay Exchange</title>

<style>
*{box-sizing:border-box}
body{
 margin:0;
 font-family:Arial,sans-serif;
 background:#f4f6fa;
 color:#172033
}
.demo{
 background:#172033;
 color:white;
 text-align:center;
 padding:8px;
 font-size:12px
}
header{
 background:white;
 padding:18px 25px;
 display:flex;
 justify-content:space-between;
 align-items:center;
 border-bottom:1px solid #ddd
}
.logo{font-size:22px;font-weight:bold}
nav{
 background:#fff;
 padding:10px;
 display:flex;
 gap:8px;
 overflow:auto;
 border-bottom:1px solid #ddd
}
nav button{
 border:0;
 background:#f0f2f6;
 padding:10px 16px;
 border-radius:8px;
 cursor:pointer
}
nav button:hover{background:#172033;color:white}
main{max-width:1200px;margin:auto;padding:25px}
.page{display:none}
.page.active{display:block}

.card{
 background:white;
 border:1px solid #e1e5ec;
 border-radius:15px;
 padding:20px;
 margin-bottom:18px
}
.dark{
 background:#172033;
 color:white
}
.balance{
 font-size:38px;
 font-weight:bold;
 margin:20px 0
}
.grid{
 display:grid;
 grid-template-columns:repeat(4,1fr);
 gap:15px
}
.coin{
 background:white;
 border:1px solid #e1e5ec;
 border-radius:12px;
 padding:15px
}
.coin b{font-size:18px}
.green{color:#16835d}
.red{color:#d04747}

button,.btn{
 cursor:pointer;
 border:0;
 border-radius:8px;
 padding:11px 16px;
 font-weight:bold
}
.primary{
 background:#172033;
 color:white
}
.secondary{
 background:white;
 border:1px solid #ddd
}

input,select{
 width:100%;
 padding:12px;
 border:1px solid #d8dde7;
 border-radius:8px;
 margin:6px 0 14px
}
label{
 font-size:13px;
 font-weight:bold
}
.two{
 display:grid;
 grid-template-columns:1fr 1fr;
 gap:15px
}

table{
 width:100%;
 border-collapse:collapse;
 background:white
}
th,td{
 padding:13px;
 border-bottom:1px solid #eee;
 text-align:left
}
th{
 font-size:12px;
 color:#778196
}
.table{
 overflow:auto
}
.search{
 max-width:400px
}
.links{
 display:flex;
 gap:10px;
 flex-wrap:wrap
}
.links a{
 text-decoration:none;
 color:white;
 background:#172033;
 padding:12px 17px;
 border-radius:8px
}
.fakecard{
 max-width:450px;
 min-height:240px;
 border-radius:18px;
 padding:25px;
 color:white;
 background:linear-gradient(135deg,#263552,#10182a);
 display:flex;
 flex-direction:column;
 justify-content:space-between
}
.fake-number{
 font-size:22px;
 letter-spacing:3px
}
.result{
 background:#f1f4f8;
 padding:18px;
 border-radius:10px;
 margin-top:15px
}
.notice{
 background:#fff7df;
 border:1px solid #ead69b;
 padding:12px;
 border-radius:8px;
 margin:10px 0
}
footer{
 text-align:center;
 padding:30px;
 color:#8992a5;
 font-size:12px
}

@media(max-width:800px){
 .grid{grid-template-columns:repeat(2,1fr)}
 .two{grid-template-columns:1fr}
}
@media(max-width:500px){
 .grid{grid-template-columns:1fr}
 main{padding:12px}
 .balance{font-size:30px}
}
</style>
</head>

<body>

<div class="demo">
DEMO / TEST ONLY — No real money, banking or card transactions
</div>

<header>
 <div class="logo">◈ DemoPay Exchange</div>
 <div>Client Account</div>
</header>

<nav>
 <button onclick="show('dashboard')">Dashboard</button>
 <button onclick="show('markets')">Markets</button>
 <button onclick="show('exchange')">Exchange</button>
 <button onclick="show('send')">Send Payment</button>
 <button onclick="show('history')">History</button>
 <button onclick="show('profile')">Profile</button>
</nav>

<main>

<!-- DASHBOARD -->
<section id="dashboard" class="page active">

<div class="card dark">
 <small>AVAILABLE DEMO BALANCE</small>
 <div class="balance">$12,450.00</div>
 <button class="secondary" onclick="show('send')">
 Send Demo Payment
 </button>
 <button class="secondary" onclick="show('exchange')">
 Exchange Currency
 </button>
</div>

<div class="grid">

<div class="card">
 <small>USD Balance</small>
 <h2>$12,450</h2>
</div>

<div class="card">
 <small>PKR Reference</small>
 <h2>₨3,463,874</h2>
</div>

<div class="card">
 <small>Bitcoin Demo</small>
 <h2>0.050 BTC</h2>
</div>

<div class="card">
 <small>Transactions</small>
 <h2 id="count">4</h2>
</div>

</div>

<h2>Popular Crypto</h2>
<div id="dashboardCoins" class="grid"></div>

</section>


<!-- MARKETS -->
<section id="markets" class="page">

<h2>Crypto & Currency Markets</h2>

<input
 class="search"
 id="search"
 placeholder="Search Bitcoin, BTC, EUR, PKR..."
 oninput="renderMarkets()"
>

<div class="table">

<table>
<thead>
<tr>
<th>Asset</th>
<th>Symbol</th>
<th>Price</th>
<th>24h</th>
<th>Market Cap</th>
</tr>
</thead>

<tbody id="cryptoTable"></tbody>
</table>

</div>

<br>

<div class="card">
<h3>Full Cryptocurrency Website</h3>
<p>
For the complete cryptocurrency market, charts and thousands of coins,
open an external market website.
</p>

<div class="links">
<a href="https://www.coingecko.com/" target="_blank">
Open CoinGecko ↗
</a>

<a href="https://coinmarketcap.com/" target="_blank">
Open CoinMarketCap ↗
</a>
</div>
</div>

<h2>Foreign Currency Rates</h2>

<div class="table">
<table>
<thead>
<tr>
<th>Currency</th>
<th>Symbol</th>
<th>Units per USD</th>
<th>USD per Unit</th>
</tr>
</thead>
<tbody id="fxTable"></tbody>
</table>
</div>

</section>


<!-- EXCHANGE -->
<section id="exchange" class="page">

<h2>Currency Exchange</h2>

<div class="card">

<label>Amount</label>
<input id="amount" type="number" value="1000">

<div class="two">

<div>
<label>From</label>
<select id="from"></select>
</div>

<div>
<label>To</label>
<select id="to"></select>
</div>

</div>

<button class="primary" onclick="convert()">
Calculate Exchange
</button>

<div class="result">
<small>Estimated Result</small>
<h2 id="result">—</h2>
<p id="note"></p>
</div>

</div>

</section>


<!-- SEND PAYMENT -->
<section id="send" class="page">

<h2>Send Demo Payment</h2>

<div class="card">

<div class="notice">
This creates only a local demo transaction.
No real payment is sent.
</div>

<label>Recipient</label>
<input id="recipient" placeholder="Example: Alex Khan">

<label>Demo Card Number</label>
<input
 id="card"
 placeholder="4242 4242 4242 4242"
 maxlength="19"
>

<label>Amount USD</label>
<input id="sendAmount" type="number" value="100">

<label>Reference</label>
<input id="reference" placeholder="Invoice / Note">

<button class="primary" onclick="sendPayment()">
Create Demo Payment
</button>

</div>

</section>


<!-- HISTORY -->
<section id="history" class="page">

<h2>Payment History</h2>

<div class="card table">

<table>
<thead>
<tr>
<th>Date</th>
<th>Recipient</th>
<th>Reference</th>
<th>Amount</th>
<th>Status</th>
</tr>
</thead>

<tbody id="historyTable">
</tbody>

</table>

</div>

</section>


<!-- PROFILE -->
<section id="profile" class="page">

<h2>Profile & Demo Card</h2>

<div class="card">

<h2>Client Account</h2>

<p>Email: client@example.test</p>
<p>Account: DEMO-2048-4821</p>
<p>Country: Pakistan</p>

</div>

<div class="fakecard">

<b>DemoPay</b>

<div class="fake-number">
4242 4242 4242 4821
</div>

<div>
CLIENT ACCOUNT
&nbsp;&nbsp;&nbsp;&nbsp;
12/30
</div>

</div>

</section>

<footer>
DemoPay Exchange — Front-end demonstration only
</footer>

</main>


<script>

/* =========================
   CRYPTO DATA
   Manual / No API
========================= */

const crypto = [

["Bitcoin","BTC",87065.80,3.5,1749.36],
["Ethereum","ETH",2735.11,2.0,333.94],
["Tether","USDT",0.9999,0.0,184.04],
["BNB","BNB",779.23,1.6,103.77],
["XRP","XRP",1.53,3.1,96.35],
["USDC","USDC",0.9999,0.0,73.93],
["Solana","SOL",121.81,4.1,71.62],
["TRON","TRX",0.3348,0.6,31.80],
["Dogecoin","DOGE",0.12,2.1,18.20],
["Cardano","ADA",0.58,1.4,20.50],
["Avalanche","AVAX",20.10,2.2,8.30],
["Chainlink","LINK",14.20,2.8,8.90],
["Polkadot","DOT",4.10,1.7,6.20],
["Polygon","POL",0.25,1.2,2.70],
["Litecoin","LTC",91.20,1.9,6.80],
["Shiba Inu","SHIB",0.000012,1.1,7.10],
["Bitcoin Cash","BCH",510,2.4,10.10],
["Stellar","XLM",0.32,1.5,9.50],
["Cosmos","ATOM",4.80,1.8,1.90],
["Uniswap","UNI",8.20,2.3,4.90]

];


/* =========================
   CURRENCY DATA
========================= */

const currencies = [

["USD","$","1"],
["EUR","€","0.8659"],
["GBP","£","0.7469"],
["PKR","₨","278.3839"],
["AED","د.إ","3.6725"],
["SAR","﷼","3.7500"],
["JPY","¥","160.4875"],
["CNY","¥","6.7751"],
["CAD","C$","1.37"],
["AUD","A$","1.53"],
["CHF","Fr","0.81"],
["INR","₹","86.5"],
["TRY","₺","41.5"],
["NZD","NZ$","1.75"],
["SGD","S$","1.28"],
["HKD","HK$","7.80"]

];


/* =========================
   PAGE NAVIGATION
========================= */

function show(page){

 document.querySelectorAll(".page")
 .forEach(x=>x.classList.remove("active"));

 document.getElementById(page)
 .classList.add("active");

 window.scrollTo(0,0);
}


/* =========================
   DASHBOARD COINS
========================= */

function renderDashboard(){

 let html="";

 crypto.slice(0,8).forEach(c=>{

 html+=`

 <div class="coin">

 <b>${c[0]}</b>
 <small>${c[1]}</small>

 <h3>$${c[2].toLocaleString()}</h3>

 <span class="${c[3]>=0?'green':'red'}">
 ${c[3]>=0?'+':''}${c[3]}%
 </span>

 </div>

 `;

 });

 document.getElementById("dashboardCoins")
 .innerHTML=html;

}


/* =========================
   MARKET TABLE
========================= */

function renderMarkets(){

 let search=
 document.getElementById("search")
 .value.toLowerCase();

 let html="";

 crypto
 .filter(c=>
 (c[0]+" "+c[1])
 .toLowerCase()
 .includes(search)
 )
 .forEach(c=>{

 html+=`

 <tr>

 <td><b>${c[0]}</b></td>

 <td>${c[1]}</td>

 <td>
 $${c[2].toLocaleString()}
 </td>

 <td class="${c[3]>=0?'green':'red'}">
 ${c[3]>=0?'+':''}${c[3]}%
 </td>

 <td>
 $${c[4]}B
 </td>

 </tr>

 `;

 });

 document.getElementById("cryptoTable")
 .innerHTML=html;


 let fx="";

 currencies.forEach(c=>{

 fx+=`

 <tr>

 <td>${c[0]}</td>

 <td>${c[1]}</td>

 <td>${c[2]}</td>

 <td>${(1/Number(c[2])).toFixed(6)}</td>

 </tr>

 `;

 });

 document.getElementById("fxTable")
 .innerHTML=fx;

}


/* =========================
   EXCHANGE SELECT BOXES
========================= */

function setupCurrency(){

 let from=document.getElementById("from");
 let to=document.getElementById("to");

 currencies.forEach(c=>{

 let option=
 `<option value="${c[0]}">
 ${c[0]}
 </option>`;

 from.innerHTML+=option;
 to.innerHTML+=option;

 });

 from.value="USD";
 to.value="PKR";

 convert();

}


/* =========================
   CONVERTER
========================= */

function convert(){

 let amount=
 Number(document.getElementById("amount").value);

 let fromCode=
 document.getElementById("from").value;

 let toCode=
 document.getElementById("to").value;

 let fromRate=
 Number(currencies.find(c=>c[0]===fromCode)[2]);

 let toRate=
 Number(currencies.find(c=>c[0]===toCode)[2]);

 let usd=amount/fromRate;

 let result=usd*toRate;

 let symbol=
 currencies.find(c=>c[0]===toCode)[1];

 document.getElementById("result")
 .innerText=
 symbol+
 result.toLocaleString(
 undefined,
 {maximumFractionDigits:6}
 );

 document.getElementById("note")
 .innerText=
 `${amount} ${fromCode} = ${result.toFixed(6)} ${toCode}`;

}


/* =========================
   DEMO PAYMENT
========================= */

function sendPayment(){

 let recipient=
 document.getElementById("recipient").value;

 let amount=
 Number(document.getElementById("sendAmount").value);

 let reference=
 document.getElementById("reference").value;

 if(!recipient || !amount){

 alert("Please enter recipient and amount.");

 return;

 }

 let history=
 JSON.parse(
 localStorage.getItem("demoHistory") || "[]"
 );

 history.unshift({

 date:new Date().toLocaleDateString(),

 recipient:recipient,

 reference:reference || "Demo Payment",

 amount:amount,

 status:"DEMO"

 });

 localStorage.setItem(
 "demoHistory",
 JSON.stringify(history)
 );

 alert("Demo payment created.");

 document.getElementById("recipient").value="";
 document.getElementById("card").value="";
 document.getElementById("sendAmount").value="";
 document.getElementById("reference").value="";

 loadHistory();

 show("history");

}


/* =========================
   PAYMENT HISTORY
========================= */

function loadHistory(){

 let history=
 JSON.parse(
 localStorage.getItem("demoHistory") || "[]"
 );

 let html="";

 let defaultHistory=[

 {
 date:"10/02/2026",
 recipient:"Demo Merchant",
 reference:"Coffee Order",
 amount:24.50,
 status:"DEMO"
 },

 {
 date:"10/01/2026",
 recipient:"Alex Khan",
 reference:"Test Invoice",
 amount:120,
 status:"DEMO"
 },

 {
 date:"09/29/2026",
 recipient:"Sample Store",
 reference:"UI Test",
 amount:75,
 status:"DEMO"
 },

 {
 date:"09/27/2026",
 recipient:"Client Account",
 reference:"Internal Transfer",
 amount:250,
 status:"DEMO"
 }

 ];

 let all=
 history.length ? history : defaultHistory;

 all.forEach(x=>{

 html+=`

 <tr>

 <td>${x.date}</td>

 <td>${x.recipient}</td>

 <td>${x.reference}</td>

 <td>$${Number(x.amount).toFixed(2)}</td>

 <td class="green">${x.status}</td>

 </tr>

 `;

 });

 document.getElementById("historyTable")
 .innerHTML=html;

 document.getElementById("count")
 .innerText=all.length;

}


/* =========================
   START
========================= */

renderDashboard();

renderMarkets();

setupCurrency();

loadHistory();

</script>

</body>
</html>
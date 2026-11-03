<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Giga Earn BD</title>

<script src="https://telegram.org/js/telegram-web-app.js"></script>
<script src="https://ad.gigapub.tech/script?id=8947"></script>

<style>
*{box-sizing:border-box}
body{
 margin:0;background:#0b1220;color:white;
 font-family:Arial,sans-serif;padding:18px;
}
.app{max-width:480px;margin:auto;padding-bottom:80px}
.header{display:flex;justify-content:space-between;align-items:center}
.logo{font-size:23px;font-weight:bold;color:#4ce0a1}
.profile{background:#1c293b;padding:10px 14px;border-radius:30px}
.card{
 background:#182438;border:1px solid #293a52;
 border-radius:18px;padding:20px;margin-top:18px;
}
.balance{font-size:36px;font-weight:bold;color:#4ce0a1}
.small{color:#aab8ca;font-size:13px}
button{
 border:0;padding:14px;border-radius:12px;
 background:#36d99a;color:#09251b;
 font-weight:bold;font-size:16px;width:100%;
}
.adbtn{margin-top:15px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.item{text-align:center;background:#182438;padding:20px 8px;
 border-radius:15px;margin-top:15px}
.item .emoji{font-size:27px}
.item p{margin-bottom:0}
.nav{
 position:fixed;bottom:0;left:0;right:0;
 background:#182438;display:flex;justify-content:space-around;
 padding:14px 5px;border-top:1px solid #304157;
}
.nav button{width:auto;background:none;color:white;padding:5px;font-size:12px}
#status{color:#aab8ca;font-size:13px;line-height:1.5}
</style>
</head>

<body>
<div class="app">

<div class="header">
 <div class="logo">⚡ GIGA EARN BD</div>
 <div class="profile">👤 <span id="name">User</span></div>
</div>

<div class="card">
 <p class="small">💰 TOTAL BALANCE</p>
 <div class="balance">৳ <span id="balance">0.00</span></div>
 <p class="small">আপনার বর্তমান আয়</p>
</div>

<div class="card">
 <h3>🎬 Watch & Earn</h3>
 <p class="small">বিজ্ঞাপন দেখে রিওয়ার্ড সংগ্রহ করুন।</p>
 <button class="adbtn" id="watchBtn" onclick="watchAd()">
 ▶ WATCH ADS
 </button>
 <p id="status">বিজ্ঞাপন দেখতে বাটনে ক্লিক করুন।</p>
</div>

<h3>📱 Dashboard</h3>
<div class="grid">
 <div class="item">
  <div class="emoji">💰</div>
  <b>My Wallet</b>
  <p class="small">আমার ব্যালেন্স</p>
 </div>
 <div class="item">
  <div class="emoji">👥</div>
  <b>Referral</b>
  <p class="small">বন্ধু আমন্ত্রণ</p>
 </div>
 <div class="item">
  <div class="emoji">📜</div>
  <b>History</b>
  <p class="small">লেনদেন</p>
 </div>
 <div class="item">
  <div class="emoji">👤</div>
  <b>Profile</b>
  <p class="small">আমার অ্যাকাউন্ট</p>
 </div>
</div>

<div class="card">
 <h3>🌟 Welcome to Giga Earn BD</h3>
 <p class="small">
 Giga Earn BD-তে আপনাকে স্বাগতম।
 বিজ্ঞাপন দেখুন এবং আপনার রিওয়ার্ড উপভোগ করুন।
 </p>
</div>

</div>

<div class="nav">
 <button onclick="home()">🏠<br>Home</button>
 <button onclick="wallet()">💰<br>Wallet</button>
 <button onclick="refer()">👥<br>Refer</button>
 <button onclick="profile()">👤<br>Profile</button>
</div>

<script>
const tg=window.Telegram?.WebApp;
tg?.ready();
tg?.expand();

const user=tg?.initDataUnsafe?.user;

if(user){
 document.getElementById("name").textContent=
 user.first_name || "User";
}

let busy=false;

async function watchAd(){
 const btn=document.getElementById("watchBtn");
 const status=document.getElementById("status");

 if(busy)return;

 if(typeof window.showGiga!=="function"){
  status.textContent="Ad loading... Please try again.";
  return;
 }

 busy=true;
 btn.disabled=true;
 status.textContent="Advertisement loading...";

 try{
  await window.showGiga();
  status.textContent=
  "Advertisement completed. Reward verification is pending.";
 }catch(e){
  status.textContent="Advertisement not completed. Try again.";
 }finally{
  busy=false;
  btn.disabled=false;
 }
}

function home(){
 window.scrollTo({top:0,behavior:"smooth"});
}
function wallet(){
 alert("Wallet information");
}
function refer(){
 if(!user)return alert("Open through Telegram");
 const link="https://t.me/YOUR_BOT_USERNAME?startapp="+user.id;
 const url="https://t.me/share/url?url="+encodeURIComponent(link);
 tg?.openTelegramLink(url);
}
function profile(){
 alert("User: "+(user?.first_name||"Guest"));
}
</script>
</body>
</html>

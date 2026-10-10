
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#063a29">
<title>PNG Ports - Member Login</title>
<style>
*{box-sizing:border-box}
body{
  margin:0;font-family:Arial,sans-serif;
  background:#f0f4f0;color:#1c2b22;
  min-height:100vh;display:flex;align-items:center;
  justify-content:center;padding:18px
}
.app{width:100%;max-width:410px}
.brand{text-align:center;margin-bottom:22px}
.logo{
  width:68px;height:68px;border-radius:20px;
  margin:auto;background:#0a5037;color:#e6c25d;
  display:grid;place-items:center;font-size:35px;
  border:2px solid #d8b64f
}
.brand h1{font-size:23px;color:#073b2a;margin:12px 0 3px}
.brand p{font-size:12px;color:#75847a;margin:0}
.card{
  background:white;padding:25px;border-radius:19px;
  box-shadow:0 10px 35px #173c2512;
  border:1px solid #e1e8e1
}
.card h2{font-size:21px;margin:0 0 5px;color:#073b2a}
.subtitle{font-size:13px;color:#7b887f;margin:0 0 22px}
label{display:block;font-size:12px;font-weight:bold;margin:14px 0 7px}
input{
  width:100%;padding:13px;border:1px solid #d8e1d9;
  border-radius:9px;font-size:14px;outline:none
}
input:focus{border-color:#0b6847}
button{
  width:100%;border:0;border-radius:9px;padding:14px;
  background:#073b2a;color:white;font-weight:bold;
  font-size:14px;margin-top:18px;cursor:pointer
}
button.secondary{background:#edf4ee;color:#0b563a;margin-top:10px}
.message{font-size:12px;margin-top:13px;line-height:1.5}
.sample{
  background:#f4f7f3;border-radius:10px;padding:13px;
  font-size:12px;margin-top:17px;line-height:1.8
}
.sample strong{color:#073b2a}
.hidden{display:none}
.dashboard-header{
  background:linear-gradient(135deg,#063a29,#0b5b3d);
  color:white;border-radius:17px;padding:22px;margin-bottom:14px
}
.dashboard-header h2{margin:0 0 5px}
.dashboard-header p{font-size:12px;color:#d5e5d9;margin:0}
.balance{
  background:#e6c25d;border-radius:13px;padding:17px;
  margin-top:18px;color:#1e3024
}
.balance small{font-size:11px}
.balance h1{margin:5px 0;font-size:30px}
.tiles{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.tile{
  background:white;border:1px solid #e1e8e1;
  padding:17px;border-radius:12px
}
.tile small{font-size:11px;color:#75847a}
.tile strong{display:block;font-size:20px;color:#073b2a;margin-top:8px}
.logout{background:white;color:#073b2a;border:1px solid #cbd9ce}
.foot{text-align:center;color:#8a968d;font-size:10px;margin-top:17px}
</style>
</head>
<body>
<div class="app">

  <div class="brand">
    <div class="logo">⚓</div>
    <h1>PNG PORTS</h1>
    <p>MEMBER APPLICATION</p>
  </div>

  <section class="card" id="loginScreen">
    <h2>Member login</h2>
    <p class="subtitle">Sign in to your trial member dashboard.</p>

    <form id="loginForm">
      <label for="phone">Mobile number</label>
      <input id="phone" type="tel" placeholder="Enter sample phone number"
        autocomplete="off" required>

      <label for="password">Password</label>
      <input id="password" type="password" placeholder="Enter trial password"
        autocomplete="off" required>

      <button type="submit">Log in</button>
    </form>

    <div class="sample">
      <strong>Trial member details</strong><br>
      Phone: <strong>70000001</strong><br>
      Password: <strong>Trial1234</strong>
    </div>

    <p class="message" id="loginMessage" role="status"></p>
  </section>

  <section class="hidden" id="dashboard">
    <div class="dashboard-header">
      <h2>Welcome, Trial Member!</h2>
      <p>Ordinary member · Trial account</p>
      <div class="balance">
        <small>Sample wallet balance</small>
        <h1>K 0.00</h1>
        <small>Demo balance only</small>
      </div>
    </div>

    <div class="tiles">
      <div class="tile">
        <small>Today's earnings</small>
        <strong>K 0.00</strong>
      </div>
      <div class="tile">
        <small>VIP level</small>
        <strong>None</strong>
      </div>
      <div class="tile">
        <small>Deposits</small>
        <strong>K 0.00</strong>
      </div>
      <div class="tile">
        <small>Withdrawals</small>
        <strong>K 0.00</strong>
      </div>
    </div>

    <div class="card" style="margin-top:14px">
      <h2>Member services</h2>
      <p class="subtitle">Explore the trial account features.</p>
      <button onclick="alert('VIP membership preview only.')">View VIP levels</button>
      <button class="secondary"
        onclick="alert('No real deposit or withdrawal is connected.')">
        Wallet
      </button>
      <button class="secondary"
        onclick="alert('Lucky wheel preview only.')">
        Lucky spin
      </button>
      <button class="logout" onclick="logout()">Log out</button>
    </div>
  </section>

  <div class="foot">
    Independent app prototype · Trial data is not a real financial account.
  </div>
</div>

<script>
const trialPhone = "70000001";
const trialPassword = "Trial1234";

document.getElementById("loginForm").addEventListener("submit", function(event) {
  event.preventDefault();

  const phone = document.getElementById("phone").value.trim();
  const password = document.getElementById("password").value;
  const message = document.getElementById("loginMessage");

  if (phone === trialPhone && password === trialPassword) {
    document.getElementById("loginScreen").classList.add("hidden");
    document.getElementById("dashboard").classList.remove("hidden");
    message.textContent = "";
  } else {
    message.style.color = "#b42318";
    message.textContent =
      "Those details do not match. Use the trial details shown on this screen.";
  }
});

function logout() {
  document.getElementById("dashboard").classList.add("hidden");
  document.getElementById("loginScreen").classList.remove("hidden");
  document.getElementById("password").value = "";
}
</script>
</body>
</html>

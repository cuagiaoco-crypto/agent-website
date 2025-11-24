# agent-website
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Agent System</title>

<style>
body { margin: 0; font-family: Arial, sans-serif; background: #f5f5f5; }

/* ----- LOGIN PAGE ----- */
#loginPage {
  padding: 25px;
  max-width: 400px;
  margin: auto;
}
.login-box {
  background: #fff;
  padding: 25px;
  border-radius: 10px;
  box-shadow: 0 0 10px #ddd;
}
input {
  width: 100%;
  padding: 12px;
  margin-top: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
}
button {
  width: 100%;
  padding: 12px;
  margin-top: 15px;
  background: #007bff;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 17px;
}

/* ----- DASHBOARD ----- */
#dashboard { display: none; padding: 15px; }
.card {
  background: #fff;
  padding: 18px;
  border-radius: 10px;
  box-shadow: 0 0 5px #ccc;
  margin-bottom: 15px;
}
.agent-item {
  background: #fff;
  padding: 12px;
  border-radius: 8px;
  margin-top: 8px;
  box-shadow: 0 0 3px #ccc;
}
</style>
</head>

<body>

<!-- LOGIN PAGE -->
<div id="loginPage">
  <h2 style="text-align:center">Đăng Nhập Agent</h2>
  <div class="login-box">
    <input id="username" placeholder="Tài khoản" />
    <input id="password" placeholder="Mật khẩu" type="password" />
    <button onclick="login()">Đăng nhập</button>
  </div>
</div>

<!-- DASHBOARD PAGE -->
<div id="dashboard">
  <h2>Agent Dashboard</h2>

  <div class="card">
    <h3>Tổng quan</h3>
    <p><b>Tổng nạp:</b> <span id="totalDeposit">12,500,000đ</span></p>
    <p><b>Lợi nhuận ròng:</b> <span id="netProfit">3,200,000đ</span></p>
  </div>

  <h3>Danh sách thành viên</h3>
  <div id="agentList"></div>
</div>

<script>
let data = [
  { name: "User01", deposit: "2,000,000đ", profit: "+500,000đ" },
  { name: "User02", deposit: "5,000,000đ", profit: "+900,000đ" },
  { name: "User03", deposit: "3,000,000đ", profit: "+700,000đ" }
];

function login() {
  let u = document.getElementById("username").value.trim();
  let p = document.getElementById("password").value.trim();

  if (u === "adminvn77" && p === "adminvn77") {
    document.getElementById("loginPage").style.display = "none";
    document.getElementById("dashboard").style.display = "block";
    loadAgents();
  } else {
    alert("Sai tài khoản hoặc mật khẩu!");
  }
}

function loadAgents() {
  let box = document.getElementById("agentList");
  box.innerHTML = "";

  data.forEach(a => {
    box.innerHTML += `
      <div class="agent-item">
        <b>${a.name}</b><br>
        Nạp: ${a.deposit}<br>
        Lợi nhuận: ${a.profit}
      </div>
    `;
  });
}
</script>

</body>
</html>

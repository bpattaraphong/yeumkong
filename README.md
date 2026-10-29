
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ยืมดี | ระบบยืม-คืนอุปกรณ์</title>
  <style>
    :root {
      --primary: #5267df;
      --light: #eef1ff;
      --bg: #f6f7fc;
      --text: #242943;
      --muted: #707790;
      --border: #e4e7f0;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: Tahoma, Arial, sans-serif;
      background: var(--bg);
      color: var(--text);
    }

    header {
      background: white;
      border-bottom: 1px solid var(--border);
      padding: 16px 5%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .brand { font-size: 24px; font-weight: bold; color: var(--primary); }
    .brand small { display: block; font-size: 12px; color: var(--muted); margin-top: 4px; }

    nav { display: flex; gap: 8px; flex-wrap: wrap; }

    button {
      cursor: pointer;
      border: 0;
      border-radius: 10px;
      padding: 11px 15px;
      font: inherit;
      font-size: 14px;
    }

    .nav-btn { background: white; color: var(--text); }
    .nav-btn.active { background: var(--light); color: var(--primary); font-weight: bold; }
    .primary { background: var(--primary); color: white; }
    .secondary { background: #eef0f6; color: var(--text); }
    .danger { background: #ffe9e9; color: #b42318; }

    main { max-width: 1100px; margin: 28px auto; padding: 0 16px 40px; }
    .hero {
      background: linear-gradient(135deg, #5267df, #8a72ed);
      color: white;
      padding: 30px;
      border-radius: 20px;
      margin-bottom: 22px;
    }

    .hero h1 { margin: 0 0 10px; font-size: 28px; }
    .hero p { margin: 0; line-height: 1.8; }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 14px;
      margin-bottom: 22px;
    }

    .stat, .panel, .item {
      background: white;
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 20px;
    }

    .stat strong { display: block; font-size: 28px; margin-top: 8px; }
    .muted { color: var(--muted); font-size: 13px; }
    .panel { margin-bottom: 20px; }
    h2 { font-size: 20px; margin: 0 0 18px; }
    h3 { margin: 0 0 8px; font-size: 17px; }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 15px;
    }

    .field { display: flex; flex-direction: column; gap: 7px; }
    .field.full { grid-column: 1 / -1; }
    label { font-size: 14px; font-weight: bold; }

    input, select, textarea {
      width: 100%;
      border: 1px solid #d9ddeb;
      border-radius: 10px;
      padding: 12px;
      font: inherit;
      background: white;
      color: var(--text);
    }

    textarea { min-height: 85px; resize: vertical; }
    input:focus, select:focus, textarea:focus {
      outline: 2px solid #dce1ff;
      border-color: var(--primary);
    }

    .items-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 14px;
    }

    .item-icon { font-size: 34px; margin-bottom: 12px; }
    .item p { color: var(--muted); font-size: 13px; line-height: 1.6; }
    .item button { width: 100%; margin-top: 8px; }

    .status {
      display: inline-block;
      padding: 5px 9px;
      border-radius: 20px;
      font-size: 12px;
      background: #fff2cc;
      color: #8a5a00;
    }

    .status.approved { background: #e1f8e8; color: #167341; }
    .status.returned { background: #e5edff; color: #3154bc; }
    .status.rejected { background: #ffe5e5; color: #b42318; }

    .request {
      padding: 15px 0;
      border-bottom: 1px solid var(--border);
    }

    .request:last-child { border-bottom: 0; }
    .request p { line-height: 1.7; overflow-wrap: anywhere; }
    .actions { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 10px; }
    .actions button { padding: 9px 12px; }

    .hidden { display: none !important; }
    .notice { font-size: 13px; color: var(--muted); line-height: 1.7; }
    footer { text-align: center; padding: 25px; color: var(--muted); font-size: 13px; }

    @media (max-width: 700px) {
      .stats { grid-template-columns: 1fr; }
      .items-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
      .form-grid { grid-template-columns: 1fr; }
      .field.full { grid-column: auto; }
      .hero h1 { font-size: 23px; }
      header { padding: 14px 16px; }
    }

    @media (max-width: 420px) {
      .items-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
  <header>
    <div class="brand">
      📦 ยืมดี
      <small>ระบบยืม–คืนอุปกรณ์ห้องเรียน</small>
    </div>
    <nav>
      <button class="nav-btn active" data-page="home">หน้าแรก</button>
      <button class="nav-btn" data-page="borrow">ยืมอุปกรณ์</button>
      <button class="nav-btn" data-page="admin">ผู้ดูแลระบบ</button>
    </nav>
  </header>

  <main>
    <section id="home">
      <div class="hero">
        <h1>ยืมง่าย คืนสะดวก 💜</h1>
        <p>ศูนย์กลางการยืม–คืนอุปกรณ์การเรียน<br>
        เลือกอุปกรณ์ กรอกข้อมูล และติดตามสถานะได้ในที่เดียว</p>
        <br>
        <button class="secondary" onclick="showPage('borrow')">เริ่มยืมอุปกรณ์ →</button>
      </div>

      <div class="stats">
        <div class="stat">
          <span class="muted">รายการอุปกรณ์</span>
          <strong id="totalItems">6</strong>
        </div>
        <div class="stat">
          <span class="muted">คำขอยืมทั้งหมด</span>
          <strong id="totalRequests">0</strong>
        </div>
        <div class="stat">
          <span class="muted">รออนุมัติ</span>
          <strong id="pendingRequests">0</strong>
        </div>
      </div>

      <section class="panel">
        <h2>🧰 อุปกรณ์ที่มีให้ยืม</h2>
        <div id="itemsGrid" class="items-grid"></div>
      </section>
    </section>

    <section id="borrow" class="hidden">
      <div class="panel">
        <h2>📝 แบบฟอร์มขอยืมอุปกรณ์</h2>
        <form id="borrowForm" class="form-grid">
          <div class="field">
            <label for="studentName">ชื่อ–นามสกุล *</label>
            <input id="studentName" required maxlength="100" placeholder="กรอกชื่อผู้ยืม">
          </div>
          <div class="field">
            <label for="studentClass">ชั้น / ห้อง *</label>
            <input id="studentClass" required maxlength="50" placeholder="เช่น ม.2/1">
          </div>
          <div class="field">
            <label for="studentId">เลขประจำตัวนักเรียน *</label>
            <input id="studentId" required maxlength="30" placeholder="กรอกเลขประจำตัว">
          </div>
          <div class="field">
            <label for="contact">ช่องทางติดต่อ</label>
            <input id="contact" maxlength="100" placeholder="เช่น อีเมลหรือเบอร์โทร">
          </div>
          <div class="field full">
            <label for="equipment">เลือกอุปกรณ์ *</label>
            <select id="equipment" required>
              <option value="">-- เลือกอุปกรณ์ --</option>
            </select>
          </div>
          <div class="field">
            <label for="quantity">จำนวนที่ต้องการ *</label>
            <input id="quantity" type="number" min="1" max="99" value="1" required>
          </div>
          <div class="field">
            <label for="borrowDate">วันที่ต้องการยืม *</label>
            <input id="borrowDate" type="date" required>
          </div>
          <div class="field">
            <label for="returnDate">วันที่กำหนดคืน *</label>
            <input id="returnDate" type="date" required>
          </div>
          <div class="field full">
            <label for="purpose">วัตถุประสงค์ในการยืม *</label>
            <textarea id="purpose" required maxlength="500" placeholder="ระบุว่าจะนำไปใช้งานอะไร"></textarea>
          </div>
          <div class="field full">
            <button class="primary" type="submit">ส่งคำขอยืมอุปกรณ์</button>
            <p class="notice">หลังส่งคำขอ กรุณารอผู้ดูแลระบบอนุมัติก่อนรับอุปกรณ์</p>
          </div>
        </form>
      </div>
    </section>

    <section id="admin" class="hidden">
      <div class="panel" id="loginPanel">
        <h2>🔐 เข้าสู่ระบบผู้ดูแล</h2>
        <p class="notice">โหมดสาธิตเท่านั้น รหัสผ่านที่ตั้งไว้ใน HTML ไม่ปลอดภัยสำหรับเว็บไซต์ใช้งานจริง</p>
        <form id="loginForm" class="form-grid">
          <div class="field">
            <label for="adminUser">ชื่อผู้ใช้</label>
            <input id="adminUser" autocomplete="username" required>
          </div>
          <div class="field">
            <label for="adminPass">รหัสผ่าน</label>
            <input id="adminPass" type="password" autocomplete="current-password" required>
          </div>
          <div class="field full">
            <button class="primary" type="submit">เข้าสู่ระบบ</button>
          </div>
        </form>
      </div>

      <div id="adminPanel" class="hidden">
        <div class="panel">
          <h2>📋 จัดการคำขอยืม</h2>
          <p class="notice">ข้อมูลในรุ่นนี้อยู่ในเบราว์เซอร์เครื่องนี้เท่านั้น</p>
          <div class="actions">
            <button class="primary" onclick="exportCSV()">ส่งออก CSV</button>
            <button class="secondary" onclick="renderRequests()">รีเฟรชรายการ</button>
            <button class="secondary" onclick="logout()">ออกจากระบบ</button>
          </div>
          <div id="requestList"></div>
        </div>

        <div class="panel">
          <h2>🧰 จัดการรายการอุปกรณ์</h2>
          <form id="addItemForm" class="form-grid">
            <div class="field">
              <label for="newItemName">ชื่ออุปกรณ์</label>
              <input id="newItemName" required maxlength="100">
            </div>
            <div class="field">
              <label for="newItemQty">จำนวนทั้งหมด</label>
              <input id="newItemQty" type="number" min="1" max="9999" value="1" required>
            </div>
            <div class="field full">
              <button class="primary" type="submit">เพิ่มอุปกรณ์</button>
            </div>
          </form>
          <div id="manageItems"></div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    ยืมดี | ระบบยืม–คืนอุปกรณ์เพื่อการเรียนรู้
  </footer>

  <script>
    const DEMO_USER = "teacher";
    const DEMO_PASS = "Teach1234";

    const defaultItems = [
      { id: 1, name: "ชุด Arduino", icon: "🤖", total: 10 },
      { id: 2, name: "โน้ตบุ๊ก", icon: "💻", total: 5 },
      { id: 3, name: "ชุดเซนเซอร์", icon: "🔌", total: 10 },
      { id: 4, name: "ชุดเครื่องมือช่าง", icon: "🛠️", total: 5 },
      { id: 5, name: "โปรเจกเตอร์", icon: "📽️", total: 2 },
      { id: 6, name: "อุปกรณ์หุ่นยนต์", icon: "🦾", total: 8 }
    ];

    let items = load("borrow_items", defaultItems);
    let requests = load("borrow_requests", []);
    let isAdmin = false;

    function load(key, fallback) {
      try {
        const data = localStorage.getItem(key);
        return data ? JSON.parse(data) : JSON.parse(JSON.stringify(fallback));
      } catch {
        return JSON.parse(JSON.stringify(fallback));
      }
    }

    function save() {
      localStorage.setItem("borrow_items", JSON.stringify(items));
      localStorage.setItem("borrow_requests", JSON.stringify(requests));
    }

    function escapeHTML(value) {
      return String(value ?? "").replace(/[&<>"']/g, char => ({
        "&": "&amp;", "<": "&lt;", ">": "&gt;",
        '"': "&quot;", "'": "&#39;"
      }[char]));
    }

    function showPage(page) {
      ["home", "borrow", "admin"].forEach(id => {
        document.getElementById(id).classList.toggle("hidden", id !== page);
      });

      document.querySelectorAll(".nav-btn").forEach(btn => {
        btn.classList.toggle("active", btn.dataset.page === page);
      });

      if (page === "home") renderHome();
      if (page === "borrow") renderEquipmentOptions();
      if (page === "admin") renderAdmin();
      window.scrollTo({ top: 0, behavior: "smooth" });
    }

    document.querySelectorAll(".nav-btn").forEach(btn => {
      btn.addEventListener("click", () => showPage(btn.dataset.page));
    });

    function getBorrowedCount(itemId) {
      return requests
        .filter(r => r.itemId === itemId && r.status === "อนุมัติแล้ว")
        .reduce((sum, r) => sum + Number(r.quantity), 0);
    }

    function available(item) {
      return Math.max(0, item.total - getBorrowedCount(item.id));
    }

    function renderHome() {
      document.getElementById("totalItems").textContent = items.length;
      document.getElementById("totalRequests").textContent = requests.length;
      document.getElementById("pendingRequests").textContent =
        requests.filter(r => r.status === "รออนุมัติ").length;

      document.getElementById("itemsGrid").innerHTML = items.map(item => `
        <article class="item">
          <div class="item-icon">${escapeHTML(item.icon || "📦")}</div>
          <h3>${escapeHTML(item.name)}</h3>
          <p>มีทั้งหมด ${item.total} ชิ้น<br>พร้อมให้ยืม ${available(item)} ชิ้น</p>
          <button class="primary" ${available(item) < 1 ? "disabled" : ""}
            onclick="chooseItem(${item.id})">เลือกยืม</button>
        </article>
      `).join("");
    }

    function renderEquipmentOptions() {
      const select = document.getElementById("equipment");
      const previous = select.value;

      select.innerHTML = '<option value="">-- เลือกอุปกรณ์ --</option>' +
        items.map(item => `
          <option value="${item.id}" ${available(item) < 1 ? "disabled" : ""}>
            ${escapeHTML(item.name)} (พร้อมยืม ${available(item)} ชิ้น)
          </option>
        `).join("");

      if (items.some(item => String(item.id) === previous && available(item) > 0)) {
        select.value = previous;
      }
    }

    function chooseItem(id) {
      showPage("borrow");
      document.getElementById("equipment").value = String(id);
    }

    document.getElementById("borrowDate").value =
      new Date().toLocaleDateString("en-CA");

    document.getElementById("returnDate").value =
      new Date(Date.now() + 86400000).toLocaleDateString("en-CA");

    document.getElementById("borrowForm").addEventListener("submit", event => {
      event.preventDefault();

      const itemId = Number(document.getElementById("equipment").value);
      const item = items.find(i => i.id === itemId);
      const quantity = Number(document.getElementById("quantity").value);
      const borrowDate = document.getElementById("borrowDate").value;
      const returnDate = document.getElementById("returnDate").value;

      if (!item) return alert("กรุณาเลือกอุปกรณ์");
      if (!Number.isInteger(quantity) || quantity < 1) {
        return alert("กรุณาระบุจำนวนให้ถูกต้อง");
      }
      if (borrowDate < new Date().toLocaleDateString("en-CA")) {
        return alert("วันที่ยืมต้องไม่เป็นวันที่ผ่านมาแล้ว");
      }
      if (returnDate < borrowDate) {
        return alert("วันที่คืนต้องไม่ก่อนวันที่ยืม");
      }

      const alreadyRequested = requests
        .filter(r => r.itemId === itemId && r.status !== "ปฏิเสธ")
        .reduce((sum, r) => sum + Number(r.quantity), 0);

      if (quantity > item.total - alreadyRequested) {
        return alert("จำนวนอุปกรณ์ที่ว่างไม่เพียงพอ");
      }

      const request = {
        id: Date.now(),
        name: document.getElementById("studentName").value.trim(),
        studentClass: document.getElementById("studentClass").value.trim(),
        studentId: document.getElementById("studentId").value.trim(),
        contact: document.getElementById("contact").value.trim(),
        itemId,
        itemName: item.name,
        quantity,
        borrowDate,
        returnDate,
        purpose: document.getElementById("purpose").value.trim(),
        status: "รออนุมัติ",
        createdAt: new Date().toLocaleString("th-TH")
      };

      requests.unshift(request);
      save();
      event.target.reset();

      document.getElementById("quantity").value = 1;
      document.getElementById("borrowDate").value =
        new Date().toLocaleDateString("en-CA");
      document.getElementById("returnDate").value =
        new Date(Date.now() + 86400000).toLocaleDateString("en-CA");

      alert("ส่งคำขอยืมแล้ว กรุณารอผู้ดูแลอนุมัติ");
      showPage("home");
    });

    document.getElementById("loginForm").addEventListener("submit", event => {
      event.preventDefault();

      const username = document.getElementById("adminUser").value;
      const password = document.getElementById("adminPass").value;

      if (username === DEMO_USER && password === DEMO_PASS) {
        isAdmin = true;
        document.getElementById("adminPass").value = "";
        renderAdmin();
      } else {
        alert("ชื่อผู้ใช้หรือรหัสผ่านไม่ถูกต้อง");
      }
    });

    function renderAdmin() {
      document.getElementById("loginPanel").classList.toggle("hidden", isAdmin);
      document.getElementById("adminPanel").classList.toggle("hidden", !isAdmin);

      if (isAdmin) {
        renderRequests();
        renderManageItems();
      }
    }

    function logout() {
      isAdmin = false;
      renderAdmin();
    }

    function statusClass(status) {
      if (status === "อนุมัติแล้ว") return "approved";
      if (status === "คืนแล้ว") return "returned";
      if (status === "ปฏิเสธ") return "rejected";
      return "";
    }

    function renderRequests() {
      const list = document.getElementById("requestList");

      if (!requests.length) {
        list.innerHTML = "<p class='notice'>ยังไม่มีคำขอยืมอุปกรณ์</p>";
        return;
      }

      list.innerHTML = requests.map(r => `
        <article class="request">
          <h3>${escapeHTML(r.itemName)} × ${r.quantity}</h3>
          <span class="status ${statusClass(r.status)}">${escapeHTML(r.status)}</span>
          <p>
            ผู้ยืม: ${escapeHTML(r.name)} (${escapeHTML(r.studentClass)})<br>
            เลขประจำตัว: ${escapeHTML(r.studentId)}<br>
            ติดต่อ: ${escapeHTML(r.contact || "-")}<br>
            วันที่ยืม: ${escapeHTML(r.borrowDate)}<br>
            วันที่คืน: ${escapeHTML(r.returnDate)}<br>
            วัตถุประสงค์: ${escapeHTML(r.purpose)}<br>
            ส่งคำขอเมื่อ: ${escapeHTML(r.createdAt)}
          </p>
          <div class="actions">
            ${r.status === "รออนุมัติ" ? `
              <button class="primary" onclick="updateStatus(${r.id}, 'อนุมัติแล้ว')">อนุมัติ</button>
              <button class="danger" onclick="updateStatus(${r.id}, 'ปฏิเสธ')">ปฏิเสธ</button>
            ` : ""}
            ${r.status === "อนุมัติแล้ว" ? `
              <button class="primary" onclick="updateStatus(${r.id}, 'คืนแล้ว')">ยืนยันรับคืน</button>
            ` : ""}
            <button class="secondary" onclick="deleteRequest(${r.id})">ลบรายการ</button>
          </div>
        </article>
      `).join("");
    }

    function updateStatus(id, status) {
      const request = requests.find(r => r.id === id);
      if (!request) return;

      if (status === "อนุมัติแล้ว") {
        const item = items.find(i => i.id === request.itemId);
        const otherApproved = requests
          .filter(r => r.itemId === request.itemId &&
            r.status === "อนุมัติแล้ว" && r.id !== id)
          .reduce((sum, r) => sum + Number(r.quantity), 0);

        if (!item || item.total - otherApproved < request.quantity) {
          return alert("อุปกรณ์ไม่เพียงพอสำหรับอนุมัติคำขอนี้");
        }
      }

      request.status = status;
      save();
      renderRequests();
      renderManageItems();
      renderHome();
    }

    function deleteRequest(id) {
      if (!confirm("ต้องการลบคำขอนี้ใช่หรือไม่?")) return;
      requests = requests.filter(r => r.id !== id);
      save();
      renderRequests();
      renderManageItems();
      renderHome();
    }

    document.getElementById("addItemForm").addEventListener("submit", event => {
      event.preventDefault();

      const name = document.getElementById("newItemName").value.trim();
      const total = Number(document.getElementById("newItemQty").value);

      if (!name || !Number.isInteger(total) || total < 1) {
        return alert("กรุณากรอกข้อมูลอุปกรณ์ให้ถูกต้อง");
      }

      items.push({
        id: Date.now(),
        name,
        icon: "📦",
        total
      });

      save();
      event.target.reset();
      document.getElementById("newItemQty").value = 1;
      renderManageItems();
      renderEquipmentOptions();
      renderHome();
      alert("เพิ่มอุปกรณ์แล้ว");
    });

    function renderManageItems() {
      document.getElementById("manageItems").innerHTML = items.map(item => `
        <div class="request">
          <strong>${escapeHTML(item.name)}</strong>
          <p class="muted">ทั้งหมด ${item.total} ชิ้น · พร้อมยืม ${available(item)} ชิ้น</p>
          <div class="actions">
            <button class="secondary" onclick="changeQuantity(${item.id})">แก้ไขจำนวน</button>
            <button class="danger" onclick="removeItem(${item.id})">ลบอุปกรณ์</button>
          </div>
        </div>
      `).join("");
    }

    function changeQuantity(id) {
      const item = items.find(i => i.id === id);
      if (!item) return;

      const result = prompt("กรอกจำนวนอุปกรณ์ทั้งหมด:", item.total);
      if (result === null) return;

      const total = Number(result);
      const currentlyBorrowed = getBorrowedCount(id);

      if (!Number.isInteger(total) || total < currentlyBorrowed || total < 1) {
        return alert("จำนวนต้องเป็นจำนวนเต็ม และไม่น้อยกว่าจำนวนที่กำลังถูกยืม");
      }

      item.total = total;
      save();
      renderManageItems();
      renderEquipmentOptions();
      renderHome();
    }

    function removeItem(id) {
      if (requests.some(r => r.itemId === id && r.status === "อนุมัติแล้ว")) {
        return alert("ลบไม่ได้ เนื่องจากยังมีอุปกรณ์ที่รอคืน");
      }

      if (!confirm("ต้องการลบอุปกรณ์นี้ใช่หรือไม่?")) return;

      items = items.filter(i => i.id !== id);
      save();
      renderManageItems();
      renderEquipmentOptions();
      renderHome();
    }

    function exportCSV() {
      if (!requests.length) return alert("ยังไม่มีข้อมูลให้ส่งออก");

      const columns = [
        "เลขคำขอ", "ชื่อผู้ยืม", "ชั้น/ห้อง", "เลขประจำตัว",
        "อุปกรณ์", "จำนวน", "วันที่ยืม", "วันที่คืน",
        "วัตถุประสงค์", "สถานะ"
      ];

      const rows = requests.map(r => [
        r.id, r.name, r.studentClass, r.studentId,
        r.itemName, r.quantity, r.borrowDate, r.returnDate,
        r.purpose, r.status
      ]);

      const csvCell = value =>
        '"' + String(value ?? "").replace(/"/g, '""') + '"';

      const csv = "\uFEFF" + [columns, ...rows]
        .map(row => row.map(csvCell).join(","))
        .join("\r\n");

      const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
      const url = URL.createObjectURL(blob);
      const link = document.createElement("a");
      link.href = url;
      link.download = "equipment-borrowing.csv";
      link.click();
      URL.revokeObjectURL(url);
    }

    renderHome();
    renderEquipmentOptions();
  </script>
</body>
</html>

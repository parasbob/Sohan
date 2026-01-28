<template>
  <div class="page">
    <!-- HEADER -->
    <header class="top-header">
      <div class="header-left">
        <img src="@/assets/govEmblem.png" class="emblem" />
        <div>
          <h1>Part Plan And Zone Certificate Portal</h1>
          <p>Government of Maharashtra</p>
          <small>Town Planning and Valuation Department</small>
        </div>
      </div>

      <div class="header-right">
        <button class="btn btn-yellow">APPLICANT LOGIN</button>
        <button class="btn btn-outline">OFFICE LOGIN</button>
      </div>
    </header>

    <!-- NAV -->
    <nav class="nav">
      <a class="active">HOME</a>
      <a>FAQ</a>
      <a>CONTACT US</a>
      <a>English ▾</a>
      <a>User Guide</a>
    </nav>

    <!-- MAIN -->
    <main class="main">
      <div class="card map-card">
        <img src="@/assets/maharashtra-map.png" alt="Map" />
      </div>

      <div class="card action-card">
        <h2>Get Part Plan/Zone Certificate</h2>
        <p>Access and manage your zoning certificates through our secure online portal</p>

        <div class="actions">
          <button class="btn btn-primary">Applicant Login</button>
          <button class="btn btn-outline-primary">Applicant Registration</button>
        </div>
      </div>
    </main>

    <h3 class="section-title">Our Reach Across Maharashtra</h3>
  </div>
</template>

<script>
export default {
  name: "LandingPage"
}
</script>

<style scoped>
/* ---------- ROOT ---------- */
.page {
  font-family: 'Poppins', sans-serif;
  background: #f5f7fb;
  color: #1f2d3d;
}

/* ---------- HEADER ---------- */
.top-header {
  background: linear-gradient(135deg, #1b4f9c, #0b6cc4);
  color: white;
  padding: 18px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-left {
  display: flex;
  gap: 16px;
}

.emblem {
  height: 58px;
}

.header-left h1 {
  font-size: 20px;
  font-weight: 600;
  margin: 0;
}

.header-left p {
  margin: 2px 0;
  font-size: 14px;
}

.header-left small {
  font-size: 12px;
  opacity: 0.9;
}

/* ---------- BUTTONS ---------- */
.btn {
  padding: 10px 18px;
  font-size: 14px;
  font-weight: 500;
  border-radius: 4px;
  cursor: pointer;
  border: none;
}

.btn-yellow {
  background: #f9c400;
  color: #003366;
}

.btn-outline {
  background: transparent;
  border: 1px solid #fff;
  color: white;
  margin-left: 10px;
}

.btn-primary {
  background: #0b5ed7;
  color: white;
  width: 260px;
}

.btn-outline-primary {
  background: white;
  border: 1px solid #0b5ed7;
  color: #0b5ed7;
  width: 260px;
}

/* ---------- NAV ---------- */
.nav {
  background: #0a3d78;
  padding: 10px 40px;
  display: flex;
  gap: 28px;
}

.nav a {
  color: white;
  font-size: 13px;
  text-decoration: none;
  opacity: 0.85;
}

.nav a.active {
  border-bottom: 3px solid #f9c400;
  padding-bottom: 6px;
  opacity: 1;
}

/* ---------- MAIN ---------- */
.main {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 40px;
  padding: 50px 60px;
}

.card {
  background: white;
  border-radius: 8px;
  padding: 30px;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
}

.map-card img {
  width: 100%;
}

/* ---------- ACTION CARD ---------- */
.action-card h2 {
  font-size: 26px;
  margin-bottom: 10px;
}

.action-card p {
  color: #6c757d;
  margin-bottom: 30px;
}

.actions {
  display: flex;
  gap: 20px;
}

/* ---------- SECTION ---------- */
.section-title {
  text-align: center;
  margin: 40px 0;
  font-weight: 600;
}
</style>

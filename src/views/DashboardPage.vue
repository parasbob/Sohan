<template>
  <div class="dashboard">
    <!-- TOP BANNER -->
    <div class="top-banner">
      <!-- Left: User -->
      <div class="user-box">
        <img src="@/assets/login.png" alt="User Avatar" class="avatar-img" />
        <div class="user-name"></div>
      </div>

      <!-- Center: Portal info -->
      <div class="portal-info">
        <div class="logos">
          <img src="@/assets/govEmblem.png" alt="Govt" />
          <div class="divider"></div>
          <img src="@/assets/tpv-logo.png" alt="TPVD" />
        </div>

        <h1>Part Plan And Zone Certificate Portal</h1>
        <p>Government of Maharashtra</p>
        <small>Town Planning and Valuation Department</small>

        <div class="apply-text">Click here to apply 👇</div>

        <div class="actions">
          <button class="btn primary">Get Part Plan 👈</button>
          <button class="btn outline">Get Zone Certificate 👈</button>
        </div>
      </div>

      <!-- Right: Settings -->
      <div class="settings-box" @click.stop="toggleMenu">
        <img src="@/assets/setting.png" alt="Settings" class="settings-img" />
        <div class="settings-text">Settings</div>
        <div v-if="showMenu" class="settings-menu">
          <div class="menu-item" @click="logout">Logout</div>
          <div class="menu-item">Change Password</div>
          <div class="menu-item">Reset Preview</div>
          <div class="menu-item danger">User Manual</div>
        </div>
      </div>
    </div>

    <!-- CONTENT CARD -->
    <div class="content-card">
      <!-- Toolbar -->
      <div class="toolbar">
        <!-- LEFT -->
        <div class="toolbar-left">
          <input type="text" placeholder="Search by name, survey no, or phone..." />
        </div>

        <!-- CENTER -->
        <div class="toolbar-center">
          <span class="approved-pill">Approved 2/2</span>
        </div>

        <!-- RIGHT -->
        <div class="toolbar-right">
          <button>🌐 Language</button>
          <button>🔽 Filter</button>
          <button>☰ Columns</button>
        </div>
      </div>

      <!-- Empty State -->
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>

      <div class="get-plan-wrapper">
        <a href="/SACHIN_ANNA_BARHALI.pdf" download class="get-plan-btn"> Get your plan </a>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  user: Object,
})
import { ref, onMounted, onBeforeUnmount } from 'vue'
const emit = defineEmits(['logout'])

const showMenu = ref(false)

const toggleMenu = () => {
  showMenu.value = !showMenu.value
  console.log('FD')
}

const logout = () => {
  showMenu.value = false
  emit('logout') // ✅ emit event
}

// close menu when clicking outside
const closeOnOutsideClick = () => {
  showMenu.value = false
}

onMounted(() => {
  window.addEventListener('click', closeOnOutsideClick)
})

onBeforeUnmount(() => {
  window.removeEventListener('click', closeOnOutsideClick)
})
</script>
<style scoped>
/* Wrapper */
.settings-wrapper {
  position: relative;
  cursor: pointer;
}

/* Icon */
.settings-img {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25);
}

/* Dropdown menu */
.settings-menu {
  position: absolute;
  top: 54px;
  right: 0;
  width: 200px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.2);
  overflow: hidden;
  z-index: 1000;
}

/* Menu item */
.menu-item {
  padding: 12px 16px;
  font-size: 14px;
  color: #333;
  cursor: pointer;
}

.menu-item:hover {
  background: #f5f7fb;
}

/* Red text */
.menu-item.danger {
  color: #e53935;
}
/* Center wrapper */
.get-plan-wrapper {
  display: flex;
  justify-content: center;
  margin-top: 100px;
  margin-bottom: 80px;
}

/* Button */
.get-plan-btn {
  background: linear-gradient(135deg, #f9c400, #f2b705);
  color: #1f2d3d;
  padding: 10px 22px;
  border-radius: 24px;
  font-weight: 600;
  font-size: 14px;
  text-decoration: none;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.18);
  transition: all 0.2s ease;
}

/* Hover */
.get-plan-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.25);
  text-decoration: none;
}

/* Active */
.get-plan-btn:active {
  transform: translateY(0);
  box-shadow: 0 3px 8px rgba(0, 0, 0, 0.2);
}
.get-plan {
  display: flex;
  justify-content: flex-end;
}

.get-plan a {
  font-weight: 600;
  color: #1a73e8;
  text-decoration: none;
  font-size: 14px;
}

.get-plan a:hover {
  text-decoration: underline;
}
.settings-box {
  display: flex;
  flex-direction: column; /* image on top, text below */
  align-items: center;
  justify-content: center;
  gap: 6px;
  cursor: pointer;
}

/* Settings icon image */
.settings-img {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #ffffff;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25);
}

/* Settings text */
.settings-text {
  font-size: 13px;
  font-weight: 600;
  color: #000;
  white-space: nowrap;
}
.dashboard {
  background: #f5f7fb;
  min-height: 100vh;
}

/* ---------------- TOP BANNER ---------------- */
.top-banner {
  position: relative;
  background-image: url('@/assets/background.png');
  background-size: cover;
  background-position: right center;
  background-repeat: no-repeat;

  padding: 30px 40px;
  display: grid;
  grid-template-columns: 200px 1fr 160px;
  align-items: center;
  min-height: 180px;
}

/* Overlay for readability */
.top-banner::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0.95) 30%,
    rgba(255, 255, 255, 0.75) 55%,
    rgba(255, 255, 255, 0.3) 75%
  );
  z-index: 0;
}

/* Ensure content stays above overlay */
.top-banner > * {
  position: relative;
  z-index: 1;
}

/* User */
.user-box {
  display: flex;
  flex-direction: column; /* avatar on top, name below */
  align-items: center;
  gap: 6px;
}

/* Avatar image */
.avatar-img {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #ffffff;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25);
}

/* User name */
.user-name {
  font-size: 13px;
  font-weight: 600;
  color: #000;
  white-space: nowrap;
}

/* Portal Info */
.portal-info {
  text-align: center;
}

.logos {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 14px;
  margin-bottom: 6px;
}

.logos img {
  height: 42px;
}

.divider {
  width: 2px;
  height: 40px;
  background: #f2b705;
}

.portal-info h1 {
  font-size: 20px;
  margin: 4px 0;
}

.portal-info p {
  margin: 0;
  font-size: 14px;
}

.portal-info small {
  font-size: 12px;
  color: #555;
}

.apply-text {
  margin: 10px 0 6px;
  font-weight: 600;
  color: #666;
}

.actions {
  display: flex;
  justify-content: center;
  gap: 14px;
}

.btn {
  padding: 10px 18px;
  border-radius: 20px;
  font-weight: 600;
  border: none;
  cursor: pointer;
}

.btn.primary {
  background: #f2b705;
  color: #000;
}

.btn.outline {
  background: #fff;
  border: 2px solid #f2b705;
}

/* Settings */
.settings {
  text-align: right;
  font-weight: 600;
  cursor: pointer;
}

/* ---------------- CONTENT CARD ---------------- */
.content-card {
  background: white;
  margin: 24px 40px;
  border-radius: 12px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
  padding: 20px;
}

/* Toolbar main */
.toolbar {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  gap: 16px;
  margin-bottom: 10px;
}

/* LEFT */
.toolbar-left input {
  width: 100%;
  max-width: 420px;
  padding: 10px 14px;
  border-radius: 8px;
  border: 1px solid #ddd;
}

/* CENTER */
.toolbar-center {
  display: flex;
  justify-content: center;
}

.approved-pill {
  background: #e6f4ea;
  color: #137333;
  padding: 6px 14px;
  border-radius: 999px;
  font-size: 13px;
  font-weight: 600;
  white-space: nowrap;
}

/* RIGHT */
.toolbar-right {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}

.toolbar-right button {
  background: #f1f3f4;
  border: 1px solid #ddd;
  padding: 8px 12px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 13px;
}

/* Empty State */
.empty-state {
  text-align: center;
  padding: 80px 20px;
  color: #555;
}

.empty-state .icon {
  font-size: 42px;
  margin-bottom: 10px;
}

.empty-state h3 {
  margin-bottom: 6px;
}
</style>

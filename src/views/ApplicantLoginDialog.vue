<template>
  <v-dialog v-model="openDialog" max-width="520" persistent scrim="rgba(0,0,0,0.55)">
    <div class="login-card">
      <!-- Header -->
      <div class="login-header">
        <div class="icon-circle">i</div>
        <h3>Applicant Login</h3>
        <button class="close-btn" @click="close">×</button>
      </div>

      <!-- Tabs -->
      <div class="login-tabs">
        <button :class="{ active: tab === 'login' }" @click="tab = 'login'">Login</button>
        <button :class="{ active: tab === 'register' }" @click="tab = 'register'">Register</button>
      </div>

      <!-- Body -->
      <div class="login-body">
        <div v-if="authError" class="error-box">
          <span class="error-icon">!</span>
          <span class="error-text">Invalid credentials</span>
        </div>
        <label>Email</label>
        <input type="email" placeholder="your@email.com" v-model="email" />

        <label>Password</label>
        <input type="password" placeholder="••••••••" v-model="password" />

        <div class="actions">
          <button class="btn-primary" @click="login">Login</button>
          <button class="btn-secondary" @click="close">Cancel</button>
        </div>

        <a class="forgot">Forgot your password?</a>
      </div>
    </div>
  </v-dialog>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['login-success'])
import users from '@/data/loginUsers.json'
const openDialog = ref(false)
const tab = ref('login')
const email = ref('')
const password = ref('')
const authError = ref(false)
const open = () => (openDialog.value = true)
const close = () => {
  authError.value = false

  email.value = ''
  password.value = ''
  authError.value = ''
  openDialog.value = false
}
const login = () => {
  console.log(email.value, password.value)
  const found = users.find((u) => u.email === email.value && u.password === password.value)

  if (!found) {
    authError.value = true
    return
  }
  emit('login-success', {
    name: 'Sohan Lakde',
    email: email.value,
  })
  // ✅ Success
  close()
}

defineExpose({ open })
</script>

<style scoped>
/* Error Alert */
.error-box {
  display: flex;
  align-items: center;
  gap: 10px;
  background: #fff1f1;
  border: 1px solid #ffcccc;
  color: #d93025;
  padding: 14px;
  border-radius: 8px;
  margin-bottom: 18px;
}

.error-icon {
  width: 22px;
  height: 22px;
  border-radius: 50%;
  background: #d93025;
  color: white;
  font-weight: bold;
  display: grid;
  place-items: center;
  font-size: 14px;
}

.error-text {
  font-weight: 600;
}
/* Dialog card */
.login-card {
  border-radius: 12px;
  background: #fff;
  overflow: hidden;
  box-shadow: 0 25px 60px rgba(0, 0, 0, 0.35);
}

/* Header */
.login-header {
  background: linear-gradient(180deg, #4f5df5, #3f48cc);
  padding: 18px;
  text-align: center;
  color: #000;
  position: relative;
}

.login-header h3 {
  margin: 0;
  font-weight: 600;
}

.icon-circle {
  position: absolute;
  left: 16px;
  top: 14px;
  background: white;
  color: #3f48cc;
  width: 26px;
  height: 26px;
  border-radius: 50%;
  font-weight: bold;
  display: grid;
  place-items: center;
}

.close-btn {
  position: absolute;
  right: 14px;
  top: 10px;
  font-size: 22px;
  background: white;
  border-radius: 50%;
  width: 28px;
  height: 28px;
  border: none;
  cursor: pointer;
}

/* Tabs */
.login-tabs {
  background: #5c63d6;
  padding: 10px;
  display: flex;
  gap: 10px;
}

.login-tabs button {
  flex: 1;
  border: none;
  border-radius: 999px;
  padding: 10px;
  font-weight: 600;
  cursor: pointer;
  background: transparent;
  color: #e0e3ff;
}

.login-tabs .active {
  background: white;
  color: #3f48cc;
}

/* Body */
.login-body {
  padding: 22px;
}

.login-body label {
  font-size: 14px;
  font-weight: 600;
  margin-top: 12px;
  display: block;
}

.login-body input {
  width: 100%;
  padding: 12px;
  border-radius: 8px;
  border: 1px solid #ddd;
  margin-top: 6px;
}

/* Buttons */
.actions {
  display: flex;
  gap: 14px;
  margin-top: 22px;
}

.btn-primary {
  flex: 1;
  background: #4f5df5;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 12px;
  font-weight: 600;
}

.btn-secondary {
  flex: 1;
  background: #f1f3f4;
  border: none;
  border-radius: 8px;
  padding: 12px;
}

/* Footer link */
.forgot {
  display: block;
  margin-top: 14px;
  text-align: center;
  color: #4f5df5;
  font-weight: 600;
  cursor: pointer;
}
</style>

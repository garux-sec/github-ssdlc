<script setup>
import { ref } from 'vue'

const isAdmin = ref(false)
const form = ref({ email: '', password: '' })
const error = ref('')

const ADMIN_EMAIL = 'admin@phisit.sec'
const ADMIN_PASS = 'pentest123'

function handleLogin(event) {
  event.preventDefault()
  const email = form.value.email.trim()
  const password = form.value.password
  if (email === ADMIN_EMAIL && password === ADMIN_PASS) {
    isAdmin.value = true
    error.value = ''
  } else {
    error.value = 'Invalid credentials'
  }
}

function handleLogout() {
  isAdmin.value = false
  form.value = { email: '', password: '' }
  error.value = ''
}
</script>

<template>
  <div class="page">
    <div class="glass">
      <header class="top">
        <div>
          <p class="eyebrow">Admin Access</p>
          <h1 class="brand">Phisit Pupiw</h1>
        </div>
        <nav class="nav">
          <RouterLink class="nav-link" to="/">← Back to Home</RouterLink>
        </nav>
      </header>

      <section class="section admin">
        <div class="section-header">
          <p class="label">หลังบ้าน</p>
          <h3>เข้าสู่ระบบเพื่อจัดการ</h3>
          <p class="section-copy">ต้องล็อกอินก่อนเข้าถึงหน้าจัดการหลังบ้าน</p>
        </div>

        <div v-if="!isAdmin" class="card admin-card">
          <form class="login-form" @submit="handleLogin">
            <div class="form-field">
              <label>Email</label>
              <input v-model="form.email" type="email" placeholder="admin@phisit.sec" required />
            </div>
            <div class="form-field">
              <label>Password</label>
              <input v-model="form.password" type="password" placeholder="•••••••••" required />
            </div>
            <button class="cta primary" type="submit">Login</button>
            <p v-if="error" class="error">{{ error }}</p>
          </form>
          <p class="hint">ตัวอย่าง: admin@phisit.sec / pentest123</p>
        </div>

        <div v-else class="card admin-panel">
          <div class="admin-top">
            <div>
              <p class="label">Authenticated</p>
              <h4>Welcome, Admin</h4>
              <p class="body">เข้าจัดการหลังบ้านได้แล้ว</p>
            </div>
            <button class="cta ghost" type="button" @click="handleLogout">Logout</button>
          </div>
          <div class="grid admin-grid">
            <div class="mini-card">
              <p class="label">Content</p>
              <p class="body">แก้ไขข้อความ โปรไฟล์ และลิงก์สำคัญ</p>
            </div>
            <div class="mini-card">
              <p class="label">Assets</p>
              <p class="body">อัปโหลดรูปพื้นหลังและสื่อประกอบ</p>
            </div>
            <div class="mini-card">
              <p class="label">Security</p>
              <p class="body">จัดการผู้ใช้ สิทธิ์ และบันทึกกิจกรรม</p>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped>
.page {
  min-height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem 1rem;
  background:
    linear-gradient(135deg, rgba(4, 20, 16, 0.9), rgba(7, 42, 32, 0.85)),
    url('https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?auto=format&fit=crop&w=1600&q=80')
      center/cover no-repeat fixed;
  color: #e9f7f2;
}

.glass {
  width: min(1300px, 100%);
  background: rgba(14, 30, 25, 0.72);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  padding: 2.5rem;
  backdrop-filter: blur(10px);
  box-shadow:
    0 25px 80px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.06);
}

.top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 1.25rem;
}

.brand {
  margin: 0.25rem 0 0;
  font-size: 1.6rem;
  color: #f7fff9;
  letter-spacing: -0.02em;
}

.nav {
  display: flex;
}

.nav-link {
  color: #d8f3e8;
  text-decoration: none;
  padding: 0.55rem 0.85rem;
  border-radius: 10px;
  border: 1px solid rgba(156, 224, 200, 0.25);
  background: rgba(156, 224, 200, 0.06);
  transition: all 0.2s ease;
}

.nav-link:hover {
  background: rgba(156, 224, 200, 0.16);
  transform: translateY(-1px);
}

.eyebrow {
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-size: 0.85rem;
  color: #9ce0c8;
}

.section {
  margin-top: 1.5rem;
  padding-top: 1rem;
}

.section-header {
  margin-bottom: 1rem;
}

.section-copy {
  color: #cde8dd;
  margin-top: 0.35rem;
}

.card {
  background: rgba(255, 255, 255, 0.03);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 1.25rem 1.5rem;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.04);
}

.card h4 {
  margin: 0.35rem 0 0.6rem;
  color: #f5fff9;
  letter-spacing: -0.01em;
}

.body {
  color: #cde8dd;
  line-height: 1.55;
}

.label {
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-size: 0.85rem;
  color: #9ce0c8;
}

.admin-card {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.login-form {
  display: grid;
  gap: 0.75rem;
}

.form-field {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.form-field label {
  font-size: 0.95rem;
  color: #cde8dd;
}

.form-field input {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(156, 224, 200, 0.3);
  border-radius: 10px;
  padding: 0.65rem 0.75rem;
  color: #f7fff9;
}

.form-field input:focus {
  outline: 2px solid rgba(63, 182, 139, 0.6);
  outline-offset: 1px;
}

.error {
  color: #ffb3b3;
  font-size: 0.95rem;
}

.hint {
  color: #9ce0c8;
  font-size: 0.95rem;
}

.admin-panel {
  display: grid;
  gap: 0.75rem;
}

.admin-top {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  align-items: center;
}

.admin-grid {
  gap: 0.75rem;
}

.mini-card {
  padding: 1rem 1.1rem;
  border-radius: 12px;
  border: 1px solid rgba(156, 224, 200, 0.25);
  background: rgba(156, 224, 200, 0.04);
}

.cta {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.65rem 1.2rem;
  border-radius: 12px;
  font-weight: 600;
  text-decoration: none;
  transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
  cursor: pointer;
  border: none;
}

.primary {
  background: linear-gradient(135deg, #3fb68b, #1d8f68);
  color: #0b1b15;
  box-shadow: 0 10px 30px rgba(63, 182, 139, 0.35);
}

.primary:hover {
  transform: translateY(-1px);
  box-shadow: 0 14px 36px rgba(63, 182, 139, 0.45);
}

.ghost {
  border: 1px solid rgba(156, 224, 200, 0.4);
  color: #d6f3e7;
  background: rgba(156, 224, 200, 0.05);
}

.ghost:hover {
  background: rgba(156, 224, 200, 0.12);
  transform: translateY(-1px);
}

@media (max-width: 900px) {
  .top {
    flex-direction: column;
    align-items: flex-start;
  }

  .glass {
    padding: 2rem;
  }

  .admin-top {
    flex-direction: column;
    align-items: flex-start;
  }
}

@media (max-width: 600px) {
  .page {
    padding: 1.5rem 1rem;
  }
}
</style>

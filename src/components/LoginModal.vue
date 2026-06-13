<script setup>
import { ref, computed } from 'vue'

const user = ref('')
const pass = ref('')
const showPass = ref(false)

const isValid = computed(() => {
  return user.value && pass.value
})

function toggleEye() {
  showPass.value = !showPass.value
}

function login() {
  alert('你被騙啦！')
}
</script>

<template>
  <div class="modal-overlay"></div>

  <div class="login-container">
    
    <div class="title">
      <img src="/img/twitch.png" />
      <h2>登入 Twitch</h2>
    </div>

    <div class="input-group">
      <label>使用者名稱</label>
      <input v-model="user" type="text" />
    </div>

    <div class="input-group">
      <label>密碼</label>

      <div class="input-wrapper">
        <input
          v-model="pass"
          :type="showPass ? 'text' : 'password'"
        />

        <span class="toggle-eye" @click="toggleEye">
          {{ showPass ? '◠' : '👁' }}
        </span>
      </div>
    </div>

    <div class="help-row">
      <a href="#" class="help-link">無法登入嗎</a>
    </div>

    <button class="btn" :disabled="!isValid" @click="login">
      登入
    </button>

    <div class="divider">或者</div>

    <button class="btn alt-btn">
      <img src="/img/google.png" /> 使用 Google 登入
    </button>

    <button class="btn alt-btn">
      <img src="/img/amazon.png" /> 使用 Amazon 登入
    </button>

    <button class="btn alt-btn">
      <img src="/img/apple.png" /> 使用 Apple 登入
    </button>

    <div class="signup">
      <span>還沒有帳號嗎？註冊</span>
    </div>

  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.75);
  z-index: 1;
}

.login-container {
  width: 500px;
  height: 500px;
  background: #18181b;
  padding: 30px;
  border-radius: 16px;
  color: white;

  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  box-sizing: border-box;
}

.title {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
  margin-top: -35px;
  margin-bottom: 5px;
}

.title img {
  height: 28px;
}

.input-group {
  margin-bottom: 5px;
}

.input-wrapper {
  position: relative;
}

input {
  width: 100%;
  padding: 8px;
  border-radius: 8px;
  border: 1px solid #555;
  background: #0e0e10;
  color: white;
  box-sizing: border-box;
}

input:focus {
  outline: none;
  border: 1px solid #9147ff;
  box-shadow: 0 0 5px #9147ff;
}

.toggle-eye {
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
}

.help-row {
  margin: 8px 0 10px;
}

.help-link {
  color: #9147ff;
  font-size: 13px;
}

.btn {
  width: 100%;
  padding: 8px;
  border: none;
  border-radius: 20px;
  margin-top: 10px;
  cursor: pointer;
  background: linear-gradient(90deg, #9147ff, #772ce8);
  color: white;
}

.btn:disabled {
  background: #2a2a2d;
  cursor: not-allowed;
}

.alt-btn {
  background: #2a2a2d;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
}

.alt-btn img {
  width: 18px;
}

.divider {
  margin: 15px 0;
  text-align: center;
  color: #aaa;
}

.signup {
  text-align: center;
  margin-top: 15px;
  font-size: 14px;
  color: #9147ff;
}
</style>
<template>
  <div class="container">
    <div class="row min-vh-100 justify-content-center align-items-center">
      <div class="col-lg-6">
        <div class="card p-5 bg-white border-0 shadow">
          <div class="card-body">
            <h2 class="text-center">Reset Your Password</h2>
            <p class="mb-5 text-center">Enter your email or username and new password</p>

            <form @submit.prevent="handleReset" class="row g-3">

              <div v-if="resetError" class="text-danger text-center" style="font-size: 14px;">
                {{ resetError }}
              </div>
              <div v-if="resetSuccess" class="text-success text-center" style="font-size: 14px;">
                {{ resetSuccess }}
              </div>

              <div class="col-lg-12">
                <div class="mb-3">
                  <div class="input-group position-relative">
                    <i class="bi bi-envelope text-dark input-group-text fs-5"></i>
                    <input
                      v-model="input"
                      type="text"
                      placeholder="Enter your email or username"
                      class="py-2 form-control"
                      :class="{ 'input-error': errors.input }"
                    />
                    <div v-if="errors.input" class="text-danger position-absolute top-100" style="font-size: 13px;">
                      {{ errors.input }}
                    </div>
                  </div>
                </div>
              </div>

              <div class="col-lg-12">
                <div class="mb-3">
                  <div class="input-group position-relative">
                    <span class="input-group-text">
                      <i class="bi bi-lock fs-5"></i>
                    </span>
                    <input
                      :type="showPassword ? 'text' : 'password'"
                      v-model="newPassword"
                      placeholder="Enter your new password"
                      class="form-control z-1"
                      :class="{ 'input-error': errors.newPassword }"
                    />
                    <i
                      :class="showPassword ? 'bi bi-eye-slash' : 'bi bi-eye'"
                      class="text-dark icon-eye fs-5 position-absolute z-3"
                      @click="togglePassword"
                    ></i>
                    <div v-if="errors.newPassword" class="text-danger position-absolute top-100" style="font-size: 13px;">
                      {{ errors.newPassword }}
                    </div>
                  </div>
                </div>
              </div>

              <div class="col-lg-12">
                <button type="submit" class="btn btn-main w-100 mt-3">Reset Password</button>
              </div>

              <p class="text-center">
                Remember your password? <router-link to="/">Login</router-link>
              </p>

            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const input = ref('')
const newPassword = ref('')
const showPassword = ref(false)
const resetError = ref('')
const resetSuccess = ref('')
const errors = ref({})
const router = useRouter()

// Simple password validation: at least 6 chars, uppercase, number, symbol
const validatePassword = (pw) => {
  if (pw.length < 6) return false
  if (!/(?=.*[A-Z])/.test(pw)) return false
  if (!/(?=.*\d)/.test(pw)) return false
  if (!/(?=.*[!@#$%^&*()_+{}\[\]:;<>,.?~\\/-])/.test(pw)) return false
  return true
}

const handleReset = () => {
  resetError.value = ''
  resetSuccess.value = ''
  errors.value = {}

  if (!input.value) {
    errors.value.input = 'Email or username is required'
  }

  if (!newPassword.value) {
    errors.value.newPassword = 'New password is required'
  } else if (!validatePassword(newPassword.value)) {
    errors.value.newPassword = 'Password must be at least 6 chars with uppercase, number & symbol'
  }

  if (Object.keys(errors.value).length > 0) return

  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const index = users.findIndex(u => u.email === input.value || u.username === input.value)

  if (index === -1) {
    resetError.value = 'User not found'
    return
  }

  users[index].password = newPassword.value
  localStorage.setItem('users', JSON.stringify(users))

  resetSuccess.value = 'Password reset successful! Redirecting to login...'
  setTimeout(() => {
    router.push('/')
  }, 2000)
}

const togglePassword = () => {
  showPassword.value = !showPassword.value
}
</script>

<style scoped>
.input-error {
  border: 1px solid red !important;
}
.icon-eye {
  right: 30px;
  top: 50% !important;
  transform: translateY(-50%);
  cursor: pointer;
}
</style>

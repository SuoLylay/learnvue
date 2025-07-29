<template>
  <div class="container">
    <div class="row min-vh-100 justify-content-center align-items-center">
      <div class="col-lg-6">
        <div class="card p-5 bg-white border-0 shadow">
          <div class="card-body">
            <h2 class="text-center">Welcome to Cambodia Academy</h2>
            <p class="mb-5 text-center">Please sign in to start your rental application</p>

            <form @submit.prevent="handleLogin" class="row g-3">

              <div v-if="loginError" class="text-danger text-center position-sticky" style="font-size: 14px;">{{
                loginError }}</div>
              <div class="col-lg-12">
                <div class="mb-3">
                  <div class="input-group position-relative">
                    <i class="bi bi-envelope text-dark input-group-text fs-5"></i>
                    <input v-model="emailInput" type="text" placeholder="e.g@gmail.com" class="py-2 form-control"
                      :class="{ 'input-error': errors.emailInput }" />
                    <div v-if="errors.emailInput" class="text-danger position-absolute top-100"
                      style="font-size: 13px;">{{ errors.emailInput }}</div>
                  </div>
                </div>
              </div>

              <div class="col-lg-12">
                <div class="mb-3">
                  <div class="input-group position-relative">
                    <span class="input-group-text">
                      <i class="bi bi-lock fs-5"></i>
                    </span>
                    <input :type="showPassword ? 'text' : 'password'" v-model="password"
                      placeholder="Enter your password" class="form-control z-1"
                      :class="{ 'input-error': errors.password }" />
                    <i :class="showPassword ? 'bi bi-eye-slash' : 'bi bi-eye'"
                      class="text-dark icon-eye fs-5 position-absolute z-3" @click="togglePassword"></i>
                    <div v-if="errors.password" class="text-danger position-absolute top-100" style="font-size: 13px;">
                      {{ errors.password }}</div>

                  </div>
                </div>
              </div>

              <div class="col-lg-12">
                <div class="d-flex justify-content-between">
                  <div class="form-check">
                    <input v-model="rememberMe" type="checkbox" class="form-check-input" id="check" />
                    <label for="check" class="form-check-label">Remember me</label>
                  </div>
                  <RouterLink to="/forget">Forgot password?</RouterLink>
                </div>
              </div>

              <div class="col-lg-12">
                <button @click.prevent="handleLogin" class="btn btn-main w-100 mt-3">Login</button>
              </div>

              <div class="col-lg-12">
                <div class="d-flex justify-content-between">
                  <hr style="width: 35%;">or continue with
                  <hr style="width: 35%;">
                </div>
              </div>

              <div class="col-lg-12">
                <div class="d-flex justify-content-center gap-3 my-3">
                  <a href="#" @click.prevent="showMessage('Facebook login is not available yet')">
                    <i class="bi bi-facebook fs-4 bg-light px-5 py-3"></i>
                  </a>
                  <a href="#" @click.prevent="showMessage('Google login is not available yet')">
                    <i class="bi bi-google fs-4 bg-light px-5 py-3"></i>
                  </a>
                  <a href="#" @click.prevent="showMessage('Telegram login is not available yet')">
                    <i class="bi bi-telegram fs-4 bg-light px-5 py-3"></i>
                  </a>
                </div>
              </div>


              <p class="text-center">Don't have an account? <router-link to="/signup"> Sign Up</router-link></p>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
const showMessage = (msg) => {
  alert(msg)
}

import { computed, ref, onMounted } from 'vue'
import { RouterLink, useRouter } from 'vue-router'

const password = ref('')
const showPassword = ref(false)
const loginError = ref('')
const errors = ref({})
const router = useRouter()

const emailInput = ref('')
const rememberMe = ref(false)

//this for auto insert @gmail.com for user
const email = computed(() => {
  const value = emailInput.value.trim() //auto add @gmail.com
  return value.includes('@') ? value : `${value}@gmail.com` //give user choose input full mail format or only name of mail can the same login
})

// remembered email and pw
onMounted(() => {
  const savedPassword = localStorage.getItem('rememberedPassword') //delete it if don't want remeber pw
  const savedEmail = localStorage.getItem('rememberedEmail')
  if (savedEmail && savedPassword) { //delete && savedPassword if don't want to save pw
    emailInput.value = savedEmail
    password.value = savedPassword
    rememberMe.value = true
  }
})

const handleLogin = () => {
  loginError.value = ''
  errors.value = {}

  // Email validation
  if (!emailInput.value) {
    errors.value.emailInput = 'Email is required'
  } else if (
    !/^[a-zA-Z0-9._%+-]+$/.test(emailInput.value) &&
    !/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(emailInput.value)
  ) {
    errors.value.emailInput = 'Invalid email format'
  }

  // Password validation
  if (!password.value) {
    errors.value.password = 'Password is required'
  } else if (password.value.length < 6) {
    errors.value.password = 'Password must be at least 6 characters'
  }

  // when it error stop here 
  if (Object.keys(errors.value).length > 0) return

  // login check =======================
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const match = users.find(u => u.email === email.value && u.password === password.value)

  if (match) {
    localStorage.setItem('isLoggedIn', 'true')
    localStorage.setItem('user', JSON.stringify({
      email: match.email,
      username: match.username,
      password: match.password
    }))

    // Handle of remember me
    if (rememberMe.value) {
      localStorage.setItem('rememberedEmail', emailInput.value)
      localStorage.setItem('rememberedPassword', password.value) //delete it if don't want remeber pw
    } else {
      localStorage.removeItem('rememberedEmail')
      localStorage.removeItem('rememberedPassword') //delete it if don't want remeber pw
    }
    // if everything true go to home 
    router.push('/home')
  } else {
    loginError.value = 'Incorrect email or password'
    setTimeout(() => {
      loginError.value = ''
    }, 3000) //else show error message and auto gone 3s
  }
}
const togglePassword = () => {
  showPassword.value = !showPassword.value
}
</script>


<style scoped>
.form-control:focus {
  box-shadow: none;
}

.icon-eye {
  right: 30px;
  top: 50% !important;
  transform: translateY(-50%);
  cursor: pointer;
}

.input-error {
  border: 1px solid red !important;
  outline: none;
  box-shadow: none;
}
</style>
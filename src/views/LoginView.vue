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
                    <input v-model="email" type="email" placeholder="Enter your email" class="py-2 form-control"
                      :class="{ 'input-error': errors.email }" />
                    <div v-if="errors.email" class="text-danger position-absolute top-100" style="font-size: 13px;">{{
                      errors.email }}</div>
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
                    <input type="checkbox" class="form-check-input" id="check">
                    <label for="check" class="form-check-label">Remember me</label>
                  </div>
                  <a href="">forgot password ?</a>
                </div>
              </div>

              <div class="col-lg-12">
                <button type="submit" class="btn btn-main w-100 mt-3">Login</button>
              </div>

              <div class="col-lg-12">
                <div class="d-flex justify-content-between">
                  <hr style="width: 35%;">or continue with
                  <hr style="width: 35%;">
                </div>
              </div>

              <div class="col-lg-12">
                <div class="d-flex justify-content-center gap-3 my-3">
                  <a href=""><i class="bi bi-facebook fs-4 bg-light px-5 py-3"></i></a>
                  <a href=""><i class="bi bi-google fs-4 bg-light px-5 py-3"></i></a>
                  <a href=""><i class="bi bi-telegram fs-4 bg-light px-5 py-3"></i></a>
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
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const showPassword = ref(false)
const loginError = ref('')
const errors = ref({}) // holds field errors
const router = useRouter()

const handleLogin = () => {
  // Clear errors first
  loginError.value = ''
  errors.value = {}

  // Email validation
  if (!email.value) {
    errors.value.email = 'Email is required'
  } else if (!/\S+@\S+\.\S+/.test(email.value)) {
    errors.value.email = 'Invalid email format'
  }

  // Password validation
  if (!password.value) {
    errors.value.password = 'Password is required'
  } else if (password.value.length < 6) {
    errors.value.password = 'Password must be at least 6 characters'
  }

  // If my validation errors, stop here
  if (Object.keys(errors.value).length > 0) return

  //  login check
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const match = users.find(u => u.email === email.value && u.password === password.value)
  if (match) {
    localStorage.setItem('isLoggedIn', 'true')
    router.push('/home')
  } else {
    loginError.value = 'Incorrect email or password'
    setTimeout(() => {
      loginError.value = ''
    }, 3000)
  }
}

// hide and show pw 
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
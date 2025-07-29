<template>
  <div class="container">
    <div class="row min-vh-100 justify-content-center align-items-center">
      <div class="col-lg-6">
        <div class="card p-5 bg-white border-0 shadow">
          <div class="card-body">
            <h2 class="text-center">Create Your Account</h2>
            <p class="mb-5 text-center">Please fill in your details to sign up</p>

            <form @submit.prevent="handleSignup" class="row g-3">

              <div v-if="signupError" class="text-danger text-center" style="font-size: 14px;">{{ signupError }}</div>

              <div class="col-lg-12">
                <div class="mb-3">
                  <div class="input-group position-relative">
                    <i class="bi bi-envelope text-dark input-group-text fs-5"></i>
                    <input v-model="email" type="email" placeholder="Enter your email" class="py-2 form-control"
                      :class="{ 'input-error': errors.email }" />
                    <div v-if="errors.email" class="text-danger position-absolute top-100" style="font-size: 13px;">{{ errors.email }}</div>
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
                    <div v-if="errors.password" class="text-danger position-absolute top-100" style="font-size: 13px;">{{ errors.password }}</div>
                  </div>
                </div>
              </div>

              <div class="col-lg-12">
                <button type="submit" class="btn btn-main w-100 mt-3">Sign Up</button>
              </div>

              <p class="text-center">Already have an account? <router-link to="/">Login</router-link></p>

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
const errors = ref({})
const signupError = ref('')
const router = useRouter()

const togglePassword = () => {
  showPassword.value = !showPassword.value
}

const handleSignup = () => {
  errors.value = {}
  signupError.value = ''

  // validation
  if (!email.value) {
    errors.value.email = 'Email is required'
  } else if (!/\S+@\S+\.\S+/.test(email.value)) {
    errors.value.email = 'Invalid email format'
  }

  if (!password.value) {
    errors.value.password = 'Password is required'
  } else if (password.value.length < 6) {
    errors.value.password = 'Password must be at least 6 characters'
  }

  if (Object.keys(errors.value).length > 0) return

  // store user in localStorage
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const exists = users.find(u => u.email === email.value)

  if (exists) {
    signupError.value = 'This email is already registered'
    return
  }

  users.push({ email: email.value, password: password.value })
  localStorage.setItem('users', JSON.stringify(users))

  router.push('/')
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

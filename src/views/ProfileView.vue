<template>
  <div class="container">
    <div class="row min-vh-100 justify-content-center align-items-center">
      <div class="col-lg-6">
        <div class="card p-5 bg-white border-0 shadow">
          <div class="card-body text-center">
            <h2 class="mb-4">Edit Profile</h2>

            <!-- Profile Image Preview -->
            <div class="mb-3">
              <img :src="previewImage || user.profileImage || defaultImage" class="rounded-circle" width="120"
                height="120" />
              <input type="file" class="form-control mt-2" @change="handleImageUpload" />
            </div>

            <!-- Full Name Input -->
            <div class="input-group mb-3 position-relative">
              <span class="input-group-text"><i class="bi bi-person"></i></span>
              <input v-model="user.username" type="text" class="form-control" placeholder="Full Name"
                :class="{ 'is-invalid': errors.username }" />
              <div class="invalid-feedback position-absolute top-100 start-0">{{ errors.username }}</div>
            </div>

            <!-- Email Input -->
            <div class="input-group mb-3 position-relative">
              <span class="input-group-text"><i class="bi bi-envelope"></i></span>
              <input v-model="emailInput" type="text" class="form-control" placeholder="Gmail name (e.g. lay)"
                :class="{ 'is-invalid': errors.emailInput }" />
              <span class="input-group-text">@gmail.com</span>
              <div class="invalid-feedback position-absolute top-100 start-0">{{ errors.emailInput }}</div>
            </div>

            <button v-if="!updated" class="btn btn-success w-100" @click="updateProfile">
              Save Changes
            </button>

            <RouterLink v-else to="/home" class="btn btn-outline-primary w-100">
              Back to Home
            </RouterLink>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const user = ref({})
const emailInput = ref('')
const previewImage = ref(null)
const errors = ref({})
const defaultImage = '/default-avatar.png' // make sure this image exists in /public
const updated = ref(false)  // track if user updated profile

onMounted(() => {
  const currentUser = JSON.parse(localStorage.getItem('user'))
  const users = JSON.parse(localStorage.getItem('users') || '[]')

  if (!currentUser) {
    router.push('/')
    return
  }

  const match = users.find(u => u.email === currentUser.email)
  if (!match) {
    router.push('/')
    return
  }

  user.value = { ...match }
  emailInput.value = match.email.replace('@gmail.com', '')
})

const handleImageUpload = (e) => {
  const file = e.target.files[0]
  if (!file) return
  const reader = new FileReader()
  reader.onload = () => {
    previewImage.value = reader.result
    user.value.profileImage = reader.result
  }
  reader.readAsDataURL(file)
}

const updateProfile = () => {
  errors.value = {}

  if (!user.value.username) {
    errors.value.username = 'Full name is required'
  } else if (/\d/.test(user.value.username)) {
    errors.value.username = 'Name must not contain numbers'
  }

  if (!emailInput.value) {
    errors.value.emailInput = 'Email name is required'
  } else if (!/^[a-zA-Z0-9._%+-]+$/.test(emailInput.value)) {
    errors.value.emailInput = 'Invalid email format'
  }

  if (Object.keys(errors.value).length > 0) return

  const newEmail = emailInput.value.trim() + '@gmail.com'
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const oldEmail = user.value.email
  const index = users.findIndex(u => u.email === oldEmail)

  if (index === -1) {
    alert('User not found.')
    return
  }

  users[index].email = newEmail
  users[index].username = user.value.username
  users[index].profileImage = user.value.profileImage || ''

  // Save to localStorage
  localStorage.setItem('users', JSON.stringify(users))
  localStorage.setItem('user', JSON.stringify(users[index]))

  updated.value = true // Mark as updated to toggle buttons
  alert('Profile updated successfully!')
  // location.reload()
}
</script>

<style scoped>
img {
  object-fit: cover;
}
</style>

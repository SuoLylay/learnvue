<template>
  <header class="fixed-top top-0">
    <nav class="navbar navbar-expand-lg" id="navbar">
      <div class="container">
        <a class="navbar-brand" href="#"><img :src="logo" alt="" style="width: 80px" /></a>
        <button class="navbar-toggler" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasNavbar"
          aria-controls="offcanvasNavbar" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="offcanvas offcanvas-start" tabindex="-1" id="offcanvasNavbar"
          aria-labelledby="offcanvasNavbarLabel">
          <div class="offcanvas-header">
            <h5 class="offcanvas-title" id="offcanvasNavbarLabel">
              Offcanvas
            </h5>
            <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
          </div>
          <div class="offcanvas-body">
            <ul class="navbar-nav m-auto">
              <li class="nav-item">
                <RouterLink class="nav-link active" to="/home">Home</RouterLink>
              </li>

              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                  aria-expanded="false">
                  Admissions
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="bachelor.html">Bachelor’s Admission</a></li>
                  <li>
                    <a class="dropdown-item" href="master.html">Master’s Admission</a>
                  </li>
                  <li>
                    <a class="dropdown-item" href="transfer.html">Transfer</a>
                  </li>
                </ul>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="event.html">Event</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="scholarship.html">Scholarship</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                  aria-expanded="false">
                  Acadamics
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Action</a></li>
                  <li>
                    <a class="dropdown-item" href="#">Another action</a>
                  </li>
                  <li>
                    <hr class="dropdown-divider" />
                  </li>
                  <li>
                    <a class="dropdown-item" href="#">Something else here</a>
                  </li>
                </ul>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" to="/about">About Us</RouterLink>

              </li>
              <li class="nav-item">
                <a class="nav-link" href="contact.html">{{ title }}</a>
              </li>
            </ul>
            <div>
              <div v-if="isLoggedIn" class="dropdown">
                <button class="btn btn-outline-light dropdown-toggle d-flex align-items-center" type="button" data-bs-toggle="dropdown">
                   <div class="d-flex align-items-center justify-content-center rounded-circle me-2 bg-dark text-light" style="width: 30px!important; height: 30px!important;">
                    {{ user?.username?.substring(0, 2).toUpperCase() }}
                  </div>
                  {{ user?.username }}
                </button>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Profile</a></li>
                  <li><a class="dropdown-item" @click="logout" style="cursor: pointer;">Logout</a></li>
                </ul>
              </div>
              <div v-else>
                <RouterLink to="/enroll" class="btn btn-main btn-outline-light me-2">Enroll Now <i
                    class="bi bi-person-plus"></i></RouterLink>
                <RouterLink to="/" class="btn btn-secondary">Login</RouterLink>
              </div>

            </div>
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>
<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'
import logo from '@/assets/img/logo.png'

const title = 'Contact'
const user = ref(null)
const isLoggedIn = ref(false)
const router = useRouter()

onMounted(() => {
  const savedUser = localStorage.getItem('user')
  if (savedUser) {
    user.value = JSON.parse(savedUser)
    isLoggedIn.value = true
  }
})

const logout = () => {
  localStorage.removeItem('user')
  localStorage.removeItem('isLoggedIn')
  router.push('/')
  
  // location.reload() it forces full page refresh, but cancels the redirect.
}
</script>

<template>
     <footer class="mt-10 pt-5 bg-main">
    <div class="container">
      <div class="row justify-content-between">
        <div class="col-lg-4">
          <div class="footer-logo">
            <img :src="logo" alt="" class="img-fluid" />
          </div>
          <p class="mt-3 color-white">Cambodia's leading digital agency, providing innovative solutions to help
            businesses thrive in the digital landscape.</p>
        </div>
        <div class="col-lg-2">
          <h5 class="text-white mb-3">Quick Links</h5>
          <ul class="list-unstyled lh-lg">
            <li><a href="#" class="text-white">Home</a></li>
            <li><a href="#" class="text-white">About</a></li>
            <li><a href="#" class="text-white">Services</a></li>
            <li><a href="#" class="text-white">Contact</a></li>
          </ul>
        </div>
        <div class="col-lg-2">
          <h5 class="text-white mb-3">Follow Us</h5>
          <ul class="list-unstyled lh-lg">
            <li><a href="#" class="text-white">Facebook</a></li>
            <li><a href="#" class="text-white">Twitter</a></li>
            <li><a href="#" class="text-white">Instagram</a></li>
            <li><a href="#" class="text-white">LinkedIn</a></li>
          </ul>
        </div>
        <div class="col-lg-3">
          <h5 class="text-white mb-3">Contact Us</h5>
          <p class="text-white" style="text-align: justify;">
            <i class="fa-solid fa-map-marker-alt me-2"></i>N0.23, st.606, Songkat Boeung Keng Kang 1, Khan Chamkarmon,
            Phnom Penh, Cambodia.
          </p>
          <p class="text-white">
            <i class="fa-solid fa-phone me-2"></i>+855 16 939 895
          </p>
          <p class="text-white">
            <i class="fa-solid fa-envelope me-2"></i>info@example.com
          </p>
        </div>
      </div>
    </div>
    <section class="py-3 mt-3" style="background-color: #1e1e3d;">
      <div class="container">
        <div class="row">
          <div class="col-12 ">
            <div class="d-flex justify-content-between">
              <a class="text-white mb-0">&copy; 2025 Cambodia Academy. All rights reserved.</a>
              <div class="footer-links">
                <a href="#" class="text-white">Terms</a>
                <a href="#" class="text-white ms-3">Privacy</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </footer>
</template>
<script setup>
    import logo from '@/assets/img/logo.png'
</script>
<template>
  <Navbar />
  <Hero />
   <!-- search  -->
    <section class="bg-main py-4">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-4">
            <h2 class="color-white">Find Your Perfect Programs</h2>
          </div>
          <div class="col-lg-8">
            <div class="row gx-3">
              <div class="col-lg-10">
                <div class="d-flex rounded overflow-hidden bg-white">
                  <select name="" id="" class="form-select border-1 border-start rounded-0 w-auto bg-transparent">
                    <option value="">Undergradute </option>
                    <option value="">Postgradute</option>
                    <option value="">Ph.D</option>
                  </select>
                  <div class="bg-white d-flex w-100 position-relative align-items-center px-3 bg-transparent">
                    <i class="fa-solid fa-magnifying-glass position-absolute"></i>
                    <input type="search" placeholder="Search undergradute degree program..."
                      class="form-control border-0 rounded-0 px-4 search w-100">    
                  </div>
                </div>
              </div>
              <button class="btn btn-accent color-white px-3 col-lg-2">Search <i
                  class="fa-light fa-magnifying-glass"></i></button>
              <div class="mt-4">
                <div class="col-lg-12">
                  <div class="row">
                    <div class="col-lg-4">
                      <div class="d-flex align-items-center">
                        <i class="fa-light fa-user-graduate fs-4 me-2 bg-success p-2 text-light"></i>
                        <div class="d-flex flex-column justify-content-center">
                          <p class="mb-0 color-secondary sub-title">Are just after A/L</p>
                          <p class="mb-0 text-light">Undergradute Degree</p>
                        </div>
                      </div>
                    </div>
                    <div class="col-lg-4">
                      <div class="d-flex align-items-center">
                        <i class="fa-light fa-user-graduate fs-4 me-2 bg-info p-2 text-light"></i>
                        <div class="d-flex flex-column justify-content-center">
                          <p class="mb-0 color-secondary sub-title">Are holding a first degree.</p>
                          <p class="mb-0 text-light">Postgradute Degree</p>
                        </div>
                      </div>
                    </div>
                    <div class="col-lg-4">
                      <div class="d-flex align-items-center">
                        <i class="fa-light fa-user-graduate fs-4 me-2 bg-accent p-2 text-light"></i>
                        <div class="d-flex flex-column justify-content-center">
                          <p class="mb-0 color-secondary sub-title">Are looking development</p>
                          <p class="mb-0 text-light">Professional Degree</p>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>  
            </div>
          </div>
        </div> 
      </div>
    </section>

       <!-- Courses -->
    <section class="mt-20 bg-white course" data-aos="fade-up">
      <div class="container">
        <div class="text-center w-75 m-auto mb-5">
          <h3>Explore Our Skills</h3>
          <p>
            We train students to express themselves clearly and
            confidently—both in writing and speaking—preparing them for
            academic presentations, leadership roles, and global careers.
          </p>
        </div>
        <div class="row gy-4">
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex">
                  <!-- <i class="bi bi-palette fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/1.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Art & Design</h5>
                    <p class="card-text">Grow your design skill</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex">
                  <!-- <i class="bi bi-database fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/3.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Data Science</h5>
                    <p class="card-text">Discover data science</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex align-items-center">
                  <!-- <i class="fa-light fa-shield-check fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/4.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Architecture</h5>
                    <p class="card-text">Grow your design skill</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex align-items-center">
                  <!-- <i class="fa-light fa-money-bill-trend-up fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/2.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Marketing</h5>
                    <p class="card-text">Take up to next level.</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex align-items-center">
                  <!-- <i class="bi bi-coin me-3 fs-1 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/6.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Account</h5>
                    <p class="card-text">Grow your accounting skill.</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex align-items-center">
                  <!-- <i class="bi bi-diagram-3 fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/5.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Management</h5>
                    <p class="card-text">Mange your buissis.</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex align-items-center">
                  <!-- <i class="bi bi-graph-up fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/6.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">Finnace</h5>
                    <p class="card-text">Discover your cash.</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
          <div class="col-lg-3">
            <a href="">
              <div class="card border-0 my-shadow">
                <div class="card-body d-flex align-items-center">
                  <!-- <i class="fa-light fa-microchip fs-1 me-3 color-accent"></i> -->
                  <img src="https://educrat-nextjs.vercel.app/assets/img/featureCards/3.svg" alt="" class="me-3">
                  <span>
                    <h5 class="card-title mt-1">IT</h5>
                    <p class="card-text">Technology in your hand.</p>
                  </span>
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
    </section>

     <!-- Event  -->
    <section class="mt-20 bg-body">
      <div class="container">
        <div class="text-center w-75 m-auto mb-5">
          <h3>Upcoming Events</h3>
          <p>
            Join us for our upcoming events and activities at Cambodia
            Academy! We have a variety of exciting opportunities for students,
            faculty, and the community to engage, learn, and grow together.
          </p>
        </div>
        <div class="row g-5">
          <div class="col-lg-12">  
            <Swiper/> 
          </div>   
        </div>
      </div>
    </section>
    <!-- modal  -->
     <div class="modal fade" id="learn-1" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
          <div class="modal-dialog modal-dialog-centered modal-dialog-scrollable modal-lg">
            <div class="modal-content p-5 rounded-5">
              <div class="modal-body">
                <div class="row">
                  <div class="col-lg-6">
                    <img :src="cardimg1" alt="" class="img-fluid" />
                  </div>
                  <div class="col-lg-6">
                    <h4 class="modal-title m-auto mb-3" id="exampleModalLabel2">
                      Seminar on master's scholarship opportunities
                      in Germany
                    </h4>
                    <div class="lh-1">
                      <p>
                        Ideal for: Students, graduates, and
                        professionals
                      </p>
                      <p>
                        <i class="fa-solid fa-calendar-days me-1 color-primary"></i>
                        April 25, 2025
                      </p>
                      <p>
                        <i class="fa-solid fa-clock me-1 color-primary"></i>
                        09:00am - 04:00pm
                      </p>
                      <h6>Presentation By</h6>
                      <div class="d-flex align-items-center">
                        <div class="presentor">
                          <img :src="modalpf" alt="" class="img-fluid" />
                        </div>
                        <span class="lh-base ms-3 mt-2">
                          <p class="mb-0">Mr.Hong Channa</p>
                          <p>Professor of Angkor</p>
                        </span>
                      </div>
                    </div>
                  </div>
                  <div class="col-lg-12">
                    <h6 class="mt-3">Event detail</h6>
                    <p class="mt-3">
                      Planning to study in Germany for your Master’s
                      degree? This seminar is designed to guide you
                      through the wide range of scholarship options
                      available to international students. Get
                      expert insights on: Major scholarship programs
                      like DAAD, Erasmus+, and university-specific
                      funding How to meet eligibility requirements
                      and application deadlines Crafting a strong
                      motivation letter and supporting documents
                      Real experiences and tips from current
                      scholarship holders Whether you're just
                      starting your application journey or
                      finalizing your documents, this seminar offers
                      valuable advice to help fund your studies in
                      Germany.
                    </p>

                    <p>
                      Take the first step toward studying in
                      Germany—join us and get one step closer to
                      securing a scholarship!
                    </p>

                    <h6>For more information</h6>
                    <p class="mb-0 pb-0">
                      <i class="fa-solid fa-phone-volume me-1 color-primary"></i>
                      (+855) 16 939 895
                    </p>
                    <p>
                      <i class="fa-solid fa-envelope color-primary me-2"></i>cambodia@gmail.edu.kh
                    </p>
                  </div>
                </div>
              </div>
              <div class="modal-footer">
                <button type="button" class="btn btn-secondary btn-sm" data-bs-dismiss="modal">
                  Close
                </button>
                <a href="#" class="btn btn-main btn-sm">Register <i class="bi bi-person-add"></i></a>
              </div>
            </div>
          </div>
        </div>
  <Footers/>

</template>
<script setup>
  import Navbar from '@/components/Navbar.vue';
  import Swiper from '@/components/layout/Swiper.vue';
  import Hero from '@/components/Hero.vue';
  import Footers from '@/components/Footer.vue';
  import cardimg1 from "@/assets/img/banner/student day.jpeg";
  import modalpf from "@/assets/img/avata/avatar-1.jpg";


  const event = [
    {
      id : 0,
      img: cardimg1,
      title: ' International Students Day of 2025',
      date: 'November 17, 2025',
      time: '09:00am - 04:00pm',
    },
    {
      id : 1,
      img: 'src/assets/img/banner/event1.jpg',
      title: 'International Students Day of 2025',
      date: 'November 17, 2025',
      time: '09:00am - 04:00pm',
    },
    {
      id : 2,
      img: 'src/assets/img/banner/event2.jpg',
      title: 'International Students Day of 2025',
      date: 'November 17, 2025',
      time: '09:00am - 04:00pm',
    },
    {
      id : 3,
      img: 'src/assets/img/banner/event3.jpg',
      title: 'International Students Day of 2025',
      date: 'November 17, 2025',
      time: '09:00am - 04:00pm',
    }
  ]

    // change bg-color navbar
  window.addEventListener("scroll", function () {
    var navbar = document.querySelector(".navbar");
    var navbarHeight = navbar.offsetHeight;

    if (window.scrollY > navbarHeight) {
      navbar.classList.add("navbar-scrolled");
      navbar.classList.add("navlink-scrolled");
    } else {
      navbar.classList.remove("navbar-scrolled");
      navbar.classList.remove("navlink-scrolled");
    }
  });

  /* When the user scrolls down, hide the navbar. When the user scrolls up, show the navbar */
  var prevScrollpos = window.pageYOffset;
  window.onscroll = function () {
    var currentScrollPos = window.pageYOffset;
    if (prevScrollpos > currentScrollPos) {
      document.getElementById("navbar").style.top = "0";
    } else {
      document.getElementById("navbar").style.top = "-150px";
    }
    prevScrollpos = currentScrollPos;
  };
</script>


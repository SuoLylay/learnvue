<template>
     <!-- herobanner  -->
  <section>
    <div id="carouselExampleFade" class="carousel slide carousel-fade" data-bs-ride="carousel">
      <div class="carousel-inner">
        <div class="carousel-item active" v-for="item in data" :key="item.id">
          <img :src="item.image" class="w-100" alt="..." style="filter: brightness(30%)" />
          <div class="carousel-caption top-50">
            <h1 class="text-uppercase title-banner color-white animate__animated animate__fadeInDown">
              {{ item.title }}
            </h1>
            <p class="color-white fs-5 animate__animated animate__fadeInUp my-3">
              {{ item.text }}
            </p>
            <div class="animate__animated animate__fadeIn">
              <a href="#" class="btn btn-main">Enroll Now <i class="bi bi-person-plus"></i></a>
              <a href="#" class="btn btn-secondary ms-3">Learn more <i class="bi bi-chevron-right"></i></a>
            </div>
          </div>
        </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleFade" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleFade" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </section>
</template>
<script setup>
import banner1 from '@/assets/img/banner/school banner.jpg'
import banner2 from '@/assets/img/banner/student-banner2.jpg'
import banner3 from '@/assets/img/banner/cmu6.jpg'

import { reactive } from 'vue';

const data = [
  {
    id: 0,
    image: banner1,
    title: 'CAMBODIA ACADAMY',
    text: 'At Cambodia Acadamy, we are committed to fostering a culture of excellence, where every student is inspired to reach their full potential.'
    },
  {
    id: 1,
    image: banner2,
    title: 'A Legacy of Excellence in Education',
    text: 'ffAt Cambodia Acadamy, we are committed to fostering a culture of excellence, where every student is inspired to reach their full potential.'
  },
  {
    id: 1,
    image: banner3,
    title: 'CAMBODIA ACADAMY',
    text: 'is the acadamy that care about value of education.'
  },
]
</script>

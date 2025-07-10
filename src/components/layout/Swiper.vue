<template>
  <Swiper
    :slides-per-view="1"
    :space-between="10"
    :pagination="{ clickable: true }"
    :breakpoints="breakpoints"
    :modules="swiperModules"
    class="mySwiper"
  >
    <SwiperSlide v-for="card in event" :key="card.id">
      <div class="card my-shadow border-0 rounded-4">
        <img
          :src="card.img"
          alt="Event Image"
          class="card-img-top rounded-4 card-img-height"
        />
        <div class="card-body">
          <h6 class="card-title mb-3">
            {{ card.title }}
          </h6>
          <div class="d-flex justify-content-end align-items-end">
            <span>
              <p class="card-text mb-0">
                <i class="fa-light fa-calendar-days me-1 color-primary"></i>
                {{ card.date }}
              </p>
              <p class="card-text">
                <i class="fa-light fa-clock me-1 color-primary"></i>
                {{ card.time }}
              </p>
            </span>
            <a
              href="#"
              class="color-primary text-decoration-none ms-auto"
              data-bs-toggle="modal"
              data-bs-target="#learn-1"
            >
              <i class="fa-solid fa-angle-right btn-outline-main rounded-circle px-2 py-1 fs-5"></i>
            </a>
          </div>
        </div>
      </div>
    </SwiperSlide>
  </Swiper>
</template>

<script setup>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue'

// Import Swiper styles
import 'swiper/css'
import 'swiper/css/pagination'

// Import Swiper module
import { Pagination } from 'swiper/modules'

// Define Swiper modules
const swiperModules = [Pagination]

// Dummy image import or use relative paths
// import cardimg1 from '@/assets/img/banner/event0.jpg'

const event = [
  {
    id: 0,
    img: 'src/assets/img/banner/event0.jpg', // Use real path or import
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
  },
  {
    id: 1,
    img: 'src/assets/img/banner/event1.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
  },
  {
    id: 2,
    img: 'src/assets/img/banner/event2.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
  },
  {
    id: 3,
    img: 'src/assets/img/banner/event3.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
  },
  {
    id: 4,
    img: 'src/assets/img/banner/event3.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
  },
]

// Optional: extract breakpoints
const breakpoints = {
  640: {
    slidesPerView: 2,
    spaceBetween: 20,
  },
  768: {
    slidesPerView: 4,
    spaceBetween: 40,
  },
  1024: {
    slidesPerView: 4.2,
    spaceBetween: 50,
  },
}
</script>

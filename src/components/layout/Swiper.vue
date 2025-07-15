<template>
  <Swiper
    :slides-per-view="1"
    :space-between="10"
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
          <h6 class="card-title mb-3">{{ card.title }}</h6>
          <div class="d-flex justify-content-end align-items-end">
            <span>
              <p class="card-text mb-0">
                <i class="fa-regular fa-calendar-days me-1 color-primary"></i>
                {{ card.date }}
              </p>
              <p class="card-text">
                <i class="fa-regular fa-clock me-1 color-primary"></i>
                {{ card.time }}
              </p>
            </span>
            <button
              class="color-primary text-decoration-none ms-auto btn btn-link p-0"
              @click="openModal(card.id)"
              aria-label="Open event details"
            >
              <i
                class="fa-solid fa-angle-right btn-outline-main rounded-circle px-2 py-1 fs-5"
              ></i>
            </button>
          </div>
        </div>
      </div>
    </SwiperSlide>
  </Swiper>

  <!-- Modal -->
  <div
    v-for="modal in event"
    :key="'modal-' + modal.id"
    class="modal fade"
    :id="'learn-' + modal.id"
    tabindex="-1"
    :aria-labelledby="'label-' + modal.id"
    aria-hidden="true"
    ref="modalRefs"
  >
    <div class="modal-dialog modal-dialog-centered modal-dialog-scrollable modal-lg">
      <div class="modal-content p-5 rounded-5">
        <div class="modal-body">
          <div class="row">
            <div class="col-lg-6">
              <img :src="modal.img" alt="Modal Image" class="img-fluid" />
            </div>
            <div class="col-lg-6">
              <h4 class="modal-title mb-3" :id="'label-' + modal.id">
                {{ modal.title }}
              </h4>
              <p>Ideal for: Students, graduates, and professionals</p>
              <p>
                <i class="fa-solid fa-calendar-days me-1 color-primary"></i>
                {{ modal.date }}
              </p>
              <p>
                <i class="fa-solid fa-clock me-1 color-primary"></i>
                {{ modal.time }}
              </p>
              <h6>Presentation By</h6>
              <div class="d-flex align-items-center">
                <div class="ms-3">
                  <p class="mb-0">Mr. Hong Channa</p>
                  <small>Professor of Angkor</small>
                </div>
              </div>
            </div>
            <div class="col-lg-12 mt-4">
              <h6>Event detail</h6>
              <p>{{ modal.description }}</p>
              <p>
                Take the first step toward studying in Germany—join us and get one step closer to
                securing a scholarship!
              </p>
              <h6>For more information</h6>
              <p>
                <i class="fa-solid fa-phone-volume me-1 color-primary"></i>
                (+855) 16 939 895
              </p>
              <p>
                <i class="fa-solid fa-envelope color-primary me-2"></i>
                cambodia@gmail.edu.kh
              </p>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary btn-sm"
            @click="closeModal(modal.id)"
          >
            Close
          </button>
          <a href="#" class="btn btn-main btn-sm"
            >Register <i class="bi bi-person-add"></i
          ></a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/pagination'
import { Pagination } from 'swiper/modules'

// Import Bootstrap JS Modal class (you must have bootstrap installed or linked in your index.html)
import Modal from 'bootstrap/js/dist/modal'

const swiperModules = [Pagination]
const breakpoints = {
  640: { slidesPerView: 2, spaceBetween: 20 },
  768: { slidesPerView: 4, spaceBetween: 40 },
  1024: { slidesPerView: 4.2, spaceBetween: 50 },
}

const event = [
  {
    id: 0,
    img: 'src/assets/img/banner/student day.jpeg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
    description: `Planning to study in Germany for your Master’s degree? This seminar is designed to guide you through a wide range of scholarship options available to international students. Get expert insights on major scholarship programs like DAAD, Erasmus+, and university-specific funding. Learn how to meet eligibility requirements, application deadlines, and craft strong documents. This seminar offers valuable advice to help fund your studies in Germany.`,
  },
  {
    id: 1,
    img: 'src/assets/img/banner/event1.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
    description: `Planning to study in Germany for your Master’s degree? This seminar is designed to guide you through a wide range of scholarship options available to international students. Get expert insights on major scholarship programs like DAAD, Erasmus+, and university-specific funding. Learn how to meet eligibility requirements, application deadlines, and craft strong documents. This seminar offers valuable advice to help fund your studies in Germany.`,
  },
  {
    id: 2,
    img: 'src/assets/img/banner/event2.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
    description: `Planning to study in Germany for your Master’s degree? This seminar is designed to guide you through a wide range of scholarship options available to international students. Get expert insights on major scholarship programs like DAAD, Erasmus+, and university-specific funding. Learn how to meet eligibility requirements, application deadlines, and craft strong documents. This seminar offers valuable advice to help fund your studies in Germany.`,
  },
  {
    id: 3,
    img: 'src/assets/img/banner/event3.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
    description: `Planning to study in Germany for your Master’s degree? This seminar is designed to guide you through a wide range of scholarship options available to international students. Get expert insights on major scholarship programs like DAAD, Erasmus+, and university-specific funding. Learn how to meet eligibility requirements, application deadlines, and craft strong documents. This seminar offers valuable advice to help fund your studies in Germany.`,
  },
  {
    id: 4,
    img: 'src/assets/img/banner/event4.jpg',
    title: 'International Students Day of 2025',
    date: 'November 17, 2025',
    time: '09:00am - 04:00pm',
    description: `Planning to study in Germany for your Master’s degree? This seminar is designed to guide you through a wide range of scholarship options available to international students. Get expert insights on major scholarship programs like DAAD, Erasmus+, and university-specific funding. Learn how to meet eligibility requirements, application deadlines, and craft strong documents. This seminar offers valuable advice to help fund your studies in Germany.`,
  },
  // add your other events here
]

const modalInstances = ref({})
const modalRefs = ref([])

onMounted(() => {
  // Initialize Bootstrap modal instances for each modal element
  modalRefs.value.forEach((modalEl) => {
    const modalId = modalEl.id
    modalInstances.value[modalId] = new Modal(modalEl, {
      backdrop: 'static',
      keyboard: false,
    })
  })
})

function openModal(id) {
  const modal = modalInstances.value[`learn-${id}`]
  if (modal) {
    modal.show()
  }
}

function closeModal(id) {
  const modal = modalInstances.value[`learn-${id}`]
  if (modal) {
    modal.hide()
  }
}
</script>

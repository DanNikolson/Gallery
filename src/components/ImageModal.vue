<template>
  <div
    v-if="showModal"
    class="fixed z-1 top-0 left-0 w-full h-full bg-black/50 flex items-center justify-center background-animation"
    @click="closeModal"
  >
    <img
      src="/public/cross.svg"
      class="absolute top-2 right-2 w-5 cursor-pointer"
      @click="closeModal"
    />

    <transition name="modal-content">
      <div class="modal-content" v-if="showModal">
        <img :src="modalImageURL" alt="Увеличенное изображение" class="modal-image" />
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const showModal = ref(false)
const modalImageURL = ref('')

const openModal = (largeImageURL) => {
  modalImageURL.value = largeImageURL
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
}
window.addEventListener('openModal', (event) => {
  openModal(event.detail.largeImageURL)
})
</script>

<style scoped>
.background-animation {
  animation: fadeIn 0.5s forwards;
}

.modal-content {
  animation: slideIn 0.5s forwards;
}

.modal-image {
  max-width: 90vw;
  max-height: 90vh;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideIn {
  from {
    transform: scale(0.5);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}
</style>

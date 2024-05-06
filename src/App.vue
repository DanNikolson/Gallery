<script setup>
import { ref } from 'vue'
import { onMounted } from 'vue'
import axios from 'axios'
import ImageList from './components/ImageList.vue'
import ImageModal from './components/ImageModal.vue'

const items = ref([])

const fetchItems = async () => {
  try {
    const { data } = await axios.get(
      `https://pixabay.com/api/?key=43742980-fd292e2d27c2d59d448f6ff81&q=science&image_type=photo`
    )
    items.value = data.hits.map((obj) => ({
      ...obj
    }))
  } catch (err) {
    console.log('Что-то пошло не так')
  }
}

onMounted(async () => {
  await fetchItems()
})
</script>

<template>
  <div class="flex mt-2 items-center flex-col">
    <h2 class="text-3xl font-bold">Галерея</h2>
  </div>

  <div class="mt-4">
    <ImageList :items="items" />
    <ImageModal />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const message = ref('Loading...')

onMounted(async () => {
  try {
    const res = await fetch('http://localhost:8080/api/status')
    const data = await res.json()
    message.value = data.message
  } catch (error) {
    message.value = 'Error fetching data'
  }
})
</script>

<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>

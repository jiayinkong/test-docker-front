<script setup>
import HelloWorld from './components/HelloWorld.vue'
import { ref, onMounted } from 'vue'
import axios from 'axios'

const data = ref([])

onMounted(() => {
  axios.get('http://localhost:3000/api/users')
    .then(res => {
      data.value = res.data
    })
})

</script>

<template>
  <ul>
    <li v-for="user in data" :key="user.id">
      {{ user.name }}
    </li>
  </ul>
</template>


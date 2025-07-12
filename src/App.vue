<script setup>
// Tambahkan 'computed' dari vue
import { ref, computed } from 'vue'

const message = ref('Halo Vue!')
const titleClass = ref('title')

const counter = ref(0)
function increment() { counter.value++ }

const text = ref('')

const awesome = ref(true)

let id = 0
const todos = ref([
  { id: id++, text: 'Belajar HTML' },
  { id: id++, text: 'Belajar CSS' },
  { id: id++, text: 'Belajar JavaScript' }
])

// Computed property untuk membalik pesan
const reversedMessage = computed(() => {
  return message.value.split('').reverse().join('')
})
</script>

<template>
  <h1 :class="titleClass">{{ message }}</h1>
  <p>Pesan terbalik: {{ reversedMessage }}</p>

  <hr>
  <button @click="increment">Counter: {{ counter }}</button>

  <hr>
  <input v-model="text" placeholder="Ketik sesuatu">
  <p>{{ text }}</p>

  <hr>
  <button @click="awesome = !awesome">Toggle</button>
  <h2 v-if="awesome">Vue is awesome!</h2>
  <h2 v-else>Oh no 😢</h2>
  
  <hr>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
    </li>
  </ul>
</template>

<style>
.title {
  color: #42b883;
}
</style>
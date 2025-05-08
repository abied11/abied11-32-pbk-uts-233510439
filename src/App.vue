<template>
  <div class="wrapper">
    <h1 class="title">🏃‍♂️ Daftar Kegiatan Olahraga</h1>

    <!-- Tambah Kegiatan -->
    <form class="form" @submit.prevent="submitTodo">
      <input
        v-model="text"
        class="input"
        type="text"
        placeholder="Contoh: Futsal,Basket,Voli..."
      />
      <button class="add-btn" type="submit">🏅 Tambah</button>
    </form>

    <!-- Daftar Kegiatan -->
    <div v-if="todos.length === 0" class="empty-msg">Belum ada rencana olahraga hari ini 💤</div>
    <ul class="list">
      <li
        v-for="(todo, index) in filteredTodos"
        :key="index"
        class="todo-item"
        :class="{ done: todo.done }"
      >
        <label>
          <input type="checkbox" v-model="todo.done" />
          <span class="todo-text">{{ todo.text }}</span>
        </label>
        <button class="delete-btn" @click="deleteTodo(index)">❌</button>
      </li>
    </ul>

    <!-- Tombol Filter -->
    <button class="filter-btn" @click="toggleFilter">
      {{ filter ? 'Tampilkan Semua Kegiatan' : 'Hanya Yang Belum Selesai' }}
    </button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const todos = ref([])
const text = ref('')
const filter = ref(false)

function submitTodo() {
  if (text.value.trim()) {
    todos.value.push({ text: text.value.trim(), done: false })
    text.value = ''
  }
}

function deleteTodo(index) {
  todos.value.splice(index, 1)
}

function toggleFilter() {
  filter.value = !filter.value
}

const filteredTodos = computed(() =>
  filter.value ? todos.value.filter(todo => !todo.done) : todos.value
)
</script>

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

    </div>
  </template>
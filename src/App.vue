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
    </div>
  </template>
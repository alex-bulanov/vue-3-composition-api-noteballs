<script setup lang="ts"></script>

<template>
  <div class="view-notes">
    <!--  -->
    <div class="card px-4 py-3">
      <div class="field">
        <label class="label">Новая заметка</label>
        <div class="control">
          <textarea class="textarea" placeholder="Введите текст заметки"></textarea>
        </div>
      </div>

      <div class="field is-grouped is-grouped-right">
        <div class="control">
          <button class="button is-link has-background-success">Добавить новую заметку</button>
        </div>
      </div>
    </div>
    <!--  -->
    <div v-for="_ in 3" :key="_" class="card">
      <header class="card-header">
        <p class="card-header-title">Component</p>
      </header>
      <div class="card-content">
        <div class="content">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?
        </div>
      </div>
      <footer class="card-footer">
        <a href="#" class="card-footer-item">Редактировать</a>
        <a href="#" class="card-footer-item">Удалить</a>
      </footer>
    </div>
  </div>
</template>

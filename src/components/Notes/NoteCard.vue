<script setup lang="ts">
import type { Note } from '@/types'

interface Props {
  note: Note
}

defineProps<Props>()
</script>

<template>
  <div class="note-card card">
    <div class="card-content">
      <div class="content">
        {{ note.content }}
      </div>
    </div>
    <footer class="card-footer">
      <a href="#" class="card-footer-item">Редактировать</a>
      <a href="#" class="card-footer-item">Удалить</a>
    </footer>
  </div>
</template>

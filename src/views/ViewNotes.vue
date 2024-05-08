<script setup lang="ts">
import { v4 as uuidv4 } from 'uuid'
import { ref } from 'vue'
import type { Note } from '@/types'

const notes = ref<Note[]>([
  {
    id: 'id1',
    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?'
  },
  {
    id: 'id2',
    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?'
  },
  {
    id: 'id3',
    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?'
  }
])

const newNoteRef = ref<HTMLTextAreaElement | null>(null)
const newNote = ref<string>('')

const handleAddNote = () => {
  const note = {
    id: uuidv4(),
    content: newNote.value
  } as Note

  notes.value.unshift(note)

  newNote.value = ''
  newNoteRef.value?.focus()
}
</script>

<template>
  <div class="view-notes">
    <!--   -->
    <div class="card px-4 py-3">
      <div class="field">
        <label class="label">Новая заметка</label>
        <div class="control">
          <textarea
            ref="newNoteRef"
            v-model="newNote"
            class="textarea"
            placeholder="Введите текст заметки"
          ></textarea>
        </div>
      </div>

      <div class="field is-grouped is-grouped-right">
        <div class="control">
          <button
            class="button is-link has-background-success"
            :disabled="!newNote"
            @click="handleAddNote"
          >
            Добавить новую заметку
          </button>
        </div>
      </div>
    </div>
    <!--  -->
    <div v-for="note in notes" :key="note.id" class="card">
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
  </div>
</template>

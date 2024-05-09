<script setup lang="ts">
import { v4 as uuidv4 } from 'uuid'
import { ref } from 'vue'
import NoteCard from '@/components/Notes/NoteCard.vue'
import type { ID, Note } from '@/types'

const notes = ref<Note[]>([
  {
    id: 'id1',
    content: '1 Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?'
  },
  {
    id: 'id2',
    content: '2 Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?'
  },
  {
    id: 'id3',
    content: '3 Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, placeat?'
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
const handleDeleteNote = (noteID: ID) => {
  const findIndex = notes.value.findIndex((item) => item.id === noteID)

  if (findIndex !== -1) {
    notes.value.splice(findIndex, 1)
  }
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
    <NoteCard v-for="note in notes" :key="note.id" :note="note" @delete="handleDeleteNote" />
  </div>
</template>

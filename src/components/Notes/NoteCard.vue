<script setup lang="ts">
import type { ID, Note } from '@/types'
import { computed } from 'vue'
import useUtils from '@/composables/useUtils'

interface Props {
  note: Note
}

const props = defineProps<Props>()
const emits = defineEmits<{
  (e: 'delete', id: ID): void
}>()

const { declOfNum } = useUtils()
const charactersLength = computed(() => {
  return `${props.note.content.length} ${declOfNum(props.note.content.length, ['символ', 'символа', 'символов'])}`
})

const handleDelete = () => {
  emits('delete', props.note.id)
}
</script>

<template>
  <div class="note-card card">
    <div class="card-content">
      <div class="content">
        {{ note.content }}

        <div class="mt-2 has-text-right has-text-grey-light">
          <small>{{ charactersLength }} </small>
        </div>
      </div>
    </div>
    <footer class="card-footer">
      <a href="#" class="card-footer-item">Редактировать</a>
      <a href="#" class="card-footer-item" @click.prevent="handleDelete">Удалить</a>
    </footer>
  </div>
</template>

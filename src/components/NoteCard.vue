<script setup>
defineProps({
  note: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["delete"]);
</script>

<template>
  <div class="note-card">
    <h3>{{ note.title }}</h3>
    <p>{{ note.content }}</p>
    <button @click="emit('delete', note.id)">삭제</button>
  </div>
</template>

<style scoped>
.note-card {
  border: 1px solid #ddd;
  padding: 0.75rem;
  margin-bottom: 0.75rem;
  border-radius: 4px;
}
.note-card h3 {
  margin: 0 0 0.5rem 0;
}
</style>

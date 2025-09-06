<script setup>
import { ref } from "vue";

const title = ref("");
const content = ref("");

const emit = defineEmits(["add"]);

function submit() {
  if (!title.value || !content.value) return;
  emit("add", title.value, content.value);
  title.value = "";
  content.value = "";
}
</script>

<template>
  <div class="note-form">
    <input v-model="title" placeholder="제목" />
    <textarea v-model="content" placeholder="내용"></textarea>
    <button @click="submit">추가</button>
  </div>
</template>

<style>
.note-form {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}
.note-form input,
.note-form textarea {
  margin-bottom: 0.5rem;
  padding: 0.5rem;
}
</style>

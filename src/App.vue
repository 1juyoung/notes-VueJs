<script setup>
import { reactive, watch } from "vue";
import NoteForm from "./components/NoteForm.vue";
import NoteCard from "./components/NoteCard.vue";

// 저장된 메모 불러오기
const saved = localStorage.getItem("notes");
const notes = reactive(saved ? JSON.parse(saved) : []);

// 메모 추가
function addNote(title, content) {
  notes.push({ id: Date.now(), title, content });
}

// 메모 삭제
function deleteNote(id) {
  const index = notes.findIndex((note) => note.id === id);
  if (index !== -1) notes.splice(index, 1);
}

// notes 배열 변경 시 localStorage에 저장
watch(
  () => notes,
  (newVal) => {
    localStorage.setItem("notes", JSON.stringify(newVal));
  },
  { deep: true }
);
</script>

<template>
  <div class="app">
    <h1 class="text-3xl font-bold mb-6">📝 메모</h1>

    <NoteForm @add="addNote" />

    <div
      v-if="notes.length > 0"
      class="w-100 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-2 gap-6 mt-6"
    >
      <NoteCard
        v-for="note in notes"
        :key="note.id"
        :note="note"
        @delete="deleteNote"
      />
    </div>
    <p v-else class="text-gray-500 mt-6">
      메모가 없습니다. 새로 작성해보세요 ✨
    </p>
  </div>
</template>

<style>
.app {
  max-width: 900px;
  min-width: 900px;
  padding: 2rem;
  font-family: "Arial", sans-serif;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}
</style>

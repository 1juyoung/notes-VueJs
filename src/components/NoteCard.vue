<script setup>
import Button from "./ui/button/Button.vue";

defineProps({
  note: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["delete"]);
</script>

<template>
  <div
    class="note-card w-full bg-white shadow-md rounded-lg p-4 flex flex-col justify-between hover:shadow-xl transition"
  >
    <div>
      <h3 class="font-semibold text-lg mb-2 text-gray-800 truncate">
        {{ note.title }}
      </h3>
      <p class="text-gray-600 text-sm line-clamp-4">{{ note.content }}</p>
    </div>
    <Button
      class="mt-4 bg-red-500 text-white py-1 rounded hover:bg-red-600 transition"
      @click="emit('delete', note.id)"
    >
      삭제
    </Button>
  </div>
</template>

<style scoped>
.note-card {
  min-height: 200px;
}
</style>

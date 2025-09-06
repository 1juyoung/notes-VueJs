<script setup>
import { ref } from "vue";
import Button from "./ui/button/Button.vue";
import Input from "./ui/input/Input.vue";
import Textarea from "./ui/textarea/Textarea.vue";

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
  <div class="note-form bg-white shadow-lg rounded-lg p-4 w-full max-w-lg">
    <Input v-model="title" placeholder="제목" class="w-full rounded p-2 mb-3" />
    <Textarea
      v-model="content"
      placeholder="내용"
      rows="4"
      class="w-full rounded p-2 mb-3 resize-none"
    ></Textarea>
    <Button
      @click="submit"
      class="w-full bg-blue-600 text-white py-2 rounded hover:bg-blue-700 transition"
    >
      추가
    </Button>
  </div>
</template>

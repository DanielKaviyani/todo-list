<script setup>
import { ref } from 'vue'

const form = ref({})

const emits = defineEmits(["submit"])

const submit = () => {
  if (!form.value.input.length || form.value.input === " ") return
  emits("submit", JSON.parse(JSON.stringify(form.value)))
  form.value = {}
}
</script>

<template>
  <form @submit.prevent>
    <div class="flex">
      <input
        v-model.trim="form.input"
        class="input"
        placeholder="type task"
      />
      <button
        class="submit-button"
        @click="submit"
      >
        Add
      </button>
    </div>
  </form>
</template>

<style lang="scss" scoped>
.input {
  @apply w-full border border-solid rounded outline-none px-4 py-2;
}

.submit-button {
  @apply bg-blue-400 text-white px-4 py-2 rounded ml-6 outline-none focus:bg-blue-600;
}
</style>
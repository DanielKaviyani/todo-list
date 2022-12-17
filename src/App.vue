<script setup>
import { ref } from "vue"
import TodoForm from "./components/todoForm.vue";

const list = ref([])

const saveData = (formObject) => {
  if (!hasData(formObject)) list.value.push(formObject)
}

const hasData = (obj) => list.value.filter(x => x.input === obj.input).length > 0
</script>

<template>
  <div class="container min-h-screen py-20">
    <div class="grid grid-cols-12">
      <div class="col-start-4 col-span-6 rounded-2xl shadow-2xl p-10 bg-secondary">
        <todo-form
          :class="list.length ? 'mb-20' : 'mb-0'"
          @submit="saveData"
        />

        <div
          v-for="(item, index) in list"
          :key="`item-${index}`"
          class="text-white font-medium bg-blue-900 px-4 rounded py-2 mt-4"
        >
          {{ item.input }}
        </div>
      </div>
    </div>
  </div>
</template>
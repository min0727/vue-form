<script setup>
const [name, modifiers] = defineModel({
  type: String,
  default: 'default value',
  set: (value) => {
    return value.toLocaleUpperCase();
  },
});
const age = defineModel('age', {
  type: Number,
  default: 0,
});
</script>

<template>
  <div>
    <h2 class="text-xl mb-2">v-modelをcomponentに</h2>
    <label for="user-name">子　名前</label>
    <input
      id="user-name"
      v-model="name"
      type="text"
      class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      placeholder="Enter name"
    />
    <label for="user-age">子　年齢</label>
          <input
            id="user-age"
            v-model="age"
            type="number"
            class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder="Enter age"
          />
  </div>
</template>

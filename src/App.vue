<script setup>
import { ref } from 'vue';

const textField = ref('');
const textArea = ref('');
const checkBox = ref(false);
</script>

<template>
  <div>
    <h1 class="text-2xl">Form</h1>
    <label for="text-field">Text Field</label>
    <input
      id="text-field"
      v-model="textField"
      type="text"
      class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      placeholder="Enter text"
    />
    <label for="text-area">Text Area</label>
    <textarea
      id="text-area"
      v-model="textArea"
      class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      rows="4"
      placeholder="Enter text"
    ></textarea>
    <label for="checkbox" class="flex items-center mt-4">
      <input
        id="checkbox"
        v-model="checkBox"
        type="checkbox"
        class="h-4 w-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-500 dark:ring-offset-gray-800"
      />
      <span class="ml-2 text-gray-900 dark:text-gray-300">契約に同意する</span>
    </label>
    <div>
      <h2 class="text-2xl">Output</h2>
      <p>Text Field: {{ textField }}</p>
      <p>
        Text Area: <span class="whitespace-pre-line">{{ textArea }}</span>
      </p>
      <p>Checkbox: {{ checkBox ? 'Checked' : 'Unchecked' }}</p>
    </div>
  </div>
</template>

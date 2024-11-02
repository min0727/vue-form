<script setup>
import { ref } from 'vue'

const textField = ref('')
const textArea = ref('')
const checkBox = ref(false)
const selectedIds = ref([])
const selectedOption = ref('')
const selectedColor = ref('#000000')
// 今日の日付を 'YYYY-MM-DD' の形式にフォーマット
const formatDate = date => {
  const year = date.getFullYear()
  const month = String(date.getMonth() + 1).padStart(2, '0')
  const day = String(date.getDate()).padStart(2, '0')
  return `${year}-${month}-${day}`
}

// 現在の日付を初期値として設定
const currentDate = ref(formatDate(new Date()))
const dropdownValue = ref('') // dropdownの初期値
const file = ref(null)
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
    ID
    <div class="flex flex-wrap gap-2 mt-2">
      <label v-for="id in [1, 2, 3, 4, 5]" :key="id" class="flex items-center">
        <input
          v-model="selectedIds"
          type="checkbox"
          :value="id"
          class="h-4 w-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-500 dark:ring-offset-gray-800"
        />
        <span class="ml-2 text-gray-900 dark:text-gray-300">{{ id }}</span>
      </label>
      <div class="mt-4">
        <h2 class="text-xl mb-2">Choose an option</h2>
        <label class="flex items-center mb-2">
          <input
            v-model="selectedOption"
            type="radio"
            name="options"
            value="Option 1"
            class="h-4 w-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-500 dark:ring-offset-gray-800"
          />
          <span class="ml-2 text-gray-900 dark:text-gray-300">Option 1</span>
        </label>
        <label class="flex items-center mb-2">
          <input
            v-model="selectedOption"
            type="radio"
            name="options"
            value="Option 2"
            class="h-4 w-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-500 dark:ring-offset-gray-800"
          />
          <span class="ml-2 text-gray-900 dark:text-gray-300">Option 2</span>
        </label>
        <label class="flex items-center">
          <input
            v-model="selectedOption"
            type="radio"
            name="options"
            value="Option 3"
            class="h-4 w-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-500 dark:ring-offset-gray-800"
          />
          <span class="ml-2 text-gray-900 dark:text-gray-300">Option 3</span>
        </label>
        <div class="mt-4">
          <h2 class="text-xl mb-2">Choose a color</h2>
          <input
            v-model="selectedColor"
            type="color"
            class="h-10 w-16 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </div>
        <label
          for="date-input"
          class="block text-sm font-medium text-gray-700 dark:text-gray-300"
          >Select a date</label
        >
        <input
          id="date-input"
          v-model="currentDate"
          type="date"
          class="mt-1 block w-full p-2.5 text-sm text-gray-900 bg-gray-50 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        />
        <label for="dropdown" class="mt-4 block">Choose an option</label>
        <select
          id="dropdown"
          v-model="dropdownValue"
          class="block w-full p-2.5 text-sm text-gray-900 bg-gray-50 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        >
          <option value="" disabled>Select an option</option>
          <option value="Option 1">Option 1</option>
          <option value="Option 2">Option 2</option>
          <option value="Option 3">Option 3</option>
        </select>
        <label for="file-upload" class="mt-4 block">Upload a file</label>
        <input
          id="file-upload"
          type="file"
          class="block w-full text-sm text-gray-900 border border-gray-300 rounded-lg cursor-pointer bg-gray-50 focus:outline-none focus:ring-blue-500 focus:border-blue-500 dark:text-gray-400 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400"
          @change="event => (file.value = event.target.files[0])"
        />
        <div>
          <h2 class="text-2xl">Output</h2>
          <p>Text Field: {{ textField }}</p>
          <p>
            Text Area: <span class="whitespace-pre-line">{{ textArea }}</span>
          </p>
          <p>Checkbox: {{ checkBox ? 'Checked' : 'Unchecked' }}</p>
          <p>Selected IDs: {{ selectedIds }}</p>
          <p>Selected Option: {{ selectedOption }}</p>
          <p>
            Color:
            <span :style="{ color: selectedColor }">{{ selectedColor }}</span>
          </p>
          <p>Selected Date: {{ currentDate }}</p>
          <p>Selected Dropdown: {{ dropdownValue }}</p>
          <p>Selected File: {{ file }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

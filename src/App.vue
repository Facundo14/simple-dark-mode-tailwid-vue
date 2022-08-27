<script setup>
import { ref } from 'vue';


// On page load or when changing themes, best to add inline in `head` to avoid FOUC
if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

// // Whenever the user explicitly chooses light mode
// localStorage.theme = 'light'

// // Whenever the user explicitly chooses dark mode
// localStorage.theme = 'dark'

// // Whenever the user explicitly chooses to respect the OS preference
// localStorage.removeItem('theme')

const toggleDarkMode = ref(document.documentElement.className === 'dark');

const changeDarkMode = () => {
  toggleDarkMode.value = document.documentElement.classList.toggle('dark');
  toggleDarkMode.value ? localStorage.theme = 'dark' : localStorage.theme = 'light'
}
</script>

<template>
  <main class="container mx-auto text-center">
    <h1 class="text-4xl dark:bg-gray-800 dark:text-white">Dark Mode</h1>
    <div class="mt-3">
      <button class="bg-gray-700 text-white rounded-xl py-3 px-4" @click="changeDarkMode">Dia/Noche {{ toggleDarkMode }}</button>
    </div>
  </main>
</template>

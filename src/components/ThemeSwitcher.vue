<script setup>
import { ref, onMounted } from 'vue';

const isDark = ref(false);

const toggleTheme = () => {
  isDark.value = !isDark.value;
  updateTheme();
};

const updateTheme = () => {
  const html = document.documentElement;
  if (isDark.value) {
    html.classList.add('dark');
    localStorage.setItem('theme', 'dark');
  } else {
    html.classList.remove('dark');
    localStorage.setItem('theme', 'light');
  }
};

onMounted(() => {
  // Check for saved theme preference or system preference
  const saved = localStorage.getItem('theme');
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  
  isDark.value = saved === 'dark' || (saved === null && prefersDark);
  updateTheme();
});
</script>

<template>
  <button
    @click="toggleTheme"
    class="group relative p-2.5 rounded-lg border transition-all duration-300"
    :class="isDark 
      ? 'bg-slate-800 border-slate-700 hover:bg-slate-700 hover:border-slate-600' 
      : 'bg-slate-100 border-slate-200 hover:bg-slate-200 hover:border-slate-300'"
    :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
  >
    <!-- Sun Icon (Light Mode) -->
    <svg
      v-if="!isDark"
      xmlns="http://www.w3.org/2000/svg"
      class="h-5 w-5 text-amber-500 transition-all group-hover:rotate-12"
      fill="currentColor"
      viewBox="0 0 24 24"
    >
      <path d="M12 2.25a.75.75 0 01.75.75v2.25a.75.75 0 01-1.5 0V3a.75.75 0 01.75-.75zM7.5 12a4.5 4.5 0 119 0 4.5 4.5 0 01-9 0zM6.37 6.37a.75.75 0 011.06 0l1.591 1.591a.75.75 0 11-1.061 1.06L6.37 7.43a.75.75 0 010-1.06zm9.258 9.258a.75.75 0 11-1.06 1.061l-1.591-1.591a.75.75 0 011.06-1.06l1.591 1.591zM21.75 12a.75.75 0 01-.75.75h-2.25a.75.75 0 010-1.5H21a.75.75 0 01.75.75zM4.5 12a.75.75 0 01-.75.75H1.5a.75.75 0 010-1.5H3.75a.75.75 0 01.75.75zm13.128-6.37a.75.75 0 011.06 0l1.591 1.591a.75.75 0 11-1.06 1.06l-1.591-1.591a.75.75 0 010-1.06zm-9.258 9.258a.75.75 0 011.06 1.061l-1.591 1.591a.75.75 0 11-1.06-1.06l1.591-1.591zM12 19.5a.75.75 0 01.75.75v2.25a.75.75 0 01-1.5 0V20.25a.75.75 0 01.75-.75z" />
    </svg>
    
    <!-- Moon Icon (Dark Mode) -->
    <svg
      v-else
      xmlns="http://www.w3.org/2000/svg"
      class="h-5 w-5 text-blue-300 transition-all group-hover:rotate-12"
      fill="currentColor"
      viewBox="0 0 24 24"
    >
      <path fill-rule="evenodd" d="M17.688 11.138a8.25 8.25 0 01-8.826 8.826.75.75 0 07-.713-1.341 6.75 6.75 0 1010.318-6.75.75.75 0 07-1.341-.713 8.25 8.25 0 01-1.438 9.878z" clip-rule="evenodd" />
    </svg>
  </button>
</template>

<style scoped>
button {
  --tw-ring-shadow: none;
}
</style>

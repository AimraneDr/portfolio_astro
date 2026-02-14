<script setup>
import { ref } from 'vue';
const commands = ref([
  { input: 'bio', output: 'Full-stack developer specializing in Laravel, React/Vue, Flutter & Django.' },
  { input: 'stack', output: 'React, Vue, Laravel, Django, Flutter, MySQL, Oracle, MongoDB.' },
  { input: 'languages', output: 'English (C1), French (Intermediate), Arabic (Native).' },
  { input: 'location', output: 'Marrakech, Morocco' },
]);
</script>

<template>
  <div class="bg-black/50 border border-slate-700 rounded-lg p-4 font-mono text-sm shadow-2xl backdrop-blur-md">
    <div class="flex gap-2 mb-4">
      <div class="w-3 h-3 rounded-full bg-red-500"></div>
      <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
      <div class="w-3 h-3 rounded-full bg-green-500"></div>
    </div>
    <div v-for="cmd in commands" :key="cmd.input" class="mb-2">
      <div class="text-emerald-400">➜ <span class="text-white">{{ cmd.input }}</span></div>
      <div class="text-slate-400 ml-4">{{ cmd.output }}</div>
    </div>
    <div class="text-emerald-400">➜ <span class="animate-pulse">_</span></div>
  </div>
</template>
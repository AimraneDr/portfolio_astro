<script setup>
import { ref, onMounted } from 'vue';

const navItems = [
  { name: 'Home', icon: 'M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6', href: '#' },
  { name: 'Work', icon: 'M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z', href: '#work' },
  { name: 'Stack', icon: 'M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4', href: '#stack' },
  { name: 'Contact', icon: 'M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z', href: '#contact' },
];

const activeSection = ref('Home');

// Simple scroll spy to update active state
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        activeSection.value = entry.target.getAttribute('id') || 'Home';
      }
    });
  }, { threshold: 0.5 });

  document.querySelectorAll('section[id]').forEach((section) => observer.observe(section));
});
</script>

<template>
  <nav class="fixed left-6 top-1/2 -translate-y-1/2 z-50 hidden lg:block">
    <div class="flex flex-col gap-4 p-3 rounded-xl border border-white/10 bg-slate-900/40 backdrop-blur-xl shadow-lg">
      <a 
        v-for="item in navItems" 
        :key="item.name"
        :href="item.href"
        class="group relative p-3 rounded-lg transition-all duration-300"
        :class="activeSection === item.name.toLowerCase() ? 'bg-blue-500/20 text-blue-400' : 'text-slate-400 hover:text-white hover:bg-white/5'"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" :d="item.icon" />
        </svg>

        <span class="absolute left-14 scale-0 group-hover:scale-100 transition-all origin-left bg-white text-black text-xs font-bold px-3 py-1.5 rounded-lg shadow-xl">
          {{ item.name }}
        </span>

        <div 
          v-if="activeSection === item.name.toLowerCase()"
          class="absolute -left-1 top-1/2 -translate-y-1/2 w-1 h-4 bg-blue-500 rounded-full"
        ></div>
      </a>
    </div>
  </nav>
</template>
<script setup>
import { computed } from 'vue';

const skills = [
  { name: 'React', type: 'Frontend', level: 'Expert', icon: '⚛️' },
  { name: 'Vue.js', type: 'Frontend', level: 'Expert', icon: '💚' },
  { name: 'Angular', type: 'Frontend', level: 'Advanced', icon: '🅰️' },
  { name: 'Tailwind CSS', type: 'Frontend', level: 'Expert', icon: '🎨' },
  { name: 'Laravel', type: 'Backend', level: 'Expert', icon: '🔴' },
  { name: 'Django', type: 'Backend', level: 'Advanced', icon: '🐍' },
  { name: 'J2EE (Java)', type: 'Backend', level: 'Advanced', icon: '☕' },
  { name: 'Node.js', type: 'Backend', level: 'Fluent', icon: '🟢' },
  { name: 'Flutter', type: 'Mobile', level: 'Advanced', icon: '📱' },
  { name: 'MySQL & Oracle', type: 'Database', level: 'Expert', icon: '🗄️' },
  { name: 'MongoDB', type: 'Database', level: 'Fluent', icon: '🍃' },
  { name: 'Shopify', type: 'Ecommerce', level: 'Advanced', icon: '🛒' },
  { name: 'Liquid', type: 'Ecommerce', level: 'Advanced', icon: '💧' },
  { name: 'C/C++', type: 'Languages', level: 'Intermediate', icon: '⚙️' },
  { name: 'WordPress', type: 'Tools', level: 'Intermediate', icon: '📝' },
  { name: 'Git', type: 'Tools', level: 'Expert', icon: '🌿' },
];

const categories = ['Frontend', 'Backend', 'Mobile', 'Database', 'Ecommerce', 'Languages', 'Tools'];
const groupedSkills = computed(() => {
  return categories.reduce((acc, category) => {
    acc[category] = skills.filter(skill => skill.type === category);
    return acc;
  }, {});
});
</script>

<template>
  <section id="stack" class="py-24 px-6 md:px-12 flex flex-col items-center max-w-7xl mx-auto">
    <div class="mb-20 text-center flex flex-col items-center">
      <h2 class="text-4xl font-black text-white italic tracking-tighter">TECH_CORE</h2>
      <div class="h-1 w-12 bg-blue-600 mt-3 rounded-full shadow-[0_0_15px_rgba(37,99,235,0.6)]"></div>
    </div>

    <div class="w-full flex flex-col gap-16">
      <div 
        v-for="category in categories" 
        :key="category"
        class="group flex flex-col items-center"
      >
        <div class="flex items-center gap-6 w-full max-w-4xl mb-8">
          <div class="h-[1px] flex-1 bg-gradient-to-r from-transparent via-white/10 to-white/10"></div>
          <h3 class="text-xs font-mono uppercase tracking-[0.4em] text-slate-500 group-hover:text-blue-500 transition-all duration-500 whitespace-nowrap">
            {{ category }}
          </h3>
          <div class="h-[1px] flex-1 bg-gradient-to-l from-transparent via-white/10 to-white/10"></div>
        </div>

        <div class="flex flex-wrap justify-center gap-4 w-full max-w-5xl">
          <div 
            v-for="skill in groupedSkills[category]" 
            :key="skill.name"
            class="relative overflow-hidden group/card w-36 md:w-44 p-5 rounded-xl border border-white/5 bg-slate-900/40 backdrop-blur-md hover:border-blue-500/40 hover:bg-slate-800/60 transition-all duration-500 hover:-translate-y-1"
          >
            <div class="absolute -inset-px bg-gradient-to-r from-blue-500/20 to-purple-500/20 opacity-0 group-hover/card:opacity-100 transition-opacity duration-500"></div>
            
            <div class="relative z-10 flex flex-col items-center text-center py-2">
              <span class="text-3xl mb-3 drop-shadow-lg">{{ skill.icon }}</span>
              <span class="text-sm font-bold text-slate-200 tracking-wide">{{ skill.name }}</span>
              <span class="text-[10px] text-slate-500 uppercase mt-2 tracking-widest font-mono">{{ skill.level }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
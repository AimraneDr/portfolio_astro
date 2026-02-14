<script setup>
</script>

<template>
  <section id="contact" class="pt-32 px-6 md:px-12 flex flex-col items-center">
    <div class="mb-16 text-center">
      <h2 class="text-xs font-mono tracking-[0.4em] text-blue-500 uppercase mb-4">Available for Hire</h2>
      <h3 class="text-5xl md:text-6xl font-black text-white italic tracking-tighter">GET_IN_TOUCH</h3>
    </div>

    <div class="relative w-full max-w-3xl rounded-2xl border border-white/10 bg-slate-900/40 backdrop-blur-xl overflow-hidden shadow-xl">
      <div class="absolute -top-24 -right-24 w-64 h-64 bg-blue-600/10 rounded-full blur-[80px]"></div>
      <div class="absolute -bottom-24 -left-24 w-64 h-64 bg-purple-600/10 rounded-full blur-[80px]"></div>

      <div class="p-12 md:p-16 relative z-10 flex flex-col items-center text-center">
        <h4 class="text-3xl font-bold text-white mb-6">Let's create something <span class="text-blue-500 italic">extraordinary.</span></h4>
        <p class="text-slate-400 leading-relaxed mb-8 max-w-2xl">
          Whether you have a specific project in mind or just want to chat about tech, I'd love to hear from you.
        </p>

        <div class="flex items-center gap-4 mb-8">
          <div class="w-12 h-12 rounded-2xl bg-white/5 flex items-center justify-center border border-white/10">
            <span class="text-blue-400">@</span>
          </div>
          <div>
            <p class="text-[10px] text-slate-500 uppercase font-mono tracking-widest">Email</p>
            <p class="text-slate-200 font-medium">aimranedr@gmail.com</p>
          </div>
        </div>

        <a 
          href="mailto:aimranedr@gmail.com" 
          class="group px-8 py-4 bg-blue-600 text-white font-bold rounded-xl hover:bg-blue-700 transition-all duration-300 flex items-center gap-2 shadow-lg hover:shadow-xl"
        >
          Send Email
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
          </svg>
        </a>

        <div class="mt-12">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-500/10 border border-emerald-500/20 text-emerald-400 text-xs">
            <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
            Fast response: ~24 hours
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
</style>
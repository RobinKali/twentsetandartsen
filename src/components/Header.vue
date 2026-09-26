<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled ? 'bg-white/90 backdrop-blur-md shadow-sm py-4' : 'bg-transparent py-6'
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex justify-between items-center">
      <div class="flex items-center">
        <a href="/" class="text-2xl font-bold text-primary-900 tracking-tight flex items-center gap-2">
          <svg class="w-8 h-8 text-primary-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path></svg>
          Twentse Tandartsen
        </a>
      </div>
      
      <!-- Desktop Menu -->
      <nav class="hidden md:flex items-center space-x-8">
        <a href="/ons-team" class="text-slate-600 hover:text-primary-600 font-medium transition-colors">Ons Team</a>
        <a href="/over-de-praktijk" class="text-slate-600 hover:text-primary-600 font-medium transition-colors">Over de Praktijk</a>
        <a href="/behandelingen" class="text-slate-600 hover:text-primary-600 font-medium transition-colors">Behandelingen</a>
        <a href="/contact" class="text-slate-600 hover:text-primary-600 font-medium transition-colors">Contact</a>
        <a href="/spoed" class="bg-primary-50 text-primary-700 px-5 py-2.5 rounded-full font-medium hover:bg-primary-100 transition-colors">Spoed</a>
      </nav>

      <!-- Mobile Menu Button -->
      <button class="md:hidden text-slate-600 hover:text-primary-600 focus:outline-none" @click="toggleMenu">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
        </svg>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div v-if="isMenuOpen" class="md:hidden bg-white shadow-lg absolute top-full left-0 right-0 border-t border-slate-100">
      <div class="px-4 pt-2 pb-6 space-y-2 flex flex-col">
        <a href="/ons-team" class="block px-3 py-3 text-base font-medium text-slate-700 hover:text-primary-600 hover:bg-slate-50 rounded-md">Ons Team</a>
        <a href="/over-de-praktijk" class="block px-3 py-3 text-base font-medium text-slate-700 hover:text-primary-600 hover:bg-slate-50 rounded-md">Over de Praktijk</a>
        <a href="/behandelingen" class="block px-3 py-3 text-base font-medium text-slate-700 hover:text-primary-600 hover:bg-slate-50 rounded-md">Behandelingen</a>
        <a href="/contact" class="block px-3 py-3 text-base font-medium text-slate-700 hover:text-primary-600 hover:bg-slate-50 rounded-md">Contact</a>
        <a href="/spoed" class="block px-3 py-3 mt-2 text-base font-medium text-primary-700 bg-primary-50 hover:bg-primary-100 rounded-md text-center">Spoed</a>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolled = ref(false);
const isMenuOpen = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20;
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

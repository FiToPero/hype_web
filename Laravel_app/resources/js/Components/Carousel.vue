<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const carousel = ref(null);
let autoScrollInterval = null;

function scrollNext() {
  if (carousel.value) {
    const maxScroll = carousel.value.scrollWidth - carousel.value.clientWidth;
    
    // Si llegamos al final, volver al inicio
    if (carousel.value.scrollLeft >= maxScroll - 10) {
      carousel.value.scrollTo({ left: 0, behavior: 'smooth' });
    } else {
      carousel.value.scrollBy({ left: 300, behavior: 'smooth' });
    }
  }
}

function scrollPrev() {
  if (carousel.value) {
    carousel.value.scrollBy({ left: -300, behavior: 'smooth' });
  }
}

// Iniciar auto-scroll cuando el componente se monta
onMounted(() => {
  autoScrollInterval = setInterval(() => {
    scrollNext();
  }, 2000); // Cada 2 segundos
});

// Limpiar el intervalo cuando el componente se desmonta
onUnmounted(() => {
  if (autoScrollInterval) {
    clearInterval(autoScrollInterval);
  }
});
</script>

<template>
  <div class="relative">
    <!-- Botón Previo -->
    <button 
      type="button" 
      class="absolute left-0 top-1/2 -translate-y-1/2 z-30 flex items-center justify-center w-10 h-10 rounded-full bg-white/30 hover:bg-white/50 focus:outline-none focus:ring-4 focus:ring-white"
      @click="scrollPrev"
    >
      <svg class="w-4 h-4 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 1 1 5l4 4"/>
      </svg>
      <span class="sr-only">Previous</span>
    </button>

    <!-- Contenedor del carousel con scroll horizontal -->
    <div 
      ref="carousel"
      class="flex gap-4 overflow-x-auto scroll-smooth snap-x snap-mandatory px-12 scrollbar-hide"
      style="scrollbar-width: none; -ms-overflow-style: none;"
    >
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/bar-protein-coco.png.webp" alt="Bar Protein Coco" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-after-dark.png.webp" alt="Can After Dark" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-buzz.png.webp" alt="Can Buzz" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-enlite-low-sugar-1.png.webp" alt="Can Enlite" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-extra-cheesecake.png.webp" alt="Can Extra Cheesecake" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-extra-watermelon.png.webp" alt="Can Extra Watermelon" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-mfp.png.webp" alt="Can MFP" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-on.png.webp" alt="Can On" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-twisted-cherry.png.webp" alt="Can Twisted Cherry" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-twisted-tropical.png.webp" alt="Can Twisted Tropical" class="w-full h-full object-cover rounded-lg"/>
      </div>
      <div class="flex-shrink-0 w-64 h-auto snap-start">
        <img src="/images/Carousel/can-up-berry.png.webp" alt="Can Up Berry" class="w-full h-full object-cover rounded-lg"/>
      </div>
    </div>

    <!-- Botón Siguiente -->
    <button 
      type="button" 
      class="absolute right-0 top-1/2 -translate-y-1/2 z-30 flex items-center justify-center w-10 h-10 rounded-full bg-white/30 hover:bg-white/50 focus:outline-none focus:ring-4 focus:ring-white"
      @click="scrollNext"
    >
      <svg class="w-4 h-4 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
      </svg>
      <span class="sr-only">Next</span>
    </button>
  </div>


</template>

<style scoped>
/* Ocultar scrollbar en todos los navegadores */
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
</style>
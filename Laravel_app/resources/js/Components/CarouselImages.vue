<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const carousel = ref(null);
let autoScrollInterval = null;

function scrollNext() {
  if (carousel.value) {
    const maxScroll = carousel.value.scrollWidth - carousel.value.clientWidth;
    
    if (carousel.value.scrollLeft >= maxScroll - 10) {
      carousel.value.scrollTo({ left: 0, behavior: 'smooth' });
    } else {
      carousel.value.scrollBy({ left: 300, behavior: 'smooth' });
    }
  }
}

onMounted(() => {
  autoScrollInterval = setInterval(() => {
    scrollNext();
  }, 2000);
});

onUnmounted(() => {
  if (autoScrollInterval) {
    clearInterval(autoScrollInterval);
  }
});
</script>

<template>
  <div class="relative">
    <div 
      ref="carousel"
      class="flex gap overflow-x-auto scroll-smooth snap-x snap-mandatory scrollbar-hide"
      style="scrollbar-width: none; -ms-overflow-style: none;"
    >
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/1_hype_lifestyle_serlua-scaled.webp" alt="Bar Protein Coco" class="w-full h-auto object-cover"/>
      </div>
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/2_hype_lifestyle_drink_xtra-scaled.webp" alt="Can After Dark" class="w-full h-auto object-cover"/>
      </div>
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/3_hype_lifestyle_drink_mojito-scaled.webp" alt="Can Buzz" class="w-full h-auto object-cover"/>
      </div>
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/4_hype_lifestyle_drink_sugarfree-scaled.webp" alt="Can Enlite" class="w-full h-auto object-cover"/>
      </div>
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/F1-simulator-scaled.webp" alt="Can Extra Cheesecake" class="w-full h-auto object-cover"/>
      </div>
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/hype-energy-drinks-front-desk-scaled.webp" alt="Can Extra Watermelon" class="w-full h-auto object-cover"/>
      </div>
      <div class="flex-shrink-0 w-full snap-start">
        <img src="/images/contact_us/hype-logo-green-scaled.webp" alt="Can MFP" class="w-full h-auto object-cover"/>
      </div>
    </div>


  </div>


</template>

<style scoped>
/* Ocultar scrollbar en todos los navegadores */
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
</style>
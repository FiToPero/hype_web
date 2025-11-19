<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import { onMounted, onUnmounted, ref } from 'vue';

const sections = ref([
    { id: 1, color: '#89fe71', height: 'h-[600px]' },
    { id: 2, color: '#df70d7', height: 'h-[900px]' },
    { id: 3, color: '#89fe71', height: 'h-[900px]' },
    { id: 4, color: '#34abeb', height: 'h-[900px]' },
    { id: 5, color: '#eb7134', height: 'h-[900px]' }
]);

const handleScroll = () => {
    const bgDashboard = document.getElementById('bg-dashboard');
    if (!bgDashboard) return;
    
    const sectionElements = document.querySelectorAll('.color-section');
    if (sectionElements.length === 0) return;
    
    // Usar el centro de la ventana como punto de referencia
    const viewportCenter = window.scrollY + window.innerHeight / 2;
    
    let currentSection = null;
    let nextSection = null;
    
    // Encontrar la sección actual basándose en la posición del viewport
    sectionElements.forEach((section, index) => {
        const rect = section.getBoundingClientRect();
        const sectionTop = rect.top + window.scrollY;
        const sectionBottom = sectionTop + section.offsetHeight; // Usar offsetHeight para altura precisa
        
        if (viewportCenter >= sectionTop && viewportCenter <= sectionBottom) {
            currentSection = { 
                element: section, 
                index, 
                top: sectionTop, 
                bottom: sectionBottom,
                height: section.offsetHeight 
            };
            if (index < sectionElements.length - 1) {
                nextSection = { element: sectionElements[index + 1], index: index + 1 };
            }
        }
    });
    
    if (!currentSection) {
        // Si estamos antes de la primera sección
        const firstSection = sectionElements[0];
        const firstTop = firstSection.getBoundingClientRect().top + window.scrollY;
        if (viewportCenter < firstTop) {
            bgDashboard.style.background = sections.value[0].color;
            return;
        }
        // Si estamos después de la última sección
        bgDashboard.style.background = sections.value[sections.value.length - 1].color;
        return;
    }
    
    const currentColor = sections.value[currentSection.index].color;
    
    if (nextSection) {
        // Calcular el progreso dentro de la sección usando su altura real
        const progressInSection = (viewportCenter - currentSection.top) / currentSection.height;
        
        // Interpolar en la segunda mitad de la sección
        if (progressInSection > 0.5) {
            const nextColor = sections.value[nextSection.index].color;
            // Normalizar la interpolación entre 0 y 1 (desde 50% hasta 100% de la sección)
            const interpolation = (progressInSection - 0.5) * 2;
            
            const color1 = hexToRgb(currentColor);
            const color2 = hexToRgb(nextColor);
            
            const r = Math.round(color1.r + (color2.r - color1.r) * interpolation);
            const g = Math.round(color1.g + (color2.g - color1.g) * interpolation);
            const b = Math.round(color1.b + (color2.b - color1.b) * interpolation);
            
            bgDashboard.style.background = `rgb(${r}, ${g}, ${b})`;
        } else {
            bgDashboard.style.background = currentColor;
        }
    } else {
        bgDashboard.style.background = currentColor;
    }
};

const hexToRgb = (hex) => {
    const result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
    return result ? {
        r: parseInt(result[1], 16),
        g: parseInt(result[2], 16),
        b: parseInt(result[3], 16)
    } : { r: 0, g: 0, b: 0 };
};

onMounted(() => {
    handleScroll();
    window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <AuthenticatedLayout>
        <div id="bg-dashboard" class="py-12 transition-colors duration-300">
            <div class="mx-auto w-full sm:px-6 lg:px-8">
                <!-- Section 1 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-4 p-10">
                        <a class="relative block p-5">
                            <img src="/images/can-mfp-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">MAXIMUM<br>ENERGY</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-mfp-zero-sugar-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                    <h2 class="text-xl font-pirulen font-bold text-black text-left">ABSOLUTE<br>ZERO SUGAR</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-enlite-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">EXTRA LOW<br>SUGAR</h2>
                            </div>
                        </a>
                    
                        <a class="relative block p-5">
                            <img src="/images/can-buzz-label-product-new.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">MARSHMALLOW<br>MAD CANDY</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-mojito-label-product-new.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                    <h2 class="text-xl font-pirulen font-bold text-black text-left">WILD<br>MINT BOOST</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-up-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">ICED BERRY<br>MAX</h2>
                            </div>
                        </a>
                    
                        <a class="relative block p-5">
                            <img src="/images/can-twisted-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">BLASTED<br>TROPICAL</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-twisted-cherry-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                    <h2 class="text-xl font-pirulen font-bold text-black text-left">EXPLOSIVE<br>CHERRY</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-gold-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">NON<br>CARBONATED</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-on-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                <h2 class="text-xl font-pirulen font-bold text-black text-left">CLASSIC</h2>
                            </div>
                        </a>
                        <a class="relative block p-5">
                            <img src="/images/can-after-dark-label-product.png" alt="Enlite Can" class="w-auto h-auto" />
                            <div class="absolute top-[200px] left-[200px] ">
                                    <h2 class="text-xl font-pirulen font-bold text-black text-left">CINNAMON<br>FIRE</h2>
                            </div>
                        </a>
                    </div>
                 
                </div>

                <!-- Section 2 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <div class="p-6 text-gray-900">
                        <a class="relative block">
                            <div class="relative">
                                <img src="/images/enlite_can.png" alt="Enlite Can" class="w-64 h-auto" />
                                <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                                    <h2 class="text-2xl font-bold text-white text-center">EXTRA LOW<br>SUGAR</h2>
                                </div>
                            </div>
                        </a>
                    </div>
                </div>

                <!-- Section 3 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <div class="p-6 text-gray-900">
                        <a class="relative block">
                            <div class="relative">
                                <img src="/images/enlite_can.png" alt="Enlite Can" class="w-64 h-auto" />
                                <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                                    <h2 class="text-2xl font-bold text-white text-center">EXTRA LOW<br>SUGAR</h2>
                                </div>
                            </div>
                        </a>
                    </div>
                </div>

                <!-- Section 4 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <div class="p-6 text-gray-900">
                        <a class="relative block">
                            <div class="relative">
                                <img src="/images/enlite_can.png" alt="Enlite Can" class="w-64 h-auto" />
                                <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                                    <h2 class="text-2xl font-bold text-white text-center">EXTRA LOW<br>SUGAR</h2>
                                </div>
                            </div>
                        </a>
                    </div>
                </div>

                <!-- Section 5 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <div class="p-6 text-gray-900">
                        <a class="relative block">
                            <div class="relative">
                                <img src="/images/enlite_can.png" alt="Enlite Can" class="w-64 h-auto" />
                                <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                                    <h2 class="text-2xl font-bold text-white text-center">EXTRA LOW<br>SUGAR</h2>
                                </div>
                            </div>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

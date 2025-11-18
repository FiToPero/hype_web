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
    
    const scrollY = window.scrollY + window.innerHeight / 2;
    
    let currentSection = null;
    let nextSection = null;
    
    sectionElements.forEach((section, index) => {
        const rect = section.getBoundingClientRect();
        const absoluteTop = rect.top + window.scrollY;
        const absoluteBottom = absoluteTop + rect.height;
        
        if (scrollY >= absoluteTop && scrollY <= absoluteBottom) {
            currentSection = { element: section, index, top: absoluteTop, bottom: absoluteBottom };
            if (index < sectionElements.length - 1) {
                nextSection = { element: sectionElements[index + 1], index: index + 1 };
            }
        }
    });
    
    if (!currentSection) {
        // Si estamos antes de la primera sección
        const firstRect = sectionElements[0].getBoundingClientRect();
        if (scrollY < firstRect.top + window.scrollY) {
            const color = sections.value[0].color;
            bgDashboard.style.background = color;
            return;
        }
        // Si estamos después de la última sección
        const lastColor = sections.value[sections.value.length - 1].color;
        bgDashboard.style.background = lastColor;
        return;
    }
    
    const currentColor = sections.value[currentSection.index].color;
    
    if (nextSection) {
        // Calcular el progreso dentro de la sección actual
        const sectionHeight = currentSection.bottom - currentSection.top;
        const progressInSection = (scrollY - currentSection.top) / sectionHeight;
        
        // Si estamos en la segunda mitad de la sección, interpolar hacia el siguiente color
        if (progressInSection > 0.5) {
            const nextColor = sections.value[nextSection.index].color;
            const interpolation = (progressInSection - 0.5) * 2; // Normalizar entre 0 y 1
            
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
                <div 
                    v-for="section in sections" 
                    :key="section.id"
                    class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10"
                    :class="section.height"
                >
                    <div class="p-6 text-gray-900">
                        <h3 class="text-2xl font-bold mb-4">Section {{ section.id }}</h3>
                        <p>Color: {{ section.color }}</p>
                        <p class="mt-2">You're logged in!</p>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

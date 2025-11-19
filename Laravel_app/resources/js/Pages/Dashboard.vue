<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import { onMounted, onUnmounted, ref } from 'vue';
import ProductSmall from '@/Components/ProductSmall.vue';
import TitleSection from '@/Components/TitleSection.vue';

// ========== CONFIGURACIÓN DE SECCIONES ==========
// Definimos un array reactivo con ref() que contiene la configuración de cada sección
// - id: identificador único de la sección
// - color: color hexadecimal que se aplicará al fondo cuando se visualice esta sección
// - height: clase de Tailwind CSS para la altura (aunque no se usa directamente, sirve de referencia)
const sections = ref([
    { id: 1, color: '#89fe71', height: 'h-[600px]' },  // Sección 1: verde claro
    { id: 2, color: '#df70d7', height: 'h-[900px]' },  // Sección 2: rosa/magenta
    { id: 3, color: '#89fe71', height: 'h-[900px]' },  // Sección 3: verde claro (repetido)
    { id: 4, color: '#34abeb', height: 'h-[900px]' },  // Sección 4: azul
    { id: 5, color: '#eb7134', height: 'h-[900px]' }   // Sección 5: naranja
]);

// ========== FUNCIÓN PRINCIPAL: MANEJO DEL SCROLL ==========
// Esta función se ejecuta cada vez que el usuario hace scroll en la página
const handleScroll = () => {
    // 1. OBTENER EL CONTENEDOR PRINCIPAL
    // Buscamos el elemento con id="bg-dashboard" que es el contenedor al que cambiaremos el color
    const bgDashboard = document.getElementById('bg-dashboard');
    // Si no existe, salimos de la función para evitar errores
    if (!bgDashboard) return;
    
    // 2. OBTENER TODAS LAS SECCIONES
    // Seleccionamos todos los elementos que tienen la clase "color-section"
    const sectionElements = document.querySelectorAll('.color-section');
    // Si no hay secciones, salimos de la función
    if (sectionElements.length === 0) return;
    
    // 3. CALCULAR EL PUNTO DE REFERENCIA (CENTRO DE LA PANTALLA)
    // window.scrollY: cuántos píxeles hemos scrolleado desde arriba
    // window.innerHeight: altura total de la ventana del navegador
    // Dividimos entre 2 para obtener el centro exacto de la pantalla visible
    const viewportCenter = window.scrollY + window.innerHeight / 2;
    
    // 4. VARIABLES PARA ALMACENAR SECCIONES
    // currentSection: la sección que está actualmente en el centro de la pantalla
    let currentSection = null;
    // nextSection: la siguiente sección (para hacer la transición de colores)
    let nextSection = null;
    
    // 5. BUSCAR LA SECCIÓN ACTUAL
    // Recorremos cada sección para determinar cuál está en el centro del viewport
    sectionElements.forEach((section, index) => {
        // getBoundingClientRect() devuelve la posición y dimensiones del elemento
        // respecto al viewport (área visible del navegador)
        const rect = section.getBoundingClientRect();
        
        // Calculamos la posición ABSOLUTA de la sección en la página
        // rect.top: distancia desde el viewport hasta el inicio de la sección
        // window.scrollY: cuánto hemos scrolleado
        // Sumamos ambos para obtener la posición real desde el inicio del documento
        const sectionTop = rect.top + window.scrollY;
        
        // Calculamos dónde termina la sección
        // section.offsetHeight: altura real del elemento en píxeles (se adapta automáticamente)
        const sectionBottom = sectionTop + section.offsetHeight;
        
        // 6. VERIFICAR SI EL CENTRO DEL VIEWPORT ESTÁ DENTRO DE ESTA SECCIÓN
        // Si viewportCenter está entre sectionTop y sectionBottom, esta es la sección actual
        if (viewportCenter >= sectionTop && viewportCenter <= sectionBottom) {
            // Guardamos toda la información relevante de la sección actual
            currentSection = { 
                element: section,           // El elemento DOM de la sección
                index,                      // El índice en el array (0, 1, 2, 3, 4)
                top: sectionTop,           // Posición donde inicia la sección
                bottom: sectionBottom,     // Posición donde termina la sección
                height: section.offsetHeight  // Altura total de la sección
            };
            
            // Si existe una siguiente sección, la guardamos para la interpolación de color
            if (index < sectionElements.length - 1) {
                nextSection = { 
                    element: sectionElements[index + 1],  // Elemento DOM de la siguiente sección
                    index: index + 1                       // Índice de la siguiente sección
                };
            }
        }
    });
    
    // 7. MANEJO DE CASOS ESPECIALES (cuando no estamos en ninguna sección)
    if (!currentSection) {
        // CASO A: Estamos ANTES de la primera sección (al inicio de la página)
        const firstSection = sectionElements[0];
        const firstTop = firstSection.getBoundingClientRect().top + window.scrollY;
        
        if (viewportCenter < firstTop) {
            // Aplicamos el color de la primera sección
            bgDashboard.style.background = sections.value[0].color;
            return;  // Salimos de la función
        }
        
        // CASO B: Estamos DESPUÉS de la última sección (al final de la página)
        // Aplicamos el color de la última sección
        bgDashboard.style.background = sections.value[sections.value.length - 1].color;
        return;  // Salimos de la función
    }
    
    // 8. OBTENER EL COLOR DE LA SECCIÓN ACTUAL
    // Accedemos al array de configuración usando el índice de la sección actual
    const currentColor = sections.value[currentSection.index].color;
    
    // 9. INTERPOLACIÓN DE COLORES (transición suave entre secciones)
    if (nextSection) {
        // Calculamos qué tan lejos estamos dentro de la sección actual
        // progressInSection es un valor entre 0 (inicio de sección) y 1 (final de sección)
        // Fórmula: (posición actual - inicio de sección) / altura total de la sección
        const progressInSection = (viewportCenter - currentSection.top) / currentSection.height;
        
        // Solo interpolamos colores en la SEGUNDA MITAD de la sección (progreso > 0.5)
        // Esto significa que el color cambia gradualmente en la parte inferior de cada sección
        if (progressInSection > 0.5) {
            // Obtenemos el color de la siguiente sección
            const nextColor = sections.value[nextSection.index].color;
            
            // Normalizamos la interpolación entre 0 y 1
            // Si progressInSection = 0.5 → interpolation = 0 (color actual 100%)
            // Si progressInSection = 1.0 → interpolation = 1 (color siguiente 100%)
            // Fórmula: (progreso - 0.5) * 2 convierte el rango 0.5-1.0 en 0-1
            const interpolation = (progressInSection - 0.5) * 2;
            
            // Convertimos ambos colores hexadecimales a RGB
            const color1 = hexToRgb(currentColor);   // Color actual (ej: {r: 137, g: 254, b: 113})
            const color2 = hexToRgb(nextColor);      // Color siguiente
            
            // Calculamos el color interpolado para cada canal RGB
            // Fórmula: colorActual + (diferencia de colores * progreso de interpolación)
            // Math.round() redondea al entero más cercano
            const r = Math.round(color1.r + (color2.r - color1.r) * interpolation);
            const g = Math.round(color1.g + (color2.g - color1.g) * interpolation);
            const b = Math.round(color1.b + (color2.b - color1.b) * interpolation);
            
            // Aplicamos el color interpolado al fondo
            bgDashboard.style.background = `rgb(${r}, ${g}, ${b})`;
        } else {
            // Si estamos en la primera mitad de la sección, usamos solo el color actual
            bgDashboard.style.background = currentColor;
        }
    } else {
        // Si no hay siguiente sección (estamos en la última), usamos el color actual
        bgDashboard.style.background = currentColor;
    }
};

// ========== FUNCIÓN AUXILIAR: CONVERTIR HEXADECIMAL A RGB ==========
// Esta función convierte un color en formato hexadecimal (#89fe71) a RGB {r, g, b}
const hexToRgb = (hex) => {
    // Expresión regular que captura los 3 pares de dígitos hexadecimales
    // [a-f\d]{2} = dos caracteres que pueden ser letras a-f o dígitos 0-9
    // Ejemplo: #89fe71 → captura "89", "fe", "71"
    const result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
    
    // Si la expresión regular encuentra coincidencias, convertimos a RGB
    return result ? {
        r: parseInt(result[1], 16),  // Primer par (red): "89" base16 → 137 base10
        g: parseInt(result[2], 16),  // Segundo par (green): "fe" base16 → 254 base10
        b: parseInt(result[3], 16)   // Tercer par (blue): "71" base16 → 113 base10
    } : { r: 0, g: 0, b: 0 };  // Si falla, devolvemos negro
};

// ========== LIFECYCLE HOOKS (CICLO DE VIDA DEL COMPONENTE) ==========

// onMounted: se ejecuta cuando el componente se monta en el DOM (está listo y visible)
onMounted(() => {
    // Ejecutamos handleScroll una vez al cargar la página para establecer el color inicial
    handleScroll();
    
    // Registramos un evento listener que ejecuta handleScroll cada vez que el usuario hace scroll
    // Esto hace que el color cambie en tiempo real mientras scrolleas
    window.addEventListener('scroll', handleScroll);
});

// onUnmounted: se ejecuta cuando el componente se va a destruir (ej: navegamos a otra página)
onUnmounted(() => {
    // Limpiamos el event listener para evitar memory leaks (fugas de memoria)
    // Es buena práctica siempre limpiar los listeners que agregamos manualmente
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <AuthenticatedLayout>
        <div id="bg-dashboard" class="py-12 transition-colors duration-300">
            <div class="mx-auto w-full sm:px-6 lg:px-8">
                <!-- Section 1 -->
                <div class="color-section m-5 shadow-sm sm:rounded-lg  h-auto">
                    <TitleSection title01="ENERGY DRINKS" title02="Maximum Energy!" />                
                    <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-4 p-10">  
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-mfp-label-product.png" 
                            alt="MFP Maximum Energy Can" 
                            text01="MAXIMUM" 
                            text02="ENERGY" 
                        />                       
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-mfp-zero-sugar-label-product.png" 
                            alt="MFP Zero Sugar Can" 
                            text01="ABSOLUTE" 
                            text02="ZERO SUGAR" 
                        />                      
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-enlite-label-product.png" 
                            alt="Enlite Can" 
                            text01="EXTRA LOW" 
                            text02="SUGAR" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-buzz-label-product-new.png" 
                            alt="Buzz Marshmallow Mad Candy Can" 
                            text01="MARSHMALLOW" 
                            text02="MAD CANDY" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-mojito-label-product-new.png" 
                            alt="Mojito Can" 
                            text01="WILD" 
                            text02="MINT BOOST" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-up-label-product.png" 
                            alt="Up Can" 
                            text01="ICED BERRY" 
                            text02="MAX" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-twisted-label-product.png" 
                            alt="Twisted Can" 
                            text01="BLASTED" 
                            text02="TROPICAL" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-twisted-cherry-label-product.png" 
                            alt="Twisted Explosive Cherry Can" 
                            text01="EXPLOSIVE" 
                            text02="CHERRY" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-gold-label-product.png" 
                            alt="Gold Can" 
                            text01="NON" 
                            text02="CARBONATED" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-on-label-product.png" 
                            alt="On Can" 
                            text01="CLASSIC"
                        /> 
                        <ProductSmall 
                            imgSrc="/images/Energy_drinks/can-after-dark-label-product.png" 
                            alt="After Dark Can" 
                            text01="CINNAMON" 
                            text02="FIRE" 
                        />
                    </div>
                </div>

                <!-- Section 2 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <TitleSection title01="PERFORMANCE DRINKS" title02="DISRUPT YOUR ROUTINE!" />                
                    <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-4 p-10">
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/can-xtra-cheesecake-label-product.png" 
                            alt="EAA Cheesecake Can" 
                            text01="EAA" 
                            text02="CHEESECAKE" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/can-xtra-watermelon-label-product.png" 
                            alt="EAA Watermelon Can" 
                            text01="EAA" 
                            text02="WATERMELON" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/can-mfppw-label-product-new.png" 
                            alt="MFP Original Can" 
                            text01="MFP" 
                            text02="ORIGINAL" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/can-tropical-label-product-new1.png" 
                            alt="Tropical Fusion Can" 
                            text01="TROPICAL" 
                            text02="FUSION" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/can-blackcurrant-label-product-new.png" 
                            alt="Wild Blackcurrant Can" 
                            text01="WILD" 
                            text02="BLACKCURRANT" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/can-apple-label-product-new1.png" 
                            alt="Apple & Blueberry Can" 
                            text01="APPLE &" 
                            text02="BLUEBERRY" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/shot-mfpshot-label-product-new1.png" 
                            alt="Energy Flavour Can" 
                            text01="ENERGY" 
                            text02="FLAVOUR" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/shot-buzz-label-product-new1.png" 
                            alt="Marshmallow Mad Candy Can" 
                            text01="MARSHMALLOW" 
                            text02="MAD CANDY" 
                        />
                        <ProductSmall 
                            imgSrc="/images/Performance_drinks/shot-rasp-label-product-new1.png" 
                            alt="Blue Raspberry Can" 
                            text01="BLUE" 
                            text02="RASPBERRY" 
                        />
                    </div>
                </div>

                <!-- Section 3 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <TitleSection title01="HYDRATION DRINKS" title02="BOOST YOUR HYDRATION!" />                
                    <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-4 p-10">
                        <ProductSmall 
                            imgSrc="/images/hydration_drinks/can-lemon-label-product-new1.png" 
                            alt="Lemon Lime Blast Can" 
                            text01="LEMON" 
                            text02="LIME BLAST" 
                        />
                        <ProductSmall 
                            imgSrc="/images/hydration_drinks/can-cherry-label-product-new1.png" 
                            alt="Cherry Apple Blast Can" 
                            text01="CHERRY" 
                            text02="APPLE BLAST" 
                        />
                    </div>
                </div>

                <!-- Section 4 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <TitleSection title01="WHEY PROTEIN" title02="ELEVATE YOUR PERFORMANCE!" />                
                    <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-4 p-10">
                        <ProductSmall 
                            imgSrc="/images/can-enlite-label-product.png" 
                            alt="Enlite Can" 
                            text01="EXTRA LOW" 
                            text02="SUGAR" 
                        />
                    </div>
                </div>

                <!-- Section 5 -->
                <div class="color-section m-5 overflow-hidden shadow-sm sm:rounded-lg backdrop-blur-sm bg-white/10 h-auto">
                    <TitleSection title01="HYDRATION DRINKS" title02="BOOST YOUR HYDRATION!" />                
                    <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-4 p-10">
                        <ProductSmall 
                            imgSrc="/images/can-enlite-label-product.png" 
                            alt="Enlite Can" 
                            text01="EXTRA LOW" 
                            text02="SUGAR" 
                        />
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

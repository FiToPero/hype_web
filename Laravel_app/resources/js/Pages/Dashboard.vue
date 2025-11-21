<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { onMounted, onUnmounted, ref } from 'vue';
import Carousel from '@/Components/Carousel.vue';
import Footer from '@/Components/Footer.vue';



</script>

<template>
    <AuthenticatedLayout>
        <div id="bg-dashboard" class=" bg-[#89fe71]">
            <!-- Section 1 -->
            <div class="w-full">
                <video
                    class="w-full h-[90vh] object-cover"
                    autoplay muted loop 
                    src="/videos/250515_Sport_Promo_Opener-2.mp4" 
                    type="video/mp4" 
                ></video>
            </div>
            <!-- Section 2 -->
            <div class="w-screen min-h-screen flex flex-col-reverse md:flex-row justify-center items-center p-6 md:p-10 lg:p-14">
                <div class="w-full md:w-1/2 text-center flex flex-col justify-center items-center gap-6 md:gap-8 lg:gap-10">
                    <h3 class="font-pirulen font-bold italic text-3xl md:text-5xl lg:text-6xl">ENERGY DRINKS</h3>
                    <h5 class="font-pirulen font-bold italic text-lg md:text-xl lg:text-2xl">MAXIMUM ENERGY</h5>
                    <a class="font-bold text-base md:text-lg lg:text-xl" href="#"><i class="fas fa-chevron-right" aria-hidden="true"></i> View energy drinks</a>
                </div>
                <div class="relative w-full md:w-1/2 h-[400px] md:h-[500px] lg:h-[600px]"> 
                    <img src="/images/welcome/MFP-sm-2-1.webp" alt="Energy Drink Image" class="absolute top-0 left-0 w-full md:w-[150%] scale-110 md:scale-150 z-10"/>
                    <img src="/images/welcome/can-sugar-free-left-rotated-1.webp" alt="Energy Drink Image" class="absolute inset-[10%] top-[15%] w-[300px] md:w-[400px] lg:w-[550px] z-20"/>
                    <img src="/images/welcome/can-mfp-right-rotated-1.webp" alt="Energy Drink Image" class="absolute inset-[30%] top-[25%] w-[300px] md:w-[400px] lg:w-[550px] z-30"/>
                </div>
            </div>
            <!-- Section 3 -->
            <div class="w-screen min-h-screen flex flex-col md:flex-row justify-center items-center p-6 md:p-10 lg:p-14">
                <div class="relative w-full md:w-1/2 h-[400px] md:h-[500px] lg:h-[600px]"> 
                    <img src="/images/welcome/explosion-entire-powder-1-1-1.webp" alt="Energy Drink Image" class="absolute top-0 left-0 w-full md:w-[150%] scale-110 md:scale-150 z-10"/>
                    <img src="/images/welcome/can-xtra-left-rotated-1-1-1-1.webp" alt="Energy Drink Image" class="absolute inset-[10%] top-[15%] w-[300px] md:w-[400px] lg:w-[550px] z-20"/>
                    <img src="/images/welcome/can-pwortd-blackcurrant-right-rotated-1000.webp" alt="Energy Drink Image" class="absolute inset-[30%] top-[25%] w-[300px] md:w-[400px] lg:w-[550px] z-30"/>
                </div>
                <div class="w-full md:w-1/2 text-center flex flex-col justify-center items-center gap-6 md:gap-8 lg:gap-10">
                    <h3 class="font-pirulen font-bold italic text-3xl md:text-5xl lg:text-6xl">PERFORMANCE <br> DRINKS</h3>
                    <h5 class="font-pirulen font-bold italic text-lg md:text-xl lg:text-2xl">DISRUPT YOUR ROUTINE</h5>
                    <a class="font-bold text-base md:text-lg lg:text-xl" href="#"><i class="fas fa-chevron-right" aria-hidden="true"></i> View performance drinks</a>
                </div>
            </div>
            <!-- Section 4 -->
            <div class="w-screen min-h-screen flex flex-col-reverse md:flex-row justify-center items-center p-6 md:p-10 lg:p-14">
                <div class="w-full md:w-1/2 text-center flex flex-col justify-center items-center gap-6 md:gap-8 lg:gap-10">
                    <h3 class="font-pirulen font-bold italic text-3xl md:text-5xl lg:text-6xl">HYDRATION <br> DRINKS</h3>
                    <h5 class="font-pirulen font-bold italic text-lg md:text-xl lg:text-2xl">BOOST YOUR HYDRATION</h5>
                    <a class="font-bold text-base md:text-lg lg:text-xl" href="#"><i class="fas fa-chevron-right" aria-hidden="true"></i> View hydration drinks</a>
                </div>                        
                <div class="relative w-full md:w-1/2 h-[400px] md:h-[500px] lg:h-[600px]"> 
                    <img src="/images/welcome/explosion-hydration-lemon-powder-768x617.webp" alt="Energy Drink Image" class="absolute top-0 left-0 w-full md:w-[150%] scale-110 md:scale-150 z-10"/>
                    <img src="/images/welcome/Hydration-left-rotated-1-768x768.webp" alt="Energy Drink Image" class="absolute inset-[10%] top-[15%] w-[300px] md:w-[400px] lg:w-[550px] z-20"/>
                    <img src="/images/welcome/Hydration-right-rotated-1-768x768.webp" alt="Energy Drink Image" class="absolute inset-[30%] top-[25%] w-[300px] md:w-[400px] lg:w-[550px] z-30"/>
                </div>
            </div>
            <!-- Section 5 -->
            <div class="w-screen min-h-screen flex flex-col-reverse md:flex-row justify-center items-center p-6 md:p-10 lg:p-14">
                <div class="w-full md:w-1/2 text-center flex flex-col justify-center items-center gap-6 md:gap-8 lg:gap-10 mt-10 md:mt-0">
                    <h3 class="font-pirulen font-bold italic text-3xl md:text-5xl lg:text-6xl">NUTRITION</h3>
                    <h5 class="font-pirulen font-bold italic text-lg md:text-xl lg:text-2xl">FUEL YOUR PASSION</h5>
                    <a class="font-bold text-base md:text-lg lg:text-xl" href="#"><i class="fas fa-chevron-right" aria-hidden="true"></i> View nutrition products</a>
                </div>
                <div class="relative w-full md:w-1/2 h-[300px] sm:h-[350px] md:h-[500px] lg:h-[600px]"> 
                    <img src="/images/welcome/creatine-tub-404x468-1.webp" alt="Creatine Tub" class="absolute inset-[38%] top-[47%] w-[180px] sm:w-[220px] md:w-[350px] lg:w-[450px] z-30"/>
                    <img src="/images/welcome/whey-tub-vanilla-761-1148.webp" alt="Whey Protein Tub" class="absolute inset-[10%] md:-inset-[10%] -top-[10%] w-[240px] sm:w-[300px] md:w-[450px] lg:w-[600px] z-20"/>
                    <img src="/images/welcome/mass-gainer-tub-strawberry-761-1148.webp" alt="Mass Gainer Tub" class="absolute inset-[40%] -top-[8%] w-[230px] sm:w-[290px] md:w-[450px] lg:w-[590px] z-10"/>
                </div>
            </div>
            <!-- End Sections -->
             <div class="w-full text-center text-5xl font-bold font-pirulen pb-6">CHECK OUT OUR INSTAGRAM</div>
        </div>
        <div class="bg-cyan-500 p-16">
            <Carousel />
        </div>
        <Footer />
    </AuthenticatedLayout>
</template>

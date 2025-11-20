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
            <div class="w-screen h-screen flex justify-center p-14">
                <div class=" w-1/2 text-center flex flex-col justify-center items-center gap-10">
                    <h3 class="font-pirulen font-bold italic text-5xl">ENERGY DRINKS</h3>
                    <h5 class="font-pirulen font-bold italic text-xl">MAXIMUM ENERGY</h5>
                    <a class="font-bold text-lg" href="#">View energy drinks</a>
                </div>
                <div class="relative w-1/2">
                    
                    <img src="/images/welcome/MFP-sm-2-1.webp" alt="Energy Drink Image" class="absolute top-0 left-0 w-[150%] scale-150  z-10"/>
                    <img src="/images/welcome/can-sugar-free-left-rotated-1.webp" alt="Energy Drink Image" class="absolute inset-[10%] top-[15%] w-[550px] z-20"/>
                    <img src="/images/welcome/can-mfp-right-rotated-1.webp" alt="Energy Drink Image" class="absolute inset-[30%] top-[25%] w-[550px] z-30"/>
                
                </div>
            </div>
          <!-- Section 3 -->
            <div class="w-full">
                 <!-- <div>
                    <h3 class="font-pirulen font-bold italic text-5xl">ENERGY DRINKS</h3>
                    <h5 class="font-pirulen font-bold italic text-xl">MAXIMUM ENERGY</h5>
                    <a class="font-bold text-lg" href="#">View energy drinks</a>
                </div>
                <div>
                    <img src="/images/welcome/MFP-sm-2-1.webp" alt="Energy Drink Image" class=""/>
                    <img src="/images/welcome/explosion-hydration-lemon-powder-768x617.webp" alt="Energy Drink Image" class=""/>
                    <img src="/images/welcome/explosion-hydration-lemon-powder-768x617.webp" alt="Energy Drink Image" class=""/>
                </div> -->
            </div>
            <!-- Section 4 -->
            <div class="w-full">

            </div>
            <!-- Section 5 -->
            <div class="w-full">
                 <!-- <div>
                    <h3 class="font-pirulen font-bold italic text-5xl">ENERGY DRINKS</h3>
                    <h5 class="font-pirulen font-bold italic text-xl">MAXIMUM ENERGY</h5>
                    <a class="font-bold text-lg" href="#">View energy drinks</a>
                </div>
                <div>
                    <img src="/images/welcome/explosion-hydration-lemon-powder-768x617.webp" alt="Energy Drink Image" class=""/>
                    <img src="/images/welcome/explosion-hydration-lemon-powder-768x617.webp" alt="Energy Drink Image" class=""/>
                    <img src="/images/welcome/MFP-sm-2-1.webp" alt="Energy Drink Image" class=""/>
                </div> -->
            </div>
        </div>
        <div class="bg-cyan-500 p-16">
            <Carousel />
        </div>
        <Footer />
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { onMounted, onUnmounted, ref } from 'vue';
import Carousel from '@/Components/Carousel.vue';
import Footer from '@/Components/Footer.vue';



</script>

<template>
    <AuthenticatedLayout>
        <div id="bg-dashboard" class=" bg-[#89fe71]">
            <div class="w-full">
              
                <video
                    class="w-full h-[90vh] object-cover"
                    autoplay muted loop 
                    src="/videos/250515_Sport_Promo_Opener-2.mp4" 
                    type="video/mp4" 
                ></video>
    
              
            
              

              

           
                
           


                

            </div>
        </div>
        <div class="bg-cyan-500 p-16">
            <Carousel />
        </div>
        <Footer />
    </AuthenticatedLayout>
</template>

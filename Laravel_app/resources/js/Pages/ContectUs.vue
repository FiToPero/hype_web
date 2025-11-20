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
         
            </div>
            <!-- Section 2 -->
            <div>

            </div>
            <!-- Section 3 -->
            <div>
            </div>
            <!-- Section 4 -->
            <div>

            </div>
            <!-- Section 5 -->
            <div>
                
            </div>
        </div>
        <div class="bg-cyan-500 p-16">
            <Carousel />
        </div>
        <Footer />
    </AuthenticatedLayout>
</template>

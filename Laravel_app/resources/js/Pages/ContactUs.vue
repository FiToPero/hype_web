<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { onMounted, onUnmounted, ref } from 'vue';
import Footer from '@/Components/Footer.vue';
import CarouselImages from '@/Components/CarouselImages.vue';



</script>

<template>
    <AuthenticatedLayout>
        <div id="bg-dashboard" class=" bg-[#89fe71]">
            <!-- Section 1 -->
            <div class="w-full">
              <CarouselImages />
            </div>
            <!-- Section 2 -->
            <div class="w-auto mx-64 text-white flex flex-col justify-center items-center ">
                <div class="my-10 p-10 px-24 bg-black bg-opacity-70 w-full text-center flex flex-col justify-center items-center">
                    <h3 class="mb-6 font-pirulen font-bold italic text-xl md:text-2xl lg:text-3xl">WANT TO BE OUR DISTRIBUTOR?</h3>
                    <p class="font-swiss text-left text-white text-md md:text-lg lg:text-xl px-10 my-4">
                        Thank you for your interest in Hype. We are constantly looking for new distributors who share our vision and ambition to help us build our brand and in turn help your business grow.
                        <br><br>
                        Hype Energy is not another energy drink clone, we are a different breed. We believe in building strong, long lasting relationships whilst giving you the support you need with your sales, marketing and design.
                    </p>
                    <a class="font-pirulen font-bold italic text-xl" href="#">APPLY <i class="fas fa-chevron-right" aria-hidden="true"></i></a>
                </div>
                <div class="my-10 p-10 px-24 bg-black bg-opacity-70 w-full text-center flex flex-col justify-center items-center">
                    <h3 class="mb-6 font-pirulen font-bold italic text-xl md:text-2xl lg:text-3xl">WANT TO BE SPONSORED BY HYPE?</h3>
                    <p class="font-swiss text-left text-white text-md md:text-lg lg:text-xl px-10 my-4">
                        If you’re looking for sponsorship and think you have something special to bring to Hype, then submit a sponsorship application at the link below!
                    </p>
                    <a class="font-pirulen font-bold italic text-xl" href="#">APPLY <i class="fas fa-chevron-right" aria-hidden="true"></i></a>
                </div>

            </div>
            <!-- Section 3 -->

            <div class="w-screen min-h-screen flex flex-col justify-center items-center bg-[url('/images/contact_us/background.webp')] bg-cover bg-center bg-no-repeat">
               <div class="w-[75%] mx-64 text-white font-pirulen font-bold italic my-10 p-10 px-24 bg-black bg-opacity-70 text-center flex flex-col justify-center items-center">
                    <h3 class="mb-6  text-xl md:text-2xl lg:text-3xl">CONTACT US</h3>
                    <hr class="w-full h-1 border-0 my-4 bg-[#89fe71]"></hr>

                    <div class="flex flex-row justify-center items-center gap-5 mb-4 text-sm">
                        <p>TEL:</p>
                        <p class="text-gray-600">+971 444 356 27</p>
                    </div>
                    <div class="flex flex-row justify-center items-center gap-5 mb-4 text-sm">
                        <p>PRESS:</p>
                        <p class="text-gray-600">press@hype.com</p>
                    </div>
                    <div class="flex flex-row justify-center items-center gap-5 mb-4 text-sm">
                        <p>OTHER INQUIRIES:</p>
                        <p class="text-gray-600">info@hype.com</p>
                    </div>
                    <hr class="w-full h-1 border-0 my-4 bg-[#89fe71]"></hr>
                
                    <div class="mt-6">
                        <h3 class="my-6  text-md">HEAD OFFICE – DUBAI</h3>
                        <div class="flex flex-col justify-center items-center gap-1 text-xs">
                            <p>Jumeirah Lake Towers,</p>
                            <p>JBC 2, Cluster V,</p>
                            <p>Office Nr. 601</p>
                            <p>PO Box 488154</p>
                            <p>Dubai, UAE</p>
                            <div class="flex flex-row justify-center items-center gap-5 mb-4 text-xs">
                                <p>TEL:</p>
                                <p class="text-gray-600">+971 444 356 27</p>
                            </div>
                        </div>
                    </div>
                    <div class="mt-6">
                        <h3 class="my-6  text-md">MARKETING  OFFICE – EU</h3>
                        <div class="flex flex-col justify-center items-center gap-1 text-xs">
                            <p>Centro de negocios Puerta de Banus,</p>
                            <p>Bloque E, Nr. 36,</p>
                            <p>Camino del Angel S/N</p>
                            <p>29660</p>
                            <p>Nueva Andalucia, Spain</p>
                            <div class="flex flex-row justify-center items-center gap-5 mb-4 text-xs">
                                <p>Tel:</p>
                                <p class="text-gray-600">+34 952 813 050</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <Footer />
    </AuthenticatedLayout>
</template>

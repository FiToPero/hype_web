<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { onMounted, onUnmounted, ref } from 'vue';
import Carousel from '@/Components/Carousel.vue';
import Footer from '@/Components/Footer.vue';



</script>

<template>
    <AuthenticatedLayout>
        <div class="w-full ">
            <!-- Section 3 -->
            <div class="w-full flex flex-col justify-center items-center bg-black">
                <img src="/images/behindHype/Hype-Energy-Drinks-Range-1024x790.webp" alt="Image" class=""/>
                <div class="w-full text-center flex flex-col justify-center items-center">
                    <div class="bg-[#89fe71] px-6 py-2 m-4">
                        <h3 class="font-pirulen text-black font-bold italic text-3xl md:text-5xl lg:text-6xl">BEHIND THE HYPE</h3>
                    </div>
                    <p class="font-swiss text-white font-bold text-xl md:text-2xl lg:text-3xl p-10 ">
                         Hype is more than just a brand. We’re a movement. Led by a former Formula 1® driver since 2000, we’re driven by passion, creativity, and ambition to become the world’s leading functional product company. 
                    </p>               
                </div>
            </div>
            <!-- Section 2 -->
             <div class="w-full flex flex-col justify-center items-center bg-[url('/images/behindHype/Hype-Energy-carbon-scaled.webp')] bg-cover bg-center bg-no-repeat">
                <video
                    class="w-[150vh] h-[80vh] object-cover my-4"
                    autoplay muted loop 
                    src="/videos/hype_corporate_video.mp4" 
                    type="video/mp4" 
                ></video>
                <div class="w-full text-center flex flex-col justify-center items-center">
                    <div class="bg-[#89fe71] px-6 py-2 mt-5">
                        <h3 class="font-pirulen text-black font-bold italic text-2xl md:text-3xl lg:text-4xl">OUR PURPOSE IS SIMPLE:</h3>
                    </div>
                    <h4 class="font-pirulen italic text-white font-bold text-xl md:text-2xl lg:text-3xl p-10">TO TRANSFORM HOW YOU LIVE, WORK, AND PLAY.</h4>
                    <p class="font-swiss text-white text-xl md:text-2xl px-36">
                        What started as a legacy energy drink brand quickly evolved into a functional product powerhouse. Our premium European ingredients impress minds across the Middle East, Australia, Europe, Africa, and Latin America. Yet, we won’t stop there.
                    </p>
                    <p class="font-swiss text-white text-xl md:text-2xl px-36 mt-6 mb-10">
                        We don’t settle for anything less than inspiring change and disrupting the game through our story-driven approach. Our commitment to innovation drives us to make functional products accessible to all. Day in and day out, we strive to make every day a good one, packed with thrilling and daring experiences.
                    </p>             
                </div>
            </div>
            <!-- Section 3 -->
            <div class="w-full flex flex-col justify-center items-center bg-[#89fe71] py-10">
                <div class="w-full text-center flex flex-col justify-center items-center">
                    <div class="bg-black px-6 py-2 m-4">
                        <h3 class="font-pirulen text-white font-bold italic text-xl md:text-2xl lg:text-3xl">THE END GAME</h3>
                    </div>
                    <p class="font-swiss text-black font-bold text-lg md:text-xl lg:text-2xl px-10 mb-4">
                        Driven to spark a global revolution in energy and performance, our intentions are clear: elevate the taste and quality of functional drinks while catering to the ever-changing moods of our customers. Aiming for nothing short of global dominance as the premier functional products brand, we lead by example and continually push boundaries.
                    </p>
                    <p class="font-swiss text-black font-bold text-lg md:text-xl lg:text-2xl px-10 ">
                        We aim to deliver innovative products with unique benefits and nutritional attributes that inspire people to live life on their own terms. 
                    </p>
                </div>
                <img src="/images/behindHype/new-behind-hype-1536x413.webp" alt="Image" class="my-5"/>
            </div>
            <!-- Section 4 -->
            <div class="flex flex-col md:flex-row  bg-[#E320A5] p-10">
                <div class="relative w-full md:w-1/2 "> 
                    <video
                        class="object-cover my-4"
                        autoplay muted loop 
                        src="/videos/Bertrand-Gachot-career.mp4" 
                        type="video/mp4" 
                    ></video>                
                </div>
                <div class="w-full md:w-1/2 text-left flex flex-col justify-center items-start gap-4 md:gap-6">
                    <div class="bg-black px-10 py-2 ml-10">
                        <h3 class="font-pirulen text-white font-bold italic text-left text-xl md:text-2xl lg:text-3xl">THE LEGACY</h3>
                    </div>
                    <p class="font-swiss text-black font-bold text-lg md:text-xl lg:text-2xl px-10">
                        Hype Energy’s rich history started in 1994, with the same visionaries behind the iconic Hard Rock Café. Since its inception, the brand has been heavily involved in motorsports. We sponsored various teams, including Arrows Formula 1® team, Benetton F1, Williams F1, the Racing Point F1 team, a Nascar team, and several motorbike teams. With a strong grip in the paddock, Hype Energy invested in sponsorships to broaden its global reach and secure worldwide distribution.
                    </p>
                    <p class="font-swiss text-black font-bold text-lg md:text-xl lg:text-2xl px-10 ">
                        As the brand grew, it became synonymous with the high-octane lifestyle of Formula 1®. This association strengthened in 1997, when F1 driver Bertrand Gachot signed a distribution deal with Hype to introduce the products in France. Bertrand Gachot transitioned from distributor to CEO in 2000, restructuring the brand and retaining four iconic products in the portfolio.
                    </p>
                    <p class="font-swiss text-black font-bold text-lg md:text-xl lg:text-2xl px-10 mb-4">
                        At Hype Energy, we embrace our motorsports heritage. We have crafted a range of innovative drinks that honor the fast-paced nature of the racing scene. Our iconic can designs boast carbon fibre elements and a matte black lid. Coupled with bold colours and thrilling flavours, Hype Energy will take you from 0-100 real quick!                    </p>
                </div>
                
            </div>
        </div>
        <Footer />
    </AuthenticatedLayout>
</template>





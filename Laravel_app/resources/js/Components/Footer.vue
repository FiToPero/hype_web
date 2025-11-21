<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
</script>
<template>
  <footer class="bg-black text-white py-6">
    <div class="grid grid-cols-8  h-[300px] mx-auto px-4">
        <div class="col-span-4 text-center">
            <ApplicationLogo class="mb-4 " />
            <div class="text-gray-300 text-md">
                <a href="#" class="hover:text-gray-400">Home | </a>
                <a href="#" class="hover:text-gray-400">Products | </a>
                <a href="#" class="hover:text-gray-400">Cocktails & Mocktails | </a>
                <a href="#" class="hover:text-gray-400">News | </a>
                <a href="#" class="hover:text-gray-400">Behind the Hype | </a>
                <a href="#" class="hover:text-gray-400">Find Us</a>
                <br>
                <a href="#" class="hover:text-gray-400">Career | </a>
                <a href="#" class="hover:text-gray-400">Privacy Policy | </a>
                <a href="#" class="hover:text-gray-400">Terms And Conditions | </a>
                <a href="#" class="hover:text-gray-400">FAQ | </a>
                <a href="#" class="hover:text-gray-400">Fraud Warning</a>
            </div>
        </div>
        <div class="col-span-2">
        </div>
        <div class="col-span-2  text-gray-300  text-left">
            <div class="flex flex-col items-start">
                <h5 class="text-md">About Hype</h5> 
                <p class="w-64 my-4 text-sm">
                    Hype is more than just a brand. We're a movement. Led by a former Formula 1® driver since 2000, we're fuelled by passion, creativity and the grit to become the world's most innovative functional product company.
                </p>
                <h5 class="text-md">Follow us!</h5>
            </div>
            <br>
            <div class="text-2xl">
                <i class="fab fa-linkedin mx-2" aria-hidden="true"></i>
                <i class="fab fa-facebook-square mx-2" aria-hidden="true"></i>
                <i class="fab fa-instagram mx-2" aria-hidden="true"></i>
                <i class="fab fa-tiktok mx-2" aria-hidden="true"></i>
            </div>
            <br>
            <p class="text-sm mt-2 text-md">&copy; 2024 Hype. All rights reserved.</p>
        </div>
 
      
    </div>
  </footer>
</template>
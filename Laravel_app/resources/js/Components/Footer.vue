<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
</script>
<template>
  <footer class="bg-black text-white py-6">
    <div class="flex items-center  h-[300px] mx-auto px-4 text-center">
        <div class="flex-1">
            <ApplicationLogo class="mx-auto mb-4 h-16" />
            <div class="text-gray-300 text-sm">
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
        <div class="flex-1 flex flex-col items-center justify-center text-gray-300">
            <div>
                <h5 class="text-md">About Hype</h5> 
                <p class="w-64 m-4 text-sm">
                    Hype is more than just a brand. We're a movement. Led by a former Formula 1® driver since 2000, we're fuelled by passion, creativity and the grit to become the world's most innovative functional product company.
                </p>
                <h5 class="text-md">Follow us!</h5>
            </div>
            <br><br>
                <div>
                    <i class="fa fa-linkedin" aria-hidden="true"></i>
                    <i class="fa fa-facebook mx-4" aria-hidden="true"></i>
                    <i class="fa fa-instagram" aria-hidden="true"></i>
                    <i class="fa fa-twitter mx-4" aria-hidden="true"></i>
                    <i class="fa fa-tiktok mx-4" aria-hidden="true"></i>
                </div>
            <br><br>
            <p class="text-sm mt-5 text-md">&copy; 2024 Hype. All rights reserved.</p>
        </div>
        
      
    </div>
  </footer>
</template>
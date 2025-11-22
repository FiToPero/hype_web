<script setup>
import { Head, Link } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

</script>

<template>
    <Head title="Welcome" />
    <div class="bg-black text-white/50">
        <div
            class="relative flex min-h-screen flex-col items-center justify-center selection:bg-[#FF2D20] selection:text-white"
        >
            <div class="relative w-full max-w-2xl px-6 lg:max-w-7xl">
           
                <main class="mt-6">
                    <div class=" rounded-lg  p-6 shadow-[0px_14px_34px_0px_rgba(0,0,0,0.08)] ring-1 ring-white/[0.05] bg-zinc-900 ring-zinc-800">
                        <ApplicationLogo class="w-20 h-20 mx-auto mb-6 text-[#89fe71]" />
                        <h3 class="text-3xl font-bold text-center text-white mb-4">Welcome to Your Application</h3>
                        <h1 class="my-5 text-center text-6xl font-pirulen italic text-[#6edc58]">HYPE ENERGY DRINK</h1>
                        <p class="text-center text-white/70 mb-6">
                            This is a starter template for your Laravel application built with Inertia.js and Vue 3.
                        </p>
                        <div class="flex justify-center space-x-4">
                            <Link
                                :href="route('dashboard')"
                                 v-if="$page.props.auth.user"
                                class="rounded-md bg-[#89fe71] px-4 py-2 font-semibold text-black hover:bg-[#6edc58] transition"
                            >Dashboard</Link>
                            <div v-else class="flex space-x-4">
                             <Link
                                :href="route('login')"
                                class="rounded-md bg-[#89fe71] px-4 py-2 font-semibold text-black hover:bg-[#6edc58] transition"
                            >Login</Link>
                             <Link
                                :href="route('register')"
                                class="rounded-md bg-[#89fe71] px-4 py-2 font-semibold text-black hover:bg-[#6edc58] transition"
                            >Register</Link>
                            </div>
                        </div>           
                    </div>
                </main>

             
            </div>
        </div>
    </div>
</template>

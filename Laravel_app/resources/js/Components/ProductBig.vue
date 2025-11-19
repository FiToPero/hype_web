<script setup>

defineProps({
    imgSrc: {
        type: String,
        required: true,
    },
    text: {
        type: String,
        required: true,
    },
    alt: {
        type: String,
        default: 'Product Image',
    },
});

</script>
<template>

<a class="relative block p-5">
    <img :src="imgSrc" :alt="alt" class="w-auto h-auto" />
    
    <h2 class="mt-3 text-xl font-pirulen font-bold text-black text-left">{{ text }}</h2>
    
</a>

</template>


<script setup>

defineProps({
    imgSrc: {
        type: String,
        required: true,
    },
    text01: {
        type: String,
        required: true,
    },
    text02: {
        type: String,
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
    <div class="absolute top-[200px] left-[200px] ">
        <h2 class="text-xl font-pirulen font-bold text-black text-left">{{ text01 }}<br>{{ text02 }}</h2>
    </div>
</a>

</template>


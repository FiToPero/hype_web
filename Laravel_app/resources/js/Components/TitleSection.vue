<script setup>
defineProps({
    title01: {
        type: String,
        required: true,
    },
    title02: {
        type: String,
        required: true,
    },
});
</script>

<template>

<div class="text-center py-8">
    <div class="bg-black inline-block px-8 py-4 mb-4">
        <h2 class="font-pirulen text-4xl text-white">{{ title01 }}</h2>
    </div>   
    <h5 class="font-pirulen text-3xl">{{ title02 }}</h5>
</div>

</template>
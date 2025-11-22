<script setup>
import { onMounted, ref } from 'vue';

const model = defineModel({
    type: String,
    required: true,
});

const input = ref(null);

onMounted(() => {
    if (input.value.hasAttribute('autofocus')) {
        input.value.focus();
    }
});

defineExpose({ focus: () => input.value.focus() });
</script>

<template>
    <input
        class="rounded-md shadow-sm border-gray-700 bg-gray-900 text-gray-300 focus:border-[#89fe71] focus:ring-[#89fe71]"
        v-model="model"
        ref="input"
    />
</template>

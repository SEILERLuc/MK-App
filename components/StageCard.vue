<template>
    <div class="flex flex-col justify-between items-center">
        <h3 class="px-2 font-bold">{{ stage.name }}</h3>
        <img :src="stage.img" class="h-auto sm:h-40 sm:w-96" :alt="stage.name" />
    </div>
</template>

<script setup>

defineProps({
    stage: {
        type: Object,
        required: true,
    }
})
</script>
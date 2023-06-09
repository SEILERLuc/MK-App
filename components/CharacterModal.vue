<template>
    <!--<n-button @click="showModal = true" class="border-none">
        <div class="m-2 flex w-32 cursor-pointer flex-wrap justify-center rounded-md bg-zinc-400 bg-gradient-to-b
            from-yellow-700 duration-300 hover:scale-110">
            <h3 class="px-2 font-bold">{{ character.name }}</h3>
            <img :src="character.img" class="h-32" :alt="character.name" />
        </div>

    </n-button>
    <n-modal v-model:show="showModal">
        <n-card style="width: 600px" title="Name" :bordered="false" size="huge" role="dialog" aria-modal="true">
            <template #header-extra>
                {{ character.name }}
            </template>
            Content
            <template #footer>
                Footer
            </template>
        </n-card>
    </n-modal>-->

    <div @click="showModal = true" class="m-2 flex flex-col justify-center w-32 h-44 cursor-pointer rounded-md bg-zinc-400 bg-gradient-to-b
            from-yellow-700 duration-300 hover:scale-110">
        <!--<n-button @click="showModal = true" class="border-none">-->
        <div class="flex flex-col justify-between items-center">
            <h3 class="px-2 font-bold">{{ character.name }}</h3>
            <img :src="character.img" class="h-36" :alt="character.name" />
        </div>
        <!--</n-button>-->

        <n-modal v-model:show="showModal">
            <n-card style="width: 600px" title="Name" :bordered="false" size="huge" role="dialog" aria-modal="true">
                <template #header-extra>
                    {{ character.name }}
                </template>
                Content : {{ character.gender }}
                <template #footer>
                    Footer
                </template>
            </n-card>
        </n-modal>
    </div>
</template>

<script setup>
const showModal = ref(false)

defineProps({
    character: {
        type: Object,
        required: true,
    }
})
</script>
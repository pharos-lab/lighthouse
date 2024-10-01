<template>
    <component :is="icon" class="w-7 h-7"/>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const icon = ref()
const props  = defineProps({
    name: String
})

onMounted(() => {
    import("@heroicons/vue/24/outline").then((icons) => {
        icon.value = icons[props.name + 'Icon']
    })
})
</script>
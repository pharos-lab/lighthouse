<template>
    <div class="h-screen bg-red-100 flex flex-col">
        <component :is="slots.default()[0]"></component>
        <div class="grow bg-teal-200 overflow-hidden flex">
            <component :is="slots.default()[1]"></component>
            <component :is="slots.default()[2]"></component>
        </div>
    </div>
</template>

<script setup>
import { onMounted, useSlots } from 'vue';

const slots = useSlots()

onMounted(() => {
    console.log(slots.default()[0])
})
</script>
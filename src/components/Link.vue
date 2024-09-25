<template>
    <a :href="props.href" class="link flex justify-center items-center px-3 py-2">
        <img v-if="props.img" 
            :src="props.img" 
            :alt="props.alt || 'add alternative text'"  
            class="bg-red-500" 
            :class="[
                props.type == 'action' ? 'h-8 w-8 rounded-full' : '',
                props.type == 'brand' ? 'max-w-64' : ''
                ]"
        >

        <template v-else>{{ props.label || 'add brand' }}</template>
    </a>
</template>

<script setup>
const props = defineProps({
    type: String,
    label: String,
    img: String,
    alt: String,
    href: String
})


</script>
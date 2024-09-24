<template>
    <header class="bg-blue-200 p-2 flex">
        <div class="brand flex justify-center items-center">
            <img :src="props.brand.img" :alt="props.brand.alt" v-if="props.brand.img">
            <p v-else>{{ props.brand.label }}</p>
        </div>
        <nav class="grow">
            <ul class="flex gap-4">
                <li v-for="(link, index) in props.links" :key="index" class="px-3 py-2">
                    <a :href="link.href">{{ link.label }}</a>
                </li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
const props = defineProps({
    links: Array,
    brand: Object,
})
</script>
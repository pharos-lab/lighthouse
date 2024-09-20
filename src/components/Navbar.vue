<template>
    <header class="bg-blue-200">
        <div class="brand"></div>
        <nav>
            <ul>
                <li v-for="(link, index) in links" :key="index">{{ link.label }}</li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
const props = defineProps({
    links: Array
})
</script>
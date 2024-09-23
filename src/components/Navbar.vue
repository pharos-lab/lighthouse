<template>
    <header class="bg-blue-200">
        <div class="brand"></div>
        <nav>
            <ul class="flex gap-4">
                <li v-for="(link, index) in links" :key="index" class="px-3 py-2">
                    <a :href="link.href">{{ link.label }}</a>
                </li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
const props = defineProps({
    links: Array
})
</script>
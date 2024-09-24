<template>
    <header class="bg-blue-200 p-2 ">
        <div class="container mx-auto flex gap-16">

            <a :href="props.brand.href" class="brand flex justify-center items-center">
                <img :src="props.brand.img" :alt="props.brand.alt" v-if="props.brand.img">
                <p v-else>{{ props.brand.label }}</p>
            </a>
            <nav class="grow">
                <ul class="flex gap-4" :class="alignmentClass">
                    <li v-for="(link, index) in props.links" :key="index" class="px-3 py-2">
                        <a :href="link.href">{{ link.label }}</a>
                    </li>
                </ul>
            </nav>
        </div>
    </header>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    links: Array,
    brand: Object,
    alignment: {
        type: String,
        default: 'center',
        validator(value) {
            return ['left', 'right', 'center'].includes(value)
        }
    }
})

const alignmentClass = computed(() => {
    return alignments[props.alignment] 
})

const alignments = {
    left: 'justify-start',
    center: 'justify-center',
    right: 'justify-end'
}
</script>
<template>
    <header class="bg-blue-200 p-2 ">
        <div class="container mx-auto flex gap-16">

            <a :href="brand.href" class="brand flex justify-center items-center" v-if="brand">
                <img :src="brand.img" :alt="brand.alt || 'add alternative text'" v-if="brand.img">
                <p v-else>{{ brand.label || 'add brand' }}</p>
            </a>
            <nav class="grow">
                <ul class="flex gap-4" :class="alignmentClass">
                    <li v-for="(link, index) in links" :key="index" class="px-3 py-2">
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

const brand = computed(() => {
    return props.links.filter(link => {       
        return link.hasOwnProperty('type') && link?.type == 'brand'
    })[0]
})

const links = computed(() => {
    return props.links.filter(link => {       
        return link?.type !== 'brand'
    })
})

const alignments = {
    left: 'justify-start',
    center: 'justify-center',
    right: 'justify-end'
}
</script>
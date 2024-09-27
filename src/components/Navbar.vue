<template>
    <header class="bg-blue-200 p-2 ">
        <div class="container mx-auto flex gap-16">
            <Link v-bind="brand" />
            <nav class="grow">
                <ul class="flex gap-4 h-full" :class="alignmentClass">
                    <Link v-bind="link" v-for="(link, index) in links" :key="index" :alignment="center" />
                </ul>
            </nav>
            <section>
                <ul class="flex gap-2">
                    <li v-for="(link, index) in actions" :key="index">
                        <Link v-if="!link.dropdown" v-bind="link"/>
                        <Dropdown v-else v-bind="link" />
                    </li>
                </ul>
            </section>
        </div>
    </header>
</template>

<script setup>
import { computed } from 'vue';
import Link from './Link.vue'
import Dropdown from './Dropdown.vue'

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
        return link?.type == 'brand'
    })[0]
})

const links = computed(() => {
    return props.links.filter(link => {       
        return link?.type !== 'brand' && link?.type !== 'action'
    })
})

const actions = computed(() => {
    return props.links.filter(link => {       
        return link?.type == 'action'
    })
})

const alignments = {
    left: 'justify-start',
    center: 'justify-center',
    right: 'justify-end'
}
</script>
<template>
    <div class="relative">
        <div class="px-3 py-2" v-if="props.img" @click="showItems = !showItems">
            <img :src="props.img" 
                :alt="props.alt || 'add alternative text'"  
                class="bg-red-500" 
                :class="[
                    props.type == 'action' ? 'h-8 w-8 rounded-full' : '',
                ]"
            >
        </div>
        <button v-else>
            {{ props.label }}
        </button>
        
        <div v-show="showItems" class="absolute bg-blue-500 right-0 rounded p-2">
            <Link v-for="(link, index) in props.dropdown" v-bind="link" :key="index"/>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import Link from './Link.vue'

const props = defineProps({
    label: String,
    type: String,
    label: String,
    img: String,
    alt: String,
    href: String,
    dropdown: Array
})

const showItems = ref(false)
</script>
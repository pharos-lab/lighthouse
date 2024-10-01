<template>
    <div class="relative cursor-pointer">
        <div class="px-3 py-2" v-if="props.img" @click="showItems = !showItems">
            <img :src="props.img" 
                :alt="props.alt || 'add alternative text'" 
                :class="[
                    props.type == 'action' ? 'h-8 w-8 rounded-full' : '',
                ]"
            >
        </div>
        <button v-else class="px-3 py-2">
            {{ props.label }}
        </button>
        
        <div v-show="showItems" class="absolute right-0 rounded p-2 top-16" :class="colorClass">
            <Link v-for="(link, index) in props.dropdown" v-bind="link" :key="index"/>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import Link from './Link.vue'
import { backgroundColor } from './backgroundColor.js';


const props = defineProps({
    label: String,
    type: String,
    label: String,
    img: String,
    alt: String,
    href: String,
    dropdown: Array,
    color: {
        type: String,
        default: 'blue',
        validator(value) {
        // The value must match one of these strings
        return ['gray', 'red', 'orange', 'yellow', 'green', 'blue'].includes(value);
        },
    },
    mode: {
        type: String,
        default: 'fill',
        validator(value) {
        // The value must match one of these strings
        return ['none', 'fill', 'light', 'outlined', 'text'].includes(value);
        },
    },
})

const colorClass = computed(() => {
  return backgroundColor[props.color][props.mode];
});

const showItems = ref(false)
</script>
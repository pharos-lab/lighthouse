<template>
    <RouterLink :to="props.to" v-if="props.to" />
    
    <a :href="props.href" class="link flex items-center px-3 py-2 gap-4" :class="alignmentClass" v-else>
        <icon :name="props.icon" v-if="props.icon"/>
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
import { computed } from 'vue';
import Icon from './Icon.vue'

const props = defineProps({
    type: String,
    label: String,
    img: String,
    alt: String,
    href: String,
    to: String,
    icon: String,
    alignment: {
        type: String,
        default: 'left',
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
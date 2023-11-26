<script setup lang="ts">
import { ref } from 'vue'
import { customAlphabet } from 'nanoid'

defineProps<{
    x1: number | string
    y1: number | string
    x2: number | string
    y2: number | string
    width?: number | string
    color?: string
}>()

const nanoid = customAlphabet('abcedfghijklmn', 10)

const id = nanoid()

</script>

<template>
    <svg class="absolute left-0 top-0 pointer-events-none" :width="Math.max(+x1, +x2) + 50"
        :height="Math.max(+y1, +y2) + 50">
        <line :x1="+x1" :y1="+y1" :x2="+x2" :y2="+y2" :stroke="color || 'currentColor'" :stroke-width="width || 2"
            :marker-end="`url(#${id})`" />
    </svg>
</template>
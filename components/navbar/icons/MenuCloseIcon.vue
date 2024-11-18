<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    :stroke-width="strokeWidth"
    viewBox="0 0 24 24"
    :height="height"
    :width="width"
    v-bind="attrs"
  >
    <path fill="none" d="M0 0h24v24H0V0z" />
    <path d="M3 18h13v-2H3v2zm0-5h10v-2H3v2zm0-7v2h13V6H3zm18 9.59L17.42 12 21 8.41 19.59 7l-5 5 5 5L21 15.59zz" />
  </svg>
</template>

<script setup lang="ts">
import { useAttrs } from 'vue'

const attrs = useAttrs()

const height = attrs.height || '1em'
const width = attrs.width || '1em'
const strokeWidth = attrs['stroke-width'] || '0'
</script>

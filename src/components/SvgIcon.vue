<script setup>
import { computed, defineProps } from 'vue'

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    default: '',
  },
})

const iconName = computed(() => `#icon-${props.name}`)
const svgClass = computed(() => {
  if (props.name)
    return `svg-icon icon-${props.name}`

  return 'svg-icon'
})
</script>

<template>
  <svg :class="svgClass" v-bind="$attrs" :style="{ color }">
    <use :xlink:href="iconName" />
  </svg>
</template>

<style lang="scss">
.svg-icon {
  width: 1em;
  height: 1em;
  fill: currentColor;
  vertical-align: middle;
}
</style>

<script lang='ts' setup>
import { computed } from 'vue'
const props = defineProps({
  mtx: {
    type: Number,
    required: true,
  },
  mty: {
    type: Number,
    required: true,
  },
  tx: {
    type: Number,
    required: true,
  },
  ty: {
    type: Number,
    required: true,
  },
})

const j = computed(() => 90 - Math.atan2(props.ty - props.mty, props.tx - props.mtx) * 180 / Math.PI)

const p = computed(() => {
  return `M${props.mtx} ${props.mty} L${props.tx} ${props.ty}`
})
const s = computed(() => {
  return `${props.tx},${props.ty + 3} ${props.tx - 3},${props.ty} ${props.tx + 3},${props.ty}`
})
</script>

<template>
  <div class="">
    <svg width="500" height="500">
      <path :d="p" stroke="red" stroke-width="2" />
      <!-- <path d="M 200 203 L 195 200 L 205 200 L 200 203" stroke="blue" fill="red" /> -->
      <polygon
        :points="s"
        :style="{ transform: `rotate(${j * -1}deg)` }"
        style="fill:red;stroke:red;stroke-width:2; transform-origin:40% 40%;"
      />

    </svg>
    {{ s }}
  </div>
</template>

  <style lang='scss' scoped>
  </style>


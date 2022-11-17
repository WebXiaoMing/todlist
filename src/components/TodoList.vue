<template>
  <ul class="todo-list">
    <template v-for="item in data">
      <slot :item="item"></slot>
    </template>
  </ul>
</template>

<script setup>
import { defineProps, onBeforeUnmount, onUnmounted } from 'vue'
const props = defineProps({
  data: {
    type: Array,
    required: true
  }
})

const handleClick = (item) => {
  item.status = 'complete'
}
 
onBeforeUnmount(() => {
  console.log('onBeforeUnmount')
})

onUnmounted(() => {
  console.log('onUnmounted')
})
</script>
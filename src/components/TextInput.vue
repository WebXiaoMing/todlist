<template>
  <input type="text" v-model="value" @keydown.enter="handleEnter">
</template>

<script steup>
import { ref, defineEmits } from 'vue'


const emit = defineEmits(['change'])

const value = ref('')

const handleEnter = (e) => {
  emit('change', e)
}

</script>
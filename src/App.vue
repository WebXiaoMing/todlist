<template>
  <div class="container">
    <TextInput @change="handleChange"/>
    <div>
      <button @click="status = 'all'">all</button>
      <button  @click="status = 'complete'">complete</button>
      <button @click="status = 'todo'">todo</button>
    </div>
    <TodoList :data="list" v-if="status === 'all'">
      <template v-slot="{ item }">
        <div 
          :style="`color: ${item.status === 'complete' ? 'green' : 'red'  }`"
          @click="item.status = 'complete'"
        >{{ item.value }}</div>
      </template>
    </TodoList>
  </div>
</template>

<script setup>
import { reactive, ref, computed, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'
import TextInput from './components/TextInput.vue'
import TodoList from './components/TodoList.vue'
const result = reactive([])

const status = ref('all')

const handleChange = (val) => {
  const str = val.target.value
  result.push({
    status: 'todo',
    value: str
  })
}

const list = computed(() => result.filter(item => item.status === status.value || status.value === 'all'))

onBeforeMount(() => {
  console.log('onBeforeMount')
})

onMounted(() => {
  console.log('onMounted')
})

onBeforeUpdate(() => {
  console.log('onBeforeUpdate')
})

onUpdated(() => {
  console.log('onUpdated')
})

onBeforeUnmount(() => {
  console.log('onBeforeUnmount')
})

onUnmounted(() => {
  console.log('onUnmounted')
})

</script>

<style>

</style>
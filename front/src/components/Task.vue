<script setup>
import { ref } from 'vue'

const tasks = ref([])

async function getTasks(){
  try{
    const data = await fetch('http://localhost:8000/tasks');
    tasks.value = await data.json()
  } catch(err){
    console.error('🔥', err)
  }
}

(async () => {
  await getTasks()
})()

</script>

<template>
  <div v-for="task in tasks" :key="task">
    {{ task }}
  </div>
</template>

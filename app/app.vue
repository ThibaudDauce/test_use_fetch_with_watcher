<template>
  <div>
    <button @click="someParam = 'test'">Set query param</button>

    {{  data  }}

    {{ error }}
  </div>
</template>
<script setup lang="ts">

const someParam = ref(null as null | string)

watch(someParam, () => {
  console.log('Some param changed')
})

const { data, error } = useFetch('https://jsonplaceholder.typicode.com/todos/1', {
  query: {
    someParam: someParam,
  }
})
</script>

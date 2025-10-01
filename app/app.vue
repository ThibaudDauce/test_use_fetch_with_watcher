<template>
  <div>
    <!-- Clicking this button fail the request, only the first time after refresh -->
    <button @click="someParam++">Set query param</button>

    {{  data  }}

    {{ error }}
  </div>
</template>
<script setup lang="ts">

const someParam = ref(1)

// Comment these lines to make it work
watch(someParam, () => {
  console.log('Some param changed')
})

const { data, error } = useFetch('https://jsonplaceholder.typicode.com/todos/1', {
  query: {
    someParam: someParam,
  }
})
</script>

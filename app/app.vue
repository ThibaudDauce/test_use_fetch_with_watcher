<template>
  <div>
    <!-- Clicking this button fail the request, only the first time after refresh -->
    <div>
    Current param {{ someParam }}. <button @click="someParam++">Set query param</button>
    </div>

    <div v-if="data">
      <strong>Data:</strong>
      {{  data  }}
    </div>

    <div v-if="error">
      <strong>Error:</strong>
      {{ error }}
    </div>
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

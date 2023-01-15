<script setup lang="ts">
const { data } = useFetch('/api/user', { body: 'testing', method: 'POST' })
</script>

<template>
  <div>
    {{ data }}
  </div>
</template>

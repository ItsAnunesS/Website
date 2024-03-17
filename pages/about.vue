<script setup lang="ts">
const user = useSupabaseUser()
</script>

<template>
  <pre v-if="user">
    {{ user }}
  </pre>
</template>

<style scoped>

</style>
<template>
  <h1><slot /></h1>
</template>

<script>
export default {
  name: 'BaseTitle'
}
</script>

<style scoped>

h1 {
  text-transform: capitalize;
  margin-bottom: 30px;
}
</style>

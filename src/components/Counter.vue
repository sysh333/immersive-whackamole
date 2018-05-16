<template>
  <div class="counter">
    <h1>{{ label }}</h1>
    <h2>{{ value }}</h2>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: ['label', 'value']
}
</script>

<style>

</style>

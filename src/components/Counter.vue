<template>
  <div class="counter">
    <h2>{{ label }}</h2>
    <h1>{{ value }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: ['label', 'value']
}
</script>

<style>
.counter {
  border: 1px solid #000;
  margin-top: 20px;
  padding: 20px;
}
.counter h1 {
  font-size: 2.5em;
  margin: 0;
  text-align: center;
}
.counter h2 {
  margin: 0;
  text-align: center;
}
</style>

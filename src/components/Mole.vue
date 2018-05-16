<template>
  <div class="mole" v-on:click="wacked">
    {{ state }}
  </div>
</template>

<script>
export default {
  name: 'Mole',
  props: ['state', 'idx'],
  methods: {
    wacked: function() {
      this.$emit('whacked', this.idx);
    }
  }
}
</script>

<style>

</style>

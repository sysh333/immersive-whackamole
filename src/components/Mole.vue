<template>
  <div class="mole" v-on:click="handleWhack">
    {{ active }}
  </div>
</template>

<script>
export default {
  name: 'Mole',
  props: ['active', 'moleId'],
  methods: {
    handleWhack: function() {
      this.$emit('whack', this.moleId);
    }
  }
}
</script>

<style>

</style>

<template>
  <div class="moles-container">
    <Mole 
      class="mole"
      v-for="(moleState, idx) in moleData"
      v-bind:key="idx"
      v-bind:moleId="idx"
      v-bind:active="moleState"
      v-on:whack="handleWhack"
    >
    </Mole>
  </div>
</template>

<script>
import Mole from './Mole';

export default {
  name: 'Moles',
  components: { 
    Mole: Mole
  },
  props: ['moleData'],
  methods: {
    handleWhack: function(moleId) {
      this.$emit('whack', moleId);
    }
  }
}
</script>

<style>

</style>

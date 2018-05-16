<template>
  <div class="moles-container">
    <Mole 
      class="mole"
      v-for="(moleState, idx) in moleData"
      v-bind:key="idx"
      v-bind:idx="idx"
      v-bind:state="moleState"
      v-on:whacked="handleWhacked"
    >
    </Mole>
  </div>
</template>

<script>
import Mole from './Mole';

export default {
  name: 'Moles',
  components: { 
    Mole
  },
  props: ['moleData'],
  methods: {
    handleWhacked: function(idx) {
      this.$emit('whacked', idx);
    }
  }
}
</script>

<style>

</style>

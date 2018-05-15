<template>
  <div class="moles-container">
    <Mole 
      class="mole"
      v-for="(moleState, idx) in moleData"
      v-bind:key="idx"
      v-bind:state="moleState"
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
  props: ['moleData']
}
</script>

<style>

</style>

<template>
  <div>
      <p>{{originalPrice}}</p>
      <p>{{this.$store.getters.doublePrice}}</p>
      <p>{{this.$store.getters.triplePrice}}</p>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
    computed:{
        ...mapGetters([])
    }
}
</script>

<style>

</style>
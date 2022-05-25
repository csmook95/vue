<template>
  <div id="app">
    <AppHeader v-bind:propsdata="str" v-on:renew="renewString"></AppHeader>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'

export default {
    data() {
        return {
            str: "아니"
        };
    },
    components: { AppHeader },
    methods:{
      renewString(){
        this.str='hi'
      }
    }
}
</script>

<style>
</style>

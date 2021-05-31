<template>
  <bootstrap-vue>
    <icons-plugin />
    <HelloWorld />  
  </bootstrap-vue>  
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue';
import HelloWorld from './components/HelloWorld.vue';

@Options({
  components: {
    HelloWorld,
    BootstrapVue,
    IconsPlugin
  },
})
export default class App extends Vue {}

</script>

<style lang="sass">
  #app 
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;

</style>

<style>

</style>

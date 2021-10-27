<template>
  <Reader id="reader-main"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Reader from './components/Reader.vue';

@Options({
  components: {
    Reader,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0;
  height: 100vh;
}
#reader-main {
  height: 100%;
}
</style>

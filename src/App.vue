<template>
  <DarkModeButton/>
  <Reader id="reader-main"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import Reader from './components/Reader.vue'
import DarkModeButton from './components/DarkModeButton.vue'


@Options({
  components: {
    Reader,
    DarkModeButton
  },
})
export default class App extends Vue {
  darkmode = false
}
</script>

<style>
/* Define styles for the default root window element */
:root {
  --background-color-primary: #ebebeb;
  --accent-color: #cacaca;
  --text-primary-color: #222;
  --element-size: 4rem;
  --slider-color: #1c53a5;
  --transition-time: 0.25s;
}

/* Define styles for the root window with dark - mode preference */
:root.dark {
  --background-color-primary: #1e1e1e;
  --accent-color: #3f3f3f;
  --text-primary-color: #f0f1f1;
  --slider-color: #63b4da;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
  height: 100vh;
  border-color: var(--accent-color);
  color: var(--text-primary-color);
  background-color: var(--background-color-primary);
  transition: background-color var(--transition-time), color var(--transition-time);
}

#reader-main {
  height: 100%;
}
</style>

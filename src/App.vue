<template>
  <div id="app">
    <Head/>
    <ButtonBar/>
  </div>
</template>

<script>
import Head from './components/Head.vue'
import ButtonBar from './components/ButtonBar.vue'
export default {
  name: 'App',
  components: {
    Head,
    ButtonBar
  }
}
</script>

<style>
#app {
  text-align: center;
  margin-top: 30px;
}
</style>

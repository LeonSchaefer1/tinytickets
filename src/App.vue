<template>
  <div id="app">
    <Head/>
    <TicketArea/>
  </div>
</template>

<script>
import Head from './components/Head.vue'
import TicketArea from './components/TicketArea.vue'


export default {
  name: 'App',
  components: {
    Head,
    TicketArea
  }
}
</script>

<style>
#app {
  text-align: center;
  margin-top: 30px;
}
</style>

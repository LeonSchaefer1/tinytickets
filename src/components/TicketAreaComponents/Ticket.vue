<template>
  <div>
      <p> Title: {{ this.title }} Content: {{ this.content }} </p>
      <input type="checkbox">
  </div>
</template>

<script>

export default {

    name: 'ticket',

    props:{
         
        title: String,
        content: String,
    }
}
</script>

<style>

</style>
<template>
  <div>
    <button @click="createTicketMaskHandler($event)" id="add-button" ></button>
    <button id="delete-button"></button>
  </div>
</template>

<script>

export default {
  name: 'ButtonBar',

  components: {
  },

  props:{
    showCreateTicketMaskParent : Boolean,
  },

  data: function () {
  return{
    showCreateTicketMask : this.showCreateTicketMaskParent,
  }
  },

  methods: {
    createTicketMaskHandler (event) {
      event.preventDefault();
      this.showCreateTicketMask = ! this.showCreateTicketMask
      this.$emit(
        'showCreateTicketMaskChild',
        this.showCreateTicketMask,
      )  
    }
  }


}
</script>

<style scoped>
button {
    display: inline-block;
    height: 134px;
    padding: 0;
    margin: 0;
    vertical-align: top;
    width: 104px;
}

#add-button {
    background-image: url( "../../assets/plus-circle-solid.svg" );
    background-size: 100px 130px;
    height: 134px;  
    width: 104px;
}

#delete-button {
    background-image: url( "../../assets/trash-alt-solid.svg" );
    background-size: 100px 130px;
    height: 134px;  
    width: 104px;
}
</style>
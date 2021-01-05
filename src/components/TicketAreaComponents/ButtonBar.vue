<template>
  <div class="flex justify-center p-3">
    <div class="px-7">
      <button  @click="createTicketMaskHandler($event)" id="add-button" ></button>
    </div>
    <div class="px-7">
          <button @click="deleteMarkedTicketsHandler($event)" id="delete-button" ></button>
    </div>
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
    },
    deleteMarkedTicketsHandler(event){
      event.preventDefault();
      this.$emit(
        'deleteAllMarkedTickets',
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
    background-size: 105px 130px;
    height: 134px;  
    width: 104px;
}

#delete-button {
    background-image: url( "../../assets/trash-alt-solid.svg" );
    background-size: 110px 130px;
    height: 130px;  
    width: 110px;
}
</style>
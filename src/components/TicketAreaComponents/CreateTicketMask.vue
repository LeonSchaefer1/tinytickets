<template>
<div>
  <input v-model="curTitle" placeholder="title">
  <input v-model="curContent" placeholder="content">
  <button @click="closeButtonHandler($event)" id="close-button"></button>
  <button @click="commitTicketHandler($event)" id="commit-button">Create Ticket</button>
</div>
</template>

<script>
export default {
name: 'CreateTicketMask',

data: function () {
  return{
    curTitle: '',
    curContent: '',
  }
},

methods:{
  closeButtonHandler(event){
    event.preventDefault();
    this.$emit(
      'closeButtonClick',
      true,
    );
  },
  commitTicketHandler(event){
    event.preventDefault();
    this.$emit(
      'newTicket',
      { 
        title: this.curTitle,
        content: this.curContent,
      },
    );
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

#close-button {
    background-image: url( "../../assets/window-close-solid.svg" );
    background-size: 100px 130px;
    height: 134px;  
    width: 104px;
}

</style>
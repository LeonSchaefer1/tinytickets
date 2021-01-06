<template>
<div class="grid justify-center p-20">

  <div>
   <div class="mt-1 relative rounded-md shadow-sm">
    <textarea v-model="curTitle" id="title" name="title" rows="1" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 mt-1 block w-96 sm:text-sm border-gray-300 rounded-md border-4 " placeholder="title"></textarea>
  </div>
  <div class="mt-1">
     <textarea v-model="curContent" id="content" name="content" rows="10" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 mt-1 block w-full sm:text-sm border-gray-300 rounded-md border-4" placeholder="content"></textarea>
  </div>
  </div>

  <div class="flex justify-center">
    <div class="px-0">
      <button @click="commitTicketHandler($event)" id="commit-button" ></button>  
    </div>
        
    <div class="px-5"></div>
      <button @click="closeButtonHandler($event)" id="close-button" ></button>
  </div>

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

props: {
  nextTicketIndex: Number,
},

methods:{

  commitTicketHandler(event){
    event.preventDefault();
    this.$emit(
      'newTicket',
      { 
        title: this.curTitle,
        content: this.curContent,
        id: this.nextTicketIndex,
        isMarked: false,
      },
    );
  },
  
  closeButtonHandler(event){
    event.preventDefault();
    this.$emit(
      'closeButtonClick',
      true,
    );
  },
  
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
    width: 100px;
}

#commit-button {
    background-image: url( "../../assets/check-square-solid.svg" );
    background-size: 100px 125px;
    height: 130px;  
    width: 100px;
}

</style>
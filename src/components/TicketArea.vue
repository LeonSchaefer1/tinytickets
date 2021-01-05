
<template>
  <!-- If no tickets are created, do this-->
  <div v-if="this.tickets.length == 0 && !showCreateTicketMask">
    <ButtonBar
      :showCreateTicketMaskParent="showCreateTicketMask"
      @showCreateTicketMaskChild="createTicketMaskHandler"
      @deleteAllMarkedTickets="deleteMarkedTickets"
    />
    <!-- If Mask to create a new ticket is open, do this-->
    <div v-if="showCreateTicketMask">
      <CreateTicketMask
        :nextTicketIndex = this.curTicketIndex
        @closeButtonClick="createTicketMaskHandler"
        @newTicket="addTicket"
      />
    </div>
    <NoTicketNotify />
  </div>
  <!-- If tickets already are created, do this-->
  <div v-else>
    <ButtonBar
      :showCreateTicketMaskParent="showCreateTicketMask"
      @showCreateTicketMaskChild="createTicketMaskHandler"
      @deleteAllMarkedTickets="deleteMarkedTickets"
    />
    <!-- If Mask to create a new ticket is open, do this-->
    <div v-if="showCreateTicketMask">
      <CreateTicketMask
        :nextTicketIndex = this.curTicketIndex
        @closeButtonClick="createTicketMaskHandler"
        @newTicket="addTicket"
      />
    </div>
    <div v-else>
      <TicketList v-bind:ticketList="tickets" />
    </div>
    
  </div>
</template>


<script>
import NoTicketNotify from "./TicketAreaComponents/NoTicketNotify.vue";
import TicketList from "./TicketAreaComponents/TicketList.vue";
import ButtonBar from "./TicketAreaComponents/ButtonBar.vue";
import CreateTicketMask from "./TicketAreaComponents/CreateTicketMask";

export default {
  name: "TicketArea",
  components: { NoTicketNotify, TicketList, ButtonBar, CreateTicketMask },

  data: function () {
    return {
      curTicketIndex: 1,
      showCreateTicketMask: false,
      tickets: [],
    };
  },

  methods: {
    createTicketMaskHandler() {
      this.showCreateTicketMask = !this.showCreateTicketMask;
    },
    addTicket(newTicket) {
      if (newTicket.title.length <= 5) {
        alert("Title should be at least 6 characters long");
      }
      if (newTicket.content.length <= 15) {
        alert("Content should be at least 16 characters long");
      } else {
        this.tickets.push(newTicket);
        this.createTicketMaskHandler();
        this.curTicketIndex++;
      }
    },
    deleteMarkedTickets(){
      var i;
      for(i = 0; i <= this.tickets.length; i++){
        if(this.tickets[i].isMarked){
          this.tickets.splice(i,1)
        }
      }
      if(this.tickets[0].isMarked){
        this.tickets.splice(0,1)
      }
    }
  },
};
</script>

<style>
</style>

<template>
  <!-- If no tickets are created, do this-->
  <div v-if="this.tickets.length == 0 && !showCreateTicketMask">
    <ButtonBar
      :showCreateTicketMaskParent="showCreateTicketMask"
      @showCreateTicketMaskChild="createTicketMaskHandler"
    />
    <!-- If Mask to create a new ticket is open, do this-->
    <div v-if="showCreateTicketMask">
      <CreateTicketMask
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
    />
    <!-- If Mask to create a new ticket is open, do this-->
    <div v-if="showCreateTicketMask">
      <CreateTicketMask
        @closeButtonClick="createTicketMaskHandler"
        @newTicket="addTicket"
      />
    </div>
    <TicketList v-bind:ticketList="tickets" />
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
      }
    },
  },
};
</script>

<style>
</style>
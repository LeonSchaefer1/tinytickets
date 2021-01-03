<template>
  <div>
    <ul id="example-1">
        <li v-for="ticket in ticketList" :key="ticket.title">
          <Ticket :title=ticket.title :content=ticket.content />
        </li>
    </ul>
  </div>
</template>

<script>
import Ticket from './Ticket.vue'
export default {
  components: { Ticket },
    name: 'TicketList',
    props:{
        ticketList: Array,
    }

}
</script>

<style>

</style>
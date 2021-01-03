<template>
  <div>
    <ul id="example-1">
        <li v-for="ticket in ticketList" :key="ticket.title">
            {{ ticket.title }}
            {{ ticket.content }}
        </li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'TicketList',
    props:{
        ticketList: Array,
    }

}
</script>

<style>

</style>
<template>
  <div>
    <div>
      <table class="grid justify-center divide-y divide-gray-200">
        <thead class="bg-gray-50">
          <tr>
            <th>
              <input type="checkbox">
            </th>
            <th
              scope="col"
              class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider w-72"
            >
              Title
            </th>
            <th
              scope="col"
              class=" py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider w-96"
            >
              Content
            </th>
          </tr>
        </thead>
        <tbody class="bg-white divide-y divide-gray-200" v-for="ticket in ticketList" :key="ticket.title" >
          <Ticket :title="ticket.title" :content="ticket.content" :id="ticket.id" :isMarked="ticket.isMarked" @markStatus="handleMarkStatusChange"/>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Ticket from "./Ticket.vue";
export default {
  components: { Ticket },
  name: "TicketList",
  props: {
    ticketList: Array,
  },

  methods: {
    handleMarkStatusChange(id, isMarked) {
      this.ticketList.forEach((ticket) => {
        if (id === ticket.id) {
          ticket.isMarked = isMarked;
        }
      });
    },
  },
};
</script>

<style>
</style>
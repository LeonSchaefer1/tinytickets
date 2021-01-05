<template>
  <div>



      
<div class="flex flex-col">
  <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
    <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
      <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-gray-50">
            <tr>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Title
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Content
              </th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200" v-for="ticket in ticketList" :key="ticket.title">
            <Ticket :title=ticket.title :content=ticket.content :id=ticket.id :isMarked=ticket.isMarked @markStatus="handleMarkStatusChange" />
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>
  </div>
</template>

<script>
import Ticket from './Ticket.vue'
export default {

  
  components: { Ticket },
    name: 'TicketList',
    props:{
        ticketList: Array,
    },

    methods: {
      handleMarkStatusChange(id, isMarked){
        this.ticketList.forEach(ticket => {
          if(id === ticket.id){
            ticket.isMarked = isMarked;
          }
        });
      }
    }
    }

</script>

<style>

</style>
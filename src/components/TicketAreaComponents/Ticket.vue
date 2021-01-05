<template>
  <div>
    <tr>
      <td class="px-6 py-4 whitespace-nowrap">
        <div class="flex items-center">
          <div class="flex-shrink-0 h-10 w-10">

            <input
            type="checkbox"
             v-model="isMarked"
             @change="changeMarkHandle($event)"
            />

            {{ this.title }}
            
          </div>
          <div class="ml-4"></div>
        </div>
      </td>
      <td class="px-6 py-4 whitespace-nowrap">
        {{ this.content }}
      </td>
    </tr>
    
  </div>
</template>

<script>
export default {
  name: "ticket",

  props: {
    id: Number,
    title: String,
    content: String,
    isMarked: Boolean,
  },

  methods: {
    changeMarkHandle(event) {
      event.preventDefault();
      this.$emit("markStatus", this.id, this.isMarked);
    },
  },
};
</script>

<style>
</style>
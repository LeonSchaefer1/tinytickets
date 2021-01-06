<template>
  <div>
    <tr>
      <td>
        <input type="checkbox" v-model="isMarked" @change="changeMarkHandle($event)"/>
      </td>
      <td class="px-6 py-4 whitespace-nowrap w-72">
        {{ this.title }}
      </td>
      <td class="py-4 whitespace-nowrap w-96 text-left">
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
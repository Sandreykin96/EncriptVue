<template>
  <div>
    <ul>
      <MessageItem
        v-for="(mes,i) of messages"
        v-bind:mes="mes"
        v-bind:index="i"
        v-on:remove-message="removeMessage"
      />
    </ul>
  </div>
</template>

<script>
import MessageItem from "@/components/MessageItem";
export default {
  props: ["messages"],
  components: {
    MessageItem
  },
  methods: {
    removeMessage(id) {
      this.$emit("remove-message", id);
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
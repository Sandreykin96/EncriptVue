<template>
  <form v-on:submit.prevent="onSubmit">
    <input type="text" v-model="title" />
    <button type="submit">Добавить</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ""
    };
  },
  methods: {
    onSubmit() {
      let newMessage = {};
      let response = fetch("http://localhost:5000/messages", {
        method: "POST",
        headers: {
          "Content-Type": "application/json;charset=utf-8"
        },
        body: JSON.stringify(this.title)
      })
      .then(response => response.json())
      .then(json => {
        newMessage = json;
        this.title = "";
        this.$emit("add-message", newMessage);
      });
    }
  }
}
</script>

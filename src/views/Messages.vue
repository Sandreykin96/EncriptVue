<template>
  <div>
    <H4>Наберите текст</H4>
    <AddMessage @add-message="addMessage" />
    <hr />
    <select v-model="filter" v-if="!loading">
      <option value="all">Все</option>
      <option value="completed">Прочитано</option>
      <option value="not completed">Не прочитано</option>
    </select>
    <Loader v-if="loading" />
    <Message
      v-else-if="filteredMessages.length"
      v-bind:messages="filteredMessages"
      @remove-message="removeMessage"
    />
    <p v-else>Нет закодированных посланий</p>
  </div>
</template>

<script>
import Message from "@/components/Message";
import AddMessage from "@/components/AddMessage";
import Loader from "@/components/Loader";

export default {
  data() {
    return {
      messages: [],
      loading: true,
      filter: "all"
    };
  },
  mounted() {
    fetch("http://localhost:5000/messages")
      .then(response => response.json())
      .then(json => {
        this.messages = json;
        this.loading = false;
      });
  },
  computed: {
    filteredMessages() {
      if (this.filter === "all") {
        return this.messages;
      }
      if (this.filter === "completed") {
        return this.messages.filter(t => t.completed);
      }
      if (this.filter === "not completed") {
        return this.messages.filter(t => !t.completed);
      }
    }
  },
  components: {
    Message,
    AddMessage,
    Loader
  },
  methods: {
    removeMessage(id) {
      this.messages = this.messages.filter(t => t.id !== id);
    },
    addMessage(todo) {
      this.messages.push(todo);
    }
  }
};
</script>
<template>
  <div>
    <li>
      <span v-bind:class="{done:mes.completed}">
        <input type="checkbox" v-on:change="mes.completed = !mes.completed" />
        <strong>{{index+1}}</strong>
        {{mes.title|uppercase}}
      </span>
      <span>
        <button class="rm" v-on:click="$emit('remove-message', mes.id)">&times;</button>
      </span>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    mes: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      // return value.toUpperCase();
      return value;
    }
  }
};
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 2 rem;
  margin-bottom: 1rem;
}
.rm {
  background: rgb(8, 56, 145);
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
}
input {
  margin-right: 1rem;
}
.done {
  text-decoration: line-through;
}
</style>
<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input v-on:change="todo.completed = !todo.completed" type="checkbox">
      <strong>{{index + 1}}</strong>
      {{todo.title | uppercase}}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
}
</script>

<style scoped>
  li {
    border: solid 1px #ccc;
    display: flex;
    justify-content: space-between;
    padding: 0.5rem 2rem;
    margin-bottom: 1rem;
  }
  .rm {
    background-color: red;
    border-radius: 50%;
    color: #fff;
    font-weight: bold;
  }
  .done {
    text-decoration: line-through;
  }
  input {
    margin-right: 1rem;
  }
</style>
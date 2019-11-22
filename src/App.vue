<template>
  <div>
    <form @submit="addTodo">
      <input class="common" v-model="input" type="text" placeholder="Things to do" />
      <button class="common" type="submit">Add</button>
    </form>
    <div v-for="({ completed, id, text }) in todos" v-bind:key="id">
      <div class="common todo-item">
        <span
          v-bind:class="{ 'done': completed }"
          @click="changeStatus(id)"
        >{{text}}</span> <a href="#" @click="deleteTodo(id)">delete</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      todos: [],
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      this.todos = [
        ...this.todos,
        {
          completed: false,
          id: this.todos && this.todos.length > 0
            ? this.todos.sort((a, b) => b.id - a.id)[0].id + 1
            : 1,
          text: this.input,
        },
      ];
      this.input = '';
    },
    changeStatus(id) {
      this.todos = this.todos.map(
        todo => (todo.id === id && ({ ...todo, completed: !todo.completed })) || todo,
      );
    },
    deleteTodo(id) {
      this.todos = [...this.todos].filter(todo => todo.id !== id);
    },
  },
  name: 'app',
};
</script>

<style>
  * {
    font-size: 16px;
  }
  body {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin: 60px auto;
    width: 415px;
    color: black;
  }
  button {
    box-shadow: none;
    border: none;
    background-color: aquamarine;
    margin-left: 5px;
    width: 125px;
  }
  button:hover {
    cursor: pointer;
    background-color: rgb(23, 255, 178);
  }
  input {
    background-color: #fafafa;
    border: none;
    margin-right: 5px;
    width: 250px;
  }
  .common {
    border-radius: 5px;
    padding: 15px;
  }
  .todo-item {
    background-color: #fafafa;
    text-align: left;
    margin-top: 15px;
  }
  .todo-item:hover {
    cursor: pointer;
  }
  .done {
    text-decoration: line-through;
  }
</style>

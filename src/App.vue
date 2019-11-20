<template>
  <div id="app">
    <Form v-bind:input="state.input" v-bind:onSubmit="onSubmit" />
    <div v-for="todo in state.todos" v-bind:key="todo">
      <div>{{todo}}</div>
    </div>
  </div>
</template>

<script>
import Form from './components/Form.vue'
import Vue from 'vue';

const state = new Vue({
  input: '',
  todos: ['learn vue', 'buy vans'],
});

const onSubmit = (e) => {
  e.preventDefault();
};

export default {
  name: 'app',
  data: () => ({
    state,
    onSubmit,
  }),
  components: {
    Form,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body, div, input, button {
  font-size: 16px;
}
</style>

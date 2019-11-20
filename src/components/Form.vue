<template>
  <form v-on:submit="onSumbit">
    <input v-model="input" type="text" placeholder="Things to do" />
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  name: 'Form',
  props: {
    input: String,
    onSumbit: Function,
  },
};
</script>

<style scoped>
  button {
    box-shadow: none;
    border: none;
    background-color: aquamarine;
    color: black;
    padding: 15px;
    border-radius: 5px;
    margin-left: 5px;
    width: 125px;
  }
  button:hover {
    cursor: pointer;
    background-color: rgb(23, 255, 178);
  }
  input {
    padding: 15px;
    background-color: #fafafa;
    border: none;
    border-radius: 5px;
    margin-right: 5px;
    width: 250px;
  }
</style>

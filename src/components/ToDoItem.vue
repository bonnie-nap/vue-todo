
<template>
  <li class="ToDoItem-Text" @click="$emit('delete', todo)">{{todo.Item}}</li>
</template>

<script>
  export default {
      name: "to-do-item",
      props: ['todo']
  }
</script>

<style>
  .ToDoItem-Text {
    color: #000000;
    background-color: #adb7bf;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 5px;
    width: auto;
  }

  .ToDoItem-Text:hover {
    background-color: pink;
    cursor: pointer;
  }
</style>


<template>
    <div class="todo-item">
      <div class="task-check">
        <input class="checkable" type="checkbox" :checked="todo.completed" @change="toggleComplete">
      </div>
      <div class="task-text">
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
      </div>
      <div class="task-action">
        <button class="btn-delete" @click="$emit('remove')">Eliminar</button>
      </div>
    </div>
  </template>
    
  <script>
  export default {
    props: {
      todo: Object
    },
    methods: {
      toggleComplete() {
        this.$emit('toggle-complete');
      }
    }
  }
  </script>
  
  <style scoped>
  .todo-item{
    text-align: left;
    width: 700px;
    padding: 20px;
    margin: 20px;
    background-color: rgb(212, 246, 212);
    border-radius: 10px;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1); /* Sombra de la tarjeta */ 
    display: flex;
    flex-direction: row;
  }
  .task-check{
    width: 5%;
    text-align: center;
  }
  .task-text{
    margin-left: 10px;
    width: 85%;
  }
  .task-action{
    width: 10%;
    margin-left: 10px;
    text-align: center;
  }
  .btn-delete{
    color: rgb(230, 122, 122);
    border: 1px solid rgb(230, 122, 122);
    border-radius: 5px;
  }
  .completed {
    text-decoration: line-through;
  }
  .checkable{
     all:unset;
     width: 10px;
     height: 10px;
     border: 2px solid rgb(69, 193, 69);
    border-radius: 2px;
    cursor: pointer;
  }
  .checkable:checked{
    background-color: green;
  }
  </style>
  
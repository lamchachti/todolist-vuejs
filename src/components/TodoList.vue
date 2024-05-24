<template>
    <div class="container">
      <h1 class="title">Todo List</h1>
      <input class="task-to-create" v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task">
      <div class="tasks-list">
        <ul  v-if="todos.length!=0">
            <li v-for="(todo, index) in todos" :key="index">
            <TodoItem :todo="todo" @toggle-complete="toggleComplete(index)" @remove="removeTodo(index)"></TodoItem>
            </li>
         </ul>
         <p v-else> No task to do</p>
      </div>
    
    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    components: {
      TodoItem
    },
    data() {
      return {
        newTodo: '',
        todos: [
            {text:'Daily Routine',completed:false},
            {text:'Read a book',completed:true}
        ]
      }
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.todos.push({ text: this.newTodo, completed: false });
          this.newTodo = '';
        }
      },
      toggleComplete(index) {
        this.todos[index].completed = !this.todos[index].completed;
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      }
    }
  }
  </script>
  
  <style scoped>
  ul{
    list-style: none;
  }
  .tasks-list{
    margin-top: 50px;
  }
  .container {
    /*max-width: 400px;*/
    margin: 0 auto;
    width: 800px;
  }

  .title{
    color: rgb(69, 193, 69);
  }
  .task-to-create{
    all:unset;
    width: 600px;
    height: 20px;
    padding: 10px 10px 10px 10px;
    border: 1px solid black;
    border-radius: 7px;
  }
  input.task-to-create:focus {
    border: 2px solid rgb(69, 193, 69);
  }
  </style>
  
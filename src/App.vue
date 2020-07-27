<template>
  <div class="" id="app">
    <div class="container grid-xs py-2">
      <img class="img-reponsive img-logo" src="@/assets/logo.png" alt="Logo Vue.js">
      <form @submit.prevent="adicionaTodo(todo)">
        <div class="input-group">
          <input type="text" v-model="todo.description" class="form-input" placeholder="Novo todo">
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
       <todo v-for="t in todos" :key="t.id" @toggle="toggleTodo" @remove="removeTodo" :todo="t"/>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from './components/Todo'

export default {
  name: "App",
  components: { Todo },
  data() {
    return { todos: [], todo: { checked: false } }
  },
  methods: {
    adicionaTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked: false };
    },
    removeTodo(todo){
      const index = this.todos.findIndex(item => item.id == todo.id)
      if (index > -1){
        this.$delete(this.todos, index);
      }
    },
    toggleTodo(todo){
      const index = this.todos.findIndex(item => item.id == todo.id)
      if (index > -1){
        const checked = !this.todos[index].checked;
        this.$set(this.todos, index, {...this.todos[index], checked});
      }
    }
  }
}
</script>

<style scoped>
  .img-logo{
    max-width: 100px;
    margin: 20px auto;    
    display: block;
  }
  .todo-list{
    padding-top: 1rem;
  }
  .flex-centered{
    border: 1px solid #4b48d6;
    border-radius: 3px;
    padding-left: 4px;  
    margin: 2px;
  }
  .btn-link-concluido{
    background-color: rgb(242, 242, 242);
    margin: 1px;
  } 
  .btn.btn-link{
    background-color: rgb(242, 242, 242);
    border: 1px solid #e85600;
    margin: 1px;
  }
  .btn-link:active{ 
    color: blue;   
    background: #e85600;
    border-color: #e85600;
}  
  </style>
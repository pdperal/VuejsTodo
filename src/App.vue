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
        <div class="tile flex-centered" v-for="t in todos" :key="t.id">
          <div class="tile-icon">
              <i class="icon icon-time"></i>
          </div>
          <dir class="tile-content">
            <div class="title-subtitle">{{ t.description }}</div>
          </dir>
          <div clas="tile-action">
            <button class="btn btn-link-concluido">Concluído</button>
            <button class="btn btn-link">
              <span class="text-error">Remover</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return { todos: [], todo: { checked: false } }
  },
  methods: {
    adicionaTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked: false };
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
  } 
</style>
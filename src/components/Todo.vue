<template>
  <div class="tile flex-centered">
    <div class="tile-icon">
      <i class="icon icon-time"></i>
    </div>
    <dir class="tile-content">
      <div class="title-subtitle">{{ todo.description }}</div>
    </dir>
    <div clas="tile-action">
      <button class="btn btn-link-concluido">Concluído</button>
      <button class="btn btn-link">
        <span class="text-error">Remover</span>
      </button>
    </div>
  </div>
</template>

<script>
export default{
    props: {
        todo: {type: Object, required: true}
    }
};
</script>
<script setup>
  defineProps(['nome', 'basic', 'tipo'])
</script>

<template>
  <button :class="[basic, tipo]">

  </button>
</template>

<style scoped>
.btn {
  color: lime;
  background: none;
}
.tarefa {
  cursor: pointer;
}
p {
  margin: 0;
}
</style>

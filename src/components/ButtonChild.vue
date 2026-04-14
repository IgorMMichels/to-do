<script setup>
  defineProps(['nome', 'basic'])
</script>

<template>
  <button :class="[basic]">
    <slot>

    </slot>
  </button>
</template>

<style scoped>
.btn {
  color: rgb(0, 0, 0);
  background: none;
  font-size: 1rem;
  padding: 6px 25px;
  margin: 4px;
  background-color: lime;
  border: none;
  border-radius: 6px;
  transition: 0.2s all ease;
  cursor: pointer;
}

.btn:hover {
  transform: translateY(-4px);
}
</style>

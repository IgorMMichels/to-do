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
  color: lime;
  background: none;
}
</style>

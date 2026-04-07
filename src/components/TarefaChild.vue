<script setup>
  defineProps(['nome', 'status'])

</script>

<template>
  <li :class="[status]">
    <slot>

    </slot>
  </li>
</template>

<style scoped>

li {
  cursor: pointer;
}

.concluida {
  text-decoration: line-through;
  opacity: 50%;
}
</style>

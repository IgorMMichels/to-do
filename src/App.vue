<script setup>
import { computed, ref } from 'vue'
const filtro = ref('')
const tarefas = ref([
  {
    id: 1,
    tarefa: 'Tarefa 1',
    status: 'concluida',
  },
  {
    id: 2,
    tarefa: 'Tarefa 2',
    status: 'concluida',
  },
  {
    id: 3,
    tarefa: 'Tarefa 3',
    status: 'pendente',
  },
  {
    id: 4,
    tarefa: 'Tarefa 4',
    status: 'pendente',
  },
])
const novaTarefa = ref('')

import tarefaChild from './components/TarefaChild.vue'

function addTarefa(novaTarefa) {
  let id = 1
  if (tarefas.value.length > 0) {
    id = tarefas.value[tarefas.value.length - 1].id + 1
  }
  tarefas.value.push({ id: id, tarefa: novaTarefa, status: 'pendente' })
}
function editTarefa(id) {

  const novoNome = prompt('Insira o novo nome da tarefa').trim()
  if (novoNome.trim() != '') {
    tarefas.value[id - 1].tarefa = novoNome
  }
}

const tarefasFiltradas = computed(() => {
  if (filtro.value.trim().length > 0) {
    return tarefas.value.filter((item) => item.tarefa.includes(filtro.value))
  } else {
    return tarefas.value
  }
})

const concluidas = computed(() => {
  return tarefas.value.filter(t => t.status === 'concluida').length
})

const pendentes = computed(() => {
  return tarefas.value.filter(t => t.status === 'pendente').length
})

// Concluir Tarefa
</script>

<template>
  <div class="container">
    <h1>Lista de Tarefas</h1>
    <input type="text" v-model="novaTarefa" />
    <button @click="addTarefa(novaTarefa)">Add</button>
    <ul>
      <tarefaChild
        v-for="tarefa in tarefasFiltradas"
        :key="tarefa"
        @click="tarefa.status=tarefa.status === 'concluida' ? 'pendente' : 'concluida'"
        :class="{ concluida: tarefa.status == 'concluida' }"

        :status="tarefa.status"
        :nome="tarefa.tarefa"
      >
        {{ tarefa.tarefa }} <button @click="editTarefa(tarefa.id)">Edit</button>
        <button @click="tarefas.splice(tarefas.indexOf(tarefa), 1)">Del</button>
      </tarefaChild>
      <p v-if="tarefasFiltradas.length == 0">Nenhum Resultado Encontrado</p>
    </ul>
    <input type="search" v-model="filtro" placeholder="Filtrar Tarefas...">
    <p>Concluídas: {{  concluidas  }}</p>
    <p>Pendentes: {{  pendentes  }}</p>
  </div>
</template>

<style scoped>
button {
  color: lime;
  background: none;
}

p {
  margin: 0;
}

.container {
  padding: 15px;
  height: 100%;
  border-radius: 15px;
}
</style>

<script setup>
import { ref } from 'vue'

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

function addTarefa(novaTarefa) {
  const id = tarefas.value[tarefas.value.length - 1].id + 1
  console.log(id)
  tarefas.value.push({id: id, tarefa: novaTarefa, status: 'pendente'})
}
function editTarefa(id) {
  const novoNome = prompt("Insira o novo nome da tarefa");

  tarefas.value[id-1].tarefa = novoNome

}

// Concluir Tarefa
</script>

<template>
  <div class="container">
    <h1>Lista de Tarefas</h1>
    <ul>
      <li v-for="tarefa in tarefas" :key="tarefa">
        {{ tarefa.tarefa }} <button @click="editTarefa(tarefa.id)">Edit</button>
        <button @click="tarefas.splice(tarefas.indexOf(tarefa), 1)">Delete</button>
      </li>
    </ul>
    <input type="text" v-model="novaTarefa" />
    <button @click="addTarefa(novaTarefa)">Adicionar</button>
  </div>
</template>

<style scoped>
li {
  cursor: pointer;
}
.concluida {
  color: lime;
}
.container {
  padding: 15px;
  height: 100%;
  background-color: #181222;
  border-radius: 15px;
}
</style>

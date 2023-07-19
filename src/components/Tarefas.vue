<template>
  <div class="m-4">
    <form @submit.prevent="salvarTarefa">
      <div class="mb-3">
        <label class="form-label">Nova Tarefas</label>
        <div class="d-flex flex-row">
          <input
            v-model="tarefa"
            type="text"
            class="form-control me-2"
            placeholder="ex: Resolver problemas"
          />
          <button type="submit" class="btn btn-primary">Salvar</button>
        </div>
      </div>
    </form>
  </div>

  <div class="m-4">
    <h1>Tarefa para realizar</h1>
    <p v-if="tarefas.length == 0">
      Você não tem nenhuma tarefa para realizar ;)
    </p>
    <ul class="list-group mb-1" v-for="(tarefa, i) in tarefas" :key="i">
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        {{ tarefa }}

        <div>
          <button
            type="button"
            title="Marcar tarefa como concluída"
            class="btn btn-success m-1"
            @click="marcarConcluida(i)"
          >
            <i class="fas fa-check"></i>
          </button>
          <button
            type="button"
            title="Excluir tarefa"
            class="btn btn-danger m-1"
            @click="removerTarefa(i)"
          >
            <i class="fas fa-close"></i>
          </button>
        </div>
      </li>
    </ul>
  </div>

  <div class="m-4">
    <h1>Tarefa realizadas</h1>
    <p v-if="tarefasConcluidas.length == 0">
      Você não concluiu todas tarefa para realizar ;(
    </p>
    <ul
      class="list-group mb-1"
      v-for="(tarefa, i) in tarefasConcluidas"
      :key="i"
    >
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        {{ tarefa }}

        <div>
          <button
            type="button"
            title="Refazer tarefa"
            class="btn btn-primary m-1"
            @click="refazerTarefas(i)"
          >
            <i class="fas fa-recycle"></i>
          </button>
        </div>
      </li>
    </ul>
  </div>

  <div class="m-4">
    <h1>Tarefa realizadas</h1>
    <p v-if="tarefasConcluidas.length == 0">
      Você não concluiu todas tarefa para realizar ;(
    </p>
    <ul
      class="list-group mb-1"
      v-for="(tarefa, i) in tarefasConcluidas"
      :key="i"
    >
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        {{ tarefa }}

        <div>
          <button
            type="button"
            title="Refazer tarefa"
            class="btn btn-primary m-1"
            @click="refazerTarefas(i)"
          >
            <i class="fas fa-recycle"></i>
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";

const tarefa = ref();
const tarefas = reactive([]);
const tarefasConcluidas = reactive([]);

function salvarTarefa() {
  tarefas.push(tarefa.value); //tarefas.unshift(tarefa.value);
  tarefa.value = "";
}

function marcarConcluida(index) {
  const tarefaConcluida = tarefas.splice(index, 1);
  tarefasConcluidas.push(...tarefaConcluida); // tarefasConcluidas.unshift(tarefaConcluida)
}
</script>

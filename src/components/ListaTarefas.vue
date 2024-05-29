<template>
    <div class="container">
      <h1>Lista de Tarefas</h1>
      <div class="form-todo form-group">
        <p>
          <input placeholder="nome" type="text" name="author" class="form-control" v-model="name"/>    
        </p>
        <p>
          <textarea placeholder="Tarefa" name="message" class="form-control" v-model="message"></textarea>
        </p>
        <button v-on:click="addTarefa" type="submit" class="btn btn-primary">Adicionar</button>
        <div class="list-group">
          <div class="list-group-item" v-for="(tarefa, index) in todasTarefas" :key="index">
            <span class="comment_author">Nome: <strong>{{ tarefa.name }}</strong></span>
            <p>Tarefa: {{ tarefa.message }}</p>
            <div>
              <a v-on:click.prevent="removeTarefa(index)" href="#" title="Excluir">Excluir</a>
            </div>
          </div>
        </div>
      </div> 
    </div>
  </template>
  
  <script>
  export default {
    name: 'ListaTarefas',
    data() {
      return {
        tarefas: [],
        name: '',
        message: ''
      };
    },
    methods: {
      addTarefa() {
        if (this.message.trim() === '') {
          return;
        }
        this.tarefas.push({
          name: this.name,
          message: this.message
        });
        this.name = '';
        this.message = '';
      },
      removeTarefa(index) {
        this.tarefas.splice(index, 1);
      }
    },
    computed: {
      todasTarefas() {
        return this.tarefas.map(tarefa => ({
          ...tarefa,
          name: tarefa.name.trim() === '' ? 'Anônimo' : tarefa.name
        }));
      }
    },
  };
  </script>
  
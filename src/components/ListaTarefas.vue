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
        <button @click="addTarefa" type="submit" class="btn btn-primary">Adicionar</button>
        <div class="list-group">
          <div class="list-group-item" v-for="(tarefa, index) in todasTarefas" :key="index">
            <span class="comment_author">Nome: <strong>{{ tarefa.name }}</strong></span>
            <p>Tarefa: {{ tarefa.message }}</p>
            <div>
              <a @click.prevent="removeTarefa(index)" href="#" title="Excluir">Excluir</a>
            </div>
          </div>
        </div>
      </div> 
    </div>
  </template>
  
  <script setup>
    import {ref, computed} from 'vue';

    const tarefas = ref([]);
    const name = ref('');
    const message = ref('');

    const addTarefa = () =>{
      if(message.value.trim() ===''){
        return;
      }
      tarefas.value.push({
        name: name.value,
        message: message.value
      });
      name.value = '';
      message.value = '';
    }

    const removeTarefa = (index) =>{
      tarefas.value.splice(index, 1);
    }

    const todasTarefas = computed(() =>{
      return tarefas.value.map(tarefa =>({
        ...tarefa,
        name: tarefa.name.trim() === ''? 'Anônimo' : tarefa.name
      }));
    })
  </script>
  
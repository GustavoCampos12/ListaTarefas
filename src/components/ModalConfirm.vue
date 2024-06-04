<template>
    <div class="modal">
      <div class="modal-content">
        <p>Deseja mesmo adicionar essa tarefa?</p>
        <div class="btn-modal">
        <button class="btn-confirm" @click="confirm">Confirmar</button>
        <button class="btn-close" @click="cancel">Cancelar</button>
        </div>
    </div>
    </div>
  </template>
  
  <script setup>
    import { defineEmits } from 'vue';
  

    const emit = defineEmits(['confirm', 'cancel']);
  
    const confirm = () => {
      emit('confirm');
    }
  
    const cancel = () => {
      emit('cancel');
    }
  </script>
  
  <style >
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      background-color: rgba(0, 0, 0, 0.5);
      display: flex;
      justify-content: center;
      align-items: center;
    }
  
    .modal-content {
      width: 300px;
      height: 150px;
      background-color: white;
      padding: 20px;
      border-radius: 5px;
    }

    .btn-close{
        margin-left: 50px;
    }
    .btn-confirm,.btn-close{
        width: 100px;
        background-color: #007bff ;
        border-color: #007bff;
        color: #fff;
        border-radius: 5px;
    }
  </style>
  
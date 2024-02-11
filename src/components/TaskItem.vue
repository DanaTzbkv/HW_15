<template>
    <div class="task-item">
      <h3>{{ task.title }}</h3>
      <p>{{ task.description }}</p>
      <p :class="['status', { completed: task.completed }]">
        {{ task.completed ? 'Выполнено' : 'Не выполнено' }}
      </p>
      <button @click="toggleComplete(task.id)" class="mark-button">
        {{ task.completed ? 'Пометить как не выполнено' : 'Пометить как выполнено' }}
      </button>
      <button @click="deleteTask(task.id)" class="delete-button">Удалить</button>
      <button @click="showDetails" class="details-button">Показать детали</button>
  
      <div v-if="showingDetails" class="details-modal">
        <div class="details-content">
          <h3>Детали задачи "{{ task.title }}"</h3>
          <slot name="details"></slot>
          <button @click="closeDetails">Скрыть детали</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['task'],
    data() {
      return {
        showingDetails: false
      }
    },
    methods: {
      toggleComplete(taskId) {
        this.$emit('toggleComplete', taskId)
      },
      deleteTask(taskId) {
        this.$emit('deleteTask', taskId)
      },
      showDetails() {
        this.showingDetails = true
      },
      closeDetails() {
        this.showingDetails = false
      }
    }
  }
  </script>
  
  <style lang="scss">
  .task-item {
    margin: 0px 0px 20px 0px;
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  
    h3,
    p {
      font-size: 18px;
      margin-bottom: 10px;
    }
  
    .status {
      font-weight: bold;
      color: #dc3545;
    }
  
    .completed {
      color: #28a745;
    }
  
    .not-completed {
      color: #dc3545;
    }
  
    .mark-button,
    .delete-button,
    .details-button {
      margin-right: 10px;
      padding: 5px 10px;
      font-size: 14px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    .mark-button {
      background-color:#28A745;
      color: #ffffff;
  
    }
  
    .delete-button {
      background-color: #dc3545;
      color: #ffffff;
    }
  
    .details-button {
      background-color: #28a745;
      color: #ffffff;
  
    }
  }
  </style>
  
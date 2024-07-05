<script setup>
import { ref } from 'vue'

const newTodo = ref('')
const todos = ref([])
</script>

<template>
  <div class="todo-app">
    <el-card class="todo-card">
      <template #header>
        <div class="todo-header">
          To Do List
        </div>
      </template>
      <div class="todo-input">
        <el-input v-model="newTodo" placeholder="New Todo"></el-input>
        <el-button type="primary" @click="addTodo">Add</el-button>
      </div>
      <div v-if="todos.length" class="todo-list">
        <el-card v-for="todo in todos" :key="todo.id" class="todo-item">
          <div class="todo-item-actions">
            <div class="todo-item-title"> {{todo.title}}</div>
            <el-button class="todo-button" @click="toggleComplete(todo)"
                        :type="todo.completed ? 'success': 'info'">
              {{todo.completed ? 'Completed': 'Not Complete'}}
            </el-button>
            <el-button type="danger" @click="deleteTodo(todo)">
              Delete
            </el-button>
          </div>
        </el-card>

      </div>
      <div v-else class="no-todos"> Currently No Todo Items </div>
    </el-card>
  </div>


</template>

<style scoped>

</style>
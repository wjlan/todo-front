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
.todo-app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: #d3d7da;
  padding: 20px;
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  
}

.todo-card {
  width: 100%;
  max-width: 500px;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  background: #ffffff;
}

.todo-header {
  font-size: 24px;
  font-weight: bold;
  text-align: center;
  padding: 16px;
  background-color: #409eff;
  color: white;
  border-radius: 8px 8px 0 0;
  margin: 0;
}

.todo-input {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 20px;
  background-color: #fff;
  border-bottom: 1px solid #a2a5a8;
}

.el-input {
  flex: 1;
}

.todo-list {
  padding: 20px;
  background-color: #fff;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 15px;
  margin-bottom: 10px;
  border: 1px solid #4f4b58;
  border-radius:8px;
  background: #a59ab1;
  transition:background 0.3s, transform 0.3s;
}

.todo-item:hover {
  background: cadetblue;
  transform: translateY(-2px);
}

.todo-item-title {
  font-weight: bold;
  flex: 1;
  margin-right: 20px;
  word-wrap: break-word;
  width: 160px;
}

.completed .todo-item-title {
  text-decoration: line-through;
  color: dimgray;
}

.todo-item-actions{
  display: flex;
  align-items: center;
}

.no-todos {
  text-align: center;
  padding: 20px;
  color: dimgray;
  font-size: 18px;
}


</style>
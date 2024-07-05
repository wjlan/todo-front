<script setup>

</script>

<template>
  <div class="todo-app">
    <el-card>
      <template #header>
        <div class="todo-header">
          To Do List
        </div>
      </template>
      <div class="todo-input">
        <el-input v-model="newTodo" placeholder="New Todo"></el-input>
        <el-button type="primary" @click="addTodo">Add</el-button>
      </div>
    </el-card>
  </div>


</template>

<style scoped>

</style>
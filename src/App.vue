<script>
export default {
  data() {
    return {
      tasks: [
        { id: 1, name: 'coding landing page use Vue', completed: false },
        { id: 2, name: 'go to Hai Duong', completed: true },
        { id: 3, name: 'reading a book', completed: true },
        { id: 4, name: 'chat with friend', completed: false },
        { id: 5, name: 'sleep', completed: true }
      ]
    }
  },
  methods: {
    removeTask(taskId) {
      const array = this.tasks.filter((task) => task.id !== taskId)
      this.tasks = array
    },
    toggleCompleted(taskId) {
      const task = this.tasks.find((task) => task.id === taskId)
      if (task) {
        task.completed = !task.completed
      }
    }
  }
}
</script>

<template>
  <h1>Todo List</h1>
  <div class="list">
    <div v-for="(task, index) in tasks" :key="task.id" class="item">
      <div :class="{ 'item-completed': task.completed }" @click="toggleCompleted(task.id)">
        {{ index + 1 }}. {{ task.name }}
      </div>
      <button class="btn" @click="removeTask(task.id)">x</button>
    </div>
  </div>
</template>

<style>
@import url('./assets/global.css');
</style>

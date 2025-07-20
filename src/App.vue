<template>
  <h1>{{name}}</h1>
  <p v-if="status === 'active'"> User is <strong>active</strong></p>
  <p v-else-if="status === 'pending'"> User is <strong>pending</strong></p>
  <p v-else> User is <strong>inactive</strong></p>

  <h3>Tasks</h3>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      <span :class="{ completed: task.completed }">{{ task.title }}</span>
    </li>
  </ul>
  <a v-bind:href="link" target="_blank">Vue.js Documentation</a>
  <a :href="link" target="_blank">Vue.js Documentation without v-bind</a>
</template>

<script>
  export default{
    data () {
      return {
        name: 'I\'m Seren',
        status: 'pending',
        tasks: [
          { id: 1, title: 'Task 1', completed: true },
          { id: 2, title: 'Task 2', completed: false },
          { id: 3, title: 'Task 3', completed: true },
        ],
        link: 'https://vuejs.org/',
      }
    },
  }
</script>
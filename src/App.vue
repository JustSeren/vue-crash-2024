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
  <br/>
  <button @click="toggleStatus">Toggle Status</button>
</template>
<script>
import { ref } from 'vue';
  export default {
    setup() {
      const name = ref('Seren Kaya');
      const status = ref('active');
      const tasks = ref([
        { id: 1, title: 'Learn Vue.js', completed: true },
        { id: 2, title: 'Build a project', completed: false },
        { id: 3, title: 'Deploy the project', completed: false }
      ]);
      const toggleStatus = () => {
        if(status.value === 'active') {
          status.value = 'pending';
        } else if (status.value === 'pending') {
          status.value = 'inactive';
        } else {
          status.value = 'active';
        }
      };
      return {
        name,
        status,
        tasks,
        toggleStatus
      };
    }
  }
</script>
<template>
  <h1>{{name}}</h1>
  <p v-if="status === 'active'"> User is <strong>active</strong></p>
  <p v-else-if="status === 'pending'"> User is <strong>pending</strong></p>
  <p v-else> User is <strong>inactive</strong></p>

  <form @submit.prevent="addTask">
    <label for="newTask"> Add Task</label>
    <br/>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <br/>
    <button type="submit">Add</button>
  </form>

  <h3>Tasks</h3>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      <span>{{ task.title }}</span>
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
        { id: 1, title: 'Learn Vue.js'},
        { id: 2, title: 'Build a project' },
        { id: 3, title: 'Deploy the project'}
      ]);
      const newTask = ref('');
      const toggleStatus = () => {
        if(status.value === 'active') {
          status.value = 'pending';
        } else if (status.value === 'pending') {
          status.value = 'inactive';
        } else {
          status.value = 'active';
        }
      };
      const addTask = () => {
        if (newTask.value.trim() !== '') {
          tasks.value.push({
            id: tasks.value.length + 1,
            title: newTask.value
          });
          newTask.value = '';
        }
      }
      return {
        name,
        status,
        tasks,
        toggleStatus,
        addTask,
        newTask
      };
    }
  }
</script>
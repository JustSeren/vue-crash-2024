<template>
  <h1>{{name}}</h1>
  <p v-if="status === 'active'"> User is <strong>active</strong></p>
  <p v-else-if="status === 'pending'"> User is <strong>pending</strong></p>
  <p v-else> User is <strong>inactive</strong></p>
</template>

<script>
  export default{
    data () {
      return {
        name: 'I\'m Seren',
        status: 'pending'
      }
    },
  }
</script>
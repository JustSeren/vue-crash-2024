<template>
  <h1>{{name}}</h1>
  <p v-if="status"> User is <strong>active</strong></p>
  <p v-else> User is <strong>inactive</strong></p>
</template>

<script>
  export default{
    data () {
      return {
        name: 'I\'m Seren',
        status: false
      }
    },
  }
</script>
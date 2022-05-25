<template>
  <SignupForm />
</template>

<script>
  import SignupForm from './components/SignupForm.vue'

  export default {
    components: { SignupForm },
    name: 'App'
  }
</script>

<style>
  #app {
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    color: #2c3e50;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    margin-top: 60px;
    text-align: center;
  }

  body {
    background: #eee;
    margin: 0;
  }
</style>

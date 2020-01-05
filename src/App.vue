<template>
  <div id="app">
    <Form />
  </div>
</template>

<script>
import Form from './components/Form'

export default {
  name: 'app',
  components: {
    Form
  }
}
</script>

<style scoped>
#app {
  display: grid;
  font-family: Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>

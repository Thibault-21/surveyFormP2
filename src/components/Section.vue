<template>
  <div class="header">
    <h1>{{title}} </h1>
    <p> {{intro}} {{name}}</p>
  </div>
</template>

<script>

export default {
  name: 'Section', 
  props: {
    title: String,
    intro: String,
    name: String, 
  }
}

</script>

<style scoped>
  template {
    font-family: Helvetica; 
    
  }
  .header {
   
    background-color: rgb(112, 148, 221);
    color: white;
    border-radius: 5px;
    margin-bottom: 10px;
    padding: 10px;
 
    
  }
</style>
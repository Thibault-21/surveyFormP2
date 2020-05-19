<template>
  <div class="main">
    <!-- <img src="'./Image/workplace.jpg"> -->
    <header>
      <slot name="header"></slot>
    </header>
    <main>
      <slot></slot>
    </main>
    <footer>
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Page',
}
</script>

<style lang="scss" scoped>
.main {
  display: grid;
  grid-template-columns: 30% 80% 30%;
  grid-template-rows: 30% 60% 30%;
}
header, footer { 
  grid-column-start: 2; 
  width: 50%; 
  background-color: rgb(135, 143, 253);
  color: white;
  padding: 5px;
  margin: 2px 0px 5px 5px;
  border-radius: 5px;
}
main { 
  grid-column-start: 2;
  width: 50%; 
  background-color: white;
  color: rgb(0, 0, 0);
  padding: 5px;
  margin: 5px 0px 5px 5px;
  border-radius: 5px;
  border: 1px solid rgb(86, 96, 240);
}
@media only screen and (max-width: 375px) {
  .main {
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: 30% 60% 30%;
  }
  header {    
    grid-row-start:1; 
    grid-row-end: 2; 
    grid-column-start:1; 
    grid-column-end: 3; 
    width: 75%; 
    background-color: rgb(135, 143, 253);
    color: white;
    padding: 5px;
    margin: 2px 0px 5px 5px;
    border-radius: 5px;
}
  main { 
    grid-column-start:1; 
    grid-column-end: 3; 
    grid-row-start:2; 
    grid-row-end: 3; 
    width: 300px; 
    background-color: white;
    color: rgb(0, 0, 0);
    padding: 5px;
    margin: 10px;
    border-radius: 5px;
    border: 1px solid rgb(86, 96, 240);
  }
  footer {
    grid-column-start:1; 
    grid-column-end: 3;
    grid-row-start:3; 
    grid-row-end: 4; 
    width: 75%; 
    background-color: rgb(135, 143, 253);
    color: white;
    padding: 5px;
    margin: 2px 0px 5px 5px;
    border-radius: 5px;
  }
  h1 {
    margin: auto;
    padding: 5px;
  }
}

</style>

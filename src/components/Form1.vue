<template>
<!-- est ce que le @submit est nommé de façon aléatoire 
ou est ce en rapport avec le type du button ? -->
                          <!-- J'ai rajouté l'événement save pour faire remonter la valeur de l'input firstName dans le formPage  à travers un composant adjacent footer 
                          et l'a réuitilisé à la fin du form -->
    <form method="POST">
      <div class="civil">
      <select class="select" v-model="gender">
        <option disabled value="">Please Select Your Gender</option>
        <option value="Ms">Ms.</option>
        <option value="Mr">Mr</option>
        <option value="Other">Other</option>
        </select>

        <input type="text" name="userInfos" v-model="firstName" placeholder="Your first Name..">
        <input type="text" name="userInfos" v-model="lastName" placeholder="Your last Name..">
      </div>
      <div class="pro">
        <input type="text" name="userInfos" v-model="email" placeholder="Your email..">
        <input type="text" name="userInfos" v-model="job" placeholder="Your job..">
      
      <select class="select" v-model="companies">
        <option disabled value="">Please Select Your Company</option>
        <option name="companies">Orange</option>
        <option name="companies">BNP</option>
        <option name="companies">Total</option>
        <option name="companies">L'Oreal</option>
        <option name="companies">Other</option>
      </select> 
      </div>
      <div class="btn">
        <button class="btn-n" type="submit" @click.prevent="submitNext">Next</button>
      </div>
    </form>
</template>

<script>
export default {
  name: 'Form1', 
  data(){
    return {
      step: 1,
      userInfos: [],
      firstName: "",
      lastName:"",
      email:"",
      job:"",
      companies: [],
      gender: ""
    }
  }, 
    methods: {
      submitNext() {

        this.$emit('onSubmitNext', this.firstName, this.lastName, this.gender);
      },
    }
}
</script>

<style lang="scss" scoped>
// @import '../style/mixins.scss';
  form { 
    display: inline-grid;
    grid-template-columns: 50% 50%;
    grid-template-rows: 40% 40% 20%;
    grid-gap: 10px;
    padding: 5px;
  
  .civil {
    grid-row-start: 1;
    grid-row-end: 2;
    grid-column-start: 1;
    grid-column-end: 3;
  }
  .pro {
    grid-row-start: 2;
    grid-row-end: 3;
    
    grid-column-start: 1;
    grid-column-end: 3;
    
  }
  .btn {
    grid-row-start: 3;
    grid-row-end: 4;
    
    grid-column-start: 2;
    grid-column-end: 2;
    margin-bottom: 40px;
  }
  select {
    height: 40px;
    border-radius: 5px;
    border: 1px solid rgb(86, 96, 240);
    width: 130px;
    margin: 5px;
  }
  input { 
    height: 35px;
    border-radius: 5px;
    border: 1px solid rgb(86, 96, 240);
    width: 130px;
    margin: 5px;
  }

  ::placeholder {
    color: rgb(86, 96, 240);
    padding: 5px;
  }
  @mixin button-next($bg-color, $color, $height, $width, $margin, $padding, $b-radius, $cursor, $border, $display){
    
    background-color: $bg-color;
    color: $color;
    height : $height; 
    width: $width; 
    margin: $margin; 
    padding: $padding; 
    border-radius: $b-radius; 
    cursor: $cursor;
    border: $border;
    grid-column-start: $display;
  }
  .btn-n {
    @include button-next(rgb(86, 96, 240), white, 35px, 80px, 5px, 5px, 5px, pointer, 1px solid rgb(86, 96, 240), 3);
  }
  .btn-n:hover {
    @include button-next(rgb(154, 161, 255), white, 35px, 80px, 5px, 5px, 5px, pointer, 1px solid rgb(154, 161, 255), 3);
  }
// button {}
}
@media only screen and (max-width: 375px) {
  .main {
    display: grid;
    grid-template-columns: 33% 33% 33%;
  }
  form { 
    display: grid;
    grid-template-columns: 50% 50%;
    grid-template-rows: 33% 33% 33%;
    grid-gap: 15px;
    padding: 10px;
    width: 250px;  
    
    select {
      height: 40px;
      border-radius: 5px;
      border: 1px solid rgb(86, 96, 240);
    }
    input { 
      height: 35px;
      border-radius: 5px;
      border: 1px solid rgb(86, 96, 240);
    } 
    ::placeholder {
      color: rgb(86, 96, 240);
      padding: 5px;
    }
    @mixin button-next($bg-color, $color, $height, $width, $margin, $padding, $b-radius, $cursor, $border, $display){ 
      background-color: $bg-color;
      color: $color;
      height : $height; 
      width: $width; 
      margin: $margin; 
      padding: $padding; 
      border-radius: $b-radius; 
      cursor: $cursor;
      border: $border;
      grid-column-start: $display;
    }
    .btn-n {
      @include button-next(rgb(86, 96, 240), white, 35px, 80px, 5px, 5px, 5px, pointer, 1px solid rgb(86, 96, 240), 3);
    }
    .btn-n:hover {
      @include button-next(rgb(154, 161, 255), white, 35px, 80px, 5px, 5px, 5px, pointer, 1px solid rgb(154, 161, 255), 3);
    }
// button {}
  }
}  
</style>

<template>
  <div>
    <form>
      <Section :title="register" :intro="introduction" :name="sectionOne"/>
      <br>
      <hr>
      <!-- ----------------- -->
      <div v-show="step === 1">
      <label userInfos="userInfos">What about you ?</label>
      <br>
      <input type="text" v-model="firstName" placeholder="Your FirstName" />
      <input type="text" v-model="lastName" placeholder="Your LastName"/>
      <input type="text" v-model="job" placeholder="Your job"/>
      <select name="companies">
        <option value="Total">Your Company</option>
        <option value="AFD">AFD</option>
        <option value="Engie">Engie</option>
        <option value="Safran">Safran</option>
      </select>
      <input type="text" v-model="email" placeholder="Your email"/>
      <input class="btn-n" type="submit" value="Next" @click.prevent="next" />
      <br>
      </div>

      <!-- ----------------- -->
      <div v-show="step === 2">
      <label userTools="userTools">Which tools do you use for communicate :</label><br>
        <input type="checkbox" v-model="communication"/> I use Skype <br>
        <input type="checkbox" v-model="communication"/> I use Webex<br>
        <input type="checkbox" v-model="communication"/> I use my inbox<br>
        <hr>
         <input class="btn-p" type="submit" value="Previous" @click.prevent="previous"/>
         <input class="btn-n" type="submit" value="Next" @click.prevent="next"/>
      </div>
      
      <!-- ----------------- -->
      <div v-show="step === 3">
      <label userTools="userTools">Which tools do you use for store your documents :</label><br>
        <input type="checkbox" v-model="storage"/> I use google drive <br>
        <input type="checkbox" v-model="storage"/> I use sharepoint<br>
        <input type="checkbox" v-model="storage"/> I use my dropbox<br>
        <hr>
        <input class="btn-p" type="submit" value="Previous" @click.prevent="previous"/>
         <input class="btn-s" type="submit" value="Submit" @click.prevent="submit"/>
      </div>
    </form>
  </div>
</template>

<script>
import Section from './Section'
export default {
  name: 'Form', 
  components: {
    Section
  }, 
  data(){
    return {
      // ------------- introduction header
      step: 1,
      register: "Survey Workplace Satisfaction",
      introduction: "Please fulfill this survey in order to improve your daily tools. You will be inform about the results.",
      // ------------- The first page information 
      firstPage:{
        firstName:"",
        lastName:"", 
        job:"",
        companies:["Total","AFD", "Engie", "Safran"],
        email:""
      },
      // ------------- the second page information 
      secondPage: { 
        communication: "",
        storage:""
      },
      // ------------- dynamic content
      sectionOne:"",
      firstThank: "Thank you ",
      lastThank: "Thank you very much for your participation"
    }
  },
  methods: { 
  next(){

    this.step++;
  }, 
  previous(){
  
    this.step--;
  },
  submit(){
    this.step++;
    delete  this.introduction;
    this.sectionOne = this.lastThank + " " + this.firstName;
 
    }
  }
}

</script>

<style scoped>
template{
  font-family: Arial, Helvetica, sans-serif;
}
input {
  border-radius: 3px;
  margin: 10px;
}
::placeholder{
  color: lightgray;
}
button {
  border-radius: 5px;
  background-color: lightblue;
}
form {

  width: 500px;
  border-radius: 5px;
  border: 1px solid lightblue;
  margin: 8px;
  padding: 10px;

}
.btn-n{
  background-color: rgb(112, 148, 221);
  color: white;
  border-radius: 5px;
  width: 80px;
  height: 30px;
  border: none;
}
.btn-p{
  background-color: rgb(221, 134, 112);
  color: white;
  border-radius: 5px;
  width: 80px;
  height: 30px;
  border: none;
}
.btn-s{
  background-color: rgb(35, 201, 43);
  color: white;
  border-radius: 5px;
  width: 80px;
  height: 30px;
  border: none;
}
</style>
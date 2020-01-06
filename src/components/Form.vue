<template>
  <div>
    <form>
      <!-- ----------------- -->
      <Section :title="register" :intro="introduction" :name="sectionOne"/>
      <div class="pageOne" v-show="step === 1">
      <label userInfos="userInfos">What about you ?</label>
      <br>
      <input type="text" v-model="firstName" placeholder="Your FirstName" />
      <input type="text" v-model="lastName" placeholder="Your LastName"/>
      <input type="text" v-model="job" placeholder="Your job"/>

      <select v-model="companies">
        <option disabled value="">Please select one</option>
        <option>Total</option>
        <option>AFD</option>
        <option>Engie</option>
        <option>Safran</option>
      </select>
      <span> {{companies}}</span>

      <input type="text" v-model="email" placeholder="Your email"/>
      <input class="btn-n" type="submit" value="Next" @click.prevent="next" />
      <br>
      </div>
      <br>
      <hr>
      <!-- ----------------- -->
      
      <div v-show="step === 2">
      <p userTools="userTools">Which tools do you use for communicate :</p><br>
        <label for="skype"> Skype</label> 
        <input type="checkbox" id="skype" value="skype" v-model="secondPage.communication"/><br>
        <label for="skype"> Webex</label>
        <input type="checkbox" id="Webex" value="Webex" v-model="secondPage.communication"/> <br>
        <label for="skype"> mailBox</label>
        <input type="checkbox" id="mailBox" value="mailBox" v-model="secondPage.communication"/><br>
        <span>{{communication}}</span>
        <hr>
         <input class="btn-p" type="submit" value="Previous" @click.prevent="previous"/>
         <input class="btn-n" type="submit" value="Next" @click.prevent="next"/>
      </div>
      
      <!-- ----------------- -->
      <div v-show="step === 3">
      <p>Which tools do you use for store your documents :</p><br>
        <label for="googleDrive"> Google Drive</label> 
        <input type="checkbox" v-model="thirdPage.storage" value="google drive"/>  <br>
        <label for="SharePoint"> SharePoint</label> 
        <input type="checkbox" v-model="thirdPage.storage" value="SharePoint"/> <br>
        <label for="dropbox"> Dropbox</label> 
        <input type="checkbox" v-model="thirdPage.storage" value="Dropbox"/> <br>
        <hr>
        <input class="btn-p" type="submit" value="Previous" @click.prevent="previous"/>
         <input class="btn-s" type="submit" value="Submit" @click.prevent="submit"/>
      </div>
    </form>
  </div>
</template>

<script>
import Section from './Section'
// import Page1 from './pages/Page1'

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
        companies:[],
        email:""
      },
      // ------------- the second page information 
      secondPage: { 
        communication: []
      },
      thirdPage: {
      // ------------- the third page information 
        storage:[]
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
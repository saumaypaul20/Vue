<template>
  <div class="hello">
      <div class="holder">

        <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a Skill..." v-model="skill" v-validate="'min:5'" name="skill">
        <transition name='alert-in' enter-active-class="animated flipInX" leave-active-class="animated flipOutX"  >
        <p class="alert" v-if="errors.has('skill')">
          {{errors.first('skill')}}
        </p>
         </transition>
        </form>

        <ul>
         <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" :key='index'>
            {{data.skill}}

            <i class=" fa fa-minus-circle" v-on:click="remove(index)"></i>
            </li>
        </transition-group>
      </ul>
      <p v-if="skills.length > 0">These are the Skills you possess.</p>
      <p v-else><em>Nothing?</em> Add a Skill man!</p>
      </div>
      
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data(){
    return {
       
      skill:'',
      skills: [
        
        {"skill" : "Vue.Js"},
        {"skill" : "Back-End Developer"},
      ]
     
    }
  },

  methods:{
    
  addSkill(){
    this.$validator.validateAll().then((res) =>{
      if(res){
        this.skills.push({skill: this.skill})
        this.skill = '';
      }else{
          console.log('Not Valid')
      }
    }) 
    
     
  },

  remove(id){
    this.skills.splice(id,1)
  }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 

.hello{
  background-color: rgb(255, 255, 255);
    box-shadow: 0px 0px 20px rgb(77, 77, 77);
    border-radius: 10px;
   
}
 
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: rgb(206, 218, 255);
    border-left: 5px solid rgb(19, 23, 87);
    margin-bottom: 2px;
    color: rgb(20, 19, 19);
  }

  p {
    text-align:center;
    padding: 30px 0;
    color:  rgb(59, 59, 59);
    font-weight: 600;
    
  }

   input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #333333;
    color: rgb(255, 255, 255);
    border-radius: 10px 10px 0 0 ;
  }

   .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 15px;
    margin-top: -20px;
 
  }

  .alert-in-enter-active {
  animation: bounce-in .5s;
}
.alert-in-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

i{
  float: right;
  cursor: pointer;
}



</style>

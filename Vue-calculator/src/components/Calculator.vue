<template>
   <div class="main_body">
      <div class="input_sec " id = "input_sec" >{{input}} <span>{{operator}}</span></div>
      <div class="numbers_pad">

        <button type="button" name="9" class="btn btn-numbers" @click="pushButton(9)">9</button>
        <button type="button" name="8" class="btn btn-numbers" @click="pushButton(8)">8</button>
        <button type="button" name="7" class="btn btn-numbers" @click="pushButton(7)">7</button>
        <br>
        <button type="button" name="6" class="btn btn-numbers" @click="pushButton(6)">6</button>
        <button type="button" name="5" class="btn btn-numbers" @click="pushButton(5)">5</button>
        <button type="button" name="4" class="btn btn-numbers" @click="pushButton(4)">4</button>
        <br>
        <button type="button" name="3" class="btn btn-numbers" @click="pushButton(3)">3</button>
        <button type="button" name="2" class="btn btn-numbers" @click="pushButton(2)">2</button>
        <button type="button" name="1" class="btn btn-numbers" @click="pushButton(1)">1</button>
        <br>

        <button type="button" id="AC" name="AC" class=" btn  btn-numbers-extra"  @click="pushButton('AC')">AC</button>
        <button type="button" name="0" class=" btn btn btn-numbers" @click="pushButton(0);">0</button>
        <button type="button" name="." class=" btn btn btn-numbers" style="background-color: #333; " @click="pushButton('.')">.</button>

      </div>

      <div class="operators_tabs">

        <button type="button" name="+" class = "btn btn-operators" @click="pushButton('+')">+</button>
        <button type="button" name="-" class = "btn btn-operators" @click="pushButton('-')">-</button>
        <button type="button" name="*" class = "btn btn-operators" @click="pushButton('*')">*</button>
        <button type="button" name="/" class = "btn btn-operators" @click="pushButton('/')">/</button>

      </div>

      <div class="equal">

        <button type="button" name="=" id ="equal" class=" btn btn-equal extra-equal" @click="equal()">=</button>

      </div>
    </div>
</template>

<script>
export default {
  name: 'Calculator',
   
  data(){
    return{
      input: '',
      operator:''

    }
  },

  methods:{
    pushButton(id){

       if(id === '.'){
        if(this.input.indexOf('.') === -1){
          this.input += id;
        }
        else if(this.input.indexOf('.') > 1 || this.input.indexOf('+') || this.input.indexOf('-') ||this.input.indexOf('*') ||this.input.indexOf('/')){
            this.input += '.';
        }
      }else if(id == 'AC'){
        this.input = ' ';
      }
      else{
        this.input += `${id}`;
      }
    },
    
    // dot(){
    //    if(this.input.indexOf('.') === -1){
    //     this.input += '.';
    //   }
    // },

    equal(){
      this.input = eval(this.input);
    }

  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main_body{

  position: relative;

  margin: 10px auto;
  border-radius: 20px;
  width: 400px;
  height: auto;
  background-color: #222 ;
  box-shadow: 0px 0px 35px #fd79a8  ;
}

.numbers_pad{
  display: inline-block;
  position: relative;
  top: 20px;
  width: 70%;
  left: 20px;
}


.input_sec{
  font-family: 'Raleway', sans-serif;
  border: none;
  position: relative;
  opacity: 1;
  padding: 10px 10px;
  border-radius: 50px;
  top: 10px;
  margin: 0 10px;
  background-color: #fff3;
  text-align: center;
  width: 90%;
  height: 30px;
  font-size: 20px;
  vertical-align: middle;
  color: #f3f3f3;
  transition: visibility 0.5s;

}

.btn-numbers{
  box-sizing: border-box;
  color: white;
  background-color: #333;
  border: none;
  border-radius: 50%;
  width: 55px;
  height: 55px;
  margin: 5px 12px;
  padding: 10px auto;
  cursor: pointer;
  font-size: 15px;
}

.btn-numbers-extra{
  box-sizing: border-box;
  color: white;
  background-color: #444;
  border: none;
  border-radius: 50%;
  width: 55px;
  height: 55px;
  margin: 5px 12px;
  padding: 10px auto;
  cursor: pointer;
  font-size: 15px;
}

.operators_tabs{
   
  box-sizing: border-box;
  width: 30%;
  float: right;
  position: relative;
  top: 20px;
  right: 20px;

}
.btn-operators{
  box-sizing: border-box;
  color: #000;
  background-color: #f7f7f7;
  border: none;
  border-radius: 50%;
  width: 55px;
  height: 55px;
  margin: 5px 12px;
  padding: 10px auto;
  cursor: pointer;
  font-size: 25px;
}



/*Equal button style*/

.btn-equal{
  color: #333;
  box-sizing: border-box;
  font-size: 25px;
  background: #f7f7f7;
  display: block;
  padding: 10px;
  width: 145px;
  height: 45px;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  margin: 10px auto;
  position: relative;
}

.btn-equal:hover {
  background: #901d8c;
  color: #fff;
  box-shadow: 0 0 15px #c000ff;
  transition: all 0.5s;
}

.btn-numbers:hover{
  box-shadow: 0 0 15px #fd79a8;
  transition: all 0.2s;
}

.btn-operators:hover{
  box-shadow: 0 0 15px #c000ff;
  transition: all 0.2s;
}
.btn-numbers-extra:hover{
  box-shadow: 0 0 15px #ff8d00;
  transition: all 0.2s;
}

.equal  {
  padding: 10px;
  margin-top: 15px;
}

@media (max-width: 480px) {
  .main_body{
    margin: 0 auto;
  }
}
</style>

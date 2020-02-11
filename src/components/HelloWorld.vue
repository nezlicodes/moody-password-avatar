<template>
  <div class="hello">
    <h1>Happy password</h1>
    <div class="container">
      <div id="form">
        <form>
          <div class="form-group">
            <label for="username">username:</label>
            <input type="text" v-model="username" name="username" id="username" placeholder="Exple: awsome_user" required>
          </div>
          
          <div class="form-group">
            <label for="password">password:</label>
            <input type="password" v-model="password" name="password" id="password" placeholder="5upp3r_$t0ng-pa$$w0rd" required>
          </div>

          <div class="form-group">
            <button @click.prevent="onSubmit()" type="submit" class='btn'>Submit</button>
          </div>
        </form>
      </div>
      <div id="emoji">
        <div class="face">
          <div class="ears container">
             <div class="ear left"></div>
            <div class="ear right"></div>
          </div>

           <div class="eyes container">
             <div class="eye left"></div>
            <div class="eye right"></div>
            <div></div>
          </div>  

          <div v-bind:class="{happy: isHappy, sad:isSad, start:isOkay}"></div>    
        </div>
      </div>
    </div>
   
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  private password = '';
  private username = '';

  onSubmit(){
    alert('Hello' + this.username)
    this.password = '';
    this.username = ''
  }

  get isSad (){
   
   return ( this.password.length <= 8 ) ?  true: false;
  }

 get isHappy (){
    const regex = new RegExp(/[!@#$%^&*)(+=._-]/g);
    return( this.password.length > 8 && regex.test(this.password) )? true: false;
  }

  get isOkay() {
    const regex = new RegExp(/[a-zA-Z0-9]/g)
    const SPEregex = new RegExp(/[!@#$%^&*)(+=._-]/g);
    return (this.password.length > 8 && regex.test(this.password) && !SPEregex.test(this.password)) ? true: false;
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.container{display:flex; justify-content:space-around; flex-wrap:wrap; align-content:space-around
}

.form-group{
  padding: 12px
}
input {
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  padding:.375rem .75rem;
  font-weight: 400;
  width: 100%;
  height: calc(1.5em + .75rem + 2px);
}
label{
  font-size: 18px;
  font-weight: 400;
}

.btn {
  display: inline-block;
    font-weight: 400;
    border: 1px solid transparent;
    padding: .375rem .75rem;
    font-size: 1rem;
    line-height: 1.5;
    border-radius: .25rem;
    color: #fff;
    background-color: #42b983
}

.face {
  width: 150px;
  height:150px;
  border: black 1px solid;
  border-radius: 50%;
}
.ear, .eye{
  height: 0.6em;
  width: 0.6em;
  border: 2px solid #42b983;
  border-radius:50%;
}

.eye{
  transform:translateY(40px);
  animation-name:blink;
  animation-duration: 1500ms;
  animation-iteration-count: infinite;

}

.ear{
  background-color:  #42b983;
}

.start{
  position: relative;
  width: 3.8em;
  height: 2em;
  display: flex;
  justify-content: center;
  border-top: solid 5px red;
  align-content: center;
  transform: translate(20px,70px);
  border-radius: 10%;
}

.happy {
  position: relative;
  width: 3.8em;
  height: 2em;
  display: flex;
  justify-content: center;
  border-bottom: solid 5px red;
  align-content: center;
  transform: translate(20px,40px);
  border-radius: 50%;
}

.sad {
   position: relative;
  width: 3.8em;
  height: 2em;
  display: flex;
  justify-content: center;
  border-top: solid 5px red;
  align-content: center;
  transform: translate(20px,70px);
  border-radius: 50%;
}

@keyframes blink {
  from {
    background-color: white
  }

  to {
    background-color: rgba(0,0,0,0.7)
  }
}
</style>

<template>
  <div class="hello">
    <h1>Moody password avatar</h1>
    <div class="container main">
      <div id="form">
        <form>
          <div class="form-group">
            <label for="username">username:</label>
            <input type="text" v-model="username" name="username" id="username" placeholder="Exple: awsome_user" required>
          </div>
          
          <div class="form-group">
            <label for="password">password:</label>
               <input type="text" v-model="password" name="password" id="password" placeholder="5upp3r_$t0ng-pa$$w0rd" required>
          </div>

          <div class="form-group">
            <button @click.prevent="onSubmit()" type="submit" class='btn'>Submit</button>
          </div>
        </form>
      </div>
      <Avatar :password='password' />
    </div>
   
  </div>
</template>

<script lang="ts">

import { Component, Prop, Vue } from 'vue-property-decorator';
import Avatar from './Avatar.vue'

@Component({components:{Avatar}})

export default class HelloWorld extends Vue {

  // data
  private password = '';
  private username = '';

  // Methods
  onSubmit(){
    alert('Hello' + this.username)
    this.password = '';
    this.username = ''
  }

  // Computed 
  get passwrd () {
    return this.password
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1{
  padding: 1em
}
.container {
  display:flex;
  justify-content:space-around;
  flex-wrap:wrap; 
  align-content:space-around;


}

 .main {
  display:flex;
  justify-content: center;
  align-content: center
}

#form{
  margin-right:5em
}

.form-group{
  padding: 12px
}

input{
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #42b983;
  padding:.375rem .75rem;
  font-weight: 400;
  width: 100%;
  height: calc(1.5em + .75rem + 2px);
}

.password{
  display: flex
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

</style>

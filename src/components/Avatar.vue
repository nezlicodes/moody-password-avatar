<template>
     <div id="emoji">
        <div class="face">
        <!--   <div class="ears container">
             <div class="ear left"></div>
            <div class="ear right"></div>
          </div> -->
           <div class="eyes container">
             <div class="eye left"></div>
            <div class="eye right"></div>
            <div></div>
          </div>  

          <div v-bind:class="{happy: isHappy, sad:isSad, start:isOkay}"></div>    
        </div>
      </div>
</template>

<script lang="ts">
import {Component, Prop ,Vue,} from 'vue-property-decorator';

@Component
export default class Avatar extends Vue {
    @Prop(String) private password = '';

    // Computed
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

<style lang="css">
.face {
  width: 150px;
  height:150px;
  border-radius: 50%;
  background-color: rgb(251,208,67);
}
.ear, .eye{
  height: 0.6em;
  width: 0.6em;
  border-radius:50%;
}

.eye{
  transform:translateY(40px);
  animation-name:blink;
  animation-duration: 1500ms;
  animation-iteration-count: infinite;

}

.ear{
 border-bottom: solid 16px #42b983;
 border-right: solid 9px #42b983;
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
  transform: translate(30px,70px);
  border-radius: 10%;
}

.happy {
  position: relative;
  width: 3.8em;
  height: 2em;
  display: flex;
  justify-content: center;
  border-bottom: solid 10px red;
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
  border-top: solid 7px red;
  align-content: center;
  transform: translate(25px,70px);
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
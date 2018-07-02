<template>

  <div class="box">
    <div class="alert alert-primary" role="alert">
       <h3>The User Component</h3>
    <span>I'm an awesome User!</span>
    <span>Name: <strong>{{switchName()}}</strong></span>
     <span>Age: <strong>{{userAge}}</strong></span>
    <button class="btn btn-warning" @click="resetName">Reset Name</button>
    <button class="btn btn-danger" @click="resetFn()">Reset Name</button>
    </div>
  </div>
</template>
<script>
import { eventBus } from '../../main';
   export default {
     props:{
       myName: {
         type: String
       },
       resetFn: Function,
       userAge:Number

     },
     methods: {
       switchName() {
         return this.myName.split("").reverse().join("");
       },
       resetName() {
         this.myName = "Huy Nguyen";
         this.$emit('nameWasReset', this.myName);
       }
     },
     created() {
       eventBus.$on('ageWasEdited', (age) => {
         this.userAge = age;

       });
     }
   }
</script>

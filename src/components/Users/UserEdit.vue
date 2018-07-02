<template>
  <div class="">
    <div class="alert alert-success" role="alert">
       <h3>The User Component</h3>
      <span>I'm an awesome User!</span>
      <span>Age: {{userAge}}</span>
      <button class="btn btn-success" @click="editAge">Edit Age</button>

    </div>
  </div>
</template>
<script>
import {eventBus} from '../../main.js';
export default {
  props :[ 'userAge'],
  methods: {
    editAge() {
      this.userAge = 30;
      // this.$emit('ageWasEdited', this.userAge)
      // eventBus.$emit('ageWasEdited', this.userAge);
      eventBus.changeAge(this.userAge);
    }
  }
}
</script>

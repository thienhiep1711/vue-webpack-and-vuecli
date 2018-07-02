<template>
  <div class="container">
    <h3>The User Component</h3>
    <span >I'm an awesome User!</span>
    <span >Name: <strong>{{name}}</strong></span>
     <span >Age: <strong>{{age}}</strong></span>
    <button class="btn btn-info" @click="changeName">Change my name</button>
    <div class="row">
      <div class="col-md-6">
      <app-user-detail
        :myName="name"
        @nameWasReset="name = $event"
        :resetFn="resetName"
        :userAge="age"
        ></app-user-detail>
    </div>
    <div class="col-md-6">
      <app-user-edit
        :userAge="age"
        @ageWasEdited="age = $event"></app-user-edit>
    </div>
    </div>
  </div>
</template>
<script>
  import UserDetail from './UserDetail.vue';
  import UserEdit from './UserEdit.vue';

  export default {
    data: function() {
      return {
        name: "Mguyen Hiep",
        age: 24
      }
    },
    methods: {
      changeName() {
        this.name = "Nguyen Ha"
      },
      resetName() {
        this.name = "Hoang Hiep"
      }
    },
    components: {
      appUserDetail: UserDetail,
      appUserEdit: UserEdit
    }

  }
</script>

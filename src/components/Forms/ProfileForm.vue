<template>
  <div>
    <div class="row">
      <div class="col-sm-7">
        <form>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Email</label>
            <div class="col-sm-10">
              <input type="email" class="form-control" placeholder="Email" :value="userData.email" @input="userData.email = $event.target.value">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Password</label>
            <div class="col-sm-10">
              <input type="password" class="form-control" placeholder="Password" v-model="userData.password">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Name</label>
            <div class="col-sm-10">
              <input type="text" class="form-control" placeholder="Name" v-model="userData.name">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Age</label>
            <div class="col-sm-10">
              <input type="text" class="form-control" placeholder="Name" v-model="userData.age">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Message</label>
            <div class="col-sm-10">
              <textarea rows="3" class="form-control" placeholder="Message" v-model="message">
              </textarea>
            </div>
          </div>
          <fieldset class="form-group">
            <div class="row">
              <legend class="col-form-label col-sm-2 pt-0">Gender</legend>
              <div class="col-sm-10">
                <div class="form-check">
                  <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios1" value="Male" checked v-model="gender">
                  <label class="form-check-label" for="gridRadios1">
                    Male
                  </label>
                </div>
                <div class="form-check">
                  <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios2" value="Female" v-model="gender">
                  <label class="form-check-label" for="gridRadios2">
                    Female
                  </label>
                </div>
              </div>
            </div>
          </fieldset>
          <div class="form-group row">
            <div class="col-sm-2">Major</div>
            <div class="col-sm-10">
              <div class="form-check">
                <input class="form-check-input" type="checkbox" v-model="major" value="Engginer">
                <label class="form-check-label" for="gridCheck1">
                  Engginer
                </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox"  v-model="major" value="ComputerSience">
                <label class="form-check-label" for="gridCheck1">
                  Computer Sience
                </label>
              </div>
            </div>
          </div>
          <div class="form-group row">
            <div class="col-sm-2">Salary</div>
            <div class="col-sm-10">
              <select name="" id="" class="form-control" v-model="selectedSalarys">
                <option :value="salary" v-for="(salary, index) in salarys" :key="index"> {{salary}}</option>
              </select>
            </div>
          </div>
           <div class="form-group row">
            <div class="col-sm-2">Active</div>
            <div class="col-sm-10">
              <app-switch v-model="dataSwitch"></app-switch>
            </div>
          </div>
          <div class="form-group row">
            <div class="col-sm-10 col-ofset-sm-2">
              <button type="submit" @click.prevent="submited" class="btn btn-primary">Sign in</button>
            </div>
          </div>
        </form>
      </div>

      <div class="col-sm-5" v-if="isSubmited">
        <div class="alert alert-success" role="alert">
         Submit Successfull
        </div>
      </div>
      <div class="col-sm-5" v-if="!isSubmited">
        <app-message :backgroundHighlight="{mainColor:'red', secondColor:'blue', delay:'4000'}"></app-message>
        <app-message :backgroundHighlight="{mainColor:'blue', secondColor:'green', delay:'3000'}"></app-message>
        <app-message :backgroundHighlight="{mainColor:'green', secondColor:'pink', delay:'2000'}"></app-message>
        <h3>Infomation</h3>
        <ul>
          <li>
            <strong>Email:</strong> {{userData.email}}</li>
          <li>
            <strong>Password:</strong> {{userData.password}}</li>
          <li>
            <strong>Name:</strong> {{userData.name}}</li>
          <li>
            <strong>Age:</strong> {{userData.age}}</li>
          <li>
            <strong>Message:</strong> {{message}}</li>
          <li>
            <strong>Gender:</strong> {{gender}}
          </li>
          <li>
            <strong>Major:</strong>  <span v-for="(item, index) in major" :key="index">{{item}}</span>
          </li>
          <li>
            <strong>Swiched</strong>
            {{selectedSalarys}}
          </li>
          <li>
            <strong>Swiched Active</strong>
            {{dataSwitch}}
          </li>
          <li>
            <strong>Submit</strong>
          </li>
        </ul>
      </div>
    </div>
  </div>

</template>
<script>
import SwitchButton from './SwitchButton.vue';
import MessageForm from './MessageForm';
  export default {
    data() {
      return {
        userData: {
          email: '',
          password: '',
          name: '',
          age: 27
        },
        message: "",
        gender: 'Male',
        major: [],
        salarys: ['10000' , '20000', '40000', '80000'],
        selectedSalarys: '20000',
        dataSwitch:true,
        isSubmited:false
      }
    },
    components: {
      "appSwitch": SwitchButton,
      "appMessage": MessageForm
    },
    methods: {
      submited() {
        this.isSubmited = true
      }
    }
  }

</script>

<style scoped>
  ul {
    list-style-type: none;
    padding: 0;

  }

  ul li {
    padding: 5px 0;
  }

</style>

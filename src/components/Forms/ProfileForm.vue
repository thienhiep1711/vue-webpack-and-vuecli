<template>
  <div>
    <div class="row">
      <div class="col-sm-7">
        <form>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Email</label>
            <div class="col-sm-10">
              <input type="email" class="form-control" placeholder="Email" :value="user.userData.email" @input="user.userData.email = $event.target.value">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Password</label>
            <div class="col-sm-10">
              <input type="password" class="form-control" placeholder="Password" v-model="user.userData.password">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Name</label>
            <div class="col-sm-10">
              <input type="text" class="form-control" placeholder="Name" v-model="user.userData.name">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Age</label>
            <div class="col-sm-10">
              <input type="text" class="form-control" placeholder="Name" v-model="user.userData.age">
            </div>
          </div>
          <div class="form-group row">
            <label class="col-sm-2 col-form-label">Message</label>
            <div class="col-sm-10">
              <textarea rows="3" class="form-control" placeholder="Message" v-model="user.message">
              </textarea>
            </div>
          </div>
          <fieldset class="form-group">
            <div class="row">
              <legend class="col-form-label col-sm-2 pt-0">Gender</legend>
              <div class="col-sm-10">
                <div class="form-check">
                  <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios1" value="Male" checked v-model="user.gender">
                  <label class="form-check-label" for="gridRadios1">
                    Male
                  </label>
                </div>
                <div class="form-check">
                  <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios2" value="Female" v-model="user.gender">
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
                <input class="form-check-input" type="checkbox" v-model="user.major" value="Engginer">
                <label class="form-check-label" for="gridCheck1">
                  Engginer
                </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" v-model="user.major" value="ComputerSience">
                <label class="form-check-label" for="gridCheck1">
                  Computer Sience
                </label>
              </div>
            </div>
          </div>
          <div class="form-group row">
            <div class="col-sm-2">Active</div>
            <div class="col-sm-10">
              <app-switch v-model="user.dataSwitch"></app-switch>
            </div>
          </div>
          <div class="form-group row">
            <div class="col-sm-10 col-ofset-sm-2">
              <button type="submit" @click.prevent="submited" class="btn btn-primary">Submit</button>
            </div>
          </div>
        </form>

      </div>

      <div class="col-sm-5" v-if="user.isSubmited">
        <div class="alert alert-success" role="alert">
          Submit Successfull
        </div>
      </div>
      <div class="col-sm-5" v-if="!user.isSubmited">
        <app-message :backgroundHighlight="{mainColor:'red', secondColor:'blue', delay:'4000'}"></app-message>
        <h3>Infomation</h3>
        <ul>
          <li>
            <strong>Email:</strong> {{user.userData.email}}</li>
          <li>
            <strong>Password:</strong> {{user.userData.password}}</li>
          <li>
            <strong>Name:</strong> {{user.userData.name}}</li>
          <li>
            <strong>Age:</strong> {{user.userData.age}}</li>
          <li>
            <strong>Message:</strong> {{user.message}}</li>
          <li>
            <strong>Gender:</strong> {{user.gender}}
          </li>
          <li>
            <strong>Major:</strong>
            <span v-for="(item, index) in user.major" :key="index">{{item}}</span>
          </li>
          <li>
            <strong>Swiched</strong>
            {{user.selectedSalarys}}
          </li>
          <li>
            <strong>Swiched Active</strong>
            {{user.dataSwitch}}
          </li>
          <li>
            <strong>Submit</strong>
          </li>
        </ul>
      </div>
      <div class="col-sm-12">
        <input type="text" class="form-control" v-model="node">
        <button class="btn btn-success" @click="fetchData">Load data</button>
        <br/>
        <table class="table table-table-bordered table-striped">
          <thead>
            <tr>
              <th>Username</th>
              <th>Name</th>
              <th>Age</th>
              <th>Gender</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(u, index) in users" :key="index">
              <td>{{u.userData.email}}</td>
              <td>{{u.userData.name}}</td>
              <td>{{u.userData.age}}</td>
              <td>{{u.gender}}</td>
            </tr>
          </tbody>
        </table>
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
        user: {
          userData: {
            email: '',
            password: '',
            name: '',
            age: 27
          },
          message: "",
          gender: 'Male',
          major: [],
          selectedSalarys: '20000',
          dataSwitch: true,
          isSubmited: false
        },
        users: [],
        resurce: {

        },
        node:'data'
      }
    },
    components: {
      "appSwitch": SwitchButton,
      "appMessage": MessageForm
    },
    methods: {
      submited() {
        this.user.isSubmited = true
        // this.resurce.save({}, this.user);
        this.resurce.saveCustomer(this.user);
      },
      fetchData() {
      this.resurce.getData({node: this.node})
           .then(response => {
            return response.json()
          })
          .then(data => {
            const resultArray = [];
            for (let key in data) {
              resultArray.push(data[key]);
            }
            this.users = resultArray;
          })
      }
    },
    created() {
      const customActions = {
          saveCustomer: {method:'POST', url: 'customer.json'},
          getData: {method:'GET'}
      }
      this.resurce = this.$resource('{node}.json', {}, customActions)
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

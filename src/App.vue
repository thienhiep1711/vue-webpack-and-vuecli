<template>
  <div class="main-wrap">
    <app-header></app-header>
    <div class="main-content">
      <div class="container">
      <div class="row">
        <div class="col-sm-3">
          <app-sidebar></app-sidebar>
        </div>
         <div class="col-sm-9">
           <div class="main-box">
             <app-user></app-user>
        <!-- <app-servers></app-servers> -->
           </div>
      </div>
      </div>

    </div>
    </div>
    <app-footer></app-footer>
  </div>
</template>

<script>
  import Header from './components/Shared/Header';
  import Footer from './components/Shared/Footer';
  import Sidebar from './components/Sidebar/Sidebar';
  import User from './components/Users/User';
  import ServerStatus from './components/Server/ServerStatus';

  import './assets/css/bootstrap.min.css';
  import './assets/css/styles.scss';
  export default {
    components: {
      'app-header': Header,
      'app-footer': Footer,
      'app-sidebar': Sidebar,
      'app-user': User,
      'app-server-status': ServerStatus,
    }
  }

</script>

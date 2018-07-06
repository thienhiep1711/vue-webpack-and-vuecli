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

  import './assets/css/bootstrap.min.css';
  import './assets/css/styles.scss';
  export default {
    data: function() {
      return {

      }
    },
    components: {
      'app-header': Header,
      'app-footer': Footer,
      'app-sidebar': Sidebar,


    },
    methods: {

    }
  }

</script>

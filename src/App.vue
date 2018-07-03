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
             <!-- <app-user></app-user> -->
             <div class="text-center">
               <button class="btn btn-success" @click="selectedComponent = 'appQuote'">News</button>
               <button class="btn btn-warning"  @click="selectedComponent = 'quoteAuthor'">Author</button>
               <button class="btn btn-primary"  @click="selectedComponent = 'quoteNew'">Quote</button>
             </div>
             <p>{{selectedComponent}}</p>
             <component :is="selectedComponent">
               <p>Default Content</p>
             </component>
             <!-- <app-quote :quote="'Hiep This is wonderful quote'">
               <h2 slot="title">{{quoteTitle}}</h2>
              <p slot="content">Nguyen Hiep recomentdation </p>
             </app-quote> -->
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
  import Quote from './components/Quote/Quote.vue';

  import Author from './components/Quote/Author.vue';
  import New from './components/Quote/New.vue';

  import './assets/css/bootstrap.min.css';
  import './assets/css/styles.scss';
  export default {
    data: function() {
      return {
        quoteTitle:"The Quote",
        selectedComponent:'appQuote'
      }
    },
    components: {
      'app-header': Header,
      'app-footer': Footer,
      'app-sidebar': Sidebar,
      'app-user': User,
      'app-server-status': ServerStatus,
      'appQuote': Quote,
      'quoteNew': New,
      'quoteAuthor' : Author,
    }
  }

</script>

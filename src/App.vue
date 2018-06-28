<template>
<div>

  <app-header></app-header>
  <app-sidebar></app-sidebar>
  <app-footer></app-footer>
  <app-servers></app-servers>

</div>

</template>

<script>
import Header from './components/Shared/Header';
import Footer from './components/Shared/Footer';
import Sidebar from './components/Sidebar/Sidebar';
import ServerStatus from './components/Server/ServerStatus';

  export default {
    components: {
      'app-header' : Header,
      'app-footer' : Footer,
      'app-sidebar' : Sidebar,
      'app-server-status' : ServerStatus,
    }
  }
</script>

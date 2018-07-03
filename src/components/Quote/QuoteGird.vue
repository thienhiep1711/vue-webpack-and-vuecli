<template>
   <div>
     <app-quote v-for="(quote, index) in quotes" :key="index" @click.native="deleteQuote(index)">{{quote}} {{index}}</app-quote>
   </div>

</template>
<script>
import Quote from './Quote';
export default {
  props: ['quotes'],
   methods: {
    deleteQuote(index) {
      this.$emit('quoteDeleted', index);
      console.log(this)
    }
  },
  components: {
    appQuote: Quote
  },


}

</script>

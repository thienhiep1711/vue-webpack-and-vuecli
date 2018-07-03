<template>
   <div>
     <div class="row">
          <div class="col-sm-6 col-sm-offet-3">
            <label for="">Quote</label>
            <textarea name="#"  class="form-control" rows="3" v-model="quote"></textarea>
     </div>
         <div class="col-sm-6 col-sm-offet-3">
            <button class="btn btn-primary" @click.prevent="createNew">Add quote</button>
     </div>
     </div>
   </div>

</template>
<script>
export default {
  data: function() {
    return {
      quote:"",

    }
  },
  methods: {
    createNew() {
      this.$emit('quoteAdded', this.quote);
      this.quote = "";
    }
  }
}

</script>

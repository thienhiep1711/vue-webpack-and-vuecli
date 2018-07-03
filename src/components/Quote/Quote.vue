<template>
   <div>
     <div class="row">
       <div class="col-12">
         <div class="box-slot">
            <slot name="title"></slot>
            <h2>
              <slot name="subtitle">The subtitle</slot>
            </h2>

         </div>

       </div>
        <div class="col-12">
          <div class="box-slot">
              <slot></slot>

          </div>
       </div>
     </div>
   </div>

</template>
<script>
export default {
  props: ['quote']
}

</script>

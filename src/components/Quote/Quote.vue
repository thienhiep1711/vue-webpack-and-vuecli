<template>
   <div>
     <div class="panel-quote item-card" >
       <slot></slot>
     </div>
   </div>

</template>
<script>
export default {
  props: ['quotes']
}

</script>

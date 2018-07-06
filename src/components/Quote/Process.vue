<template>
  <div class="progress">
  <div class="progress-bar progress-bar-striped bg-success" role="progressbar" :style="{width: (quoteCounts/maxQuotes)* 100 + '%'}" :aria-valuenow="{width: (quoteCounts/maxQuotes)* 100}" aria-valuemin="0" aria-valuemax="100">
    {{quoteCounts}} / {{maxQuotes}}
  </div>
</div>
</template>
<script>
  export default  {
    props:['maxQuotes', 'quoteCounts']
  }
</script>

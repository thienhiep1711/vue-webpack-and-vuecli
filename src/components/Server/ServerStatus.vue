<template>
<div>
  <p>Status Server: {{status}}</p>
  <button @click="changeStatus">Change Status</button>
</div>

</template>
<script>
export default {
  data: function() {
    return {
      status: "Warning"
    }

  },
  methods : {
    changeStatus() {
      this.status = "Normal";
    }
  }
}
</script>

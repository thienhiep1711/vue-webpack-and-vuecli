<template>
    <div>
      <div class="switch">
        <div class="switch__button" id="on" @click="switched(true)" :class="{active: value}">
          ON
        </div>
         <div class="switch__button" id="off"  @click="switched(false)" :class="{active: !value}">
          OFF
        </div>
      </div>
    </div>
</template>
<script>
  export default {
    props:['value'],
    methods: {
      switched(isOn) {
        this.$emit('input', isOn);
      }
    }
  }
</script>
<style>
.switch__button {
  width: 50px;
  height: 30px;
  text-align: center;
  line-height: 30px;
  color: #444;
  border: 1px solid #e5e5e5;
  display: inline-block;
  float: left;

}
.switch__button:hover {
  cursor: pointer;

}
.switch__button.active {
  background-color: green;
  color: #fff;
}
</style>

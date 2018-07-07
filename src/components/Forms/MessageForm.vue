<template>
  <div>
    <div class="message-alert" v-local-highlight="backgroundHighlight" v-text="'This change updated'">

    </div>
    <div class="message-alert" v-local-highlight:color.delayed.blink="backgroundHighlight" v-html="'<strong>This is directive with html</strong>'">

    </div>
  </div>

</template>
<style>
  .message-alert {
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #e5e5e5;
    border-radius: 4px;
    background-color: #fbfbfb;
    color: #fff;
  }

</style>

<script>
  export default {
    props: ['backgroundHighlight'],
    directives: {
      'local-highlight': {
        bind(el, binding, vnode) {
          var delay = 0;
          if (binding.modifiers['delayed']) {
            delay = 2000;
          }
          if (binding.modifiers['blink']) {
            let mainColor = binding.value.mainColor;
            let secondColor = binding.value.secondColor;
            let currentColor = mainColor;
            setTimeout(() => {
              setInterval(() => {
                if (currentColor == secondColor ? currentColor = mainColor : currentColor = secondColor) {
                  if (binding.arg == 'color') {
                    el.style.color = currentColor;
                  } else {
                    el.style.backgroundColor = currentColor;
                  }
                }
              }, 1000);
            }, binding.delay)
          }
          else {
            if (binding.arg == 'color') {
                el.style.color = binding.value.mainColor;
              } else {
                el.style.backgroundColor = binding.value.mainColor;
              }
          }
        }
      }
    }
  }

</script>

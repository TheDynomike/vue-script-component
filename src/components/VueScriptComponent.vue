<template>
  <div :id="compId">
  </div>
</template>

<script>
import postscribe from "postscribe"
var ready = require('document-ready')

export default {
  name: "VueScriptComponent",
  props:["script"],
  data() {
    return {
      compId: Date.now() //we will use date.now as a soft ID so that users may load multiple vue-script-components without conflicting ids
    };
  },

  mounted() {
    var vm = this
    ready(function () {
      let addEl = new Promise((resolve, reject) => {
          postscribe(
            `#${vm.compId}`,
            `${vm.script}`,
            {
              done: function(x) {}
            }
          );

        resolve()
      });      
      addEl.then(function(result) {
          //do nothing
      })
    })
  }
}

</script>

<style scoped>

</style>
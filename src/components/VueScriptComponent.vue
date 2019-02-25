<template>
  <div :id="compId" :key="id"></div>
</template>

<script>
import postscribe from "postscribe";
var ready = require("document-ready");

export default {
  name: "VueScriptComponent",
  data() {
    let randomID = Math.random()
      .toString(36)
      .substring(7);
    return {
      compId: Date.now() + randomID
    };
  },
  props: {
    id: {
      type: String,
      default: null
    },
    script: {
      type: String,
      default: null
    }
  },
  mounted() {
    var vm = this;
    ready(function() {
      let addEl = new Promise((resolve, reject) => {
        postscribe(`#${vm.compId}`, `${vm.script}`, {
          done: function(x) {}
        });

        resolve();
      });
      addEl.then(function(result) {
        //do nothing
      });
    });
  }
};
</script>

<style scoped>
</style>
<template>
  <div ref="blueteam" class="hello">
    Hello from {{ msg }}!

    <button @click="handleClick()">Publish message!</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  methods: {
    handleClick() {
      const event = new CustomEvent('blue-team', { 
        detail: { "msg": "hello world" },
        // to bubble up through the DOM
        bubbles: true,
        // event shouldn't be cancellable as it is a transient message to emit
        cancelable: false,
        // allow red-team to listen to <blue-team> without shadowRoot
        // if false, red-team must listen to blueteam.shadowRoot
        composed: true 
      });

      this.$refs.blueteam.dispatchEvent(event);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

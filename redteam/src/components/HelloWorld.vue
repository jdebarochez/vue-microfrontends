<template>
  <div class="hello">
    <h1>Hello from {{ msg }}</h1>
    Blue team says {{ blueMsg }}
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      blueMsg: ""
    }
  },
  mounted() {
    const blueTeam = document.querySelector('blue-team');
    let $self = this;
    blueTeam.addEventListener('blue-team', function (e) { 
      $self.blueMsg = e.detail.msg;
    }, false);
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

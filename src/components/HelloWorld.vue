<template>
  <div class="hello">
    <h1>{{ message }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>if-visible example</h3>
    <p v-if="visible">I am visible!</p>
    <button v-on:click="switchVis">{{ showHide }}</button>
    <h3>Interaction with user</h3>
    <p>{{ userMsg }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
    <h3>Ecosystem</h3>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    message: String,
    visible: Boolean,
    userMsg: String,
    reverseMessage: Function,
    switchVis: Function,
    showHide: String,
  },
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

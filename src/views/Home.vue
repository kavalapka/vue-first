<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld message="My First Vue.js App" :userMsg="userMsg"
                :visible="visible" :switchVis="switchVis"
                :showHide="showHide"/>
    <Rating :grade="5" :maxStars="5" :hasCounter="true"/>
    <Users :users="users" :isVisible="false"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '../components/HelloWorld.vue';
import Users from '../components/Users.vue';
import Rating from '../components/Rating.vue';

function switchVis() {
  this.visible = !this.visible;
  this.showHide = this.visible ? 'Hide' : 'Show';
}

export default {
  name: 'home',
  components: {
    Users,
    HelloWorld,
    Rating,
  },
  data() {
    return {
      visible: true,
      showHide: 'Hide',
      userMsg: 'It is user message',
      users: null,
    };
  },
  methods: {
    switchVis,
  },
  async created() {
    const userResponse = await fetch('https://jsonplaceholder.typicode.com/users');
    this.users = await userResponse.json();
  },
};
</script>

<style>
  h3 {
    margin: 40px 0 0;
    color: #2c3e50;
  }
</style>

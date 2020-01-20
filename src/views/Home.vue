<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld message="My First Vue.js App" :userMsg="userMsg"
                :reverseMessage="reverseMessage" :visible="visible" :switchVis="switchVis"
                :showHide="showHide"/>
    <Rating :grade="3" :maxStars="5" :hasCounter="true"/>
    <Users :users="users"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '../components/HelloWorld.vue';
import Users from '../components/Users.vue';
import Rating from '../components/Rating.vue';

function reverseMessage() {
  this.userMsg = this.userMsg.split('').reverse().join('');
}

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
    reverseMessage,
    switchVis,
  },
  async created() {
    const userResponse = await fetch('https://jsonplaceholder.typicode.com/users');
    this.users = await userResponse.json();
  },
};
</script>

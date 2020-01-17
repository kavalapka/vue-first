<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld message="My First Vue.js App" :userMsg="userMsg"
                :reverseMessage="reverseMessage" :visible="visible" :switchVis="switchVis"
                :showHide="showHide"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
//
// const show: 'Show',
//   hide: 'Hide',
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
    HelloWorld,
  },
  data() {
    return {
      visible: true,
      showHide: 'Hide',
      userMsg: 'It is user message',
    };
  },
  methods: {
    reverseMessage,
    switchVis,
  },
};
</script>

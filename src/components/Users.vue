<template>
  <div class="users-container">
    <button type="button" class="btn btn-success users" @click="showUsers">
      Get Users Data (API request)
    </button>
    <table class="table" v-if="visible">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Name</th>
          <th scope="col">Email</th>
          <th scope="col">City</th>
        </tr>
      </thead>
      <tbody>
      <tr v-for="user in users" v-bind:key="user.id">
        <th scope="row">{{user.id}}</th>
        <td>{{user.name}}</td>
        <td>{{user.email}}</td>
        <td>{{user.address.city}}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Users',
  props: {
    users: Array,
    isVisible: Boolean,
  },
  data() {
    return {
      visible: this.isVisible,
    };
  },
  methods: {
    showUsers() {
      this.visible = !this.visible;
    },
  },
};
</script>

<style>
  .users {
    margin: 10px 0;
  }
  .table {
    width: 80%;
    margin: 0 10%;
  }
</style>

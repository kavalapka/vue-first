<template>
  <div class="users-container">
    <h3 class="users">Users:</h3>
    <table class="table">
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
  },
};
</script>

<style>
  .users {
    margin-bottom: 5%;
  }
</style>

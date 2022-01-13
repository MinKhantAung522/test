<template>
  <div>
    <table class="table text-start">
      <thead>
        <tr>
          <th scope="col">No</th>
          <th scope="col">Name</th>
          <th scope="col">Phone</th>
          <th scope="col">Website</th>
          <th scope="col">Email</th>
          <td scope="col" class="text-start"><button class="btn btn-success" @click="addEmployee">Add Employee</button></td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in user_lists" :key="user.id">
          <td>{{user.id}}</td>
          <td>{{user.name}}</td>
          <td>{{user.phone}}</td>
          <td>{{user.website}}</td>
          <td>{{user.email}}</td>
          <td class="text-start"><button class="btn btn-primary me-3">Edit</button><button class="btn btn-danger">Delete</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ["user_lists","addUser"],
  methods:{
    addEmployee(){
      this.$router.push("/adduser")
    }
  },
};
</script>

<style>
</style>
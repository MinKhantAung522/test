<template>
  <div>
    <table class="table text-start">
      <thead>
        <tr>
          <th scope="col">No</th>
          <th scope="col">FullName</th>
          <th scope="col">Phone</th>
          <th scope="col">Email</th>
          <th scope="col">Age</th>
          <th scope="col">Job Position</th>
          <th scope="col" class="text-start">
            <button class="btn btn-success" @click="addEmployee">
              Add Employee
            </button>
            <button class="btn btn-danger ms-2" @click="deleteAll">
              Delete All Employee
            </button>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in user_lists" :key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.fullname }}</td>
          <td>{{ user.phoneNo }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.age }}</td>
          <td>{{ user.jobPosition }}</td>
          <td class="text-start">
            <button class="btn btn-primary me-3" @click="edit(user)">
              Edit</button
            ><button class="btn btn-danger me-3" @click="Remove(user.id)">Delete</button>
            <button class="btn btn-info" @click="view">View</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  props: ["user_lists", "addUser"],
  methods: {
    addEmployee() {
      this.$router.push("/adduser");
    },
    edit(user) {
      this.$router.push("/edit/" + user.id);
    },
    Remove(id){
      axios.delete("https://testing-api-mock.herokuapp.com/users/"+id)
      .then(()=>{
        this.$emit("delete",id);
      })
      .catch((err)=>{
        console.log(err.message);
      })
    },
    deleteAll(){
      axios.delete("https://testing-api-mock.herokuapp.com/users")
      .then(()=>{
        this.$emit("deleteAll");
      })
      .catch((err)=>{
        console.log(err);
      })
    }
  },
};
</script>

<style>
</style>
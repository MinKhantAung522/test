<template>
  <div class="d-flex justify-content-center bg-white pt-5">
    <form @submit.prevent="addUser">
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">Name:</label>
        <input
          type="text"
          class="form-control mt-2"
          id="exampleFormControlInput1"
          placeholder="first name"
          v-model="user.name"
        />
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">PhoneNumber:</label>
        <input
          type="text"
          class="form-control mt-2"
          id="exampleFormControlInput1"
          placeholder="last name"
          v-model="user.phone"
        />
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">Website:</label>
        <input
          type="text"
          class="form-control mt-2"
          id="exampleFormControlInput1"
          placeholder="last name"
          v-model="user.website"
        />
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">Email address:</label>
        <input
          type="email"
          class="form-control mt-2"
          id="exampleFormControlInput1"
          placeholder="name@example.com"
          v-model="user.email"
        />
      </div>
     

      <button type="submit" class="my-3 btn btn-success">Add Employee</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      user: {
        name: "",
        phone: "",
        website: "",
        email: "",
      },
    };
  },
  methods: {
    addUser() {
      axios
        .post("https://jsonplaceholder.typicode.com/users",{
            name: this.user.name,
            phone:this.user.phone,
            email:this.user.email,
            website:this.user.website,
        })
        .then(() => {
          this.$router.push("/");
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>
<template>
  <div class="d-flex justify-content-center bg-white pt-5">
    <form @submit.prevent="editCustomer">
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">Name:</label>
        <input
          type="text"
          class="form-control mt-2"
          required
          placeholder="Name"
          v-model="customer.name"
        />
      </div>
      <div class="form-group mb-3">
        <label for="cars">MaritalStats:</label>
        <select
          id="cars"
          name="cars"
          class="form-control mt-2"
          v-model="customer.maritalStatus"
          required
        >
          <option value="Single">Single</option>
          <option value="Married">Married</option>
          <option value="Divorced">Divorced</option>
          <option value="Windowed">Windowed</option>
        </select>
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">Email:</label>
        <input
          type="email"
          class="form-control mt-2"
          required
          placeholder="email"
          v-model="customer.email"
        />
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">phoneNo:</label>
        <input
          type="tel"
          class="form-control mt-2"
          placeholder="phoneNo"
          v-model="customer.phoneNo"
        />
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">City:</label>
        <input
          type="text"
          class="form-control mt-2"
          placeholder="City"
          v-model="customer.city"
        />
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">Address:</label>
        <input
          type="text"
          class="form-control mt-2"
          placeholder="Address"
          v-model="customer.address"
        />
      </div>
      <div class="form-group mb-3">
        <label for="cars">Status:</label>
        <select
          id="cars"
          name="cars"
          class="form-control mt-2"
          v-model="customer.status"
          required
        >
          <option value="Active">Active</option>
          <option value="Inactive">Inactive</option>
        </select>
      </div>
      <div class="form-group mb-3">
        <label for="exampleFormControlInput1">dateOfBirth:</label>
        <input
          type="date"
          class="form-control mt-2"
          placeholder="Address"
          v-model="customer.dateOfBirth"
        />
      </div>
      <button type="submit" class="my-3 btn btn-success">Edit Customer</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: ["id"],
  data() {
    return {
      customer: {
        name: "",
        maritalStatus: "",
        email: "",
        phoneNo: "",
        city: "",
        address: "",
        status: "",
        dateOfBirth: "",
        fid:""
      },
    };
  },
  methods: {
    editCustomer() {
      const data = {
        name: this.customer.name,
        maritalStatus: this.customer.maritalStatus,
        email: this.customer.email,
        phoneNo: this.customer.phoneNo,
        city: this.customer.city,
        address: this.customer.address,
        status: this.customer.status,
        dateOfBirth: this.customer.dateOfBirth,
        id:this.customer.fid
      };

      axios
        .put(
          "https://demo.judosoft.com/technical-assessment/api/customer",
          data
        )
        .then(() => {
          alert("customer updated")
          this.$router.push("/");
        })
        .catch(function (error) {
          console.log(error.message);
        });
    },
  },
  mounted() {
    axios
      .get(
        "https://demo.judosoft.com/technical-assessment/api/customer/" + this.id
      )
      .then((res) => {
        console.log(res);
        const fetcheduser = res.data;
        console.log(fetcheduser);
        this.customer.fid = fetcheduser.id
        this.customer.name = fetcheduser.name;
        this.customer.maritalStatus = fetcheduser.maritalStatus;
        this.customer.email = fetcheduser.email;
        this.customer.phoneNo = fetcheduser.phoneNo;
        this.customer.city = fetcheduser.city;
        this.customer.address = fetcheduser.address;
        this.customer.status = fetcheduser.status;
        this.customer.dateOfBirth = fetcheduser.dateOfBirth;
      });
  },
};
</script>

<style>
</style>
<template>
  <div class="home">
    <h1>Test</h1>
    <div class="d-flex justify-content-between">
      <div>
        <button class="btn btn-primary me-4" @click="addCustomer">
          AddCustomer
        </button>
      </div>

      <div class="d-flex flex-column bd-highlight mb-3">
        <div class="p-2 bd-highlight">
          <input type="text" v-model="name" placeholder="search by name" />
        </div>
        <div class="p-2 bd-highlight">
          <input type="text" v-model="email" placeholder="search by email" />
        </div>
        <button class="btn btn-primary" @click="search">Search</button>
      </div>
    </div>
    <SingleList :customerLists="customerLists"></SingleList>
  </div>
</template>

<script>
import SingleList from "../components/SingleList";
import axios from "axios";
export default {
  name: "Home",
  components: {
    SingleList,
  },
  data() {
    return {
      customerLists: [],

      name: "",
      maritalStatus: "",
      email: "",
      phoneNo: "",
      city: "",
      address: "",
      status: "",
      dateOfBirth: "",
    };
  },
  methods: {
    search() {
      this.getList();
    },
    getList() {
      let link =
        "https://demo.judosoft.com/technical-assessment/api/customer?" +
        "name=" +
        this.name +
        "&email=" +
        this.email;
      axios.get(link).then((data) => {
        this.customerLists = data.data.customerList;
      });
    },
    addCustomer() {
      this.$router.push("/adduser");
    },
  },
  mounted() {
    axios
      .get("https://demo.judosoft.com/technical-assessment/api/customer")
      .then((res) => {
        console.log(res.data.customerList, "data");
        this.customerLists = res.data.customerList;
      });
  },
};
</script>

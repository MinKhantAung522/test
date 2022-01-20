<template>
  <div>
    <table class="table table-bordered border-dark text-start">
      <thead>
        <tr>
          <th scope="col">No</th>
          <th scope="col">Name</th>
          <th scope="col">DateOfBirth</th>
          <th scope="col">MartialStatus</th>
          <th scope="col">Email</th>
          <th scope="col">PhoneNo</th>
          <th scope="col">City</th>
          <th scope="col">Address</th>
          <th scope="col">status</th>
          <th class="text-start">
            
           
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="customer in customerLists" :key="customer.id">
          <td>{{ customer.id }}</td>
          <td>{{ customer.name }}</td>
          <td>{{ customer.dateOfBirth }}</td>
          <td>{{ customer.martialStatus }}</td>
          <td>{{ customer.email }}</td>
          <td>{{ customer.phoneNo }}</td>
          <td>{{customer.city}}</td>
          <td>{{customer.address}}</td>
          <td>{{customer.status}}</td>
          <td class="text-start">
            <button class="btn btn-primary me-1 mb-2" @click="edit(customer)">
              Edit</button
            >
            <button class="btn btn-success" @click="view(customer.id)">View</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  props: ["customerLists", "addUser"],
  methods: {
    edit(customer) {
      this.$router.push("/edit/" + customer.id);
    },
    view(customer){
      this.$router.push("/view/"+customer)
    }
  
  },
};
</script>

<style>
</style>
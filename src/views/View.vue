<template>
  <div class="text-center">
      <p>id - "{{singleCustomer.id}}"</p>
      <p>Name - "{{singleCustomer.name}}"</p>
      <p>dateOfBirth - "{{singleCustomer.dateOfBirth}}"</p>
      <p>martialStatus - "{{singleCustomer.maritalStatus}}"</p>
      <p>Email - "{{singleCustomer.email}}"</p>
      <p>phoneNo - "{{singleCustomer.phoneNo}}"</p>
      <p>city - "{{singleCustomer.city}}"</p>
      <p>address - "{{singleCustomer.address}}"</p>
      <p>status - "{{singleCustomer.status}}"</p>
      <button class="btn btn-success" @click="toEdit">Edit Detail</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
props:["id"],
data(){
    return{
        singleCustomer:[]
    }
},
methods:{
    toEdit(){
        this.$router.push("/edit/"+this.id)
    }
},
mounted(){
    axios.get("https://demo.judosoft.com/technical-assessment/api/customer/"+this.id)
    .then((res)=>{
        this.singleCustomer = res.data;
    })
    .catch((err)=>{
        console.log(err);
    })
}
}
</script>

<style>

</style>
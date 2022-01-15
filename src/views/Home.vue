<template>
  <div class="home">
    <h1>Employee Management System</h1>
    
   <SingleList :user_lists="user_lists" @delete ="deletee($event)" @deleteAll="deleteAll"></SingleList>
    
  </div>
</template>

<script>


import SingleList from '../components/SingleList';
import axios from "axios";
export default {
  name: 'Home',
  components: {
    SingleList,
  },
  data(){
    return{
      user_lists:[]
    }
  },
  methods:{
    deletee(id){
      console.log(id);
      this.user_lists = this.user_lists.filter((user)=>{
        return user.id != id;
      })
    },
    deleteAll(){
      this.user_lists = [];
    }
  },
  mounted(){
    axios.get("https://testing-api-mock.herokuapp.com/users")
    .then((res)=>{
      console.log(res.data.results);
      return res.data.results;
    })
    .then((data)=>{
      this.user_lists = data;
    })
  }
}
</script>

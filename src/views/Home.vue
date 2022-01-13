<template>
  <div class="home">
    
   <SingleList :user_lists="user_lists"></SingleList>
    
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
  mounted(){
    axios.get("https://jsonplaceholder.typicode.com/users")
    .then((res)=>{
      console.log(res.data);
      return res.data;
    })
    .then((data)=>{
      this.user_lists = data;
    })
  }
}
</script>

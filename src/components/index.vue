<script>
import axios from "axios"
export default{
  name:"index",
  components:{},
  data(){return{
  };},
  methods:{
  },mounted(){
    axios({
      url:'http://web.hcskia.cloud:8311/user/profile',
      method:"GET",
      headers:{
        'Content-Type':'application/json',
        'Authorization':document.cookie
      }
    }).then(function(success){
      const data = success.data;
      console.log(data);
      const userID = data['userId'];
      const qq = data['qq'];
      document.getElementById("wellcomeText").textContent = userID + " 欢迎回来！";
    }).catch(function(error){

    });
    }
}


</script>

<template>
  <div class="pages">
    <h3 id="wellcomeText">
    </h3>
  </div>
</template>

<style scoped>
</style>

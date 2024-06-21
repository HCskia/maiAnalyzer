<script>
import axios from 'axios'
export default{
  name:"userProfile",
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
      document.getElementById("userIdText").textContent = userID;
      document.getElementById("qqText").textContent = qq;
    }).catch(function(error){

    });
    }
}


</script>

<template>
  <div class="pages">
    <h2>用户名：</h2><a id="userIdText"></a>
    <h2>QQ：</h2><a id="qqText"></a>
  </div>
</template>

<style scoped>
</style>

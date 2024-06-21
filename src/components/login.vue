<script setup>
import axios from "axios"
import Cookies from "js-cookie";
import cookies from 'js-cookie'
import { onMounted } from "vue";

const UserId = defineModel("UserId")
const UserQQ = defineModel("qq")

onMounted(() => {
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
    UserId.value = data['userId'];
    UserQQ.value = data['qq'];
    document.getElementById("loginButton").textContent = "重新登陆";
  }).catch(function(error){

  });
})

function login(){
  axios({
    url:'http://web.hcskia.cloud:8311/user/login',
    method:"POST",
    headers:{
      'Content-Type':'application/json'
    },
    data:{
      "userId":UserId.value,
      "qq":qq.value
    }
  })
    .then(function(success){
      console.log(success.data);
      Cookies.set("Authorization",success.data);
    })
    .catch(function(error){
      console.log(error);
    });
  }


</script>

<template>
  <div>
    <div class="login">
        <label>用户名:
            <input v-model="UserId" type="text">
        </label>
        <label>QQ:
            <input v-model="UserQQ" type="text">
        </label>
        <button id="loginButton" @click="login">登录</button>
    </div>
  </div>
</template>


<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}
</style>

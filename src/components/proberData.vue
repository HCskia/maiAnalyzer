<script>
import axios from 'axios'
import { reactive } from 'vue';

var UserID = ""
var qq = ""
var verData = [];
export default{
  name:"proberData",
  components:{},
  data(){return{
  };},
  methods:{
    dataRefresh(){
        console.log(UserID);
        axios({
            url:'https://www.diving-fish.com/api/maimaidxprober/query/plate',
            method:"POST",
            headers:{
            'Content-Type':'application/json'
            },
            data:{
                "qq":qq,
                "version":['maimai PLUS', 'maimai でらっくす BUDDiES', 'maimai でらっくす', 'maimai MURASAKi', 'maimai', 'maimai でらっくす Splash PLUS', 'MiLK PLUS', 'maimai GreeN', 'maimai MiLK', 'maimai でらっくす Splash', 'maimai FiNALE', 'maimai GreeN PLUS', 'maimai でらっくす UNiVERSE', 'maimai ORANGE', 'maimai ORANGE PLUS', 'maimai PiNK', 'maimai PiNK PLUS', 'maimai MURASAKi PLUS', 'maimai でらっくす FESTiVAL']
            }
        }).then(function(success){
            verData = success.data
            
            axios({
                url:'http://web.hcskia.cloud:8311/mai/datarefresh',
                method:"POST",
                headers:{
                    'Content-Type':'application/json',
                    'Authorization':document.cookie
                },
                data:{
                    "data":verData
                }
                }).then(function(success){

                }).catch(function(error){
            });
            
        }).catch(function(error){
            console.log(error);
        });
    }
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
      UserID = data['userId'];
      qq = data['qq'];
      document.getElementById("userIdText").textContent = UserID;
      document.getElementById("qqText").textContent = qq;
    }).catch(function(error){

    });
    }
}
</script>

<template>
  <div class="pages">
    <h3>用户名：</h3><h3 id="userIdText"></h3>
    <h3>QQ：</h3><h3 id="qqText"></h3>
    <a @click="dataRefresh" rel="noopener">数据刷新/导入</a>
  </div>
</template>

<style scoped>
</style>

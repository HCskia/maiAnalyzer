<script>
import axios from 'axios'
import { reactive } from 'vue';

export default{
  name:"analyzer",
  components:{},
  data(){return{
  };},
  methods:{
  },mounted(){
    axios({
      url:'http://web.hcskia.cloud:8311/mai/getdata',
      method:"GET",
      headers:{
        'Content-Type':'application/json',
        'Authorization':document.cookie
      }
    }).then(function(success){
      const data = success.data;
      console.log(data);
      var addHTML = "";
      for(let elem of data){
        addHTML += "<tr><td>" + elem["Achievements"] + "</td>";
        addHTML += "<td>" + elem["Fc"] + "</td>";
        addHTML += "<td>" + elem["Fs"] + "</td>";
        addHTML += "<td>" + elem["Id"] + "</td>";
        addHTML += "<td>" + elem["Level"] + "</td>";
        addHTML += "<td>" + elem["LevelIndex"] + "</td>";
        addHTML += "<td>" + elem["Title"] + "</td>";
        addHTML += "<td>" + elem["Type"] + "</td></tr>";
        //console.log(addHTML);
      }
      document.getElementById("tableBody").innerHTML += addHTML;
    }).catch(function(error){

    });
    }
}
</script>

<template>
  <div class="pages">
    <table>
        <thead>
            <tr>
                <th>完成度</th>
                <th>FC</th>
                <th>FS</th>
                <th>乐曲ID</th>
                <th>乐曲等级</th>
                <th>乐曲级别</th>
                <th>标题</th>
                <th>谱面类型</th>
            </tr>
        </thead>
    </table>
    <tbody id="tableBody">
        <!-- <tr>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr> -->
    </tbody>
  </div>
</template>

<style scoped>
</style>

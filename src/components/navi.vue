<script>
export default{
  name:"Navi",
  components:{},
  data(){return{

  };},
  methods:{
    pageToLogin(){
      this.$parent.ShowLogin();
    },
    pageToIndex(){
      this.$parent.ShowIndex();
    },
    pageToUserProfile(){
      this.$parent.ShowUserProfile();
    },
    pageToProberData(){
      this.$parent.ShowProberData();
    },
    pageToAnalyzer(){
      this.$parent.ShowAnalyzer();
    }
  }
}

</script>

<template>
  <div class="Text">
    <img alt="maimai Logo" class="logo" src="../assets/maimailogo.png" width="215" height="125"/>
    <ul>
        <li><h3><a @click="pageToIndex" target="_blank" rel="noopener">首页</a></h3></li>
        <li><h3><a @click="pageToUserProfile" target="_blank" rel="noopener">用户</a></h3></li>
        <li><h3><a @click="pageToAnalyzer" target="_blank" rel="noopener">成绩分析</a></h3></li>
        <li><h3><a @click="pageToProberData" target="_blank" rel="noopener">查分器导入</a></h3></li>
        <li><h3><a @click="pageToLogin" target="_blank" rel="noopener">登录</a></h3></li>
    </ul>
  </div>
</template>

<style scoped>
.Text h3 {
  text-align: center;
  font-size: 1.15rem;
}

.Text{
    margin: 1rem;
}

.logo {
  display: block;
  margin: 0 2rem 0 0;
}

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
}

li {
    float: left;
}

li:last-child {
    border-right: none;
}

li a {
    color: rgb(0, 0, 0);
    text-align: center;
    padding: 14px 25px;
    text-decoration: none;
}

</style>

<script>
import Index from './components/index.vue'
import navi from './components/navi.vue'
import Login from './components/login.vue'
import userProfile from './components/userProfile.vue'
import proberData from './components/proberData.vue'
import analyzer from './components/analyzer.vue'
import { createApp, ref, onMounted} from 'vue'
import { createStore } from 'vuex'

const PageApp = createApp(Index);

export default{
  name:"MainPage",
  components: {navi,},
  data(){
    return{
      ShowLogin(){
        const PageApp = createApp(Login);
        PageApp.mount("#pages");
      },
      ShowIndex(){
        const PageApp = createApp(Index);
        PageApp.mount("#pages");
      },
      ShowUserProfile(){
        const PageApp = createApp(userProfile);
        PageApp.mount("#pages");
      },ShowProberData(){
        const PageApp = createApp(proberData);
        PageApp.mount("#pages");
      },ShowAnalyzer(){
        const PageApp = createApp(analyzer);
        PageApp.mount("#pages");
      }
    };
  },
  mounted(){
    PageApp.mount("#pages");
  }
}

</script>

<template>
  <header>
    <div class="navi">
      <navi/>
    </div>
  </header>
  <child id="pages"></child>
</template>

<style scoped>
header {
  line-height: 1.5;
  margin: 0 auto
}
template{
  
}

@media (min-width: 1024px) {
  header {
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
}
</style>

<template>
  <div class="container"  :class="darkMode ? 'dark' : 'light'" >
    <AppHeader  :darkMode="darkMode" @toggle-dark-mode="toggleDarkMode" />
    <SearchUser  :darkMode="darkMode" @githubUser="updateGitHubUser" />
     <UserInfo :darkMode="darkMode" v-if="githubUser" :githubUser="githubUser" />   <!-- null ya da undefined kontrolü için v-if-->
   
  </div>
    
</template>

<script>
import AppHeader from "@/components/AppHeader.vue"
import SearchUser from "./components/SearchUser.vue"
import UserInfo from "@/components/UserInfo.vue"

export default {
  components: {
    AppHeader : AppHeader,
    SearchUser : SearchUser,
    UserInfo : UserInfo,
  },
  data() {
      return {
        githubUser: null, // Başlangıçta null olarak ayarlayın
        darkMode:true,
        
      };
  },
  methods: {
    updateGitHubUser(user) {
      this.githubUser = user; // SearchUser componentinden gelen veriyi güncelleyin
    },

    toggleDarkMode() {
      this.darkMode = !this.darkMode;
    },
   

 }
}
</script>

<style >
.container{
background-color: var(--body-bg-color);
width:100%;
/*height: 100vh; */
min-height:100vh;
display:flex;
flex-direction: column;
justify-content: center;
align-items: center;

}
*{
  margin:0;
  padding:0;
}


</style>

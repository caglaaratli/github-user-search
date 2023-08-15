<template>
    <div class="search-ınfo-container">
      <div class="search">
        <div class="searchText">
          <img width="20" height="20" src="@/assets/icon-search.svg">
          <input
             v-model="searchUserInput"
              class="input-field"
              type="text"
              placeholder="Please enter here GitHub user name ... "
          />
        </div>
        <div class="btn-search">
            <button @click="searchUsers()">Search</button>
        </div>
      </div>

      <div class="userInfoContainer">
        <UserInfo v-if="githubUser" :githubUser="githubUser" :colorMode="colorMode"/> <!-- null ya da undefined kontrolü için v-if-->
      </div>

    </div> 
</template>

<script>
import axios from  'axios'
import UserInfo from "@/components/UserInfo.vue"

export default {
    data() {
      return {
      githubUser : null,
      searchUserInput :''
      }
    
    },

    components: {
      UserInfo : UserInfo,
    },


    methods : {
        async searchUsers() {
            try {
           const response = await axios.get(
              `https://api.github.com/users/${this.searchUserInput}`
            );
           this.githubUser = response.data;
           console.log(this.githubUser);
           this.searchUserInput='';
  
           } catch (error) {
            console.error(error);
            this.githubUser = null;
           }
          
        },
    },
    props: ["colorMode"],

    
}
</script>

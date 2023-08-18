<template>
      <div class="search" :class="darkMode ? 'dark' : 'light'">
        <div class="searchText" >
          <img width="20" height="20" src="@/assets/icon-search.svg">
          <input
             v-model="searchUserInput"
              class="input-field" :class="darkMode ? 'dark' : 'light'"
              type="text"
              placeholder="Enter here GitHub user name ... "
              @keydown.enter="searchUsers()"
          />
        </div>
        
        <button class="btn-search" :class="darkMode ? 'dark' : 'light'"  @click="searchUsers()">Search</button>
       
      </div>

</template>

<script>
import axios from  'axios' 


export default {
    data(){
      return{
        githubUser:null,
        searchUserInput: '',
      }
    },
    props: {
      darkMode: {
        types:Boolean,
        required:true, 
        },
  },

    methods : {
        async searchUsers() {
            try {
           const response = await axios.get(
              `https://api.github.com/users/${this.searchUserInput}`
            );
           this.githubUser = response.data;
           console.log(this.githubUser);
           this.$emit("githubUser", this.githubUser)
           this.searchUserInput='';
           
  
           } catch (error) {
            console.error(error);
            this.githubUser = null;
           }
          
        },
    },
   

    
}
</script>


<style >
.search{
  display:flex;
  justify-content: space-between;
  width:730px;
  height:60px;
  align-items: center;  
  border-radius: 15px;
  background-color: var(  --search-bg-color);
}
.searchText{
  display:flex;
  align-items: center;
  height:100%;
}

.searchText img{
  margin-left:20px;
}


.input-field{
  height:100%;
  width:500px;
  margin-left:20px;
  border:none;
  outline:none;
  font-size:18px;
  color:var(--search-color);
  background-color: var( --search-bg-color);
}

.placeholder{
  opacity:1;
  color:var(--search-color),
}

.btn-search{
  height:50px;
  width:106px;
  background-color: #0079ff ;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  color:var(--search-color) ;
  font-size:16px;
  margin-right:16px;
  cursor: pointer;
  outline:none;
  border:none;
}

@media screen and (max-width:769px) {
  .search{
    width:574px;
  }
  .input-field{
    width:400px;
  }
}

@media screen and (max-width:415px) {
  .search{
    width:327px;
    margin-left:10px;
    height:60px;
  }
  .input-field{
    width:160px;
    font-size:12px;
  }
  .searchText img{
    margin-left:15px;
  }
  .btn-search{
    width:84px;
    height:46px;
    font-size:12px;
  }
}
</style>
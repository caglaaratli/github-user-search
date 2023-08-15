<template>
  <div class="container">
    <AppHeader :colorMode="colorMode" @colorModeChanged="updateColorMode"  />
    <SearchUser :colorMode="colorMode"  ></SearchUser> 
  </div>
    
</template>

<script>
import AppHeader from "@/components/AppHeader.vue"
import SearchUser from "./components/SearchUser.vue"

export default {
  components: {
    AppHeader : AppHeader,
    SearchUser : SearchUser
  },
  data() {
    return {
      colorMode: "light",
    };
  },
  methods: {
    updateColorMode(newColorMode) {
      this.colorMode = newColorMode;
    },
  },
  
 }
</script>

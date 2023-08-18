<template>
    <div class="header">
        <div class="head" :class="darkMode ? 'dark' : 'light'" >devFinder</div>
        <div class="light-dark-mode">
          <button class="color-mode-btn" :class="darkMode ? 'dark' : 'light'" @click="toggleDarkMode" aria-label="Toogle light mode">
            {{ darkMode ? 'LIGHT' : 'DARK' }}
           <img  width="20" height="20" :src="darkMode ? require('@/assets/icon-sun.svg') : require('@/assets/icon-moon.svg')">
          </button>
          <!-- <button class="color-mode__btn dark--hidden" aria-label="Toggle dark mode">
           DARK
           <img  width="22" height="22" src="@/assets/icon-moon.svg">
          </button> -->

        </div> 
    </div>

</template>

<script>
export default {
  props: {
    darkMode: {
        types:Boolean,
        required:true, 
        },
  },
  methods: {
    toggleDarkMode() {
      this.$emit('toggle-dark-mode'); // Ana bileşene dark mode durumu değiştiğini iletiyoruz
    },
  },
};
</script>

<style >

.head{
  color:var( --head-color);
  font-weight: bold;
  font-size:26px;
}
.header{
  display:flex;
  justify-content: space-between;
  align-items: center;
  width: 730px;
  margin-bottom: 25px;
}


.color-mode-btn{
  font-size:13px;
  outline:none;
  background-color:var( --body-bg-color);
  border:none;
  cursor:pointer;
  color:var(--darklight-color);
  display: flex;
  justify-content: space-between;
  width:78px;
  align-items: center;
  

}

@media screen and (max-width:769px) {
  .header{
    width:574px;
  }

}

@media screen and (max-width:415px) {
  .header{
    width:327px;
    margin-left:10px;
    height:60px;
  }

}

</style>
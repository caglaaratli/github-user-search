<template>
    <div class="header" :class="{ dark: color-mode === 'dark', light: color-mode === 'light' }">
        <div class="head">devFinder</div>
        <div class="light-dark-mode">
          <button class="color-mode__btn light--hidden" aria-label="Toogle light mode">
           LIGHT
           <img  width="22" height="22" src="@/assets/icon-sun.svg">
          </button>
          <button class="color-mode__btn dark--hidden" aria-label="Toggle dark mode">
           DARK
           <img  width="22" height="22" src="@/assets/icon-moon.svg">
          </button>

        </div> 
    </div>

</template>

<script>
export default {
  props: ["color-mode"],
  // ...
};
</script>
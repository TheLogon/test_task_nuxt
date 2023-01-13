<template>
  <header class="header">
    <div class="header__container">
      <div class="header__inner">
        <div class="header__logo">
          <img src="@/assets/img/logo.svg" alt="" />
        </div>
        <div id="burger" :class="{ active: burger }" @click.prevent="toggle">
          <span></span>
          <span></span>
          <span></span>
        </div>
        <div id="header__menu" :class="{ active: burger }">
          <a href="#" class="header__menu_item active">About</a>
          <a href="#" class="header__menu_item">Map</a>
          <a href="#" class="header__menu_item">Zoos</a>
          <a href="#" class="header__menu_item">Donate</a>
          <a href="#" class="header__menu_item">Contact us</a>
        </div>
        <p class="header__copyright">Designed by ©</p>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      burger: false,
    };
  },
  methods: {
    toggle() {
      this.burger = !this.burger;
    },
  },
};
</script>

<style lang="scss"></style>

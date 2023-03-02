<template>
  <header class="header">
    <div class="container-sm">
      <nav class="navbar">

        <div class="navbar-brand">
          <a href="/">
            <img
                src="./img/sezam-logo.png"
                alt="sezam"
                width="144"
                height="55"
            />
          </a>
        </div>
        <button
            class="burger-menu"
            :class="{ active: showMenu }"
            @click="showMenu = !showMenu"
        >
          <span class="burger-menu__icon"/>
          <span class="burger-menu__icon"/>
          <span class="burger-menu__icon"/>
        </button>
        <div
            class="popup-menu"
            v-if="showMenu"
            :class="{ show: showMenu }"
        >
          <div class="popup-menu__link">
            <a href="#">Главная</a>
            <a href="#">Главная</a>
            <a href="#">Главная</a>
            <a href="#">Главная</a>
          </div>
          <Social />
        </div>
      </nav>
    </div>
  </header>
</template>

<style lang="scss">


.burger-menu {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 20px;
  background-color: transparent;
  border: none;
  cursor: pointer;

  &__icon {
    display: block;
    width: 100%;
    height: 3px;
    background-color: #fff;
    transition: transform 0.3s ease-in-out;

    &:first-child {
      transform-origin: top left;
    }

    &:nth-child(2) {
      width: 80%;
      margin-left: 20%;
    }

    &:last-child {
      transform-origin: bottom left;
    }
  }
}


.burger-menu.active .burger-menu__icon:first-child {
  transform: rotate(45deg);
}

.burger-menu.active .burger-menu__icon:last-child {
  transform: rotate(-45deg);
}

.burger-menu.active .burger-menu__icon:nth-child(2) {
  opacity: 0;
}

.popup-menu {
  position: fixed;
  top: 85px;
  left: 0;
  z-index: 1000;
  width: 100%;
  height: 100%;
  background-color: #fff;
  color: #000;
  transform: translateX(-100%);
  transition: transform 0.3s ease-in-out;

  &__link {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 24px;
    padding: 30px;
    position: relative;

    &::before {
      content: '';
      width: 30%;
      height: 5px;
      border-radius: 20px;
      position: absolute;
      bottom: 0;
      left: 35%;
      right: 35%;
      background: yellow;
    }
  }
}

.popup-menu.show {
  transform: translateX(0);
}

</style>


<script lang="ts">
import Social from "@/components/social/Social.vue";

export default {
  components: {Social},
  data() {
    return {
      isActive: false,
      showMenu: false,
    };
  },
};
</script>
<template>
  <b-navbar class="is-light">
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <div class="home-logo">
          <a href="">
            <h3 class="home-logo--h3">
              Quotes
            </h3>
            <p class="home-logo--p">every day</p>
          </a>
        </div>
      </b-navbar-item>
    </template>

    <template slot="end">
      <b-navbar-item tag="div">
        <DarkMode>
          <em slot="lightIcon"><img src="../../assets/images/sun.png"/></em>
          <em slot="darkIcon"><img src="../../assets/images/moon.png"/></em>
        </DarkMode>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>

<script>
import DarkMode from "vue-dark-mode-switcher";

export default {
  components: {
    DarkMode
  }
};
</script>

<style lang="scss" scoped>
.theme-dark {
  .navbar {
    background-color: $tundora;
  }

  .home-logo {
    &--p {
      color: $white;
    }
  }
}

.home-logo {
  text-align: center;

  &--h3 {
    color: $radicalRed;
    font-weight: 300;
    font-size: 50px;
    line-height: 0.65;
    font-family: "Lobster", cursive;
  }

  &--p {
    font-size: 14px;
    margin-left: 50px;
    color: $emperor;
    font-weight: 400;
    text-transform: capitalize;
    font-style: italic;
    font-family: "Mansalva", cursive;
  }
}
</style>

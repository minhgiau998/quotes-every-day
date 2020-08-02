<template>
  <section class="hero is-fullheight-with-navbar">
    <div class="hero-body">
      <nuxt keep-alive />
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
.hero.is-fullheight-with-navbar {
  min-height: calc(100vh - 68.8px);
}
</style>

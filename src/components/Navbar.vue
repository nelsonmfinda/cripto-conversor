<template>
  <nav class="navbar is-black">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <img
          src="https://bulma.io/images/bulma-logo-white.png"
          alt="Bulma: a modern CSS framework based on Flexbox"
          width="112"
          height="28"
        />
      </a>
      <div class="navbar-burger burger" data-target="navMenuColorblack-example">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>

    <div id="navMenuColorblack-example" class="navbar-menu">
      <div class="navbar-end">
        <a class="navbar-item" href="https://bulma.io/">Login</a>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  props: {}
};
</script>

<style scoped>
</style>
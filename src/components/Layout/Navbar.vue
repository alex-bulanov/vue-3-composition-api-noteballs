<script setup lang="ts">
import { ref } from 'vue'

const showMobileNav = ref<boolean>(false)
</script>

<template>
  <nav class="navbar is-success" role="navigation" aria-label="main navigation">
    <div class="container px-4">
      <div class="navbar-brand">
        <RouterLink class="navbar-item is-size-3 is-family-code has-text-weight-semibold" to="/"
          >Noteballs</RouterLink
        >

        <a
          role="button"
          class="navbar-burger"
          :class="{ 'is-active': showMobileNav }"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbarBasicExample"
          @click.prevent="showMobileNav = !showMobileNav"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu" :class="{ 'is-active': showMobileNav }">
        <div class="navbar-end">
          <RouterLink class="navbar-item" active-class="is-active" to="/"> Заметки </RouterLink>
          <RouterLink class="navbar-item" active-class="is-active" to="stats">
            Статистика
          </RouterLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<style lang="scss">
.navbar-menu {
  @media screen and (max-width: 1023px) {
    position: absolute;
    left: 0;
    width: 100%;
  }
}
</style>

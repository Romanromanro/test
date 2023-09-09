<template>
  <nav class="navbar is-success"
       role="navigation"
       aria-label="main navigation">
    <div class="container is-max-desktop px-2">
      <div class="navbar-brand">
        <div class="navbar-item is-size-4 is-family-monospace">
          Noteballs
        </div>
        <a
            @click.prevent="showMobileNav = !showMobileNav"
            role="button"
            class="navbar-burger"
            :class="{'is-active': showMobileNav}"
            aria-label="menu"
            aria-expanded="false"
            data-target="navbarBasicExample"
            ref="navBarmBurgerRef">
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="navbarBasicExample"
           class="navbar-menu"
           :class="{'is-active': showMobileNav}"
      ref="navBarmenuBar">
        <div class="navbar-end">
          <RouterLink
              @click="showMobileNav = false"
              class="navbar-item is-active"
              to="/"
              active-class="is-active">
            Notes
          </RouterLink>
          <RouterLink
              @click="showMobileNav = false"
              class="navbar-item"
              to="/stats"
              active-class="is-active">
            Stats
          </RouterLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
/*
import
*/

import {ref} from 'vue'
import { onClickOutside } from '@vueuse/core'
/*
  mobile nav
*/
const showMobileNav = ref(null)
const navBarmenuBar = ref(null)
const navBarmBurgerRef = ref(false);
onClickOutside(navBarmenuBar, () => {
  showMobileNav.value = false
},{
  ignore: [navBarmBurgerRef]
})
</script>

<style scoped>
@media (max-width: 1023px) {
  .navbar-menu {
    position: absolute;
    left: 0;
    width:100%
  }
}
</style>
<script setup lang="ts">
import NavHamburgerMenu from '@/components/NavHamburgerMenu.vue'
import NavList from '@/components/NavList.vue'
import { onMounted, onUnmounted } from 'vue'

const hamburgerToggle = () => {
  let nav_lists = document.getElementById('nav-list');
  let opaque_bg = document.getElementById('opaque_bg');

  let get_css_prop = getComputedStyle(nav_lists);
  let right = get_css_prop.getPropertyValue("right");

  // slide out the bg color if nav bar was previously hidden, else hide
  opaque_bg.style["left"] = ( right === "-200px" ) ? "0" : "-130vw";
  // slide out the nav-menu items if right was previously hidden, else hide
  nav_lists.style["right"] = ( right === "-200px" ) ? "0px" : "-200px";
}

// the #nav-list CSS right: property hangs on its javascript assigned value 
// after switching back to desktop view. So we need to correct this
// Get screen width as adjustment is being made
const canvasResize = () => {
  // Get realtime screen width as it is being resized
  let current_screen_width = window.innerWidth;

  if ( current_screen_width >= 700 ) {
    document.getElementById('nav-list').style["right"] = "0px";
	document.getElementById('opaque_bg').style["left"] = "-130vw";
  }

}
// Attaching the event listener function for window's resize
// window.addEventListener("resize", canvasResize);

// when this component is loaded
onMounted(() => {
  window.addEventListener("resize", canvasResize);
})

// when this component is droped
onUnmounted(() => {
  window.removeEventListener("resize", canvasResize);
})

</script>

<template>
  <nav>
    <div class="hamburger" @click="hamburgerToggle">
      <NavHamburgerMenu />
    </div>
    <div id="nav-list">
    <NavList />
    </div>
    <div id="opaque_bg" @resize="canvasResize()" ></div>
  </nav>
</template>

<style scoped>
nav {
  position: relative;
}

#opaque_bg {
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.7);
  position: fixed;
  top: 0;
  left: -130vw;
  z-index: 1;
  transition: left 0.2s;
}

.hamburger {
  display: block;
  width: 40px;
  height: 20px;
  position: fixed;
  top: var(--max-vertical-margin);
  right: var(--moderate-horizontal-margin);
  z-index: 3;
}

#nav-list {
  display: block;
  position: fixed;
  top: var(--max-vertical-margin);
  right: -200px;
  z-index: 2;
  transition: right 0.3s;
}


@media (min-width: 700px) {
  .hamburger {
    display: none;
  }

  #nav-list {
    position: relative;
    top: 0;
    right: 0;
  }

  #opaque_bg {
	display: none;
  }

}
</style>

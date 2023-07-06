<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Introduction	from '@/components/Introduction.vue'
import SocialIcon from '@/components/SocialIcon.vue'
import HamburgerMenu from '@/components/HamburgerMenu.vue'
import NavList from '@/components/NavList.vue'

// **********************************************
// HEADER SCRIPTS START							*
// **********************************************
const hamburgerToggle = () => {
	let nav_lists = document.getElementById('nav-list');

	let get_css_prop = getComputedStyle(nav_lists);
	let right = get_css_prop.getPropertyValue("right");

	nav_lists.style["right"] = ( right === "-200px" ) ? "var(--moderate-horizontal-margin)" : "-200px";
}

// the #nav-list CSS right: property hangs on its javascript assigned value 
// after switching back to desktop view. So we need to correct this
// Get screen width as adjustment is being made
const canvasResize = () => {
	// Get realtime screen width as it is being resized
	let current_screen_width = document.body.clientWidth;

	if ( current_screen_width >= 1024 ){
		document.getElementById('nav-list').style["right"] = "";
	}

}
// Attaching the event listener function for window's resize
window.addEventListener("resize", canvasResize);

// **********************************************
// HEADER SCRIPTS ENDS							*
// **********************************************
</script>

<template>
  <header>
	<Introduction name="Daniel E. Uyi" />
	<SocialIcon />
	<!-- Continue with styling the header bg. Then add SPA links -->
	<nav>
	  <div class="hamburger" @click="hamburgerToggle">
	  	<HamburgerMenu />
	  </div>
	  <div id="nav-list" @click="canvasResize">
		<NavList />
	  </div>

	</nav>

  </header>

</template>

<style scoped>
/****************************/
/* HEADER STYLES STARTS 	*/
/****************************/
header {
	margin: 2vh 0;
}

nav {
  position: relative;
}

.hamburger {
  display: block;
  position: fixed;
  top: var(--max-vertical-margin);
  right: var(--moderate-horizontal-margin);
  z-index: 2;
}

#nav-list {
  display: block;
  position: fixed;
  top: var(--max-vertical-margin);
  right: -200px;
  z-index: 1;
  transition: right 1s;
}


@media (min-width: 1024px) {
  .hamburger {
    display: none;
  }

  #nav-list {
	position: relative;
	top: 0;
	right: 0;
  }

}
/************************/
/* HEADER STYLES ENDS 	*/
/************************/
</style>

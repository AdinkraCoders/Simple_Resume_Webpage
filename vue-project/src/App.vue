<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Introduction  from '@/components/Introduction.vue'
import SocialIcon from '@/components/SocialIcon.vue'
import NavBuilder from '@/components/NavBuilder.vue'
import SlideShow from '@/components/SlideShow.vue'
</script>

<template>
  <header>
	<Introduction name="Daniel E. Uyi" />
	<SocialIcon />
	<NavBuilder />
  </header>
  <article>
	<SlideShow />
  </article>
  <footer>
	  Designed with ❤️ by Daniel Uyi for 42 Schools Inception Project.
  </footer>

</template>

<style scoped>
header {
  margin: 0;

}

footer {
  text-align: center;
  background-color: var(--color-bg-shade1);
}

@media (min-width: 700px) {
  header {
    grid-row: 1;
    grid-column: 1;
  }

  article {
    grid-row: 1;
    grid-column: 2;
  }

  footer {
    grid-row: 2;
    grid-column: 1/3;
  }
}
</style>

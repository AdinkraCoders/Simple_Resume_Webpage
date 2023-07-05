<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Introduction	from '@/components/Introduction.vue'
import SocialIcon from '@/components/SocialIcon.vue'
</script>

<template>
  <header>
	<Introduction name="Daniel E. Uyi" />
	<SocialIcon />
	<!-- Continue with styling the header bg. Then add SPA links -->

  </header>

</template>

<style scoped>
header {
	margin: 2vh 0;
}
</style>

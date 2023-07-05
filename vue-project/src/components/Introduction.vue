<script setup lang="ts">
  defineProps<{
  	name: string,
  }>()
</script>

<template>
  <img class="logo" src="@/assets/images/profile.png" />
  <span class="owner-name">{{ name }}</span>
</template>

<style scoped>
.logo {
	display: block;
	height: 179px;
	width: 179px;
	margin: var(--max-vertical-margin) auto var(--moderate-vertical-margin);
}

.owner-name {
	display: block;
	color: #49515a;
    font-size: 2rem;
	font-family: 'Montserrat', sans-serif;
    font-weight: 700;
	text-align: center;
}
</style>

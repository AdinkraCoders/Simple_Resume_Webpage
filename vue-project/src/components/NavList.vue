<script setup lang="ts">
  import { RouterLink } from 'vue-router'
</script>

<template>
  <ul>
	<li><RouterLink to="/">Home</RouterLink></li>
	<li><RouterLink to="/about">About</RouterLink></li>
	<li><RouterLink to="/skills">Skills</RouterLink></li>
	<li><RouterLink to="/contact">Contact</RouterLink></li>
  </ul>
</template>

<style scoped>
ul {
  display: block;
  position: relative;
  top: 0;
  width: 200px;
  list-style-type: none;
  margin: 0;
  padding: 0 ;
}

ul > li:nth-of-type(odd) {
  background-color: var(--color-bg-shade1);
}

ul > li:nth-of-type(even) {
  background-color: var(--color-bg-shade0);
}

ul > li {
  border-bottom: 1px solid rgb(221,221,221);
  padding: 6px 8px;
  letter-spacing: 0.05em;
  transition: padding 0.5s;
  cursor: pointer;
}

ul > li > a {
  text-decoration-line: none;
}

ul > li:hover {
	padding-left: 4px;
}

ul > li:first-child {
	border-top-left-radius: 0;
	padding-top: 5vh;
}
ul > li:last-child {
	border-top-right-radius: 0;
	padding-bottom: 90vh;
}

@media (min-width: 700px) {
  ul {
    display: block;
	position: relative;
	top: 0;
	width: 100%;
	text-align: center;
  }

  ul > li {
	display: inline-block;
	position: relative;
	width: 25%;
	margin: 0;
	padding: 5px 0;
  }

  ul > li:first-child {
	border-top-left-radius: 15px;
	padding-top: 0;
  }

  ul > li:last-child {
	border-top-right-radius: 15px;
	padding-bottom: 0;
  }
}
</style>

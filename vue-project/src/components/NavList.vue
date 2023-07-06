<template>
  <ul>
	<li>Home</li>
	<li>About</li>
	<li>Skills</li>
	<li>Contact</li>
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
  padding: 0;
  transition: 0.5s;
}

ul > li:nth-of-type(odd) {
  background-color: var(--color-bg-shade1-light-mode);
}

ul > li:nth-of-type(even) {
  background-color: var(--color-bg-shade0-light-mode);
}

ul > li {
  border-bottom: 1px solid rgb(221,221,221);
  padding: 6px;
  letter-spacing: 0.05em;
  transition: 0.5s;
}

ul > li:hover {
	padding-left: 4px;
}

ul > li:first-child {
	border-top-left-radius: 15px;
}
ul > li:last-child {
	border-bottom-left-radius: 15px;
}

@media (min-width: 1024px) {
  ul {
    display: block;
	position: relative;
	top: 0;
	width: 100vw;
	text-align: center;
  }

  ul > li {
	display:inline-block;
	position:relative;
	background-color:#4c4c4c;
	width: 10%;
	margin: 0;
	padding: 5px 0;
	transition: 0.5s;
  }

  ul > li:last-child {
	border-top-right-radius: 15px;
	border-bottom-left-radius: 0;
  }
}
</style>

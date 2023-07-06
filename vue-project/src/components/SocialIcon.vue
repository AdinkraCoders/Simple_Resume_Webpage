<template>
  <ul>
	<li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/twitter_color.svg" alt="Twitter" title="Twitter" /></a></li>
	<li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/linkedin_color.svg" alt="Linkedin" title="Linkedin" /></a></li>
	<li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/github_color.svg" alt="Github" title="Github" /></a></li>
	<li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/google_color.svg" alt="Google" title="Google" /></a></li>
  </ul>
</template>

<style scoped>
ul {
  display: block;
  height: 40px;
  overflow: hidden;
  margin: var(--moderate-vertical-margin) 0;
  list-style-type: none;
  padding: 0;
  text-align: center;

}

ul img {
  padding: 5px;
  border-radius: 10px;
  background-color: var(--color-bg-shade1);
  width: 36px;
  height: 36px;
  transition: width 0.5s, height 0.5s;
}

ul li {
  display: inline-block;
  height: 36px;
  width: 36px;
  overflow: hidden;
  margin: 0 2px;
}

ul img:hover {
  width: 40px;
  height: 40px;
}
</style>

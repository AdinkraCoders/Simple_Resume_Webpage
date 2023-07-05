<template>
  <ul class="social-icon">
    <li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/twitter_color.svg" alt="Twitter" title="Twitter" /></a></li>
    <li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/linkedin_color.svg" alt="Linkedin" title="Linkedin" /></a></li>
    <li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/github_color.svg" alt="Github" title="Github" /></a></li>
    <li><a href="#"><img src="https://raw.githubusercontent.com/LeCoupa/vuesocial/master/assets/networks/google_color.svg" alt="Google" title="Google" /></a></li>
  </ul>
</template>

<style scoped>
ul.social-icon {
	margin: var(--moderate-vertical-margin) 0;
	list-style-type: none;
    padding: 0;
	text-align: center;
}

ul.social-icon img {
	padding: 5px;
    border-radius: 10px;
    background-color: #d8dde4;
    width: 36px;
    height: 36px;
	transition: width 0.5s, height 0.5s;
}

ul.social-icon li {
	display: inline-block;
	margin: 0 2px;
}

ul.social-icon img:hover {
    width: 37px;
    height: 37px;
}
</style>

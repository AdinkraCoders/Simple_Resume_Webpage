<script setup lang="ts">
  const descriptionToggle = (idName : string) => {
	const editId = document.getElementById(idName);
	const visibility = getComputedStyle(editId).getPropertyValue("display");
	const rotateSvg = document.getElementById(idName + '_svg');
	  if ( visibility == "none" ) {
		editId.style["display"] = "block";
		rotateSvg.style["transform"] = "rotate(90deg)";
	  }
	  else {
		editId.style["display"] = "none";
		rotateSvg.style["transform"] = "rotate(0deg)";
	  }
  }
</script>

<template>
  	<div id="description">
	  <button class="desc_button" @click="descriptionToggle('details')"><svg id="details_svg" fill="none" viewBox="0 0 16 16" width="12" height="12"><path fill="#000" fill-rule="evenodd" d="M5 2v12l6-6.001L5 2Z" clip-rule="evenodd"></path></svg> Details</button>
	  <span id="details"> helo, wie geht's dir?</span>
	  <button class="desc_button" @click="descriptionToggle('reviews')"><svg id="reviews_svg" fill="none" viewBox="0 0 16 16" width="12" height="12"><path fill="#000" fill-rule="evenodd" d="M5 2v12l6-6.001L5 2Z" clip-rule="evenodd"></path></svg> Reviews</button>
	  <span id="reviews"> helo, wie geht's dir?</span>
	</div>
</template>

<style scoped>
#description {
  margin: 10px auto;
}
.desc_button {
  display: block;
  width: 100%;
  border: none;
  background-color: var(--color-bg-shade1);
  padding: 5px 2px;
  font-size: 1rem;
  cursor: pointer;
  text-align: left;
  transition: background-color 0.5s;
}
.desc_button:hover {
  background-color: var(--color-bg-shade0);
}

#details, #reviews {
  display: none;
  width: 100%;
  border: none;
  padding: 0 4px 30px 22px;
  font-size: 0.9rem;
  text-align: left;
  transition: display 0.5s;
}

#details_svg, #reviews_svg {
  transition: transform 0.3s;
}
</style>

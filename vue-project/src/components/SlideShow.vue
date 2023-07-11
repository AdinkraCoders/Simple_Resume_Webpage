<script setup lang="ts">
  import { onMounted, onUnmounted } from 'vue'
  import SlideDescription from '@/components/SlideDescription.vue'

  // ********************************************************************
  // 						Globals Start								*
  // ********************************************************************
  let g_slideItem;	// For storing document.getElementById('slide-items') on mousedown
  let g_backupLeft; // For backing up initial value of #slide-items.left before the mousedown event
  let g_sliderWidth;// For holding size of slider width where slides are displayed
  let g_minLeft;	// For holding lowest possible value of #slide-items.left determined by number of slides * g_sliderWidth

  let g_pressed = false; 	// temporarily set to true when mouse is held down
  let g_startX;			// For catching starting position of mousedown event on x-axis

  let g_currentLeft = 0;	// For storing current value of #slide-items.left during drag event

  //1. get starting left position of #slide-items and save to g_backupLeft global var
  //2. calc width of window where #slide-items are displayed and save to g_sliderWidth global var
  //3. calc lowest possible valid value of #slide-items.left and save to g_minLeft global var
  const initialBackups = () => {
	//1.
	g_slideItem = document.getElementById('slide-items');
	const leftTmp = getComputedStyle(g_slideItem).getPropertyValue("left");
	g_backupLeft = parseInt(leftTmp);

	//2.
	let windowTmp = document.getElementById('slider-window');
	windowTmp = getComputedStyle(windowTmp).getPropertyValue("width");
	g_sliderWidth = parseInt(windowTmp);

	//3.
	const slideCount = document.getElementsByClassName('one-slide').length;
	g_minLeft = g_sliderWidth * (slideCount - 1) * -1;
  }

  const resetBackups = () => {
	// reset necessary global vars
	g_pressed = false;
  	g_startX = null;
	g_backupLeft = null;
	g_currentLeft = 0;
  	g_slideItem = null;
	g_sliderWidth = null;
	g_minLeft = null;
  }
  
  // ********************************************************************
  // 						Globals Ends								*
  // ********************************************************************
  // ********************************************************************
  // 						Drag to slide Start							*
  // ********************************************************************
  const mouseDown = (event) => {
	initialBackups();

    g_pressed = true;
    g_startX = event.offsetX;
  }

  const mouseMove = (event) => {
	if ( g_pressed == false )
	  return;

	//necessary for holding on to mousemove event while mousedown event is also active
	event.preventDefault();

	// #slide-items.left cannot be greater than 0px or less than the last image slide
	const diff = event.offsetX - g_startX;
	if ( ((g_backupLeft + diff) > 0) || ((g_backupLeft + diff) < g_minLeft) )
	  return;

	// change #slide-items.left according to mouse x-axis movement
	g_currentLeft = g_backupLeft + diff;
	g_slideItem.style["left"] = g_currentLeft + "px";
  }

  const mouseUp = (event) => {
	if ( g_pressed != true )
	  return;

	// set #slide-items.left to proper value if a drag occured
	if ( g_currentLeft  && g_currentLeft != g_backupLeft ) {
	  const roundUpLeft = g_currentLeft % g_sliderWidth;
	  const roundDownLeft = g_sliderWidth + roundUpLeft;

	  if ( g_currentLeft > g_backupLeft )
		g_slideItem.style["left"] = (g_currentLeft - roundUpLeft) + "px"; // drag to right
	  else
		g_slideItem.style["left"] = (g_currentLeft - roundDownLeft) + "px"; // drag to left
	}

	resetBackups();
  }
  // ********************************************************************
  // 						Drag to slide Ends							*
  // ********************************************************************
  // ********************************************************************
  // 				left and right click to slide starts				*
  // ********************************************************************
  const slideLeft = () => {
	initialBackups();

	if ( ((g_backupLeft + g_sliderWidth) > 0) ) {
	  resetBackups();
	  return false;
	}
	
	g_slideItem.style["left"] = (g_backupLeft + g_sliderWidth)+ "px";
	resetBackups();
	return true;
  }

  const slideRight = () => {
	initialBackups();

	if ( ((g_backupLeft - g_sliderWidth) < g_minLeft) ) {
	  resetBackups();
	  return false;
	}

	g_slideItem.style["left"] = g_backupLeft - g_sliderWidth + "px";
	resetBackups();
	return true;
  }
  // ********************************************************************
  // 				left and right click to slide ends					*
  // ********************************************************************
  // ********************************************************************
  // 				Reset slides onResize Starts						*
  // ********************************************************************
  const slideResize = () => {
	initialBackups();
	g_slideItem.style["left"] = 0;
	resetBackups();
  }
  // ********************************************************************
  // 				Reset slides onResize Ends							*
  // ********************************************************************
  // ********************************************************************
  // 				Automatically show slides starts					*
  // ********************************************************************
  let g_flag = true;

  const displaySlides = () => {
	if ( g_flag )
	  if ( ! slideLeft() )
	    g_flag = false;

	if ( ! g_flag )
	  if ( ! slideRight() )
	    g_flag = true;
  }
  // ********************************************************************
  // 				Automatically show slides Ends						*
  // ********************************************************************
  // ********************************************************************
  // 				Event Listeners and Intervals Start					*
  // ********************************************************************
  let g_intervalId;
  // when this component is loaded into DOM
  onMounted(() => {
	// So that #slide-items.left is reset to 0 on screen resize
	window.addEventListener("resize", slideResize);

    // So that #slide-items.left is auto-changed every 5 seconds
	g_intervalId = setInterval(displaySlides, 5000);
  })

  // when this component is droped from DOM
  onUnmounted(() => {
    window.removeEventListener("resize", slideResize);

	clearInterval(g_intervalId);
  })
  // ********************************************************************
  // 				Event Listeners and Intervals Ends					*
  // ********************************************************************
</script>

<template>
  <div id="advert_box">
	<div id="slider-window" @mousedown="(event) => mouseDown(event)" @mousemove="(event) => mouseMove(event)" @mouseup="(event) => mouseUp(event)" @mouseleave="(event) => mouseUp(event)" @resize="slideResize">
  	  <div id="slide-items">
		<img class="one-slide" src="@/assets/images/1.jpg" />
	  	<img class="one-slide" src="@/assets/images/2.jpg" />
	  	<img class="one-slide" src="@/assets/images/3.jpg" />
		<img class="one-slide" src="@/assets/images/4.jpg" />
	  	<img class="one-slide" src="@/assets/images/1.jpg" />
	  	<img class="one-slide" src="@/assets/images/2.jpg" />
	  	<img class="one-slide" src="@/assets/images/3.jpg" />
		<img class="one-slide" src="@/assets/images/4.jpg" />
	  </div>
	  <button class="slide-left" @click="slideLeft">&#10094;</button>
	  <button class="slide-right" @click="slideRight">&#10095;</button>
    </div>
	
	<SlideDescription />
  </div>

</template>

<style scoped>
#slider-window {
  display: block;
  border-radius: 10px;
  width: calc(50vw - 8rem);
  aspect-ratio: 2 / 3;
  margin: 0 auto;
  overflow: hidden;
  position: relative;
}
#slide-items {
  display: block;
  position: relative;
  top: 0;
  left: 0;
  width: 5000px; /* must be greater than sum of width of all images in the slides */
  height: auto;
  transition: left 0.2s;
}
#slide-items > img {
  display: inline-block;
  width: calc(50vw - 8rem);
  aspect-ratio: 2 / 3;
}

.slide-left {
  position: absolute;
  top: 50%;
  left: 0%;
  transform: translate(-0%,-50%);
  -ms-transform: translate(-0%,-50%);
}
.slide-right {
  position: absolute;
  top: 50%;
  right: 0%;
  transform: translate(-0%,-50%);
  -ms-transform: translate(-0%,-50%);
}
.slide-left, .slide-right {
  border-radius: 10px;
  border: none;
  display: inline-block;
  text-decoration: none;
  text-align: center;
  cursor: pointer;
  color: #fff!important;
  background-color: #000!important;
}
.slide-left:hover, .slide-right:hover {
  color: #000!important;
  background-color: #fff!important;
}

@media (min-width: 700px) {
  #slider-window {
	width: calc(25vw - 4rem);
  }

  #slide-items > img {
    width: calc(25vw - 4rem);
  }
}

</style>


<template>
  <span class="icon-bars"></span>
  <span class="icon-bars overlay"></span>
</template>

<style scoped>
.icon-bars {
  display: block;
  position: relative;
  left: 0;
  top: 0px;
  margin: 0;
  height: 3px;
  width: 40px;
  background: rgb(13, 26, 38);
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.icon-bars::before {
  content: '';
  display: block;
  position: relative;
  left: 0;
  top: 6px;
  margin: 0;
  height: 3px;
  width: 40px;
  background: rgb(13, 26, 38);
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.icon-bars::after {
  content: '';
  display: block;
  position: relative;
  left: 0;
  top: 9px;
  margin: 0;
  height: 3px;
  width: 40px;
  background: rgb(13, 26, 38);
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.icon-bars.overlay {
  position: relative;
  top: -3px;
  background: rgb(97, 114, 129);
  background: rgb(183, 199, 211);
  animation: middleBar 3s infinite 0.5s;
  -webkit-animation: middleBar 3s infinite 0.5s;
} @keyframes middleBar {
    0% {width: 0px}
    50% {width: 40px}
    100% {width: 0px}
  } @-webkit-keyframes middleBar {
	  0% {width: 0px}
	  50% {width: 40px}
	  100% {width: 0px}
    }

.icon-bars.overlay::before {
  background: rgb(97, 114, 129);
  background: rgb(183, 199, 211);
  animation: topBar 3s infinite 0.2s;
  -webkit-animation: topBar 3s infinite 0.2s;
	} @keyframes topBar {
    0% {width: 0px}
    50% {width: 40px}
    100% {width: 0px}
  } @-webkit-keyframes topBar {
	  0% {width: 0px}
	  50% {width: 40px}
	  100% {width: 0px}
    }

.icon-bars.overlay::after {
  background: rgb(97, 114, 129);
  background: rgb(183, 199, 211);
  animation: bottomBar 3s infinite 1s;
  -webkit-animation: bottomBar 3s infinite 1s;
	} @keyframes bottomBar {
    0% {width: 0px}
    50% {width: 40px}
    100% {width: 0px}
  } @-webkit-keyframes bottomBar {
	  0% {width: 0px}
	  50% {width: 40px}
	  100% {width: 0px}
    }

</style>

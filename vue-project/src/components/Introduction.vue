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
  font-size: 2rem;
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  text-align: center;

  color: transparent;
  --metal-tex: url(https://images.unsplash.com/photo-1501166222995-ff31c7e93cef?crop=entropy&cs=tinysrgb&fm=jpg&ixid=MnwzMjM4NDZ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2NTcyMDc2NzU&ixlib=rb-1.2.1&q=80);
  background-image: var(--metal-tex);
  background-size: cover;
  background-clip: text;
  -webkit-background-clip: text;
}
</style>

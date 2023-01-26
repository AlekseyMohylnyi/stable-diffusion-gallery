<template>
  <Navigation />
  <router-view />
</template>

<script>
import Navigation from "@/components/Navigation.vue";

export default {
  name: "App",
  components: {
    Navigation,
  },
};
</script>

<style>
:root {
  --black: #000000;
  --white: #ffffff;
  --accent: tomato;
  --grey: rgba(37, 37, 38, 0.5);

  --main-color: var(--black);
  --bg-color: var(--white);
  --nav-btn-bg: inherit;

  --nav-height: 3.2rem;

  --transition: 250ms ease-out;
  --transition-long: 500ms ease-out;
}

@import url("https://fonts.googleapis.com/css2?family=Lobster&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  padding-top: var(--nav-height);
  min-height: 100vh;
  /* background-color: var(--bg-color); */
  color: var(--main-color);
  font-family: "Lobster", cursive;
  font-size: 18px;
  font-weight: 400;  
}
</style>

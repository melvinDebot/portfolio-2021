<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800;900&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}
:root {
  --white-color: #f4f4f4;
  --light-color: #f4f4fc;
  --black-color: #141414;
  --green-color: #16bf15;
}
body {
  background: var(--white-color);
  color: var(--black-color);
  transition: all 0.5s ease-in-out;
}
.dark-mode {
  background: var(--black-color);
  color: var(--white-color);
  transition: all 0.5s ease-in-out;
}
.dark-mode,
span {
  border: 1px solid var(--white-color);
}

[data-theme="dark"] {
  --white-color: black;
  --black-color: white;
  --green-color: #1c542c;
  --light-color: #3f3f43;
}
[data-theme="light"] {
  --white-color: white;
  --black-color: black;
  --green-color: #16bf15;
  --light-color: #f4f4fc;
}

.flex {
  display: flex;
  justify-content: center;
  align-items: center;
}
.gsap-marker-scroller-end {
  display: none;
}
.flex--col {
  flex-direction: column;
}

.display {
  border: 1px solid red;
}

/* #nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
} */
</style>

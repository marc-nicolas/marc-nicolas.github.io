<template>
  <div id="app">
    <div class="shape-blob"></div>
    <div class="shape-blob one"></div>
    <div class="shape-blob two"></div>

    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">Über mich</router-link>
      <router-link to="/projects">Projekte</router-link>
      <router-link to="/skills">Kenntnisse</router-link>
      <router-link to="/contact">Kontakt</router-link>
    </nav>

    <transition name="fade" mode="out-in">
      <router-view class="view" />
    </transition>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {};
  },
};
</script>

<style lang="scss" >
@import "@/main.scss";

@import url("https://fonts.googleapis.com/css2?family=Arvo:ital,wght@0,400;0,700;1,400;1,700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

.shape-blob {
  z-index: 0;
  background: #ed1250;
  height: 200px;
  width: 200px;
  border-radius: 30% 50% 20% 40%;
  animation: transform 20s ease-in-out infinite both alternate,
    movement_one 40s ease-in-out infinite both;
  opacity: 0.7;
  position: absolute;
  left: 90%;
  top: 50%;
}
.shape-blob.one {
  height: 500px;
  width: 500px;
  left: -200px;
  top: -150px;
  transform: rotate(-180deg);
  animation: transform 30s ease-in-out infinite both alternate,
    movement_two 60s ease-in-out infinite both;
}

.shape-blob.two {
  height: 350px;
  width: 350px;
  left: 500px;
  top: -150px;
  transform: rotate(-180deg);
  animation: transform 30s ease-in-out infinite both alternate,
    movement_two 60s ease-in-out infinite both;
}

@keyframes transform {
  0%,
  100% {
    border-radius: 33% 67% 70% 30% / 30% 30% 70% 70%;
  }
  20% {
    border-radius: 37% 63% 51% 49% / 37% 65% 35% 63%;
  }
  40% {
    border-radius: 36% 64% 64% 36% / 64% 48% 52% 36%;
  }
  60% {
    border-radius: 37% 63% 51% 49% / 30% 30% 70% 70%;
  }
  80% {
    border-radius: 40% 60% 42% 58% / 41% 51% 49% 59%;
  }
}

@keyframes movement_one {
  0%,
  100% {
    transform: none;
  }
  50% {
    transform: translate(50%, 20%) rotateY(10deg) scale(1.2);
  }
}

@keyframes movement_two {
  0%,
  500% {
    transform: none;
  }
  50% {
    transform: translate(50%, 20%) rotate(-200deg) scale(1.2);
  }
}
$main-padding: 80px;
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  background: #101112;
  height: 100%;
}
html {
  height: 100%;
}

nav {
  display: flex;
  flex-direction: column;
  font-size: 80px;
  text-transform: uppercase;
  justify-content: center;
  position: relative;
  min-width: 600px;

  a {
    text-decoration: none;
    color: #ffffff;
    opacity: 0.25;
    line-height: 120px;
    transition: 0.2s;

    &:hover {
      color: #ffffff;
      opacity: 0.5;
    }
    &.router-link-exact-active {
      font-size: 85px;
      opacity: 1;
    }
  }
}

#app {
  font-family: "Rubik", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

  height: 100%;
  display: flex;
  flex-direction: row;
  padding: 0 $main-padding;
  overflow: hidden;
}

.view {
  overflow-clip-margin: 100px;
  flex-grow: 1;
  overflow: clip;
  z-index: 100;
  overflow-y: scroll;
  max-height: 100%;
  min-height: 100%;

  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.fade-enter-active,
.fade-leave-active {
  transition: 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

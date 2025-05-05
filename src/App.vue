<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import IssueButtonIcon from './components/IssueButtonIcon.vue'

import { ref } from 'vue'

const showIframe = ref(false)
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
      {{ showIframe }}
    </div>
  </header>
  <div class="demo-fixed-button-wrapper">
    <button class="demo-fixed-button" @click="showIframe = !showIframe">
      <IssueButtonIcon class="icon" />
    </button>
    <Transition name="slide-fade">
      <div class="demo-iframe-container" v-if="showIframe">
        <iframe src="https://issue-management-system-dev.crepowerful-develop.com/login" />
      </div>
    </Transition>
  </div>
  <RouterView />
</template>

<style scoped lang="scss">
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
.demo-fixed-button-wrapper {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 1000;
}

.demo-fixed-button {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  color: #fff;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  background: #fff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);

  .icon {
    color: #FAA;
    transition: all 0.3s ease;
  }
}

.demo-fixed-button:hover {
  transform: scale(1.1);

  .icon {
    color: #F88
  }
}

.demo-iframe-container {
  position: absolute;
  transform: translateY(-100%);
  top: -20px;
  right: 0;
  width: 400px;
  height: 600px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  overflow: hidden;


  iframe {
    width: 100%;
    height: 100%;
    border: none;
  }
}

// 動畫效果
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  opacity: 0;
}
</style>

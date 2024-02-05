<script setup lang="ts">
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'

const lemonLoaded = ref(false)

async function loadLemon() {
  if (lemonLoaded.value) return;

  return new Promise((resolve) => {
    const script = document.createElement("script");
    script.src = "https://app.lemonsqueezy.com/js/lemon.js";
    script.defer = true;
    script.onload = () => {
      lemonLoaded.value = true
      resolve(true);
    };
    document.body.appendChild(script);
  });
}

loadLemon()
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <!-- <TheWelcome /> -->
    <a class="lemonsqueezy-button" href="https://store.amazonus.app/checkout/custom/ae1d198f-ab92-4ab5-8766-191e88eb3f24?signature=03e6052c15cdd240b0f9f298b83a62f9f94d1ab6d57f322037eb01d6ee07c76c">
        Click To Buy My Product - from Lemon Squeezy
    </a>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
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
}
</style>

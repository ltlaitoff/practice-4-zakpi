<script setup>
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
import mainImage from '../../img/ph1.jpg'

function onClick(e) {
	const target = e.target
	const { width: currentWidht, height: currentHeight } =
		target.getBoundingClientRect()

	target.style.width = `${
		currentWidht >= 800 ? currentWidht - 100 : currentWidht + 50
	}px`

	target.style.height = `${
		currentHeight >= 500 ? currentHeight - 100 : currentHeight + 50
	}px`
}

</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
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

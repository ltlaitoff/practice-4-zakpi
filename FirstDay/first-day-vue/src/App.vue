<script setup>


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

</template>

<style scoped></style>

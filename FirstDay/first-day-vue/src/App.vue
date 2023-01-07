<script setup>
import { ref } from 'vue'
import image from './assets/images/image.jpg'

const currentSelectedId = ref(null)

const onMouseEnter = id => {
	currentSelectedId.value = id
}

const onMouseLeave = () => {
	currentSelectedId.value = null
}

function onClick(e) {
	const target = e.target

	const { width: currentWidht, height: currentHeight } =
		target.getBoundingClientRect()

	target.style.width = `${
		currentWidht >= 800 ? currentWidht - 50 : currentWidht + 100
	}px`

	target.style.height = `${
		currentHeight >= 500 ? currentHeight - 100 : currentHeight + 50
	}px`
}
</script>

<template>
	<div class="task">
		<div class="task-title">
			Завдання 3
			<span class="task-score">(2 бали)</span>
		</div>
		<div class="task-description">
			Додайте в документ 300-400 блоків div квадратної форми з розмірами сторін
			30px, і кольором фону Додавання елементів виконайте за допомогою циклу.
			циклу. Додайте подія при наведенні миші, яке буде скруглять дані блоки за
			допомогою border-radius до кола. Для уповільнення ефекту заокруглення в
			CSS можна додати transition.
		</div>
		<div class="task-content">
			<div class="three-container">
				<div
					:class="[
						'three-block',
						{ 'three-block-hover': id === currentSelectedId }
					]"
					v-for="id in 400"
					:key="id"
					@mouseenter="onMouseEnter(id)"
					@mouseleave="onMouseLeave(id)"
				></div>
			</div>
		</div>
	</div>

	<div class="task">
		<div class="task-title">
			Завдання 8
			<span class="task-score">(2 бали)</span>
		</div>
		<div class="task-description">
			Змінити розмір зображення при натисканні миші
		</div>
		<div class="task-content">
			<img
				class="eight-image"
				:src="image"
				alt="image"
				@click="onClick"
			/>
		</div>
	</div>
</template>

<style>
.task {
	display: block;
}

.task-title {
	font-size: 24px;
	color: #52525b;
}

.task-score {
	color: #059669;
}

.task-description {
	color: #71717a;
	font-size: 18px;

	margin-bottom: 30px;
}

.eight-image {
	max-width: 800px;
	max-height: 500px;
	width: 100%;
	height: 100%;

	background-size: cover;
}

.three-container {
	display: flex;
	justify-content: center;
	flex-wrap: wrap;
	gap: 10px;
}

.three-block {
	width: 30px;
	height: 30px;
	border: 2px solid #38bdf8;
	transition: 0.3s border-radius;

	background-color: #fff7ed;
}

.three-block-hover {
	border-radius: 50%;
}
</style>

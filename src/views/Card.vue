<script lang="ts" setup>
defineProps({
	name: {
		default: "Name",
		type: String,
	},
	description: {
		default: "Description",
		type: String,
	},
});

function formatText(text: string, length: number) {
	if (text.length <= length) {
		return text;
	}
	return text.substring(0, length) + "...";
}
</script>

<template>
	<div class="cardContainer">
		<div class="card">
			<p class="name">{{ name }}</p>
			<p class="description max-w-full">{{ formatText(description, 200) }}</p>
		</div>
	</div>
</template>

<style scoped>
.cardContainer {
	position: relative;
	display: flex;
	align-items: center;
	justify-content: center;
}

.card {
	position: relative;
	overflow: hidden;
	width: 100%;
	height: 300px;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	padding: 20px 10px;
	border-radius: 10px;
	backdrop-filter: blur(30px);
	background-color: rgba(65, 65, 65, 0.308);
	border: 1px solid rgba(255, 255, 255, 0.089);
	cursor: inherit;
}

.name {
	text-align: center;
	width: 100%;
	font-weight: 700;
	font-size: 0.9em;
	letter-spacing: 1.2px;
	color: white;
}

.description {
	text-align: center;
	width: 100%;
	font-weight: 500;
	font-size: 0.7em;
	letter-spacing: 1.2px;
	color: rgb(197, 197, 197);
}

.cardContainer::before {
	width: 100px;
	height: 100px;
	content: "";
	position: absolute;
	background-color: rgb(144, 161, 255);
	z-index: -1;
	border-radius: 50%;
	left: 100px;
	top: 50px;
	transition: all 1s;
}

.cardContainer:hover::before {
	transform: translate(-50px, 50px);
}
</style>
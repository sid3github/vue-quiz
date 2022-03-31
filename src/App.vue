<template>
	<h2>{{ appTitle }}</h2>
	<img
		alt="Vue logo"
		src="./assets/logo.png"
		class="animate__animated animate__backInDown"
	/>
	<p>Current Score: {{ scoreData }} / 5</p>
	<QuestionsLayout @scoreUpdate="fetchScore($event)" :scoreData="scoreData" />
</template>

<script>
import QuestionsLayout from "./components/QuestionsLayout.vue";

export default {
	name: "App",
	components: {
		QuestionsLayout,
	},
	data() {
		return {
			scoreData: 0,
			appTitle: "Vue Quiz App",
		};
	},
	methods: {
		fetchScore(data) {
			console.log(data);
			this.scoreData = data;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

img {
	height: 100px;
}
</style>

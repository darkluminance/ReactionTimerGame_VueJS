<template>
	<img src="./assets/RNAicon.png" alt="iconset" srcset="" />
	<br /><br /><br />

	<h1>Ninja Reaction Timer</h1>

	<br /><br />
	<button @click="startGame" :disabled="isPlaying">Play</button>

	<Block v-if="isPlaying" :delay="delay" @gameend="endGame"> </Block>

	<Results v-if="score" :score="score"></Results>
	<!-- 
	<h3 v-show="score">Your score is : {{ score }} ms</h3> -->
</template>

<script>
	import Block from './components/Block.vue';
	import Results from './components/Results.vue';

	export default {
		name: 'App',
		components: {
			Block,
			Results,
		},
		data() {
			return {
				isPlaying: false,
				delay: null,
				score: null,
			};
		},
		methods: {
			startGame() {
				this.isPlaying = true;
				this.score = null;
				this.delay = 2000 + Math.random() * 6000;
				console.log('You clicked this bitch. Hehehe  ' + this.delay);
			},

			endGame(reactiontime) {
				this.score = reactiontime;
				this.isPlaying = false;
			},
		},
	};
</script>

<style scoped>
	button {
		width: 100px;
		height: 38px;
		background: #6c5ce7;
		border: none;
		color: #e7e7e7;
	}
	button:hover {
		opacity: 0.69;
	}
	button[disabled] {
		opacity: 0.18;
		cursor: not-allowed;
	}
</style>

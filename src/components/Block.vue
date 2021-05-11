<template>
	<div class="beforetext" v-if="!showBlock">
		<br /><br />
		The Block is coming. Get ready to give the best click of your life...
	</div>
	<div class="block" v-show="showBlock" @click="blockClicked">
		<h3>Click Me</h3>
	</div>
</template>

<script>
	export default {
		props: ['delay'],
		data() {
			return {
				showBlock: false,
				timer: null,
				reactionTime: 0,
			};
		},
		mounted() {
			/* console.log('Mounted'); */
			setTimeout(() => {
				this.showBlock = true;
				this.startTimer();
			}, this.delay);
		},
		updated() {
			console.log('component updated');
		},
		unmounted() {
			console.log('component unmounted');
		},

		methods: {
			blockClicked() {
				console.log('Block clicked  ' + this.reactionTime + ' ms..');
				this.stopTimer();
			},

			startTimer() {
				this.timer = setInterval(() => {
					this.reactionTime += 10;
				}, 10);
			},

			stopTimer() {
				clearInterval(this.timer);
				this.$emit('gameend', this.reactionTime);
			},
		},
	};
</script>

<style>
	.block {
		width: 400px;
		height: 48px;
		border-radius: 28px;
		background: #00b894;
		color: white;
		text-align: center;
		padding: 100px 0;
		margin: 40px auto;
	}
</style>

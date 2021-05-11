<template>
	<br /><br /><br />
	<h2>Your reaction time was {{ score }} ms</h2>
	<p>
		You got the rank <span style="color: #00b894">{{ rating }}</span>
	</p>
</template>

<script>
	export default {
		props: ['score'],
		data() {
			return {
				rating: null,
			};
		},
		methods: {
			getRank() {
				if (this.score <= 250) this.rating = 'Ninja Fingers';
				else if (this.score <= 400) this.rating = 'Ultra Rapid Reflexes';
				else if (this.score <= 600) this.rating = 'Rapid Reflexes';
				else this.rating = 'Snail Pace..';
			},
		},
		mounted() {
			this.getRank();
		},
	};
</script>

<style></style>

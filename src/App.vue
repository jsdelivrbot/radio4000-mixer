<template>
	<div id="app">
		<section>
			<radio4000-player slug="sugar-hiccup" :volume="volA"></radio4000-player>
			<radio4000-player slug="200ok" :volume="volB"></radio4000-player>
		</section>
		<controls>
			<input type="range" v-model.number="balance">
		</controls>
	</div>
</template>

<script>
export default {
	name: 'youtube-mixer',
	data() {
		return {
			balance: 50
		}
	},
	computed: {
		volA() {
			return this.balance * -1 + 100
		},
		volB() {
			return this.balance
		}
	}
}
</script>

<style>
body {
	margin: 0;
}
</style>

<style scoped>
#app {
	padding: 1rem;
	height: 100vh;
	box-sizing: border-box;
	background-color: #ccc;
	display: flex;
	flex-flow: column nowrap;
}
#app>section{
	flex: 1;
	display: flex;
	margin-bottom: 1em;
}
#app>section> * {
	flex: 50%;
	max-width: none;
	height: auto;
	border: 1px solid black;
}
#app>controls {
	width: 80%;
	margin: 1rem auto;
}
input[type="range"] {
	width: 100%;
}
</style>

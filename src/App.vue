<template>
	<div id="app">
		<div class="Decks">
			<radio4000-player slug="sugar-hiccup" :volume="volA"></radio4000-player>
			<radio4000-player slug="200ok" :volume="volB"></radio4000-player>
		</div>
		<input type="range" v-model.number="balance">
		<p>{{balance}}</p>
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
	padding: 0 0.5em 1em;
}
.Decks {
	display: flex;
	margin-bottom: 1em;
}
.Decks > * {
	flex: 50%;
	max-width: none;
	border: 1px solid;
	border-width: 1em 0.5em;
}
input[type="range"] {
	display: block;
	width: 80%;
	margin: 0 auto;
}
p {
	text-align: center;
}
</style>

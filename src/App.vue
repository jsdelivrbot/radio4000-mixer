<template>
	<div id="app">
		<header>
			<form class="split" @submit.prevent="updateDecks">
				<input v-model="inputA" @blur="updateDecks" placeholder="Enter radio for deck A…">
				<input v-model="inputB" @blur="updateDecks" placeholder="Enter radio for deck B…">
				<button type="submit">load</button>
			</form>
		</header>
		<section class="split">
			<radio4000-player v-show="deckA" :slug="deckA" :volume="volA"></radio4000-player>
			<radio4000-player v-show="deckB" :slug="deckB" :volume="volB"></radio4000-player>
		</section>
		<menu>
			<input type="range" v-model.number="balance">
		</menu>
	</div>
</template>

<script>
export default {
	name: 'youtube-mixer',
	data() {
		return {
			inputA: '',
			inputB: '',
			deckA: '',
			deckB: '',
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
	},
	methods: {
		updateDecks() {
			this.deckA = this.inputA
			this.deckB = this.inputB
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
#app>header button {
	display: none;
	max-width: 4rem;
}
.split {
	display: flex;
}
.split > * {
	flex: 50%;
}
#app>header input {
	min-height: 2em;
	padding: 0 0.5em;
	border-top: 1px solid #999;
	border-left: 1px solid #999;
	border-right: 1px solid #999;
	background-color: #fafafa;
}

#app>section{
	flex: 1;
	margin-bottom: 1em;
}
#app>section> * {
	max-width: none;
	height: auto;
}

#app>menu {
	width: 80%;
	padding: 0;
	margin: 1rem auto;
}
input[type="range"] {
	width: 100%;
}
</style>

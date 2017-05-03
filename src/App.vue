<template>
	<div id="app">
		<header>
			<form class="split" @submit="reload">
				<input v-model="inputA" placeholder="Deck A">
				<input v-model="inputB" placeholder="Deck B">
			</form>
		</header>
		<section class="split">
			<radio4000-player :slug="slugA" :volume="volA"></radio4000-player>
			<radio4000-player :slug="slugB" :volume="volB"></radio4000-player>
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
			deckA: '',
			deckB: '',
			inputA: '',
			inputB: '',
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
		reload(event) {
			event.preventDefault()
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

.split {
	display: flex;
}
.split > * {
	flex: 50%;
}

#app>section{
	flex: 1;
	margin-bottom: 1em;
}
#app>section> * {
	max-width: none;
	height: auto;
	border: 1px solid black;
}

#app>menu {
	width: 80%;
	margin: 1rem auto;
}
input[type="range"] {
	width: 100%;
}
</style>

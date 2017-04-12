<template>
  <div id="app">
    <div class="Decks">
      <Radio4000Player slug="sugar-hiccup" :volume="balance" />
      <Radio4000Player slug="200ok" :volume="balance" />
    </div>
    <input type="range" v-model.number="balance">
    <p>{{balance}}</p>
  </div>
</template>

<script>
import Vue from 'vue'
import Radio4000Player from 'radio4000-player/src/App.vue'

export default {
	name: 'youtube-mixer',
  data() {
    return {
      balance: 50
    }
  },
	components: {
		Radio4000Player 
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

<script setup lang="ts">
import GameOver from './components/GameOver.vue'
import { Ref, ref } from 'vue';
import Field from './components/Field.vue'
import { Player } from './models';

const board: Ref<string[]> = ref(new Array(9).fill(''))
const currentPlayer: Ref<Player> = ref('Player 1')
const onSwitchPlayer = () => {
  currentPlayer.value === 'Player 1' ? currentPlayer.value = 'Player 2' : currentPlayer.value = 'Player 1'
}
const gameOver = ref(false)

</script>

<template>
  <Field :board="board" :player="currentPlayer" @switch-player="onSwitchPlayer" @game-over="gameOver = true" />
  <GameOver v-if="gameOver" />
</template>

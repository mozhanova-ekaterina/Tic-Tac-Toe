<script setup lang="ts">
import Restart from './components/Restart.vue'
import GameOver from "./components/GameOver.vue";
import { Ref, ref } from "vue";
import Field from "./components/Field.vue";
import { Player } from "./models";

const board: Ref<string[]> = ref(new Array(9).fill(""));
const currentPlayer: Ref<Player> = ref("Игрок 1");
const onSwitchPlayer = () => {
  currentPlayer.value === "Игрок 1"
    ? (currentPlayer.value = "Игрок 2")
    : (currentPlayer.value = "Игрок 1");
};
const gameOver = ref(false);
const winner = ref('');
const restart = () => {
  board.value.fill("");
  gameOver.value = false;
  currentPlayer.value = "Игрок 1";
};
const onGameOver = (player?: Player) => {
  gameOver.value = true
  winner.value = player as Player
}
</script>

<template>
  <main class="flex p-10 gap-5 justify-between">
    <section>
      <Field :board="board" :player="currentPlayer" @switch-player="onSwitchPlayer" @game-over="onGameOver" />
    </section>
    <section class="border p-2 rounded-xl flex flex-col gap-2">
      <Restart @restart="restart" />
      <GameOver v-if="gameOver" :winner="winner" />
    </section>
  </main>

</template>

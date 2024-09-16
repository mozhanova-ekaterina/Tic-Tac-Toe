<script lang="ts" setup>
import { PropType } from 'vue';
import Cell from './Cell.vue'
import { Player } from '../models';
import { winConditions } from '../utils';

const props = defineProps({
  player: { type: String as PropType<Player>, required: true },
  board: { type: Array<string>, required: true }
})

const emit = defineEmits(['switchPlayer', 'gameOver'])

const onClick = (e: Event): void => {
  const target = e.target as HTMLElement
  props.player === 'Игрок 1' ? props.board[+target.id] = 'X' : props.board[+target.id] = 'O'
  setTimeout(() => {
    if (haveWinner()) emit('gameOver', props.player)
    else if (!haveWinner() && noMoves()) emit('gameOver')
    else emit('switchPlayer')
  }, 500);
}

const haveWinner = (): boolean => {
  for (let i = 0; i < winConditions.length; i++) {
    let [a, b, c] = winConditions[i]
    if (props.board[a] && props.board[a] === props.board[b] && props.board[a] === props.board[c]
    ) {
      return true
    }
  }
  return false
}

const noMoves = (): boolean => props.board.every(cell => cell !== '')


</script>
<template>
  <div class="grid grid-cols-3 grid-rows-3 gap-2 max-w-fit mx-auto">
    <Cell @click="onClick" v-for="(cell, index) in props.board " :value="cell" :id="index" />
  </div>
</template>
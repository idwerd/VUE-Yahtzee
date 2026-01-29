<script setup>
const diceValues = defineModel('diceValues');
const count = defineModel('count');

function rollDice() {
  for (let die in count.value) {
    count.value[die] = 0;
  }

  for (let i = 0; i < 5; i++) {
    diceValues.value[i] = Math.floor(Math.random() * 6 + 1);
  }
  diceValues.value.forEach(countValues);
}

function countValues(currentValue) {
  count.value[currentValue]++;
}
</script>

<template>
  <section id="yahtzee">
    <table class="scoreblok">
      <thead>
        <th colspan="5"><h2>Worp</h2></th>
      </thead>
      <tr>
        <td class="dice" v-for="(die, index) in diceValues" :key="index">{{ die }}</td>
      </tr>
    </table>
    <button id="throw-button" @click="rollDice">Gooien!</button>
  </section>
</template>

<style scoped></style>

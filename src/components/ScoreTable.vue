<script setup>
import {computed} from 'vue';

const diceValues = defineModel('diceValues');
const count = defineModel('count');

const ones = computed(() => calculateScoresPartOne(1));
const twos = computed(() => calculateScoresPartOne(2));
const threes = computed(() => calculateScoresPartOne(3));
const fours = computed(() => calculateScoresPartOne(4));
const fives = computed(() => calculateScoresPartOne(5));
const sixs = computed(() => calculateScoresPartOne(6));
const subtotal = computed(() => addAllDice());
const bonus = computed(() => (subtotal.value >= 63 ? 35 : 0));
const totalPartOne = computed(() => subtotal.value + bonus.value);

const calculateScoresPartOne = die => {
  return count.value[die] * die;
};

const threeOfAKind = computed(() => (checkIdenticals(3) ? addAllDice() : 0));
const carre = computed(() => (checkIdenticals(4) ? addAllDice() : 0));
const fullHouse = computed(() => (checkFullHouse() || checkIdenticals(5) ? 25 : 0));
const smallStraight = computed(() => (checkStraights(4) ? 30 : 0));
const bigStraight = computed(() => (checkStraights(5) ? 40 : 0));
const topscore = computed(() => (checkIdenticals(5) ? 50 : 0));
const chance = computed(() => addAllDice());
const totalPartTwo = computed(
  () =>
    threeOfAKind.value +
    carre.value +
    fullHouse.value +
    smallStraight.value +
    bigStraight.value +
    topscore.value +
    chance.value,
);
const total = computed(() => totalPartOne.value + totalPartTwo.value);

const checkIdenticals = xOfAKind => {
  for (let value in count.value) {
    if (count.value[value] >= xOfAKind) {
      return true;
    }
  }
  return false;
};

// Toch een fullhouse functie gemaakt, want bij checkidenticals gaf hij ook
// true als er van als er minimaal 3 waren gegooid van 1 soort (bv: 3, 3, 3, 5, 4)
const checkFullHouse = () => {
  let fullHouseTwo = false;
  let fullHouseThree = false;
  for (let value in count.value) {
    if (count.value[value] === 2) {
      fullHouseTwo = true;
    }
    if (count.value[value] === 3) {
      fullHouseThree = true;
    }
  }
  if (fullHouseTwo === true && fullHouseThree === true) {
    return true;
  }
  return false;
};

const checkStraights = sequence => {
  let counter = 0;

  for (let value in count.value) {
    if (count.value[value] == 0) {
      counter = 0;
    } else if (count.value[value] > 0) {
      counter++;
    }
    if (counter == sequence) {
      return true;
    }
  }
  return false;
};

const addAllDice = () => {
  let totalPips = 0;
  for (let i = 0; i < diceValues.value.length; i++) {
    totalPips += diceValues.value[i];
  }
  return totalPips;
};
</script>

<template>
  <section id="verwerken">
    <table id="deel-1">
      <tr>
        <th colspan="3"><h2>SCOREBLOK DEEL 1</h2></th>
      </tr>
      <tr>
        <th>Dobbelsteen</th>
        <th>Puntentelling</th>
        <th>1e spel</th>
      </tr>
      <tr>
        <td>Enen</td>
        <td>Tel alle Enen</td>
        <td class="punten points-part1">
          {{ ones }}
        </td>
      </tr>
      <tr>
        <td>Tweeën</td>
        <td>Tel alle Tweeën</td>
        <td class="punten points-part1">
          {{ twos }}
        </td>
      </tr>
      <tr>
        <td>Drieën</td>
        <td>Tel alle Drieën</td>
        <td class="punten points-part1">
          {{ threes }}
        </td>
      </tr>
      <tr>
        <td>Vieren</td>
        <td>Tel alle Vieren</td>
        <td class="punten points-part1">
          {{ fours }}
        </td>
      </tr>
      <tr>
        <td>Vijven</td>
        <td>Tel alle Vijven</td>
        <td class="punten points-part1">
          {{ fives }}
        </td>
      </tr>
      <tr>
        <td>Zessen</td>
        <td>Tel alle Zessen</td>
        <td class="punten points-part1">
          {{ sixs }}
        </td>
      </tr>
      <tr>
        <td colspan="2">Totaalpunten</td>
        <td class="punten" id="totalpoints-part1">
          {{ subtotal }}
        </td>
      </tr>
      <tr>
        <td>Bonus</td>
        <td>Totaalpunten >= 63 dan 35 punten</td>
        <td class="punten" id="bonus">
          {{ bonus }}
        </td>
      </tr>
      <tr>
        <td colspan="2">Totaal</td>
        <td class="punten total-part1">
          {{ totalPartOne }}
        </td>
      </tr>
    </table>

    <table id="deel-2">
      <tr>
        <th colspan="3"><h2>SCOREBLOK DEEL 2</h2></th>
      </tr>
      <tr>
        <th>Combinatie</th>
        <th>Puntentelling</th>
        <th>1e spel</th>
      </tr>
      <tr>
        <td>Three of a kind</td>
        <td>Totaal v.d. 5 stenen</td>
        <td class="punten points-part2" id="three-of-a-kind">
          {{ threeOfAKind }}
        </td>
      </tr>
      <tr>
        <td>Carré</td>
        <td>Totaal v.d. 5 stenen</td>
        <td class="punten points-part2" id="carre">
          {{ carre }}
        </td>
      </tr>
      <tr>
        <td>Full house</td>
        <td>25 punten</td>
        <td class="punten points-part2" id="fullhouse">
          {{ fullHouse }}
        </td>
      </tr>
      <tr>
        <td>Kleine straat</td>
        <td>30 punten</td>
        <td class="punten points-part2" id="kleine-straat">
          {{ smallStraight }}
        </td>
      </tr>
      <tr>
        <td>Grote straat</td>
        <td>40 punten</td>
        <td class="punten points-part2" id="grote-straat">
          {{ bigStraight }}
        </td>
      </tr>
      <tr>
        <td>Topscore</td>
        <td>50 punten</td>
        <td class="punten points-part2" id="topscore">
          {{ topscore }}
        </td>
      </tr>
      <tr>
        <td>Chance</td>
        <td>Totaal v.d. stenen</td>
        <td class="punten points-part2" id="chance">
          {{ chance }}
        </td>
      </tr>
      <tr>
        <td colspan="2">Totaal deel 2</td>
        <td class="punten total-part2" id="total-part2">
          {{ totalPartTwo }}
        </td>
      </tr>
      <tr>
        <td colspan="2">Totaal deel 1</td>
        <td class="punten total-part1">
          {{ totalPartOne }}
        </td>
      </tr>
      <tr>
        <td colspan="2"><strong>TOTAAL</strong></td>
        <td class="punten" id="allpoints">
          <strong>
            {{ total }}
          </strong>
        </td>
      </tr>
    </table>
  </section>
</template>

<style scoped></style>

<script setup>
/*
Dit component toont een tabel met alle mogelijke 
Yahtzee-scores. De array met gegooide dobbelstenen ( dice ) 
wordt via een v-model doorgegeven van App.vue naar ScoreTable. 
Gebruik binnen ScoreTable computed properties om de mogelijke 
scores te berekenen op basis van de huidige waarden in de 
dice array en geef deze weer in de template van ScoreTable.
*/
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
        <td class="punten points-part1">0</td>
      </tr>
      <tr>
        <td>Tweeën</td>
        <td>Tel alle Tweeën</td>
        <td class="punten points-part1">0</td>
      </tr>
      <tr>
        <td>Drieën</td>
        <td>Tel alle Drieën</td>
        <td class="punten points-part1">0</td>
      </tr>
      <tr>
        <td>Vieren</td>
        <td>Tel alle Vieren</td>
        <td class="punten points-part1">0</td>
      </tr>
      <tr>
        <td>Vijven</td>
        <td>Tel alle Vijven</td>
        <td class="punten points-part1">0</td>
      </tr>
      <tr>
        <td>Zessen</td>
        <td>Tel alle Zessen</td>
        <td class="punten points-part1">0</td>
      </tr>
      <tr>
        <td colspan="2">Totaalpunten</td>
        <td class="punten" id="totalpoints-part1">0</td>
      </tr>
      <tr>
        <td>Bonus</td>
        <td>Totaalpunten >= 63 dan 35 punten</td>
        <td class="punten" id="bonus">0</td>
      </tr>
      <tr>
        <td colspan="2">Totaal</td>
        <td class="punten total-part1">0</td>
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
        <td class="punten points-part2" id="three-of-a-kind">0</td>
      </tr>
      <tr>
        <td>Carré</td>
        <td>Totaal v.d. 5 stenen</td>
        <td class="punten points-part2" id="carre">0</td>
      </tr>
      <tr>
        <td>Full house</td>
        <td>25 punten</td>
        <td class="punten points-part2" id="fullhouse">0</td>
      </tr>
      <tr>
        <td>Kleine straat</td>
        <td>30 punten</td>
        <td class="punten points-part2" id="kleine-straat">0</td>
      </tr>
      <tr>
        <td>Grote straat</td>
        <td>40 punten</td>
        <td class="punten points-part2" id="grote-straat">0</td>
      </tr>
      <tr>
        <td>Topscore</td>
        <td>50 punten</td>
        <td class="punten points-part2" id="topscore">0</td>
      </tr>
      <tr>
        <td>Chance</td>
        <td>Totaal v.d. stenen</td>
        <td class="punten points-part2" id="chance">0</td>
      </tr>
      <tr>
        <td colspan="2">Totaal deel 2</td>
        <td class="punten total-part2" id="total-part2">0</td>
      </tr>
      <tr>
        <td colspan="2">Totaal deel 1</td>
        <td class="punten total-part1">0</td>
      </tr>
      <tr>
        <td colspan="2"><strong>TOTAAL</strong></td>
        <td class="punten" id="allpoints"><strong>0</strong></td>
      </tr>
    </table>
  </section>
</template>

<style scoped></style>

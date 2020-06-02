<template>
<div>
<div class="hpbars">
      <p>
          Player ⚔️ 🛡️
      </p>
      <div class="bar"
      :style="{ width: playerHp + '%'}">
            {{ playerHp }}
      </div>
      <p>
         Enemy Monster 👹
      </p>
      <div class="bar"
      :style="{ width: enemyHp + '%'}">
        {{ enemyHp }}
      </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'HealthBars',
  props: {
    playerHp: Number,
    enemyHp: Number
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Chelsea+Market&display=swap');
  * {
    font-family: 'Chelsea Market', cursive;
    font-size: 1.5rem;
    color: gray;
  }
  .hpbars {
      text-align: center;
    }
  .bar {
      background: greenyellow;
      margin: auto;
      border-radius: 20px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
</style>
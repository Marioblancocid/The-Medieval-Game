<template>
<div>
<div class="inventory">
  Special Attacks: {{ specialAttacks }}
<img id="sp" src="https://iconsetc.com/icons-watermarks/simple-red-gradient/ocha/ocha_security-attack/ocha_security-attack_simple-red-gradient_512x512.png">
  Heal Potions: {{ healPotions }}
<img src="https://cdn.domestika.org/c_limit,dpr_auto,f_auto,q_auto,w_820/v1486945396/content-items/001/862/857/Pocion-Salud-original.png?1486945396">
    </div>
</div>
</template>

<script>
export default {
  name: 'Inventory',
  props: {
    specialAttacks: Number,
    healPotions: Number
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Chelsea+Market&display=swap');
.inventory{
  display: flex;
  align-items: center;
  justify-content: center;
  color: gray;
}
img {
  max-width: 100px;
}
#sp {
  max-width: 50px;
  margin: 0 1rem;
}
</style>
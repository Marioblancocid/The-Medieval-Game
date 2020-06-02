<template>
<div>
    <div class="options">
      <button @click="attackEvent">
        ATTACK
      </button>
      <button @click="specialEvent">
        SPECIAL MOVE
      </button>
      <button @click="healEvent">
        HEAL
      </button>
      <button @click="giveUpEvent">
        GIVE UP
      </button>
    </div>
</div>
</template>

<script>
export default {
  name: 'OptionButtons',
  methods: {
    attackEvent(){
      this.$emit("attack")
    },
    healEvent(){
      this.$emit("heal")
    },
    specialEvent(){
      this.$emit("special")
    },
    giveUpEvent(){
      this.$emit("giveUp")
    }
  },
  props: {
  }
}
</script>

<style scoped>
    .options {
      width: 80%;
      padding: 1rem;
      border: 3px dashed slateblue;
      margin: auto;
      margin-top: 1rem;
      background-image: linear-gradient(to bottom right, rgb(88, 40, 143) , black);
    }
    .options button {
      border: 5px dashed rgb(50, 42, 97);
      background: slateblue;
      padding: 1rem;
      margin: 0.667rem;
      font-weight: bold;
    }
</style>
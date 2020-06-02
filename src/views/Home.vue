<template>
  <div class="home">
    <p>
      {{ speak }}
    </p>
    <button @click="changeDialog" v-show="this.dialogs[this.dialog].game">
      Keep going
    </button>
    <button v-show="!this.dialogs[this.dialog].game">
      <router-link :to="{ name: 'Game' }">
      Fight
      </router-link>
    </button>
  </div>
</template>

<script>
// @ is an alias to /src
/* import HelloWorld from '@/components/HelloWorld.vue' */

export default {
  name: 'Home',
  data() {
    return {
      dialog: 0,
      dialogs: [
        { text: 'Hi! Welcome to The Medieval Game.', dialog: 0, game: true },
        { text: 'This is a hard game where you have to make right choices.', dialog: 1, game: true },
        { text: 'Try to beat your enemy!', dialog: 2, game: false }
      ]
    }
  },
  created() {
    document.title = "Home | MedievalGame"
  },
  computed: {
    speak(){
      return this.dialogs[this.dialog].text
    }
  },
  methods: {
    changeDialog(){
      this.dialog++
    }
  }
}
</script>

<style scoped>
  .home {
    background: rgb(56, 29, 121);
    border: 5px darkslategray dotted;
    padding: 1rem;
    color:rgb(120, 81, 211);
    font-weight: bold;
  }
  button {
  font-size: 0.9rem;
  padding: 0.3rem;
  border-radius: 20px;
  background: rgba(6, 44, 102, 0.267);
  color: rgb(120, 81, 211);
  font-weight: bold;
}
  a {
  font-size: 0.9rem;
  padding: 0.3rem;
  border-radius: 20px;
  background: rgba(6, 44, 102, 0.267);
  color: rgb(120, 81, 211);
  text-decoration: none;
}
</style>
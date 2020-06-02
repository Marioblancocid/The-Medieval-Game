<template>
  <div>
    <section>
    <!--BARRAS DE VIDA -->
    <HealthBars :playerHp='playerHp' :enemyHp='enemyHp'></HealthBars>
    <!--/BARRAS DE VIDA -->
    <!--OPCIONES DE JUEGO -->
    <OptionButtons v-on:attack="attack" v-on:special="specialAttack" v-on:heal="heal" v-on:giveUp="giveUp"></OptionButtons>
    <!--/OPCIONES DE JUEGO -->
    <!-- INVENTORY -->
    <Inventory :specialAttacks='specialAttacks' :healPotions='healPotions'></Inventory>
    <!-- /INVENTORY -->
    <!-- LOGS -->
    <Logs :Logs='Logs'></Logs>
    <!-- /LOGS -->
</section>
  </div>
</template>

<script>
import HealthBars from '@/components/HealthBars.vue'
import OptionButtons from '@/components/OptionButtons.vue'
import Inventory from '@/components/Inventory.vue'
import Logs from '@/components/Logs.vue'
// Importando Sweet Alert 2
import Swal from 'sweetalert2'

export default {
        name: 'Game',
        components: {
          HealthBars, OptionButtons, Inventory, Logs
        },
        data () {
          return {
            playerHp: 80 ,
            enemyHp: 80,
            healHp: 20,
            healPotions: 3,
            specialAttacks: 2,
            specialAttackDMG: 10,
            Logs: []
          }
        },
        created() {
          document.title = "The MedievalGame"
        },
        methods: {
            attack(){
              //MAKES IMPOSSIBLE TO ATTACK IF YOU ARE DEATH
              if (this.playerHp <= 0) {
                return
              }

              let damage = this.calculateDamage(3, 10);
              this.enemyHp -= damage;

              //PREVENTS ENEMY HP TO BE LESS THAN 0
              if (this.enemyHp <= 0) {
                this.enemyHp = 0;
                Swal.fire({
                title: 'You Win!' ,
                text:  'Get ready for the next battle, I will beat you!',
                confirmButtonText:  ':D',
                });
              this.goHome()
              }

              //SAVES THE MOVE ON LOGS
              let log = { log: `⚔️ The player has done ${damage} points of damage ⚔️` }
              this.enemyAttack();
              this.Logs.unshift(log);

            },
            calculateDamage(min, max){
              return Math.max(Math.floor(Math.random() * max) + 1, min)
            },

            enemyAttack(){
              //MAKES IMPOSSIBLE TO ATTACK IF ENEMY IS DEATH
              if (this.enemyHp <= 0) {
                return
              }

              let damage = this.calculateDamage(10,16);
              this.playerHp -= damage;

              //SAVES THE MOVE ON LOGS
              let log = { log: `⚔️ The enemy has done ${damage} points of damage ⚔️` }
              this.Logs.unshift(log);
              if (this.Logs[4]) {
                this.Logs.length = 3
              }
              //PREVENTS USER HP TO GO LOWER THAN 0
              if (this.playerHp <= 0) {
                this.playerHp = 0;
                Swal.fire({
                title: 'You Lose!' ,
                text:  'Are you going to give up??',
                confirmButtonText:  ':D',
            });
            this.goHome()
              }
            },

            heal() {
              //YOU CAN ONLY USER HEAL POTIONS IF YOU ARE LOWER THAN 50HP
              //IF YOU HAVE HEALPOTIONS LEFT
              //AND IF YOU ARE NOT DEATH
              if ((this.playerHp>50) || (this.healPotions <= 0) || (this.playerHp===0)) {
                return;
              }
              this.playerHp += this.healHp
              this.healPotions -= 1
              this.enemyAttack()
              let log = { log: `❤️ The player healed ${this.healHp} points of life ❤️` }
              this.Logs.unshift(log);
            },
            specialAttack(){
              if (this.specialAttacks<=0 || this.playerHp===0) {
                return;
              }
              this.enemyHp -= this.specialAttackDMG
              this.specialAttacks -= 1
              this.enemyAttack()
              //PREVENTS ENEMY HP TO BE LESS THAN 0
              if (this.enemyHp <= 0) {
                this.enemyHp = 0;
              }
              let log = { log: `💥 The player used the Special Attack and has dealt ${this.specialAttackDMG} points of life 💥` }
              this.Logs.unshift(log);
            },
            giveUp(){
            this.playerHp= 80;
            this.enemyHp= 80;
            this.healPotions= 3;
            this.specialAttacks= 2;
            Swal.fire({
                title: 'You surrended! LOL' ,
                text:  'Are you going to give up??',
                confirmButtonText:  ':D',
            });
            this.Logs = [];
            this.goHome()
            },
            goHome(){
              this.$router.push('/')
            }
        }
      }
    </script>

<style scoped>
  section {
    background: rgb(56, 29, 121);
    border: 5px darkslategray dotted;
    padding: 1rem;
  }
</style>
<template>
    <div :class='["PokeStats", "framed", isPlayer ? "player" : "opponent"]'>
      <div class="name">
        {{ poke.name }}
      </div>
      <div class="healthBar">
        <div class="bar-background">
          <p>HP</p>
          <div class="bar" :style="{ width: `${widthOfHealthBar}%`, backgroundColor: healthBarColor }"></div>
        </div>
      </div>
    </div>
</template>
  
  
<script>
export default {
  props: {
    poke: {
      type: Object,
    },
    turn: {
      type: Boolean,
    },
    currentHp: {
      type: Number,
    },
    isPlayer: {
      type: Boolean,
    },
  },
  computed: {
    widthOfHealthBar() {
        if(this.currentHp > 0 ){
           return Math.floor((this.currentHp / this.poke.stats.hp) * 100)
        }
      return 0;
    },
    healthBarColor() {
      const percentage = this.widthOfHealthBar;
      if (percentage > 60) {
        return "green";
      } else if (percentage > 30) {
        return "yellow";
      } else {
        return "red";
      }
    },
  },
};
</script>
<style scoped>
p {
  padding-left: 1vw;
  padding-right: 1vw;
  color: orange;
  font-weight: bold;
  font-size: 1.1em;
}

.PokeStats {
  position: absolute;
  width: 50%;
  height: 20vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 3vh;
  background: white;
}

.healthBar {
  align-self: center;
  width: 100%;
}

.bar-background {
  display: flex;
  align-items: center;
  background: grey;
}

.bar {
  height: 4vh;
  background-color: green;
  margin-right: 1vw;
  transition: width 1s ease-in-out, background-color 1s ease-in-out; /* Smooth transitions */
}

.name {
  text-transform: capitalize;
  font-weight: bold;
  font-size: 1.4em;
}

.PokeStats.player {
  right: 1vw;
  bottom: 30vh;
}

.PokeStats.opponent {
  left: 1vw;
  top: 2vh;
}
</style>

<template>
  <div class="PokeCard">
    <div v-if="pokemon" :class="['Container',pokemon.type]">
      <div class="typeAndSuch">
        <img :src="pokeTypeIcon" :alt="pokemon.type">
        <p>{{pokemon.type}}</p>
      </div>
      <div class="ImageAndName">
        <h2>{{ pokemon.name }}</h2>
        <img :src="pokemon.frontSprite" alt="Front Sprite">
      </div>
      <button @click="openProfile(pokemon.name)">View Stats</button>
    </div>
  </div>
</template>
<!-- add button that if we pass a prop we will have a button with afunc that adds to team -->
<script>
import typeIcons from "../../assets/data/typeIcons.json";
export default {
  props: {
      pokemon: {
          type: Object,
          required: true
      },
      choose:{
          type: Boolean,
          required: false,
      }
  },
  data(){
    return {
      typeIcons:typeIcons,
      pokeTypeIcon:null
    }
  },
  methods:{
    getIcon(item){
      for(const iconObject of this.typeIcons){
        if(iconObject.name == item.type){
          this.pokeTypeIcon = iconObject.image
        }
      }
    },
    openProfile(poke){
      this.$router.push(`/pokemon/profile/${poke}`,this.choose)
    }
  },
  created(){
    this.getIcon(this.pokemon);
    console.log(this.pokemon.type)
  }
}
</script>

<style scoped>
* {
  font-family: HomeVideo;
}
.PokeCard {
  height: 20vw;
  width: 20vw;
}

.Container {
  display: flex;
  flex-direction: row;
  height: 100%;
  width: 100%;
  border: 2px solid ;
  border-radius: 15px;
}

.typeAndSuch, .ImageAndName {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.typeAndSuch {
  width: 15%;
  align-items: center;
  margin-top: 2vh;
  margin-left: 1vh;
}

.typeAndSuch > img {
  width: 80%;
}

.typeAndSuch > p {
  display: flex;
  text-orientation: upright;
  writing-mode: vertical-rl;
  margin: 0;
  letter-spacing: normal;
  font-size: 1.1em;
  margin-right: 1vh;
}

.ImageAndName {
  width: 85%;
  height: 100%;
  align-items: center;
  justify-content: center;
}

.ImageAndName > img {
  width: 100%;
}


.fairy {
  background: linear-gradient(135deg, #EE99AC, #FFCCD4);
}

.rock {
  background: linear-gradient(135deg, #B8A038, #D1C07E);
}

.steel {
  background: linear-gradient(135deg, #B8B8D0, #D0D0E0);
}

.water {
  background: linear-gradient(135deg, #6890F0, #98A9F0);
}

.ghost {
  background: linear-gradient(135deg, #705898, #9B81B8);
}

.psychic {
  background: linear-gradient(135deg, #F85888, #FF9CA6);
}

.poison {
  background: linear-gradient(135deg, #A040A0, #B070B0);
}

.flying {
  background: linear-gradient(135deg, #A890F0, #C6B7F0);
}

.fire {
  background: linear-gradient(135deg, #F08030, #FFA068);
}

.normal {
  background: linear-gradient(135deg, #A8A878, #C6C69E);
}

.grass {
  background: linear-gradient(135deg, #78C850, #A0D870);
}

.ice {
  background: linear-gradient(135deg, #98D8D8, #C2EBEB);
}

.fighting {
  background: linear-gradient(135deg, #C03028, #D87070);
}

.electric {
  background: linear-gradient(135deg, #F8D030, #FFE670);
}

.dark {
  background: linear-gradient(135deg, #705848, #9B7E68);
}

.ground {
  background: linear-gradient(135deg, #E0C068, #F2DE98);
}

.bug {
  background: linear-gradient(135deg, #A8B820, #C6D030);
}
</style>

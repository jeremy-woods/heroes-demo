<template>
  <div class="overflow-auto">
    <h1>HEROES</h1>
    <div v-for="hero in heroes" v-bind:key="hero.id" class="col-md-3 col-sm-6 col-xs-12 hero-wrap">
      <div v-if="hero.id < 9" class="hero-container">
        <router-link :to="{ name: 'HeroDetail', params: { id: hero.id }}">
          <div class="hero-image"><b-img v-bind:src="hero.images.lg" fluid ></b-img></div>
          <div class="hero-name">{{ hero.name }}</div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HeroesList",
  data() {
    return {
      heroes: null,
    };
  },
  created: function () {
    axios
      .get("https://akabab.github.io/superhero-api/api/all.json")
      .then((res) => {
        this.heroes = res.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style scoped>
h1 {
  background-color: #ec1d24;
  color: #ffffff;
  font-weight: bold;
  letter-spacing: -4px;
}
.hero-wrap {
  float: left;
}
.hero-container {
  margin: 40px 20px;
}
.hero-name {
  background-color: white;
  color: #ec1d24;
  font-size: 2em;
  font-weight: bold;
  height: 2.6em;
}
</style>

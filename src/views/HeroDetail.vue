<template>
<div>
    <h1>Your Hero</h1>
        <div class="card text-center">
        <div class="card-body">
            <div class="hero-image card-body"><b-img v-bind:src="hero.images.lg" fluid ></b-img></div>
        </div>
        <div class="card-footer pb-0 pt-3">
            
            <div class="hero-details">
                <div class="hero-stats">
                    <ul class="list-group">
                        <li class="list-group-item">
                            <div class="hero-name">{{ hero.name }}</div>
                        </li>
                        <li class="list-group-item">
                            <span class="stat-name">Weight: </span>
                            <span class="stat-value">{{ hero.appearance.weight[0] }}</span>
                        </li>
                        <li class="list-group-item">
                            <span class="stat-name">Intellegence: </span>
                            <span class="stat-value">{{ hero.powerstats.intelligence }}</span>
                        </li>
                        <li class="list-group-item">
                            <span class="stat-name">Strength: </span>
                            <span class="stat-value">{{ hero.powerstats.strength }}</span>
                        </li>
                        <li class="list-group-item">
                            <span class="stat-name">Speed: </span>
                            <span class="stat-value">{{ hero.powerstats.speed }}</span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import axios from "axios";

export default {
  name: "HeroDetail",
  data() {
    return {
      hero: null,
    };
  },
  created: function () {
    let turl = "https://akabab.github.io/superhero-api/api/id/" + this.$route.params.id + ".json";
    axios
      .get(turl)
      .then((res) => {
        this.hero = res.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style scoped>
 h1 {
  background-color: #EC1D24;
  color: #ffffff;
  font-weight: bold;
  letter-spacing: -4px;
}
.card {
  display: block;
  margin: 1rem auto;
  max-width: 500px;
  width: 500px;
}
.hero-name {
  background-color: white;
  color: #EC1D24;
  font-size: 2em;
  font-weight: bold;
  height: 2.6em;
}
.stat-name {
    float: left;
}
.stat-value {
    float: right;
}
</style>
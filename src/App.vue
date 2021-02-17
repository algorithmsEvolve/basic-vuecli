<template>
  <div id="app">
    <Header v-on:ganti-hero="gantiHero"></Header>

    <main>
      <p>Hero-Hero Terbaik Minggu Ini</p>
      <article v-if="!selectedHero">
        <Hero
          v-for="(item, index) in hero"
          :hero="item"
          :index="index"
          :key="item.id"
        ></Hero>
      </article>
      <article v-else>
        <Hero :hero="selectedHero" :index="0"></Hero>
      </article>
    </main>

    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Hero from "./components/Hero.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Hero,
  },
  data: function () {
    return {
      hero: [
        {
          id: 1,
          nama: "Aurora",
          type: "Mage",
          gambar: "aurora.jpg",
        },
        {
          id: 2,
          nama: "Zilong",
          type: "Fighter",
          gambar: "zilong.jpg",
        },
        {
          id: 3,
          nama: "Akai",
          type: "Tank",
          gambar: "akai.jpg",
        },
        {
          id: 4,
          nama: "Bruno",
          type: "Marksman",
          gambar: "bruno.jpg",
        },
        {
          id: 5,
          nama: "Layla",
          type: "Marksman",
          gambar: "layla.jpg",
        },
        {
          id: 6,
          nama: "Gatotkaca",
          type: "Tank",
          gambar: "gatotkaca.png",
        },
      ],
      selectedHero: "",
    };
  },
  methods: {
    gantiHero: function () {
      this.selectedHero = this.randomHero();
    },
    randomHero() {
      return this.hero[Math.floor(Math.random() * this.hero.length)];
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

main img {
  width: 80px;
  border: 1px solid #ccc;
}

article {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

main {
  text-align: center;
}
</style>

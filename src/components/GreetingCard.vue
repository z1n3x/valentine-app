<template>
  <div class="greeting-card" :style="{ backgroundColor: config.backgroundColor, borderColor: config.accentColor }">
    <h1>Happy Valentine’s Day, {{ config.girlfriendName }}!</h1>
    <p>{{ config.message }}</p>
    <div class="photos">
      <img 
        v-for="(photo, index) in config.photos" 
        :key="index" 
        :src="getAsset(photo)" 
        alt="A lovely memory" />
    </div>
  </div>
</template>

<script>
import config from "../config.js";

export default {
  name: "GreetingCard",
  data() {
    return {
      config
    };
  },
  methods: {
    // This method helps resolve the path of assets
    getAsset(path) {
      return new URL(`./${path}`, import.meta.url).href;
    }
  }
};
</script>

<style scoped>
.greeting-card {
  max-width: 800px;
  margin: 40px auto;
  padding: 20px;
  text-align: center;
  border: 5px solid;
  border-radius: 15px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
.greeting-card h1 {
  margin-bottom: 20px;
  font-size: 2.5rem;
  color: #333;
}
.greeting-card p {
  font-size: 1.2rem;
  color: #555;
}
.photos {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 20px;
}
.photos img {
  max-width: 250px;
  margin: 10px;
  border-radius: 10px;
  transition: transform 0.3s;
}
.photos img:hover {
  transform: scale(1.05);
}
</style>

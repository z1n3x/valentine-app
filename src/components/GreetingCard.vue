<template>
  <div class="greeting-page">
    <div class="card">
      <h1>Happy Valentine’s Day, {{ config.girlfriendName }}!</h1>
      <p class="message">{{ config.message }}</p>
      
      <div class="section photos">
        <h2>Our Special Moments</h2>
        <div class="gallery">
          <img 
            v-for="(photo, index) in config.photos" 
            :key="index" 
            :src="getAsset(photo)" 
            alt="A special moment" />
        </div>
      </div>
      
      <div class="section memories">
        <h2>Memories Together</h2>
        <div class="gallery">
          <div class="memory" v-for="(memory, index) in config.memories" :key="index">
            <img :src="getAsset(memory.image)" alt="Memory" />
            <p>{{ memory.description }}</p>
          </div>
        </div>
      </div>
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
    getAsset(path) {
      return require(`../${path}`);
    }
  }
};
</script>

<style scoped>
.greeting-page {
  min-height: 100vh;
  background: url("../assets/hearts-bg.jpg") repeat;
  background-color: #ffccd5;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.card {
  background: rgba(255, 255, 255, 0.95);
  border: 3px solid #ff4081;
  border-radius: 15px;
  padding: 30px;
  max-width: 800px;
  width: 100%;
  text-align: center;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.card h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
  color: #d81b60;
}

.card .message {
  font-size: 1.2rem;
  margin-bottom: 30px;
  color: #555;
}

.section {
  margin-bottom: 30px;
}

.section h2 {
  margin-bottom: 20px;
  color: #d81b60;
}

.gallery {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.gallery img, .memory img {
  border-radius: 5px;
  max-width: 300px;
  width: 100%;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s;
}

.gallery img:hover, .memory img:hover {
  transform: scale(1.05);
}

.memory p {
  margin-top: 10px;
  font-size: 1rem;
  color: #333;
  max-width: 250px;
}
</style>

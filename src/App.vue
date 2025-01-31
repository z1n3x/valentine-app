<template>
  <div id="app">
    <GreetingCard />
  </div>
</template>

<script>
import GreetingCard from "./components/GreetingCard.vue";

export default {
  name: "App",
  components: {
    GreetingCard
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  background: #fafafa;
}
</style>

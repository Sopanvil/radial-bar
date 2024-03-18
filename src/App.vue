<template>
  <div id="app">
    <CircleBar :percentage="percentageValue" />
    <number-input v-model.number="percentageValue" :min="0" :max="1" :step="0.01" inline></number-input>
  </div>
</template>

<script>
import CircleBar from "./components/CircleBar.vue";

export default {
  name: "App",
  data() {
    return {
      percentageValue: 0.4,
    };
  },
  components: {
    CircleBar,
  },
};
</script>

<style>
html {
  padding: 0;
  margin: 0;
  background: #231540;

}
#app {
  margin-top: 60px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>

<template>
  <div class="hello">
    <svg class="stat-circle" width="200" viewBox="0 0 140 140">
      <circle ref="circle" class="bg" cx="70" cy="70" r="52" />
      <circle ref="progress" class="progress" cx="70" cy="70" r="52" stroke-linecap="round" />
      <text x="51%" y="56%">{{ Math.round(percentage * 100) }}%</text>
    </svg>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    percentage: {
      type: Number,
    },
  },
  data() {
    return {
      radius: 0,
      circumference: 0,
    };
  },
  mounted() {
    this.radius = this.$refs.progress.r.baseVal.value;
    this.circumference = 2 * Math.PI * this.radius;
    this.setProgress();
  },
  watch: {
    percentage() {
      this.setProgress();
    },
  },
  methods: {
    setProgress() {
      const offset = this.circumference - this.percentage * this.circumference;
      this.$refs.progress.style.strokeDashOffset = offset;
      this.$refs.progress.style.strokeDasharray = `${this.circumference} ${this.circumference}`;
      this.$refs.progress.style.strokeDashoffset = offset;
    },
  },
};
</script>

<style lang="scss" scoped>
.stat-circle {
  circle.bg {
    fill: none;
    stroke: #4f4466;
    stroke-width: 10;
  }
  circle.progress {
    fill: none;
    stroke: #ebe424;
    stroke-width: 10;
    filter: drop-shadow(0px 0px 4px #ebe424e7);
    transform-origin: center;
    transform: rotate(-90deg);
    transition: 0.3s;
  }
  text {
    font-size: 20px;
    text-anchor: middle;
    fill: #ebe424;
  }
}
</style>

<template>
  <div class="suits-container">
    <div class="suits">
      <svg
        v-for="(suitStyles, i) in suitStyles"
        :key="i"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 100 100"
        :style="suitStyles"
      >
        <path
          opacity="0.1"
          fill="currentColor"
          class="text-white"
          stroke="red"
          d="M 10,30
             A 20,20 0,0,1 50,30
             A 20,20 0,0,1 90,30
             Q 90,60 50,90
             Q 10,60 10,30 z"
        />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({ suitStyles: [] }),
  created() {
    const numSuits = 10;
    const minSize = 10;
    const maxSize = 80;
    const minDuration = 10;
    const maxDuration = 30;
    for (let i = 0; i < numSuits; i++) {
      let size = minSize + Math.random() * (maxSize - minSize);
      let top = Math.random() * window.innerHeight;
      top += "px";
      size += "px";
      let animationDuration =
        minDuration + Math.random() * (maxDuration - minDuration);
      animationDuration += "s";
      let animationDelay = Math.random() * maxDuration;
      animationDelay += "s";
      this.suitStyles.push({
        position: "absolute",
        animationDuration,
        animationDelay,
        width: size,
        height: size,
        top,
      });
    }
  },
};
</script>

<style scoped>
.suits-container {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
.suits {
  position: relative;
  width: 100%;
  height: 100%;
}
.suits svg {
  left: -80px;
  animation: slide-right 5s linear infinite;
}
@keyframes slide-right {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(calc(100vw + 80px));
  }
}
</style>

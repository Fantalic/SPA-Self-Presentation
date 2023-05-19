<template>
    <div>
      <p>
        <span
          v-for="(letter, index) in text"
          :key="index"
          class="letter"
          :style="getAnimationDelay(index)"
        >
          {{ letter }}
        </span>
      </p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        text: "Your animated text",
      };
    },
    methods: {
      getAnimationDelay(index) {
        const delay = index * 0.1 + "s";
        return {
          animationDelay: delay,
        };
      },
    },
  };
  </script>
  
  <style>
  .letter {
    opacity: 0;
    animation: fadeIn 0.5s ease-in-out forwards;
    transform: translateX(100px);
  }
  
  @keyframes fadeIn {
    0% {
      opacity: 0;
      transform: translateX(100px);
    }
    100% {
      opacity: 1;
      transform: translateX(0);
    }
  }
  </style>
  
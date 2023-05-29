<script setup lang="ts">
import { ref } from 'vue'

interface IProps {
  text:string,
  fontSize?:number
}
const props = withDefaults(defineProps<IProps>(),{
  text:"",
  fontSize:0
})

let lines:Ref<string[]> = ref(["hallo ? "]);

function splitTextIntoLines(text:string) {
  lines = ref(text.split("\n"));
}

function getAnimationDelay(letterIndex:number, lineIndex:number) {
  const delay = lineIndex * 0.1 + letterIndex * 0.05 + "s";
  return {
    animationDelay: delay,
  };
}

splitTextIntoLines(props.text)

</script>
<template>
  <div class="aText" :style="(fontSize>0)? `font-size:${props.fontSize}em`:''">
    <p v-for="(line, lineIndex) in lines" :key="lineIndex">
    <span
      v-for="(letter, letterIndex) in line"
      :key="letterIndex"
      class="letter"
      :style="getAnimationDelay(letterIndex, lineIndex)"
    >
      {{ letter }}
    </span>
  </p>
  </div>
</template>

<style>
.letter {
  opacity: 0;
  animation: fadeIn 0.1s ease-in-out forwards;
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
.aText{
  color: honeydew;
  font-size: x-large;
}
</style>

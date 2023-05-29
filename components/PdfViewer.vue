<script setup lang="ts">
import { ref } from 'vue'
import PdfEmbed from 'vue-pdf-embed'

interface IProps {
  pdfUrl:string
}

const props = withDefaults(defineProps<IProps>(), {
  pdfUrl: ""
})

const currentPage = ref(1)
const scale = ref(2)

const nextPage = () => {
  currentPage.value += 1
}

const previousPage = () => {
  currentPage.value -= 1
}

const zoomIn = () => {
  scale.value += 0.1
}

const zoomOut = () => {
  scale.value -= 0.1
}

</script>

<template>
  <div>
    <div class="frame">
      <PdfEmbed :source="pdfUrl" :page="currentPage" :scale="scale" />
    </div>
    <div>
      <button @click="previousPage">Previous</button>
      <button @click="nextPage">Next</button>
      <button @click="zoomIn">Zoom In</button>
      <button @click="zoomOut">Zoom Out</button>
    </div>
  </div>
</template>

<style scoped>
.frame{
  padding: 5rem;
  margin: 5rem ;
}
</style>


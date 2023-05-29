<script setup lang="ts">
import { ref } from 'vue'
import PdfEmbed from 'vue-pdf-embed'

interface IProps {
  pdfUrl:string
  pageCount:number
}

const props = withDefaults(defineProps<IProps>(), {
  pdfUrl: "",
  pageCount:0
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
      <button v-if="currentPage>1" class="b-bl-corner" @click="previousPage">Previous</button>
      <button v-if="props.pageCount != 0 && currentPage < props.pageCount" class="b-br-corner" @click="nextPage">Next</button>
    </div>
    <div>

      <!-- <button @click="zoomIn">Zoom In</button>
      <button @click="zoomOut">Zoom Out</button> -->
    </div>
  </div>
</template>

<style scoped>
.frame{
  padding: 5rem;
  margin: 5rem ;
  position: relative;
}
.b-br-corner{
  position: absolute;
  bottom: 20px;  
  right: 20px; 
}
.b-bl-corner{
  position: absolute;
  bottom:20px;
  left:20px;
}
</style>


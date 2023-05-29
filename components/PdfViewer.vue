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
    </div>
        <button v-if="currentPage>1" class="b b-bl-corner" @click="previousPage">{{"<<< "}}</button>
        <button v-if="props.pageCount != 0 && currentPage < props.pageCount" class="b b-br-corner" @click="nextPage"> >>></button>
    
    <div>

      <!-- <button @click="zoomIn">Zoom In</button>
      <button @click="zoomOut">Zoom Out</button> -->
    </div>
  </div>
</template>

<style scoped>
.frame{
  /* padding: 5rem;
  margin: 5rem ; */
  position: relative;
  max-height: 70vh;
  overflow-y:scroll;
}
.b{
  background-color:#555;
  font-size: 2em;
  color: white;
  transition: opacity 0.3s ease; 
  opacity: 0.6;
  border-radius: 1rem;
}
.b:hover{
  opacity: 1;
}
.b-br-corner{
  position: absolute;
  bottom: 5rem;  
  right: 5rem; 
}
.b-bl-corner{
  position: absolute;
  bottom:5rem;
  left:5rem;
}
</style>


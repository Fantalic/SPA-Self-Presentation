<template>
  <div>
    <pdf-embed :src="pdfUrl" :page="currentPage" :scale="scale" />
    <div>
      <button @click="previousPage">Previous</button>
      <button @click="nextPage">Next</button>
      <button @click="zoomIn">Zoom In</button>
      <button @click="zoomOut">Zoom Out</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import PdfEmbed from 'vue-pdf-embed'

export default {
  components: {
    PdfEmbed
  },
  props: {
    pdfUrl: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const currentPage = ref(1)
    const scale = ref(1)

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

    return {
      currentPage,
      scale,
      nextPage,
      previousPage,
      zoomIn,
      zoomOut
    }
  }
}
</script>
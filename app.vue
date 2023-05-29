<script setup>
import AnimatedText from "@/components/AnimatedText.vue";
import FullscreenScroll from "@/components/FullscreenScroll.vue";
import PdfViewer from '@/components/PdfViewer.vue'

const text = "" + 
  "Hi! \n" + 
  "My name is Wilke Oncken. \n"+
  "I was born in the upper north-west part of germany on the north coast in lower saxony. \n" +
  "This is an SPA ( Single Page application ) I made, to give a small inside in my abilities as an webdeveloper and also to introduce myself with a small presentation.\n" +
  "I started programming, when I was 16 on the 'Fachgymnasium für Informatik' in Aurich. Since I got many interests, I decided late, that I want to focus on programming, to\n"+
  "earn my dayly breed. I am also a musican and martial artist and overall I see myself as an artist, where I also see programming as an creative expression in a way and also\n" +
  "as an art." 

</script>
<template>
  <div style="margin:0; padding:0; box-sizing: border-box;">
    <FullscreenScroll :section-count="6">
      <template #section-slot-1>
        <AnimatedText :text="text"></AnimatedText>
      </template>
      <template #section-slot-2>
        CV here 
        <link rel="icon" href="./public/favicon.ico" /> 
        <PdfViewer pdfUrl="./CV.pdf" />
      </template>
    </FullscreenScroll>
  </div>
</template> 

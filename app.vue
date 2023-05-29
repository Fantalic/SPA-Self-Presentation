<script setup>
import AnimatedText from "@/components/AnimatedText.vue";
import FullscreenScroll from "@/components/FullscreenScroll.vue";
import PdfViewer from '@/components/PdfViewer.vue'
import Lazyload from "@/components/Lazyload.vue";
import Menu from "@/components/Menu.vue"

const text = "" + 
  "Hi! \n" + 
  "My name is Wilke Oncken. \n"+
  "I was born in the upper north-west part of germany on the north coast in lower saxony. \n \n" +
  "This is an SPA ( Single Page application ) I made, to give a small inside in my abilities as an webdeveloper and also to introduce myself with a small presentation.\n" +
  "\n\n"+
  "I started programming, when I was 16 on the 'Fachgymnasium für Informatik' in Aurich. Since I got many interests, I decided late, that I want to focus on programming, to "+
  "earn my dayly breed. I am also a musican and martial artist and overall I see myself as an artist, where I also see programming as an creative expression in a way and also " +
  "as an art." 

</script>
<template>
  <div style="margin:0; padding:0; box-sizing: border-box;">
    <FullscreenScroll :section-count="6" >
      <template #default="{section}">
        <Menu :topic-idx="section"></Menu>
      </template>
      <template #section-slot-1>
        <AnimatedText :text="text" :font-size="0" style="margin:auto; padding: 5rem; margin-top:5rem"/>
      </template>
      <template #section-slot-2>
        <Lazyload v-slot="{isLoaded}">
          <template v-if="isLoaded">
            <PdfViewer 
              class="section-content"
              pdfUrl="./CV.pdf" 
              :page-count="2" 
            />
          </template>
        </Lazyload>
      </template>
      <template #section-slot-3> 
        <iframe class="section-content" src="https://github.com/Fantalic?tab=repositories"></iframe>
      </template>
    </FullscreenScroll>
  </div>
</template> 
<style >
body {
  margin: 0;
  padding: 0;
}
html{
  overflow: hidden;
}
::-webkit-scrollbar {
    width: 0px;
    background: transparent; /* make scrollbar transparent */
}
</style>
<script>
import AnimatedText from "@/components/AnimatedText.vue";

export default {
  components: {
    AnimatedText,
  },
  data() {
    return {
      options: {
        licenseKey: 'YOUR_KEY_HEERE',
        menu: '#menu',
        anchors: ['page1', 'page2', 'page3'],
        sectionsColor: ['#41b883', '#ff5f45', '#0798ec'],
      },
    }
  }
}
</script>
<template>

  <div>
    <!-- <NuxtWelcome /> -->
    <full-page ref="fullpage" :options="options" id="fullpage">
      <div class="section">
        <AnimatedText></AnimatedText> 
      </div>
      <div class="section">Second section ...</div>
    </full-page>
  </div>
</template>

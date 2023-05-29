<script setup lang="ts">

interface IProps {
  sectionCount:number
}

const props = withDefaults(defineProps<IProps>(), {
  sectionCount: 1
})

const currentSectionIdx = ref(1)

const sectionColors =  [
    '#2c3e50', // Dark Blue-Grey
    '#3498db', // Blue
    '#e74c3c', // Red
    '#27ae60', // Green
    '#f39c12', // Orange
    '#9b59b6', // Purple
    '#1abc9c', // Teal
    '#e67e22', // Dark Orange
    '#16a085', // Dark Cyan
    '#c0392b', // Dark Red
]

function scrollToSection(idx:number) {
    if(idx > props.sectionCount || idx < 0 ) return
    currentSectionIdx.value = idx
        const nextSectionElement = document.getElementById(`section-${idx}`);
        if (nextSectionElement) {
            nextSectionElement.scrollIntoView({ behavior: 'smooth' });
        }
}

</script>

<template>
    <div id="FssContainer" >    
      <slot :section="currentSectionIdx" ></slot>
      <div 
          v-for="idx in sectionCount" 
          :key="idx" 
          class="section" 
          :id="`section-${idx}`"
          :style="'background-color:' + sectionColors[idx]"
      > 
          <button v-if="idx > 1" class="scroll-button b-top" @click="scrollToSection(idx-1)">{{"^^^^^"}}</button>
          <div class="frame">
            <slot :name="`section-slot-${idx}`"></slot>
          </div>
          <button v-if="idx < props.sectionCount" class="scroll-button b-bottom" @click="scrollToSection(idx+1)">VVVVV</button>
      </div>
    </div>
</template>
  
<style>
.frame{
  padding: 2rem;
}
.section {
  min-height: 100vh; /* Set section height to full viewport height */
  width: 100%;
  margin:0px;
  padding: 0px;
  outline:none;
  display:inline-block;
  position: relative;
}
.scroll-button {
  position: absolute;
  z-index: 9999; /* Ensure the button appears above other elements */
  display: inline-block;
  padding: 10px 20px;
  border: black;
  border-radius: 4px;
  color: black;  
  font-weight: bold;
  text-decoration: none;
  transition: opacity 0.3s ease; 
  opacity: 0.1;
}
.scroll-button:hover {
  background-color: #555; /* Replace with your chosen hover background color */
  opacity: 1;
  color: #fff; /* Replace with your chosen text color */
  /* Add any additional hover effects here */
}

.b-top{
  right:0;
  top: 0rem;
  width:100%;
  /* padding-top:1.5rem */
}
.b-bottom{
  bottom:0;
  left:0;
  width: 100%;
  /* padding-bottom: 1.5rem; */
}
.section-content{
  margin:2rem; 
  margin-top:7rem
}


</style>
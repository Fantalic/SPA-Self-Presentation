<script setup lang="ts">

interface IProps {
  sectionCount:number
}

const props = withDefaults(defineProps<IProps>(), {
  sectionCount: 1
})

let currentSectionIdx = ref(1); 

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
    currentSectionIdx.value = idx;

    if (currentSectionIdx.value <= props.sectionCount) {
        const nextSectionElement = document.getElementById(`section-${currentSectionIdx.value}`);
        if (nextSectionElement) {
            nextSectionElement.scrollIntoView({ behavior: 'smooth' });
        }
    }
}

</script>

<template>
    <div id="FssContainer" >    
        <!-- <button v-if="currentSectionIdx > 1" class="fixed-button bl-corner" @click="scrollToSection(currentSectionIdx-1)">{{"<<< previous Page"}}</button> -->
        <div 
            v-for="idx in sectionCount" 
            :key="idx" 
            class="section" 
            :id="`section-${idx}`"
            :style="'background-color:' + sectionColors[idx]"
        > 
            <div class="frame">
              <slot :name="`section-slot-${idx}`">hallo</slot>
            </div>
            <button v-if="currentSectionIdx < props.sectionCount" class="fixed-button br-corner" @click="scrollToSection(currentSectionIdx+1)">VVVVV</button>
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
.fixed-button {
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
.fixed-button:hover {
  background-color: #555; /* Replace with your chosen hover background color */
  opacity: 1;
  color: #fff; /* Replace with your chosen text color */
  /* Add any additional hover effects here */
}

.br-corner{
  /* bottom: 20px;  */
  /*right: 20px;  */
  right:0;
  bottom: 0rem;
  width:100%;
  padding-bottom: 1.5rem;
}
.bl-corner{
  bottom:20px;
  left:20px;

}
body {
  margin: 0;
  padding: 0;
}

</style>
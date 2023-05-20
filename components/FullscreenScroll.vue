<script setup lang="ts">
export interface IProps {
    sectionCount:number
}

const props = withDefaults(defineProps<IProps>(), {
  sectionCount: 1
})

let currentSectionIdx = 1; 

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
    currentSectionIdx = idx;

    if (currentSectionIdx <= props.sectionCount) {
        const nextSectionElement = document.getElementById(`section-${currentSectionIdx}`);
        if (nextSectionElement) {
            nextSectionElement.scrollIntoView({ behavior: 'smooth' });
        }
    }
}

</script>

<template>
    <div id="FssContainer" >
        <button class="fixed-button br-corner" @click="scrollToSection(currentSectionIdx+1)">next Page >>></button>
        <button class="fixed-button bl-corner" @click="scrollToSection(currentSectionIdx-1)">{{"<<< previous Page"}}</button>
        <div 
            v-for="idx in sectionCount" 
            :key="idx" 
            class="section" 
            :id="`section-${idx}`"
            :style="'background-color:' + sectionColors[idx]"
        >
          <slot :name="`section-slot-${idx}`">hallo</slot>
        </div>
    </div>
</template>
  
<style>
.section {
    min-height: 100vh; /* Set section height to full viewport height */
    width: 100%;
    margin:0px;
    padding: 0px;
    outline:none;
    display:inline-block;
}
.fixed-button {
  position: fixed;
  z-index: 9999; /* Ensure the button appears above other elements */
  display: inline-block;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  background-color: #333; /* Replace with your chosen background color */
  color: #fff; /* Replace with your chosen text color */
  font-size: 16px;
  font-weight: bold;
  text-decoration: none;
  transition: background-color 0.3s ease; 
}
.fixed-button:hover {
  background-color: #555; /* Replace with your chosen hover background color */
  /* Add any additional hover effects here */
}

.br-corner{
  bottom: 20px; /* Adjust the desired position */
  right: 20px; /* Adjust the desired position */
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
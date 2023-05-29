<script setup lang="ts">
import { vElementVisibility } from '@vueuse/components'

const isLoaded = ref(false)

function onElementVisibility(v:boolean){
    if(v){
        // once visible, stays visible
        isLoaded.value = true;
    }
}

</script>
<template>
<div v-element-visibility="onElementVisibility">
    <slot :isLoaded="isLoaded"></slot>
</div>
</template> 
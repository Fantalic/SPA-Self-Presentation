<script setup lang="ts">
import { vElementVisibility } from '@vueuse/components'

const isVisible = ref(false)

function onElementVisibility(v:boolean){
    if(v){
        // once visible, stays visible
        isVisible.value = true;
    }
}

</script>
<template>
<div v-element-visibility="onElementVisibility">
    <slot :isVisible="isVisible"></slot>
</div>
</template> 
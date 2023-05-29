<script setup lang="ts">
    interface IProps {
        topicIdx:number
    }

    const props = withDefaults(defineProps<IProps>(), {
     topicIdx:1
    })
    const topics = ["Introduction","Curriculum Vitae", "Projects"]
    const opened = ref(false)

</script>
<template>
    <div class="menu">
        <div class="container">
            <button class="m-button" @click="opened=!opened"> <img src="menu.png" width="50" height="50"/></button>
        <!-- <span class="m-header">{{ topics[topicIdx-1] }}</span> -->
        <template  v-for="topic,idx in topics" >
            <AnimatedText
              v-if="topicIdx=== idx+1 "
              :text="topic" 
              :font-size="4"
            />
        </template>
        </div>


        <div v-if="opened">
            hallo 
        </div>
    </div>
    
</template>
<style>
.menu{
  position: fixed;
  z-index: 999;
  margin-top: 3rem;
  margin-left: 2rem;
}
.container{
  display: flex;
  flex-wrap: wrap;
}
.m-button{
  border-radius: 50%;
  height: 4rem;
}
.m-header{
    font-size: 5rem;
}
</style>
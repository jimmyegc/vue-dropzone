<script setup>
import { ref } from 'vue'
import DropZone from './components/DropZone.vue'

let dropzoneFile = ref("")
let previewImage = ref("")

const drop = (e) => {
  dropzoneFile.value = e.dataTransfer.files[0]
  previewImage = URL.createObjectURL(dropzoneFile.value)
}

const selectedFile = () => {
  dropzoneFile.value = document.querySelector('.dropzoneFile').files[0]
  previewImage = URL.createObjectURL(dropzoneFile.value)  
}

</script>

<template>  
  <div class="home">
    <h1>DropZone</h1>
    <DropZone @drop.prevent="drop" @change="selectedFile" />
    <span class="file-info">File: {{ dropzoneFile.name }}</span>      
    <img :src="previewImage" alt="">
  </div>  
</template>

<style scoped lang="scss">
.home {
  height: 100vh; 
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;
  
  h1 {
    font-size: 40px;
    margin-bottom: 32px;
  }
  .file-info {
    margin-top: 32px;
  }
}

</style>

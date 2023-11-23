<script setup>
import { ref } from 'vue'
const active = ref(false)
const toggleActive = () => {
  active.value = !active.value  
}
</script>

<template>
  <div 
    @dragenter.prevent="toggleActive" 
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
    :class="{ 'active-dropzone': active }"
    class="dropzone">
    <span>Drag of Drop File</span>
    <span>OR</span>
    <label for="dropzoneFile">Select File</label>
    <input type="file" id="dropzoneFile" class="dropzoneFile" >    
  </div>  
</template>

<style scoped lang="scss">
.dropzone {
  width: 400px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 16px;
  border: 2px dashed #41b883;
  background-color: white;
  transition: .3s ease all;
  
  label {
    padding: 8px 12px;
    color: #fff;
    background-color:  #41b883;
    transition: .3s ease all;
  }

  input { 
    display: none;
  }

}

.active-dropzone {
  color: #fff;
  border-color: #fff;
  background-color: #41b883;
  
  label {
    background-color: #FFF;
    color: #41b883;
  }
}

</style>


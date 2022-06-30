<template lang="pug">
h1 {{ bigTitle }}
div(style="display: inline-block;")
  input(type="file" id="fileupload" accept="image/gif, image/jpeg, image/png" @Change="uploadImg")
  div
    img.imgBox(:src="objectURL")
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'tesseract-ocr',
  setup () {
    const bigTitle = ref('tesseract-ocr')
    const objectURL = ref(null)

    function uploadImg (img) {
      let file = img.target.files[0];
      objectURL.value = window.URL.createObjectURL(file)
    }

    return {
      bigTitle,
      objectURL,
      uploadImg
    }
  }
}
</script>

<style>
.imgBox {
  height: 500px;
  width: 500px;
  border: solid 1px;
}
</style>
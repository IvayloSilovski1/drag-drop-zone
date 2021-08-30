<template>
  <div class="home">
    <h1>Drag and Drop you file into our DropZone</h1>
    <DropZone @drop.prevent="drop" @change="selectedFile" />
    <span class="file-info">Uploaded File: {{ dropzoneFile.name }}</span>
  </div>
</template>

<script>
import DropZone from "../components/DropZone.vue";
import { ref } from "vue";

export default {
  name: "Home",
  components: {
    DropZone,
  },

  setup() {
    let dropzoneFile = ref("");

    const drop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0];
    };

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".dropzoneFile").files[0];
    };

    return { dropzoneFile, drop, selectedFile };
  },
};
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #f1f1f1;

  h1 {
    margin: 2rem auto;
    font-size: 2rem;
    width: 40rem;
    justify-content: center;
    align-items: center;
    align-self: center;
  }

  .file-info {
    margin-top: 2rem;
  }
}
</style>

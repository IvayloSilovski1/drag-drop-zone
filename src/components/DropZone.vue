<template>
  <div
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @drop.prevent="toggleActive"
    @dragover.prevent
    class="dropzone"
    :class="{ 'active-dropzone': active }"
  >
    <span>Drag or Drop File</span>
    <span> OR </span>
    <label for="dropzoneFile">Select File</label>
    <input type="file" id="dropzoneFile" class="dropzoneFile" />
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "DropZone",
  setup() {
    const active = ref(false);
    const toggleActive = () => {
      active.value = !active.value;
    };
    return { active, toggleActive };
  },
};
</script>


<style scoped lang="scss">
.dropzone {
  width: 40rem;
  height: 20rem;
  background-color: #ccc;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 1rem;
  border: 0.3rem dashed #41b883;
  border-radius: 1.5rem;
  transition: 0.3s ease all;

  label {
    padding: 0.5rem 0.7rem;
    color: #fff;
    background-color: #41b883;
    transition: 0.3s ease all;
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
    background-color: #fff;
    color: #41b883;
  }
}
</style>

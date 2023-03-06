<script setup>
import { ref } from "vue";
const hidden = ref("hidden");
function setHidden() {
  hidden.value = hidden.value == "hidden" ? "" : "hidden";
}
</script>

<template>
  <form>
    <legend>Hidden Input Controls</legend>
    <fieldset class="unique">
      <div class="row">
        <div class="col-auto">
          <label for="hidden-control" class="form-label">Hidden control:</label
          ><br /><input
            id="hidden-control"
            class="form-control"
            :type="hidden"
            value="This was hidden"
          />
        </div>
      </div>
      <button type="button" @click="setHidden()">Press</button>
    </fieldset>
  </form>
</template>

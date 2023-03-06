<script setup>
import { toNumber } from "@vue/shared";
import { ref } from "vue";
const percent = ref(0);
var paused = false;
const text = ref("in Progress");
var interval = window.setInterval(updateVal, 100);
function changeValue(id) {
  if (percent.value > toNumber(document.getElementById(id).value)) {
    percent.value = document.getElementById(id).value;
    paused = true;
    setTimeout(() => {
      paused = false;
    }, 3000);
  } else {
    percent.value = document.getElementById(id).value;
  }
}
function updateVal() {
  if (!paused) {
    if (percent.value < 100) {
      percent.value++;
    }
  }
  text.value = percent.value < 100 ? "in Progress" : "Finished";
}
</script>

<template>
  <form style="user-select: none">
    <legend>Numeric Selection and Display Controls</legend>
    <fieldset>
      <div class="row">
        <div class="col-auto">
          <label for="number-picker" class="form-label">Enter number</label
          ><input
            id="number-picker"
            class="form-control"
            type="number"
            name="num"
            min="1"
            max="100"
            :value="percent"
            @change="changeValue('number-picker')"
          />
        </div>
        <div class="col-auto">
          <label for="percentage" class="form-label">Percentage {{ percent }}</label
          ><input
            id="percentage"
            class="form-range"
            type="range"
            name="percentage"
            min="0"
            max="100"
            :value="percent"
            @input="changeValue('percentage')"
          />
        </div>
      </div>
      <div class="row">
        <div class="col-auto">
          <label id="download-label" for="download-progress" class="form-label"
            >Download {{ text }}</label
          >
          <progress id="download-progress" max="100" :value="percent"></progress>
        </div>
        <div class="col-auto">
          <label for="health" class="form-label">Health</label
          ><meter
            id="health"
            min="00"
            max="100"
            low="25"
            high="75"
            optimum="100"
            :value="percent"
          ></meter>
        </div>
      </div>
    </fieldset>
  </form>
</template>

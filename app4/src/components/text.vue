<script setup>
import { ref, reactive } from "vue";
const textAnim = ref("");
const lorem = reactive({
  p1:
    "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Nunc consequat interdum varius sit. Risus pretium quam vulputate dignissim suspendisse in est ante. Risus commodo viverra maecenas accumsan lacus vel facilisis volutpat est. Sagittis id consectetur purus ut. Magna fermentum iaculis eu non diam phasellus. In nisl nisi scelerisque eu ultrices vitae auctor eu. Sit amet luctus venenatis lectus. Dolor magna eget est lorem ipsum dolor sit. Sem viverra aliquet eget sit amet. Venenatis a condimentum vitae sapien pellentesque habitant. Fringilla phasellus faucibus scelerisque eleifend donec. Sit amet consectetur adipiscing elit ut aliquam purus. Adipiscing at in tellus integer feugiat scelerisque varius morbi enim. Id volutpat lacus laoreet non curabitur gravida arcu ac tortor.",
  p2:
    "Amet nisl suscipit adipiscing bibendum est ultricies. Porta non pulvinar neque laoreet suspendisse. Sit amet cursus sit amet dictum sit. Maecenas ultricies mi eget mauris pharetra et. Sit amet mauris commodo quis imperdiet massa tincidunt nunc. Urna porttitor rhoncus dolor purus non enim. Vel quam elementum pulvinar etiam non quam lacus suspendisse. Libero nunc consequat interdum varius sit amet mattis vulputate. Justo eget magna fermentum iaculis eu non. Nulla facilisi cras fermentum odio eu feugiat pretium nibh ipsum. Sit amet aliquam id diam maecenas ultricies mi eget mauris. Fermentum odio eu feugiat pretium nibh. Massa tincidunt nunc pulvinar sapien et. Id diam vel quam elementum pulvinar etiam. Donec ac odio tempor orci dapibus ultrices in iaculis. Tellus mauris a diam maecenas sed enim ut sem viverra. Amet venenatis urna cursus eget nunc. Eu consequat ac felis donec et. Sociis natoque penatibus et magnis dis parturient montes nascetur.",
  p3:
    "Tincidunt praesent semper feugiat nibh. Enim praesent elementum facilisis leo vel fringilla. Dui sapien eget mi proin sed libero enim sed faucibus. Sapien et ligula ullamcorper malesuada. Non pulvinar neque laoreet suspendisse interdum consectetur libero id. Commodo quis imperdiet massa tincidunt nunc pulvinar. Mattis molestie a iaculis at erat pellentesque adipiscing commodo. Feugiat nibh sed pulvinar proin gravida. Mattis molestie a iaculis at erat pellentesque adipiscing commodo elit. Lorem mollis aliquam ut porttitor. Blandit turpis cursus in hac. Vitae proin sagittis nisl rhoncus mattis rhoncus urna neque viverra.",
});
function toggleAnim() {
  textAnim.value = textAnim.value === "" ? "animated-text" : "";
}
</script>

<template>
  <button @click="toggleAnim()">Toggle</button>
  <div :class="textAnim">
    {{ lorem.p1 }}
    {{ lorem.p2 }}
    {{ lorem.p3 }}
  </div>
</template>

<style>
.animated-text {
  text-transform: uppercase;
  background-image: linear-gradient(
    -225deg,
    #231557 0%,
    #44107a 29%,
    #ff1361 67%,
    #fff800 100%
  );
  background-size: auto auto;
  background-clip: border-box;
  background-size: 200% auto;
  color: #fff;
  background-clip: text;
  text-fill-color: transparent;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: textclip 2s linear infinite;
  display: inline-block;
}

@keyframes textclip {
  to {
    background-position: 200% center;
  }
}
</style>

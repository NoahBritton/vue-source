<script setup>
import Title from "@/components/title.vue";
import Text from "@/components/text.vue";
</script>

<template>
  <header>
    <Title />
  </header>

  <main>
    <Text />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
}
</style>

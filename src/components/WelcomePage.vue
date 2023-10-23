<script setup>
import PaliaMainPage from './palia/Palia_MainPage.vue'
</script>

<template>
  <div class="title">
    Blak Book
  </div>
  <div class="description">
    A site created by "BlakWaltz" that can serve as a helper or a guide to some specific games played by him.
  </div>

  <div class="">
    <!-- buttons -->
  </div>
  <div>
    <PaliaMainPage />
  </div>
</template>

<style scoped>
.title {
  font-size: 1.5rem;
  text-align: left;
  top: -10px;
}

.description {
  font-size: 1.2rem;
  text-align: left;
}

@media (min-width: 1024px) {
  .title {
    text-align: center;
  }

  .description {
    text-align: center;
  }

}
</style>

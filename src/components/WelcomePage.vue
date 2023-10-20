<script setup>
import MainPage from './palia/MainPage.vue'
</script>

<template>
  <div class="gridWrapper">
    <div class="gridMain">
      <div class="title">
        Blak Book
      </div>
      <div class="description">
        A site created by "BlakWaltz" that can serve as a helper or a guide to some specific games played by him.
      </div>
    </div>
    <div class="gridSub">
      <MainPage/>
    </div>
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

  .gridWrapper {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .gridMain {
    grid-column: 1;
    grid-row: 1;
  }

  .gridSub {
    grid-column: 2;
    grid-row: 1;
  }
}
</style>

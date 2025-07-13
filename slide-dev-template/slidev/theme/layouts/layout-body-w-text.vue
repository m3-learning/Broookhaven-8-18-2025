<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
  image: {
    type: String,
    required: false,
  }
})
</script>

<template>
  <div class="slidev-layout mainer">
    <div
      style="
        position: absolute;
        z-index: 100;
        left: 2.5%;
        top: 1%;
        width: 95%;
        height: 10%;
        transform-origin: left left;
        border: 1px solid black;
      "
    >
      <div class="title-large">
        {{  titleText }}
      </div>
    </div>

    <!-- Main Content Section (2/3 Height) -->
    <div class="main-content">
      <div class="image-container">
        <img v-if="image" :src="image" class="proportional-image rounded-2xl border-image" />
        <slot v-else></slot>
      </div>
    </div>

    <!-- Footer Content Section (1/3 Height) -->
    <div class="main-body">
      <slot name="text" />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.mainer {
  @apply h-full w-full relative;
  background-image: url("../assets/Drexel-background.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: grid;
  grid-template-rows: 5% 75% 20%;
  @apply text-center py-15 h-full grid;
}

/* Title Section */
.title-section {
  position: absolute;
  top: 1%;
  left: 2.5%;
  width: 95%;
  height: 10%;
  z-index: 100;
  transform-origin: left left;
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: left;
  text-align: center;
}

/* Main Content Section */
.main-content {
  grid-row: 2;
  @apply border-black overflow-auto;
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Image Container */
.image-container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Proportional Image */
.proportional-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

/* Footer Content Section */
.footer-content {
  grid-row: 3;
  border: 1px solid black;
}
</style>

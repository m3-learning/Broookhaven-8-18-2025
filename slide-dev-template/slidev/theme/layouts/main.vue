<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
})
</script>

<template>
  <div class="slidev-layout custom-layout">
    <div
      style="
        position: absolute;
        z-index: 100;
        left: 2.5%;
        top: 1%;
        width: 95%;
        height: 10%;
        transform-origin: left left;
      "
    >
      <div class="title-large">
        {{  titleText }}
      </div>
    </div>
    <div
      class="main-body"
      style="
        position: absolute;
        top: 13%;
        left: 2.5%;
        width: 95%;
        height: 75%;
        text-align: left;
      "
    >
      <slot />
    </div>
  </div>

  <div class="custom-slide-number">
      <SlideNumber />
  </div>

</template>

<style lang="postcss">
.slidev-layout.mainer {
  background-image: url("../assets/Drexel-background.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  @apply text-center py-15 h-full grid;
}
</style>
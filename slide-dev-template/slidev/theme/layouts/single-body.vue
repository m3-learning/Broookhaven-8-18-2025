<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
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
    <div
      class="main-body"
      style="
        position: absolute;
        top: 13%;
        left: 2.5%;
        width: 95%;
        height: 75%;
        border: 1px solid black;
        text-align: left;
      "
    >
      <slot />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.mainer {
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  @apply text-center py-15 h-full grid;
}
</style>
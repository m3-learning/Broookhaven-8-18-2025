<template>
  <div class="slidev-layout cover">
    <div class="my-auto w-full">
      <slot />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.cover {
  background-image: linear-gradient(rgba(255, 255, 255, 0.7), rgba(255, 255, 255, 0.7)),
    url("../assets/coverimage.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  @apply font-serif grid;
}

.slidev-layout.cover h1 {
  @apply text-6xl leading-tight font-bold text-center;
}

.slidev-layout.cover h1 + p {
  @apply text-2xl -mt-6 text-center;
}
</style>

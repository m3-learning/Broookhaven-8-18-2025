<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
  subtitleText: {
    type: String,
    default: 'Default Subtitle',
  },
  image: {
    type: String,
    required: false,
  },
  lineSpacing: {
    type: [String, Number],
    default: 1.2
  },
  titleHeight: {
    type: [String, Number],
    default: 10
  },
  mainHeight: {
    type: [String, Number],
    default: 65
  },
  footerHeight: {
    type: [String, Number],
    default: 25
  }
})
</script>

<template>
  <div class="slidev-layout mainer" @click.stop>
    <!-- Title Section (Absolutely Positioned) -->
    <div
      style="
        position: absolute;
        z-index: 100;
        left: 2.5%;
        top: 1%;
        width: 95%;
        height: 10%;
        transform-origin: left left;
        /* border: 1px solid black; */
        display: flex;
        align-items: center;
        justify-content: left;
        text-align: center;
      "
    >
      <div class="title-large">
        {{ titleText }}
      </div>
    </div>

    <!-- Subtitle Section -->
    <div class="subtitle-section">
      <div class="subtitle-text">
        {{ subtitleText }}
      </div>
    </div>

    <!-- Main Content Section -->
    <div class="main-content" @click.stop>
      <div class="image-wrapper" @click.stop>
        <div class="image-container" @click.stop>
          <img v-if="image" :src="image" class="proportional-image"/>
          <slot v-else></slot>
        </div>
      </div>
    </div>

    <!-- Footer Content Section -->
    <div class="footer-content" @click.stop>
      <slot name="text" />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.mainer {
  @apply h-full w-full relative;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: grid;
  grid-template-rows: v-bind('`${titleHeight}% ${mainHeight}% ${footerHeight}%`');
  padding-top: v-bind('`${titleHeight}%`');
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* Subtitle Section */
.subtitle-section {
  grid-row: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  border: 1px solid black;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

.subtitle-text {
  @apply text-2xl font-semibold;
  color: #2B90B6;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* Main Content Section */
.main-content {
  grid-row: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
  border: 1px solid black;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* Image Wrapper */
.image-wrapper {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
  border: 1px solid black;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* Image Container */
.image-container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
  border: 1px solid black;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* Proportional Image */
.proportional-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  margin: 0;
  padding: 0;
  border: none !important;
  outline: none !important;
  box-shadow: none !important;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* Footer Content Section */
.footer-content {
  grid-row: 3;
  border: 1px solid black;
  text-align: left;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  padding: 0;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

/* List styling in footer */
.footer-content ul {
  margin: 0;
  padding: 0;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}

.footer-content li {
  line-height: 1.2;
  pointer-events: none;
  user-select: none;
  -webkit-user-select: none;
}
</style>

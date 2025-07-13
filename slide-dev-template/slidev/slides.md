---
# You can also start simply with 'default'
theme: ./theme
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
title: Add Title Here
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade-out
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true

# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# <span style="color:#C5C5C5; -webkit-text-stroke: 1px black; text-shadow: 0 0 40px white;">Here is your title</span>

## <span style="color:#C5C5C5; -webkit-text-stroke: 1px black; text-shadow: 0 0 20px white;">Joshua C. Agar</span>

## <span style="color:#C5C5C5; -webkit-text-stroke: 1px black; text-shadow: 0 0 20px white;">Drexel University</span>

## <span style="color:#C5C5C5; -webkit-text-stroke: 1px black; text-shadow: 0 0 20px white;">Department of Mechanical Engineering and Mechanics</span>

## <span style="color:#C5C5C5; -webkit-text-stroke: 1px black; text-shadow: 0 0 20px white;">{{ new Date().toLocaleDateString() }}</span>

<!-- <div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div> -->

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/m3-learning" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: main
title-text: "Main Slide Layout"
---

# <span v-click="1">Level 1</span>
## <span v-click="2">Level 2</span>
### <span v-click="3">Level 3</span>
#### <span v-click="4">Level 4</span>
##### <span v-click="5">Level 5</span>
###### <span v-click="6">Level 6</span>

<ul>
  <li v-click="3" v-motion="fade">🧑‍💻 - <strong>Developer Friendly</strong> - code highlighting, live coding with autocompletion</li>
  <li v-click="4" v-motion="fade">🤹 - <strong>Interactive</strong> - embed Vue components to enhance your expressions</li>
  <li v-click="5" v-motion="fade">🎥 - <strong>Recording</strong> - built-in recording and camera view</li>
  <li v-click="6" v-motion="fade">📤 - <strong>Portable</strong> - export to PDF, PPTX, PNGs, or even a hostable SPA</li>
  <li v-click="7" v-motion="fade">🛠 <strong>Hackable</strong> - virtually anything that's possible on a webpage is possible in Slidev</li>
</ul>


<p style="text-align: center;">
  Read more about [Why Slidev?](https://sli.dev/guide/why)
</p>

---
layout: main-custom-layout
titleText: "My Title"
subtitleText: "My Subtitle"
image: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
---

::text::
- line 1
- line 2
- line 3

---
layout: main-custom-layout
titleText: "No Subtitle"
image: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
---

::text::
- line 1
- line 2
- line 3


---
layout: two-column
titleText: "Comparison of Methods"
subtitleText: "Experimental vs Simulation"
leftHeading: "Experimental Setup"
rightHeading: "Simulated Model"
leftImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
rightImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
columns: 2
---

::left::


::right::

::text::
- Additional insights and discussions.

---
layout: two-column
titleText: "Comparison of Methods"
subtitleText: "Experimental vs Simulation"
leftHeading: "Experimental Setup"
rightHeading: "Simulated Model"
leftImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
rightImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
columns: 2
---

::left::


::right::

::text::
- Additional insights and discussions.
- 
---
layout: two-column
titleText: "Comparison of Methods"
subtitleText: "Experimental vs Simulation"
rightHeading: "Simulated Model"
leftImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
rightImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
columns: 2
---

::left::


::right::

::text::
- Additional insights and discussions.


---
layout: two-column
titleText: "Comparison of Methods"
subtitleText: "Experimental vs Simulation"
leftImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
rightImage: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
columns: 2
---

::left::


::right::

::text::
- Additional insights and discussions.


---
layout: layout-body-w-text-subtitle
titleText: "My Title"
subtitleText: "Here is some text"
image: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
---

::text::

- athkjkasda
- skdla;sd
- akdlskd
  
---
layout: layout-body-w-text-subtitle
titleText: "My Title"
subtitleText: "My Subtitle"
image: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
lineSpacing: 1.2
mainHeight: 70     # Increase main content height
footerHeight: 30   # Decrease footer height
showSubtitle: false
---

::text::

- First item
- Second item
- Third item

---
layout: ncolumns
titleText: "My Multi-Column Layout"
columns: 3
images: 
  - "https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true"
  - "https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true"
  - "https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true"
titles:
  - "First Image"
  - "Second Image"
  - "Third Image"
---

::text::

Footer content goes here.

---
layout: center
class: text-center
title: Superposition of Equilateral Triangles Filling a Circle
---

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'

const numTriangles = ref(1)
const maxTriangles = 90
const stepSize = 3
const delay = 500 // ms

// Triangle: equilateral, inscribed in unit circle, centered at origin
const baseTriangle = Array.from({ length: 3 }, (_, i) => {
  const theta = i * (2 * Math.PI / 3) - Math.PI / 2
  return [Math.cos(theta), Math.sin(theta)]
})

// Rotate triangle around origin
function rotateTriangle(tri: number[][], angle: number) {
  return tri.map(([x, y]) => [
    Math.cos(angle) * x - Math.sin(angle) * y,
    Math.sin(angle) * x + Math.cos(angle) * y,
  ])
}

// Compute rotated copies
const rotatedTriangles = computed(() => {
  const step = (2 * Math.PI) / numTriangles.value
  return Array.from({ length: numTriangles.value }, (_, i) =>
    rotateTriangle(baseTriangle, i * step)
  )
})

// Animation loop
let intervalId: number | null = null
onMounted(() => {
  intervalId = window.setInterval(() => {
    if (numTriangles.value < maxTriangles) {
      numTriangles.value += stepSize
    } else if (intervalId !== null) {
      clearInterval(intervalId)
    }
  }, delay)
})

onUnmounted(() => {
  if (intervalId !== null) clearInterval(intervalId)
})
</script>

<svg width="500" height="500" viewBox="-1.2 -1.2 2.4 2.4">
  <circle cx="0" cy="0" r="1" fill="none" stroke="#ccc" stroke-width="0.005" />
  <g>
    <transition-group name="fade" tag="g">
      <polygon
        v-for="(tri, i) in rotatedTriangles"
        :key="i"
        :points="tri.map(p => p.join(',')).join(' ')"
        fill="#FFD700"
        stroke="none"
      />
    </transition-group>
  </g>
</svg>

::text::
_Automated animation: triangle superposition filling a circle._





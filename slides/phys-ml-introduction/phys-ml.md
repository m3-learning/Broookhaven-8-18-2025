---
layout: main-custom-layout
titleText: "JPEG Compression"
mainHeight: 40
textboxHeight: 25
reference: "https://medium.com/geekculture/how-jpeg-compression-works-a751cd877c8c"
---

<CrossfadeImages :images="[
  'jpeg-compression.gif',
  'compressed-pld.jpg',
  'DCT-art.jpg'
]" />

<template #text>
<div class="text-left">
  <ul class="list-disc pl-4">
    <li>JPEG Compression: replicates images by decomposing them into a sum of basis images of the discrete cosine transform (DCT) --> There is no understanding of the image</li>
    <li> Neural Networks: can learn to reconstruct images from a compressed representation --> We need physics to make extrapolations from learned representations</li>
  </ul>
</div>
</template>

---
layout: main-custom-layout
titleText: "Physics-Informed Machine Learning"
mainHeight: 50
textboxHeight: 15
---

<CrossfadeImages :images="[
  'physics-informed-neural-network.png'
]" />

<template #text>
<div class="text-left">
  <ul class="list-disc pl-4">
    <li>We want to ensure parsimony of the learned representation --> Therefore we need to include physics in the learning process</li>
  </ul>
</div>
</template>

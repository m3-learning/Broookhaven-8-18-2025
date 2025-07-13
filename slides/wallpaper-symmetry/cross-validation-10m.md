---
layout: ncolumns
titleText: "Cross Validation: 10M Training Images"
columns: 3
images:
  - sym/confusion_matrix/10m train.svg
  - sym/confusion_matrix/10m valid.svg
  - sym/confusion_matrix/10m atoms.svg
titles:
  - "Training"
  - "Validation"
  - "Cross Validation"
titleClicks: [1, 2, 3]
columnWidths: [1,1,1]
textboxHeight: 15
mainHeight: 50
---

<template #col0-text>
<div class="text-center text-sm">
  Training data is used to fit the model parameters
</div>
</template>

<template #col1-text>
<div class="text-center text-sm">
  Validation data helps tune hyperparameters and prevent overfitting
</div>
</template>

<template #col2-text>
<div class="text-center text-sm">
  K-fold cross validation provides more robust performance estimates
</div>
</template>

<template #text>
<div v-click="3" class="text-left">
  <ul class="list-disc pl-4">
    <li>10M vision transformers start to learn robust understanding of symmetry within statistical bounds of the training dataset</li>
    <li>Massive scale data not typical in materials science or chemistry is required</li>
  </ul>
</div>
</template>

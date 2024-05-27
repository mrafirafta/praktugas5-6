<!-- src/components/InfoComponent.vue -->
<template>
    <div class="info-container row justify-around items-center q-gutter-md">
      <q-item>
        <q-item-section avatar>
          <q-icon name="mdi-star" color="yellow" />
        </q-item-section>
        <q-item-section>
          <div class="text-h6">4.8</div>
          <div class="text-caption text-green">Cek ulasan</div>
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section avatar>
          <q-icon name="mdi-map-marker" color="red" />
        </q-item-section>
        <q-item-section>
          <div class="text-h6">4.79 km</div>
          <div class="text-caption text-green">Jarak</div>
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section avatar>
          <q-icon name="mdi-currency-usd" />
        </q-item-section>
        <q-item-section>
          <div class="text-h6">16rb-40rb</div>
          <div class="text-caption text-green">$$$$</div>
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section avatar>
          <q-icon name="mdi-thumb-up" color="red" />
        </q-item-section>
        <q-item-section>
          <div class="text-h6">5 rating</div>
          <div class="text-caption text-green">Rasa enak</div>
        </q-item-section>
      </q-item>
    </div>
  </template>
  
  <script>
  export default {
    name: 'InfoComponent'
  };
  </script>
  
  <style scoped>
  .info-container {
    background-color: white;
    padding: 10px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  </style>
  
<template>
  <q-layout view="hHh lpR fFf">
    <!-- Left Drawer -->
    <q-drawer v-model="leftDrawerOpen" side="left" bordered class="bg-grey-1">
      <q-list>
        <q-item-label header>Navigation</q-item-label>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            Home
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="shopping_cart" />
          </q-item-section>
          <q-item-section>
            Cart
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="info" />
          </q-item-section>
          <q-item-section>
            About
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <!-- Navbar -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          Sekarsa Coffe & Space
        </q-toolbar-title>
        <q-btn dense flat round icon="shopping_cart" />
      </q-toolbar>
    </q-header>

    <!-- Main Content -->
    <q-page-container>
      <q-page padding class="q-pa-md">
        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          arrows
          infinite
          animated
          control-color="black"
          swipeable
          transition-prev="slide-right"
          transition-next="slide-left"
          height="590px"
          class="bg-dark text-white shadow-2 rounded-borders"
        >
          <q-carousel-slide v-for="(image, index) in carouselImages" :key="index" :name="index" :img-src="image">
          </q-carousel-slide>
        </q-carousel>

        <!-- Info Component -->
        <info-component class="q-my-md" />

        <!-- Cards -->
        <div class="q-mt-xl row justify-center">
          <q-card v-for="(product, index) in products" :key="product.name" class="my-card q-mb-xl q-pa-md col-xs-12 col-sm-6 col-md-4 col-lg-3">
            <q-img :src="product.image" :alt="product.name" class="my-card-img">
              <q-badge color="red" floating>{{ product.discount }} Diskon</q-badge>
            </q-img>
            <q-card-section>
              <div class="text-h6 text-center">{{ product.name }}</div>
              <div class="text-subtitle1 text-center">{{ product.price }}</div>
            </q-card-section>
            <q-card-actions align="center">
              <q-btn flat label="Tambah" color="primary" />
              <q-btn flat icon="delete" color="red" @click="deleteProduct(index)" />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-Brown-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          &copy; Sekarsa Coffe & Space
        </q-toolbar-title>
        <div>
          <q-btn flat round icon="facebook" />
        </div>
        <div>
          <q-btn flat round icon="telegram" />
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue';
import InfoComponent from './InfoComponent.vue';

export default {
  components: {
    InfoComponent
  },
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref(0);
    const carouselImages = [
      'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/615ce689-a134-4666-a968-1ef37678313d_Go-Biz_20240324_120838.jpeg?auto=format',
      'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/5612ca56-9f72-4af7-992d-5cebac4b6566_Go-Biz_20240324_121117.jpeg?auto=format',
      'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/08aaaaba-96b9-46ff-be22-45340c74ceb9_Go-Biz_20240324_120928.jpeg?auto=format',
      'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/cbc68610-79d5-4584-ad71-c1b5d615f238_Go-Biz_20240324_121047.jpeg?auto=format'
    ];
    const products = ref([
      { name: 'Sekarsa', price: 'Rp. 20.000', image: 'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/615ce689-a134-4666-a968-1ef37678313d_Go-Biz_20240324_120838.jpeg?auto=format', discount: '5%' },
      { name: 'Selaksa', price: 'Rp. 25.000', image: 'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/5612ca56-9f72-4af7-992d-5cebac4b6566_Go-Biz_20240324_121117.jpeg?auto=format', discount: '5%' },
      { name: 'Serasa', price: 'Rp. 25.000', image: 'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/08aaaaba-96b9-46ff-be22-45340c74ceb9_Go-Biz_20240324_120928.jpeg?auto=format', discount: '10%' },
      { name: 'Seaksara', price: 'Rp. 25.000', image: 'https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/cbc68610-79d5-4584-ad71-c1b5d615f238_Go-Biz_20240324_121047.jpeg?auto=format', discount: '5%' }
    ]);

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    const deleteProduct = (index) => {
      products.value.splice(index, 1);
    };

    return {
      leftDrawerOpen,
      toggleLeftDrawer,
      slide,
      carouselImages,
      products,
      deleteProduct
    };
  }
};
</script>

<style>
.my-card {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
.my-card-img {
  border-radius: 10px 10px 0 0;
  height: 200px;
}
.rounded-borders {
  border-radius: 10px;
}
.q-footer {
  border-top: 1px solid #003285;
}
</style>

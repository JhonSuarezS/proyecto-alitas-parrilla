<template>
  <div class="home">
    <div>
      <NavBar></NavBar>
    </div>
    <div>
      <SideBar></SideBar>
    </div>
    <div>
      <CartShop></CartShop>
    </div>
  </div>
</template>

<script lang="ts">
import NavBar from '@/components/NavBar.vue';
import Vue from 'vue';
import CartShop from '@/components/CartShop.vue';
import SideBar from '@/components/SideBar.vue';

export default Vue.extend({
  name: 'HomeView',
  components: {
    NavBar,
    CartShop,
    SideBar
},
});
</script>

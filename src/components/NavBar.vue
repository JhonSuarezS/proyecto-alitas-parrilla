<template>
  <div class="container-navbar container-fluid">
   <div class="container py-2">
     <nav class="navbar navbar-collapse navbar-dark">
         <div class="contain">
          <b-row>
            <b-col cols="1">
               <span class="float-start">
                 <button class="navbar-toggler" type="button" @click.prevent="showOffcanvasMenu()">
                     <span class="navbar-toggler-icon"></span>
                 </button>
             </span>
            </b-col>
            <b-col cols="5">
            </b-col>
            <b-col cols="5">
              <div class="input-group margin-nav nav">
                <input type="search" class="form-control" placeholder="Buscar producto" aria-label="Recipient's username" aria-describedby="basic-addon2">
                <button class="btn btn-danger" type="button">Buscar</button>
              </div> 
            </b-col>

            <b-col cols="1">
              <span class="float-start">
                  <button class="icon-car navbar-toggler" type="button" @click.prevent="showOffcanvasCart()">
                  <b-icon icon="cart3" font-scale="2" class=""></b-icon>
                  <span class="total-quantity">{{ totalQuantity }}</span> 
                  </button>   
                </span> 
            </b-col>
            
          </b-row>  
         </div>
         <div class="offcanvas offcanvas-start" aria-labelledby="offcanvasWithBackdropLabel" id="offcanvasWithBackdrop" :class="showMenu ? 'show' : ''" tabindex="-1" :style="{ visibility: showMenu ? 'visible' : 'hidden' }">
             <div class="offcanvas-header">
                 <h5 class="offcanvas-title-center" id="">Alitas Parrilla</h5>
                 <button type="button" class="btn-close text-reset" @click.prevent="showOffcanvasMenu()"></button>
             </div>
             <div class="offcanvas-body">
              <img src="@/assets/img/Logo-Parrilla.jpg" class="img-fluid container-img-sidebar"  alt="Responsive image">
                 <ul>
                  <li class="link"><router-link to="/"><button  type="button" class="btn btn-dark button-navbar"><b-icon icon="house"></b-icon>    Inicio</button></router-link></li>
				          <li class="link"><router-link to="/carta"><button type="button" class="btn btn-dark button-navbar"><b-icon icon="menu-button-wide-fill"></b-icon>    Menú</button></router-link></li>
                  <li class="link"><button type="button" class="btn btn-dark button-navbar"><b-icon icon="telephone"></b-icon>   Domicilios</button></li>
                 </ul>
             </div>
             <div class="style"></div>
         </div>

         <div class="offcanvas offcanvas-end" aria-labelledby="offcanvasWithBackdropLabel" id="offcanvasWithBackdrop" :class="showCart ? 'show' : ''" tabindex="-1" :style="{ visibility: showCart ? 'visible' : 'hidden' }">
             <div class="offcanvas-header">
                 <h5 class="offcanvas-title-center" id="">Mi Carrito</h5>
                 <button type="button" class="btn-close text-reset" @click.prevent="showOffcanvasCart()"></button>
             </div>
             <div class="offcanvas-body">
              <img src="@/assets/img/Logo-Parrilla.jpg" class="img-fluid container-img-cart"  alt="Responsive image">
             <ul>
				     <li :key="cart.name" v-for="cart in $store.state.cart">
				     	{{ cart.name }}
				     </li>
			       </ul>
             </div>
             <div class="style"></div>
         </div>
     </nav>
    </div>
  </div>
</template>

<script lang="ts">
import '@/assets/estilos/navbar.css'
import inventory from './../database/menu.json'
export default {
    name: 'NavBar',
    components:{
    
    },
     data(){
        return {
          showMenu: false,
          showCart: false,
          products:[],
        }
    },
    methods: {
        showOffcanvasMenu(){
            this.showMenu ? this.showMenu = false : this.showMenu = true;
        },
        showOffcanvasCart(){
            this.showCart ? this.showCart = false : this.showCart = true;
        },
        totalQuantity() {
        return this.products.reduce(
        (total, product) => total + product.quantity,
        0
      )
    }
    }
}
</script>


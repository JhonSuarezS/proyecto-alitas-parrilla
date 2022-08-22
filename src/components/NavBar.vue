<template>
  <div class="container-navbar container-fluid">
   <div class="container py-2">
     <nav class="navbar navbar-collapse navbar-dark">
         <div class="contain">
          <b-row>
            <b-col>
               <span class="float-start">
                 <button class="navbar-toggler" type="button" @click.prevent="showOffcanvasMenu()">
                     <span class="navbar-toggler-icon"></span>
                 </button>
             </span>
            </b-col>
            <b-col>
              <img src="@/assets/img/logo_alitas.jpg" class="img-fluid container-img-navbar"  alt="Responsive image">
            </b-col>
            <b-col>
              <div class="input-group margin-nav">
                <input type="search" class="form-control" placeholder="Buscar producto" aria-label="Recipient's username" aria-describedby="basic-addon2">
                <button class="btn btn-danger" type="button">Buscar</button>
                <button><p class="h2 mb-2"><b-icon icon="cart3" font-scale="1" class=""></b-icon></p></button>
              </div>
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
                  <li class="link"><button  type="button" class="btn btn-dark button-navbar"><b-icon icon="house"></b-icon>    Inicio</button></li>
                  <li class="link"><button type="button" class="btn btn-dark button-navbar"><b-icon icon="menu-button-wide-fill"></b-icon>    Menú</button></li>
                  <li class="link"><button type="button" class="btn btn-dark button-navbar"><b-icon icon="telephone"></b-icon>   Domicilios</button></li>
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
export default {
    name: 'NavBar',
     data(){
        return {
          showMenu: false
        }
    },
    methods: {
        showOffcanvasMenu(){
            this.showMenu ? this.showMenu = false : this.showMenu = true;
        }
    }
}
</script>


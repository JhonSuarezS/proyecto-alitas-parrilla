<template>
  <div class="home">
    <div>
      <NavBar />
    </div>
	<div class="container-fluid no-padding no-margin">
		<div class="header-bg">
			<h1>Alitas a la parrilla</h1>
			<h5>Te llevamos el menu hasta tu casa</h5>
			<router-link to="/carta"><button class="btn btn-alitas">  Conoce nuestro Menú</button></router-link>
		</div>
	</div>
	<div class="catalogo">
		<div class="container">
			<div class="row">
				<div class="col-lg-4" :key="item.id" v-for="item in products">
					<Item 
						@showModalItem="variableProducto"
						:name="item.title"
						:price="item.price"
						:image="item.image"
						:item="item"
					/>
				</div>
			</div>
		</div>
	</div>
		<b-modal v-model="modalShow" hide-footer>
			<template #modal-title>
				<img :src="selectedItem.image" style="width:150px;display:block;margin:auto" alt="">
				<h3>{{ selectedItem.title }}</h3>
				<h5>por tan solo: <b> {{ selectedItem.price }} </b></h5>
			</template>
			<div class="d-block text-center">
				<span class="badge badge-warning">{{ selectedItem.category }}</span>
				<p>{{ selectedItem.description }}</p>
			</div>
			<b-button class="mt-3" block @click="modalShow = false">Cancelar</b-button>
		</b-modal>
  </div>
</template>

<script lang="ts">
import NavBar from '@/components/NavBar.vue';
import Vue from 'vue';
import CartShop from '@/components/CartShop.vue';
import SideBar from '@/components/SideBar.vue';
import Item from '@/components/itemDetails.vue'
import './../assets/estilos/home.css'

export default Vue.extend({
	name: 'HomeView',
	components: {
		NavBar,
		CartShop,
		SideBar,
		Item
	},
	data(){
		return {
			products : [],
			modalShow: false,
			selectedItem:{
				title:'',
				category:'',
				description:'',
				price:'',
				image:''
			}
		}
	},	
	methods:{
		getProduct(){
			fetch('https://fakestoreapi.com/products')
            .then(res=>res.json())
            .then((json)=>{
					this.products = json
					console.log(this.products)
				}
			)
		},
		variableProducto(item: any){
			console.log(item)
			this.selectedItem = item
			this.modalShow = true
		}
	},
	mounted(){
		this.getProduct()
	}
});
</script>

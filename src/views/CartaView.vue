<template>
	<div>
		<NavBarVue />
		<div class="container-fluid">
			<div class="row">
				<div class="col-lg-12">
					<h1 class="text-center"> Descubre el Menu </h1>
					<div class="text-center">
						<span class="badge badge-pill badge-alitas" v-bind:key="cat" v-on:click="filterCategory(cat)" v-for="cat in categories">{{ cat }}</span>
					</div>
				</div>
				<div class="">
					<div class="row" v-bind:key="product.categoria" v-for="product in products">
						<div class="col-lg-12">
							<h5>{{ product.categoria }}</h5>
						</div>
						<hr>
						<div class="col-lg-4 container-carta " v-bind:key="details.name" v-for="details in product.value">
							<div class="products-item">
								<div class="add-cart-item">
											<!--<button v-if="counter > '0'" class="btn btn-alitas left" @click="counter--">-</button>
									        
											<span style="margin: 10%; ">{{counter}}</span>
											
											<button class="btn btn-alitas right" @click="counter++"> +</button>-->
																		
											<button type="button" class="btn btn-warning" @click="addToCart(details), totalQuantity()" title="Agregue producto al carrito">+</button>
										</div>	
								<div class="row">
									<div class="col-lg-4" style="">
										<img :src="assets+details.img" class="img-product img-fluid" alt=""/>
									</div>
									<div class="col-lg-8">
										<p class="title-product">{{ details.name }}</p>
										<p class="price-product">{{ formatNumber((parseFloat(details.value).toFixed(2))) }}</p>
										<small>{{ details.desc }}</small>
									</div>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import '../assets/estilos/Carta.css'
import inventory from './../database/menu.json'
import NavBarVue from '@/components/NavBar.vue'
import NavBar from '@/components/NavBar.vue'
export default {
	name: "Menu",
	components:{
		NavBarVue,
		NavBar
	},
	data() {
		return {
			categories:[],
			products:[],
			assets:'../assets/img/',
			counter: 0,
		}
	},
	methods:{
		getCategories(){
			console.log(inventory.categorias)
			inventory.categorias.map((c) => this.categories.push(c))
		},
		filterCategory(category){
			//console.log(inventory.productos)
			this.products = []
			inventory.productos.map((v) => {
				if (v.categoria.toLowerCase() == category.toLowerCase()) {
					let struct = {
						categoria:v.categoria,
						value:v.value
					}	
					this.products.push(struct)
				}
			})
			//inventory.productos.filter(x => x.categoria.toLowerCase().indexOf(category.toLocaleLowerCase()) > -1)
			console.log(this.products)
		},
		formatNumber(number){
			return Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(number)
		},
		getProducts(){
			this.products = inventory.productos
		},
		addToCart(details){
			this.$store.state.cart.push(details)
		},
	},
	mounted(){
		this.getCategories()
		this.getProducts()
	}
}
</script>
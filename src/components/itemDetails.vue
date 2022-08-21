<template>
	<div class="item">
		<div class="card">
			<div class="card-image">
				<img :src="image" alt="" class="card-img-top">
			</div>
			<div class="card-body">
				<p class="title-products">{{ name.substring(0,20) }}</p>
				<p>por {{ price }}</p>
				<button class="btn btn-alitas" @click="showModalItem(item)">
					Comprar ahora
				</button>
			</div>
		</div>
	</div>
</template>

<script lang="ts">
	import Vue from 'vue'
	import './../assets/estilos/itemDetails.css'
	export default {
		name:'Item',
		props: {
			name:{
				type: String,
				required: true,
			},
			price:{
				type: Number,
				required: true,
			},
			image: {
				type: String,
				required: true,
			},
			item: {
				type:Object,
				required: true,
			}
		},
		data() {
			return {
				params:{}
			}
		},
		methods: {
			showModalItem(item: any) {
				this.$emit('showModalItem', item)
			}	
		}
	}
</script>
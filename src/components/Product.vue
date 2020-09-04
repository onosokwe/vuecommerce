<template>
	<div class="card mb-4">
		<div class="card-body text-center">
			<h5 class="text-center card-title">
				{{ product.title }}
			</h5>
			<p class="text-center text-muted card-text display-6">
				$ {{ product.price }}
			</p>
			<button 
				:disabled="isInCart"
				@click="$emit('add-to-cart', product)"
				class="btn btn-primary text-center">
				{{ isInCart ? "Added to Cart" : "Add To Cart" }}
			</button>
		</div>
	</div>
</template>

<script>
export default {
	props:['product', 'isInCart']
}
</script>
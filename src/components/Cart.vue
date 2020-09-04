<template>
	<h4 class="text-center display-6">Cart</h4>
	<ul class="list-group">
		<li class="list-group-item" v-for="item in items" :key="item.id">
			{{ item.title }} - $ {{ Number(item.price, 2) }}
			<button 
				@click="$emit('remove-from-cart', item)"
				class="btn badge btn-danger float-right">
				Remove from Cart
			</button>
		</li>
	</ul>
	<div class="card p-3 my-5" v-if="total">
		<h4 class="text-center"> $ {{ total }} </h4>
		<button 
			@click="$emit('pay')" 
			class="btn btn-block btn-success"
			:disabled="items.length === 0">
			Pay Now
		</button>
	</div>
</template>

<script>

export default {
	props: ['items'],
	computed: {
		total(){
			return this.items.reduce((acc, item) => acc + Number(item.price, 2), 0) 
		}
	}
}
</script>
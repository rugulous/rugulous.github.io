<script setup>
defineProps({
	item: {
		type: Object,
		required: true
	}
});

function formatIngredients(list) {
	const ingredients = list.map(i => i.title).join(", ");

	const lastComma = ingredients.lastIndexOf(",");
	if(lastComma > -1){
		return ingredients.slice(0, lastComma) + " and" + ingredients.slice(lastComma + 1);
	}

	return ingredients;
}

function isInStock(item) {
	return !item.ingredients.some(i => !i.inStock);
}
</script>

<template>
	<div class="mb-3" :class="{'no-stock': !isInStock(item)}">
		<p class="lead mb-0">{{ item.title }} <span v-if="!isInStock(item)" class="text-danger">Out of Stock</span></p>
		<small class="d-block text-secondary mb-2">Contains {{ formatIngredients(item.ingredients) }}</small>

		
			<p class="m-0" v-for="variant in item.variants"><strong>{{ variant.name }}</strong> {{ variant.price }}</p>

	</div>
</template>

<style scoped>
	.no-stock{
		border: 1px solid #F00;
		background-color: rgba(255,0,0,0.1);
	}
</style>
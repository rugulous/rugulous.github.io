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
	<div class="mb-3">
		<p class="lead mb-0">{{ item.title }} <span v-if="!isInStock(item)" class="text-danger">Out of Stock</span></p>
		<small class="text-secondary">Contains {{ formatIngredients(item.ingredients) }}</small>
	</div>
</template>
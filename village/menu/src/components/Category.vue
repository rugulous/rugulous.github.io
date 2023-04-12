<script setup>
import Item from './Item.vue';

defineProps({
	title: {
		type: String,
		required: true
	},
	items: {
		type: Array,
		required: true
	}
});

function formatTitle(title){
	const result = title.replace(/([A-Z])/g, " $1");
	return result.charAt(0).toUpperCase() + result.slice(1);
}

</script>

<template>
	<div class="mb-5">
	<h2 class="display-4">{{ formatTitle(title) }}</h2>
	<Item v-for="item in items" :item="item" />
	</div>
</template>

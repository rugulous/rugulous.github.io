<script setup>
import Category from './components/Category.vue';

let menu = [];
let loading = true;

fetch('menu.json').then(res => res.json()).then(json => {
	console.log(json);
	loading = false;
});
</script>

<template>
	<div class="container d-flex flex-column h-100" v-if="loading">
		<div class="rainbow-spinner main-loader">
			<div class="spinner-grow" role="status">
				<span class="visually-hidden">Loading...</span>
			</div>
		</div>
	</div>

	<div class="container" v-if="!loading">
		<h1 class="display-2 text-center">Menu</h1>
	</div>
</template>
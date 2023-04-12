<script setup>
import {reactive} from 'vue';
import Category from './Category.vue'

const emit = defineEmits(['loaded']);
const data = reactive({
	loaded: false,
	menu: {}
});

data.menu = await fetch('menu.json').then(res => res.json());
emit('loaded');
data.loaded = true;
</script>

<template>
	<div class="container" v-if="data.loaded">
		<h1 class="display-2 text-center mb-5 pt-3">Menu</h1>

		<Category v-for="key in Object.keys(data.menu)" :title="key" :items="data.menu[key]" />

		<button class="btn btn-light chooser">Help Me Decide!</button>
	</div>
</template>

<style scoped>
	.container{
		padding-bottom: 2rem;
	}

	.chooser{
		position: fixed;
		bottom: 0;
		width: 100%;
		left: 0;
	}
</style>
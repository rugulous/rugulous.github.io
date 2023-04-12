<script setup>
import {reactive} from 'vue';

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
		<h1 class="display-2 text-center">Menu</h1>
	</div>
</template>
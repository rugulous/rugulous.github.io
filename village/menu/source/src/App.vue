<script setup>
import {reactive} from 'vue';

import Loader from './components/Loader.vue';
import Menu from './components/Menu.vue';

const data = reactive({
	loading: true
});
</script>

<template>
	<Loader :loading="data.loading" />

	<Suspense>
		<Menu @loaded="data.loading = false" />
	</Suspense>
</template>
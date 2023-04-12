<script setup>
defineProps({
  loading: {
    type: Boolean,
    required: true
  }
})
</script>

<template>
	<div class="container d-flex flex-column h-100" v-if="loading">
		<div class="rainbow-spinner main-loader">
			<div class="spinner-grow" role="status">
				<span class="visually-hidden">Loading...</span>
			</div>
		</div>
	</div>
</template>
<script setup>
import {onMounted} from 'vue';

onMounted(() => {
	const script = document.createElement("script");
	script.src = "bootstrap.min.js";
	document.body.appendChild(script);
	script.addEventListener("load", () => {
		modal = new bootstrap.Modal(document.getElementById("chooserModal"));
	})
})

let modal = null;

function show(menu) {
	modal.show();
}

defineExpose({
	show
});
</script>

<template>
	<div class="modal fade" id="chooserModal" tabindex="-1" aria-labelledby="chooserModalLabel" aria-hidden="true">
		<div class="modal-dialog">
			<div class="modal-content bg-dark">
				<div class="modal-header">
					<h1 class="modal-title fs-5" id="chooserModalLabel">Help Me Decide!</h1>
					<button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
				</div>
				<div class="modal-body">
					You should drink <strong>Vodka Coke</strong>
				</div>
				<div class="modal-footer">
					<button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
				</div>
			</div>
		</div>
	</div>
</template>
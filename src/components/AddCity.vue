<template>

<div id="exampleModal">
	<div class="modal-dialog" role="document">
		<div class="modal-content">
			<div class="modal-body">
				<input type="text" placeholder="Enter city name...">
			</div>
			<div class="modal-footer">
				<button type="button" class="btn btn-secondary" @click="handleClose()">Cancel</button>
				<button type="button" class="btn btn-success">Finish</button>
			</div>
		</div>
	</div>
</div>

</template>

<script>
	export default {
		name: 'AddCity',
		methods:{
			handleClose() {
				this.$emit("close");
			}
		}

	}
</script>
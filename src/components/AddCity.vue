<template>

<div id="exampleModal">
	<div class="modal-dialog" role="document">
		<div class="modal-content">
			<div class="modal-body">
				<input type="text" v-model="city" placeholder="Enter city name...">
			</div>
			<div class="modal-footer">
				<button type="button" class="btn btn-secondary" @click="handleClose()">Cancel</button>
				<button type="button" class="btn btn-success" @click="handleAddCity()">Finish</button>
			</div>
		</div>
	</div>
</div>

</template>

<script>
	export default {
		name: 'AddCity',
		data() {
			return {
				city: "",
			}
		},
		methods:{
			handleClose() {
				// trigger close modal in parent component
				this.$emit("close");
			},
			handleAddCity() {
				// check if there is any cities in local storage
				var existingEntries = JSON.parse(localStorage.getItem("cities"));

				if (existingEntries == null) existingEntries = [];
				if (this.city != "") {
					// add city to existing array
					existingEntries.push(this.city)

					// save to localstorage
					localStorage.setItem("cities", JSON.stringify(existingEntries));

					// trigger refresh list in parent component
					this.$emit("refresh")
				} else { alert("Field city can not be empty."); }
				
			}
		}

	}
</script>
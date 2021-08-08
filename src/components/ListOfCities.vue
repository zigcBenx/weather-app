<template>
	<div class="main">
		<div class="select-city">
			<div class="select-wrapper" v-if="cities.length > 0">
				<select>
					<option v-bind:key="city" v-for="city in cities">{{city}}</option>
				</select>
			</div>

			<div v-else>No cities</div>

			<button class="btn btn-primary add-city" @click="toggleModal">Add city</button>
		</div>

		<AddCity v-if="showModal" @close="toggleModal" @refresh="updateCityList"/>
	</div>
</template>

<script>
	import AddCity from './AddCity.vue'
	export default {
		name: 'ListOfCities',
		components: {
			AddCity,
		},
		props: {},
		data() {
			return {
				cities: [],
				showModal: false
			}
		},
		mounted(){
			// call method for gathering cities from storage
			this.updateCityList()
		},
		methods:{
			toggleModal() {
				// toggle modal for adding new city
				this.showModal = !this.showModal;
			},
			updateCityList() {
				// get city list from local storage
				var cities = JSON.parse(localStorage.getItem("cities"));

				if (cities.length > 0) {
					this.cities = cities;
				}

				// close modal
				this.showModal = false;
			}
		}
	}
</script>

<style scoped>
select {
	display: inline-block;
	padding: 10px;
	color: #313131;
	font-size: 20px;
	border:none;
	outline: none;
	background: none;

	box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
	background-color: rgba(255, 255, 255, 0.5);
	transition: 0.4s;
}

.add-city {
	font-size: 20px;
	margin-bottom:5px;
}
</style>
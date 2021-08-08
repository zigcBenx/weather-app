<template>
	<div class="main">
		<div class="select-city" v-if="cities.length > 0">
			<select v-bind:key="city.id" v-for="city in cities">
				<option>{{city.name}}</option>
			</select>

			<button class="btn btn-primary add-city" @click="toggleModal">Add city</button>
		</div>

		<div v-else>No cities</div>

		<AddCity v-if="showModal" @close="toggleModal"/>
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
				cities: [
				{id:1, name: 'Ljubljana'}
				],
				showModal: false
			}
		},
		mounted(){
			// call method for gathering cities from storage
		},
		methods:{
			toggleModal() {
				this.showModal = !this.showModal;
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
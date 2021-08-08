<template>
	<div class="main">
		<div class="select-city" v-if="cities.length > 0">
			<select v-bind:key="city.id" v-for="city in cities">
				<option>{{city.name}}</option>
			</select>
		</div>

		<div v-else>No cities</div>
		<button class="btn btn-primary" @click="toggleModal">Add city</button>

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
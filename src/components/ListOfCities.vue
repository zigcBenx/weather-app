<template>
	<div class="main">
		<select v-show="cities.length > 0" v-bind:key="city.id" v-for="city in cities">
			<option>{{city.name}}</option>
		</select>
	</div>
</template>

<script>
	export default {
		name: 'ListOfCities',
		props: {},
		data() {
			return {
				cities: [
				{id:1, name: 'Ljubljana'}
				]
			}
		},
		mounted(){
			// call method for gathering cities from storage
		},
		methods:{
			
		}
	}
</script>
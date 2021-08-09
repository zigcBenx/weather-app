<template>
	<div class="main">
		<div class="select-city">
			<div class="select-wrapper" v-if="cities != undefined && cities.length > 0">
				<div class="refresh" @click="getTempForCities()">&nbsp;</div>
				<select @change="cityChanged($event)" v-model="selectedCity">
					<option value="" disabled selected>Select city</option>
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
				showModal: false,
				api_key: '6f9a33953521ce556ec7d259aaf2b161',
				api_url: 'http://api.openweathermap.org/data/2.5/',
				selectedCity: ''
			}
		},
		mounted() {
			// call method for gathering cities from storage
			this.updateCityList();
		},
		methods: {
			toggleModal() {
				// toggle modal for adding new city
				this.showModal = !this.showModal;
			},
			updateCityList() {
				// get city list from local storage
				var cities = JSON.parse(localStorage.getItem("cities"));

				if (cities != undefined && cities.length > 0) {
					this.cities = cities;
				}

				// close modal
				this.showModal = false;

				this.getTempForCities();
			},
			cityChanged(event) {
				// selected city
				var cityName = event.target.value;
				cityName = cityName.includes('~') ? cityName.split('~')[0] : cityName;
				this.selectedCity = cityName;
				this.makeRequest(this.selectedCity)
			},
			makeRequest(city) {
				// get weather for selected city
				if (city != "") {
					fetch(`${this.api_url}weather?q=${city}&units=metric&APPID=${this.api_key}`)
						.then(res => {
							return res.json();
						}).then(this.setWeather);
				}
			},
			setWeather(weather) {
				// send weather data to parent
				this.$emit('updateWeather', weather);
			},
			getTempForCities() {
				// populate select options with cities temperature
				var currentCities = this.cities;
				this.cities = [];
				currentCities.forEach((city) => {
					var temp = 0;
					city = city.includes('~') ? city.split('~')[0] : city;
					if (city != "") {
						fetch(`${this.api_url}weather?q=${city}&units=metric&APPID=${this.api_key}`)
							.then(res => {
								return res.json();
							}).then((data) => {
								temp = data.main.temp;
								this.cities.push(city + '~' + Math.round(temp) + '°C');
							});
					}				
				});
			},
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

.refresh {
	width:25px;
	display: inline-block;
	cursor:pointer;
	background-image: url("https://cdn.iconscout.com/icon/free/png-512/refresh-1781197-1518571.png");
	background-position: center;
    background-size: contain;
    background-repeat: no-repeat;
}
</style>
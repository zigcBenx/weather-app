<template>
	<div class="wrapper">
		<div class="weather-info">

			<div class="location">{{weatherInfo.city}}</div>

			<div class="temp-wrapper">
				<div>{{weatherInfo.temperature}}</div>
			</div>
			<p>{{weatherInfo.humidity}}</p>
			<h4>{{weatherInfo.description}}</h4>
		</div>
	</div>
</template>

<script>
	
	export default {
		name: 'WeatherInformation',
		data() {
			return {
				weatherInfo: {
					city: "Ljubljana",
					temperature: "45°C",
					humidity: "45%",
					description: "delno oblačno"
				}
			}
		}
	}
</script>

<style scoped>
	.wrapper {
		max-width: 650px;
		margin: auto;
		border-radius: 40px !important;
		color: white;
		background-image: linear-gradient(to bottom, rgb(98 177 255 / 25%), rgb(22 160 240 / 75%));
		text-shadow: 2px 2px 2px #707070;
	}

	.temp-wrapper {
		display:inline-block;
		padding:0px  20px;

		color: #FFF;
		font-size: 102px;
		font-weight: 900;
		text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
		background-color:rgba(255, 255, 255, 0.25);
		border-radius: 16px;
		margin: 30px 0px;
		box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
	}

	.location {
		color: #FFF;
		font-size: 32px;
		font-weight: 500;
		text-align: center;
		text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
	}

</style>
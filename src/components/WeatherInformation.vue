<template>
	<div class="wrapper" v-if="weather.name != null">
		<div class="weather-info" :class="getBg(weather)">

			<div class="location">{{weather.name}}, {{weather.sys.country}}</div>
			<div class="date">{{ dateBuilder() }}</div>

			<div class="temp-wrapper">
				<div>{{Math.round(weather.main.temp)}}°C</div>
			</div>
			<p>Humidity: {{weather.main.humidity}}%</p>
			<div class="weather-type">{{weather.weather[0].main}}</div>

		</div>
	</div>
</template>

<script>
	
	export default {
		name: 'WeatherInformation',
		props: ['weather'],
		methods: {
			getBg(weather) {
				return Math.round(weather.main.temp) >= 10 ? 'hot-bg' : 'cold-bg';
			},
			dateBuilder () {
				let d = new Date();
				let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
				let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
				let day = days[d.getDay()];
				let date = d.getDate();
				let month = months[d.getMonth()];
				let year = d.getFullYear();
				return `${day} ${date} ${month} ${year}`;
			}
		}
	}
</script>

<style scoped>
	.wrapper {
		max-width: 650px;
		margin: auto;
		color: white;
		text-shadow: 2px 2px 2px #707070;
		border-radius: 15px;
	}
	.cold-bg {
		background-image: linear-gradient(to bottom, rgb(98 177 255 / 35%), rgb(22 160 240 / 75%));
		background-image: url("https://i.pinimg.com/564x/96/c3/72/96c372bbc2a4326cd4e88f34a6c48303.jpg");
		background-repeat: no-repeat;
		background-position: center;
		background-size: cover;
		border-radius: 40px !important;
	}

	.hot-bg {
		background-image: linear-gradient(to bottom, rgb(239 210 74 / 35%), rgb(236 165 35 / 75%));
		background-image: url("https://i.pinimg.com/564x/a8/65/6a/a8656ab00fa8abfbee70005c7efeae2a.jpg");
		background-repeat: no-repeat;
		background-position: center;
		background-size: cover;
		border-radius: 40px !important;
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

	.date {
		color: #FFF;
		font-size: 20px;
		font-weight: 300;
		font-style: italic;
		text-align: center;
	}

	.weather-type {
		color: #FFF;
		font-size: 48px;
		font-weight: 700;
		font-style: italic;
		text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
	}

</style>
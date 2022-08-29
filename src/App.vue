<script setup>
import Nav from './components/Navigation.vue'
import DogCard from './components/DogCard.vue';
import axios from 'axios';
</script>

<template>
	<div id="app">
		<Nav />

		<div class="btn-div">
			<div class="row">
				<div class="col-md-12">
					<button type="button" @click="getDogImages" class="btn btn-primary gap-2 col-2 mx-auto"
						typeof="button">
						Dogs!
					</button>
				</div>
			</div>
		</div>

		<div class="gallery row align-items-center">
			<p v-if="error" class="error">Unable to get images</p>
			<div v-for="dog in dogs" class="col" style="align-content: center;">

				<DogCard :imgUrl="dog" />
			</div>
		</div>

		<footer>
			<p>&copy; 2020</p>
		</footer>
	</div>
</template>

<script>
export default {
	data() {
		return {
			dogs: {},
			error: false,
		}
	},
	methods: {
		getDogImages: function () {
			axios.get('https://dog.ceo/api/breeds/image/random/20')
				.then(response => {
					this.dogs = response.data.message;
				})
				.catch(error => {
					this.error = true;
					console.log(error);
				});
		},
	}
}
</script>

<style scoped>
body {
	background-color: #f5f5f5;
}

.btn-div {
	text-align: center;
	margin-top: 40px;
}

.gallery {
	margin: 40px auto;
	max-width: 80%;
	padding-bottom: 100px;
	border-top: #212529 1px solid;
	padding-top: 40px;
}

footer {
	position: fixed;
	bottom: 0px;
	width: 100%;
	height: 100px;
	display: flex;
	justify-content: center;
	align-items: center;
	color: #f5f5f5;
	background-color: #212529;
}

.error {
	color: red;
	text-align: center;
}
</style>

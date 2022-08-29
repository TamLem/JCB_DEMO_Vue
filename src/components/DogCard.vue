<script setup>
defineProps({
  imgUrl: {
    type: String,
    required: true
  },
})
</script>

<template>
	<div class="card img-container">
		<div class="card-body p-2">
			<img id="dog-image" class="mx-auto" :src="imgUrl" :href="imgUrl" alt="just another dog picture" />
		</div>
	</div>
</template>

<style scoped>

	#dog-image {
		max-width: 300px;
    max-height: 400px;
    transition: transform .5s ease;
	}

  #dog-image:hover {
    transform: scale(1.1);
  }
  .img-container {
    border-radius: 0px;
    border:none;
    overflow: hidden; 
    text-align: center;
    object-fit: contain;
  }
</style>

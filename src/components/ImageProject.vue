<template>
	<div>
		<div :id="'carousel_' + id" class="carousel carousel-dark slide" data-bs-ride="carousel">
			<div class="carousel-inner">
				<div :class="'carousel-item ' + (i == 0 ? 'active' : '')" v-for="(img, i) in images" :key="i">
					<img :src="img" />
				</div>
			</div>
			<button class="carousel-control-prev" type="button" :data-bs-target="'#carousel_' + id" data-bs-slide="prev">
				<span class="carousel-control-prev-icon" aria-hidden="true"></span>
				<span class="visually-hidden">Previous</span>
			</button>
			<button class="carousel-control-next" type="button" :data-bs-target="'#carousel_' + id" data-bs-slide="next">
				<span class="carousel-control-next-icon" aria-hidden="true"></span>
				<span class="visually-hidden">Next</span>
			</button>
		</div>
	</div>
</template>

<script setup>
	import { defineProps } from 'vue';

	defineProps({
		images: Array,
		id: Number,
	});

	// const index = ref(0);
</script>

<style scoped>
	.carousel-inner img {
		width: 100%;
	}
	.carousel-inner {
		min-height: 224px;
		border: 1px solid #eee;
	}
</style>

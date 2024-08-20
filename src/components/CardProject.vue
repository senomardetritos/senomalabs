<template>
	<div class="project">
		<div class="my-card">
			<div class="card-left">
				<div>
					<h2>{{ item.name }}</h2>
					<div class="language">
						<div v-for="(language, i) in item.languages" :key="i">
							<div class="badge">{{ language }}</div>
						</div>
					</div>
					<h5>{{ item.description }}</h5>
				</div>
				<div class="links">
					<div v-for="(link, i) in item.links" :key="i">
						<a :href="link" target="_blank">{{ i }}</a>
					</div>
				</div>
			</div>
			<div class="card-right" v-if="item.images">
				<ImageProject :images="item.images" :id="id" />
			</div>
		</div>
	</div>
</template>

<script setup>
	import { defineProps } from 'vue';
	import ImageProject from '../components/ImageProject.vue';
	defineProps({
		item: Object,
		id: Number,
	});
</script>

<style scoped>
	.project .my-card {
		display: flex;
		flex-direction: column;
		justify-content: center;
		width: 100%;
		gap: 4px;
		background: var(--bg-light);
		padding: 24px;
		margin-bottom: 32px;
	}
	.project .my-card h2 {
		font-weight: 700;
		font-size: 32px;
		font-family: 'New Amsterdam', sans-serif;
		letter-spacing: 1px;
	}
	.project .my-card .badge {
		font-weight: 300;
		background-color: var(--bg-orange);
	}
	.project .my-card h5 {
		font-weight: 300;
		font-size: 16px;
		text-align: justify;
	}
	.project .my-card h6 {
		font-weight: 100;
		padding: 4px;
		margin: 0px;
		font-size: 14px;
	}
	.project .language {
		display: flex;
		gap: 12px;
		margin-bottom: 24px;
	}
	.project .links {
		display: flex;
		flex-direction: row;
		gap: 8px;
		margin-top: 24px;
		margin-bottom: 24px;
	}
	.project .links a {
		background: var(--bg-dark);
		color: var(--bg-light);
		padding: 8px 16px;
		border-radius: 8px;
		text-decoration: none;
		font-size: 12px;
	}

	@media (min-width: 900px) {
		.project .my-card {
			flex-direction: row;
			justify-content: space-between;
			gap: 36px;
		}
		.project .my-card .card-left,
		.project .my-card .card-right {
			width: 50%;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
		}
		.project .links a {
			font-size: 14px;
		}
	}
</style>

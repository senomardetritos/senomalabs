<template>
	<div>
		<HeaderProject @filter="filter" />
		<main class="conteiner">
			<div v-for="(item, i) in dataList" :key="i">
				<CardProject :item="item" :id="i" />
			</div>
		</main>
	</div>
</template>

<script setup>
	import { ref, computed } from 'vue';
	import data from './db/data';
	import HeaderProject from './components/HeaderProject.vue';
	import CardProject from './components/CardProject.vue';

	const itemFilter = ref('Todos');

	const dataList = computed(() => {
		if (itemFilter.value == 'Todos') return data;
		return data.filter((item) => {
			if (item.languages.includes(itemFilter.value)) {
				return true;
			} else {
				return false;
			}
		});
	});

	function filter(item) {
		itemFilter.value = item;
	}
</script>

<style scoped>
	.conteiner {
		padding: 24px;
	}
	@media (min-width: 1200px) {
		.conteiner {
			padding: 24px 128px;
		}
	}
</style>

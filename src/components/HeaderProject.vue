<template>
	<nav class="nav">
		<div class="nav-item"><img :src="Logo" /></div>
		<div class="nav-item">
			<a href="#" v-for="(item, i) in languages" :key="i" :class="actualFilter === item ? 'active' : ''" @click="filter(item)">{{ item }}</a>
		</div>
	</nav>
</template>

<script setup>
	import { ref, defineEmits } from 'vue';
	import Logo from '../assets/logo.png';

	const emits = defineEmits(['filter']);
	const actualFilter = ref('Todos');
	const languages = ref(['Todos', 'Vue', 'Pinia', 'Vuex', 'PHP']);

	function filter(item) {
		actualFilter.value = item;
		emits('filter', item);
	}
</script>

<style scoped>
	.nav {
		display: flex;
		background: var(--bg-white);
		position: sticky;
		top: 0px;
		z-index: 1;
		padding: 0 24px;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
	}
	.nav .nav-item img {
		height: 80px;
	}
	.nav .nav-item a {
		display: inline-block;
		padding: 2px 0px;
		margin: 0px 8px;
		color: var(--bd-dark);
		text-decoration: none;
		font-family: 'New Amsterdam';
		letter-spacing: 1px;
	}

	.nav .nav-item a.active {
		border-bottom: 3px solid var(--bg-orange);
	}

	@media (min-width: 1200px) {
		.nav {
			padding: 0px 128px;
		}
	}
</style>

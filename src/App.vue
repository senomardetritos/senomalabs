<template>
	<div>
		<HomeProject />
		<SobreProject />
		<HabilidadesProject />
		<ExperienciasProject />
		<ProjetosProject />
		<div v-for="(item, i) in data" :key="i">
			<CardProject :item="item" :id="i" />
		</div>
		<ContatoProject />
	</div>
</template>

<script setup>
	import data from './db/data';
	import HomeProject from './components/HomeProject.vue';
	import SobreProject from './components/SobreProject.vue';
	import HabilidadesProject from './components/HabilidadesProject.vue';
	import ExperienciasProject from './components/ExperienciaProject.vue';
	import ProjetosProject from './components/ProjetosProject.vue';
	import ContatoProject from './components/ContatoProject.vue';
	import CardProject from './components/CardProject.vue';
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

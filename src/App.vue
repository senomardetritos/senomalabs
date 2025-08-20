<template>
	<div>
		<MenuHeader />
		<HomeProject />
		<SobreProject />
		<HabilidadesProject />
		<ExperienciasProject />
		<ProjetosProject />
		<ContatoProject />
	</div>
</template>

<script setup>
	import MenuHeader from './components/MenuHeader.vue';
	import HomeProject from './components/HomeProject.vue';
	import SobreProject from './components/SobreProject.vue';
	import HabilidadesProject from './components/HabilidadesProject.vue';
	import ExperienciasProject from './components/ExperienciaProject.vue';
	import ProjetosProject from './components/ProjetosProject.vue';
	import ContatoProject from './components/ContatoProject.vue';
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

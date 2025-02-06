<template>
	<div class="site-container sobre" id="sobre">
		<div class="sobre-header">
			<div class="dados">
				<h1>SOBRE</h1>
				<h2>Lucas Torres dos Anjos</h2>
				<p>Profissional com mais de 20 anos de experiência em Tecnologia da Informação, com atuação em empresas de diversos segmentos, incluindo:</p>
			</div>
			<div class="foto">
				<img :src="Foto" />
			</div>
		</div>
		<div class="sobre-body">
			<ul>
				<li>GIS para máquinas agrícolas.</li>
				<li>WMS para armazéns de café.</li>
				<li>Sistemas de contratos (compra e venda, barter e invoices).</li>
				<li>Rastreabilidade e classificação de café.</li>
				<li>Redes sociais corporativas.</li>
				<li>Desenvolvimento de aplicativos nativos (iOS e Android), web apps e sites institucionais.</li>
			</ul>
			<p>Ao longo da minha trajetória, adquiri sólida experiência como desenvolvedor back-end, com foco em PHP e frameworks como CakePHP e Laravel.</p>
			<p>Também atuei no desenvolvimento de aplicativos móveis utilizando Objective-C para iOS e Java para Android, além de criar web apps com Angular e Vue.js.</p>
			<p>No front-end, trabalhei com projetos em Vue.js, Angular e React, sempre buscando entregar interfaces intuitivas e de alta performance.</p>
		</div>
	</div>
</template>

<script setup>
	import Foto from '../assets/foto.png';
</script>

<style scoped>
	.site-container.sobre {
		background-color: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 100vh;
	}
	.site-container.sobre .sobre-header {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 12px;
	}
	.site-container.sobre .sobre-header h1 {
		font-weight: 700;
		font-size: 56pt;
	}
	.site-container.sobre .sobre-header h2 {
		font-weight: 700;
		font-size: 24pt;
		margin-bottom: 24px;
	}
	.site-container.sobre .sobre-body {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 0px;
	}
	.site-container.sobre .sobre-body ul {
		margin-bottom: 32px;
	}
	.site-container.sobre .sobre-body ul li {
		font-weight: 600;
	}
	.site-container.sobre .sobre-body p {
		margin: 4px 0;
	}
</style>

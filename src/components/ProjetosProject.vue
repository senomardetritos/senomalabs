<template>
	<div class="site-container projeto" id="projetos">
		<div class="projeto-header">
			<div class="dados">
				<h1>PROJETOS</h1>
				<div class="projetos">
					<h2>Projetos Pessoais de Aprendizado e Treinamento</h2>
					<p>Ao longo da minha jornada como desenvolvedor, dediquei parte do meu tempo à criação de projetos pessoais, com o objetivo de aprimorar minhas habilidades técnicas e explorar novas tecnologias. Esses projetos foram essenciais para consolidar conhecimentos e experimentar soluções inovadoras. Abaixo, destaco alguns dos trabalhos que desenvolvi:</p>
					<ul>
						<li v-for="(item, i) in data" :key="i">
							<h3>
								<a :href="'#' + item.name">{{ item.name }}</a>
							</h3>
						</li>
					</ul>
					<p>Esses projetos pessoais foram fundamentais para o meu crescimento profissional, permitindo-me experimentar novas tecnologias, consolidar conceitos e desenvolver soluções criativas e funcionais.</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
	import data from '../db/data';
</script>

<style scoped>
	.site-container.projeto {
		background: url(../assets/background.png);
		background-color: #888;
		background-position: center center;
		background-size: auto 100vh;
		background-blend-mode: multiply;
		color: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 100vh;
	}
	.site-container.projeto .projeto-header {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 24px;
	}
	.site-container.projeto .projeto-header h1 {
		font-weight: 700;
		font-size: 56pt;
		margin-bottom: 24px;
	}
	.site-container.projeto .projeto-header .projetos h2 {
		font-weight: 700;
		font-size: 14pt;
		margin-bottom: 12px;
	}
	.site-container.projeto .projeto-header .projetos h3 {
		font-weight: 500;
		font-size: 12pt;
		margin-bottom: 8px;
	}
	.site-container.projeto .projeto-header .projetos h3 a {
		color: #fff;
	}
</style>

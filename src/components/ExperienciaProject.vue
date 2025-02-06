<template>
	<div class="site-container experiencia" id="experiencia">
		<div class="experiencia-header">
			<div class="dados">
				<h1>EXPERIÊNCIA</h1>
				<div class="group" v-for="(item, i) in experiencias" :key="i">
					<div>
						<div class="empresa-header">
							<h2>{{ item.empresa }}</h2>
							<h3>{{ item.data }}</h3>
						</div>
						<div class="empresa-header">
							<h4>{{ item.cargo }}</h4>
							<a @mouseover="item.show = true">Saiba mais</a>
						</div>
						<h6>{{ item.resumo }}</h6>
						<div @mouseleave="item.show = false" class="modal-atuacao" v-if="item.show">
							<div class="empresa-header">
								<h2>{{ item.empresa }}</h2>
								<h3>{{ item.data }}</h3>
							</div>
							<div class="empresa-header">
								<h4>{{ item.cargo }}</h4>
							</div>
							<span v-for="(exp, j) in item.atuacao" :key="j">
								<h5>{{ exp.title }}</h5>
								<ul>
									<li v-for="(atua, k) in exp.itens" :key="k">
										{{ atua }}
									</li>
								</ul>
							</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
	import { ref, onMounted } from 'vue';
	import experienciasDB from '../db/experiencia';

	const experiencias = ref([]);

	onMounted(() => {
		experiencias.value = experienciasDB;
	});
</script>

<style scoped>
	.site-container.experiencia {
		background-color: #fff;
		color: #000;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 100vh;
	}
	.site-container.experiencia .experiencia-header {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: flex-start;
		width: var(--w-size);
	}
	.site-container.experiencia .experiencia-header h1 {
		font-weight: 700;
		font-size: 56pt;
		margin-bottom: 24px;
	}
	.site-container.experiencia .experiencia-header .group {
		margin: 18px 0;
		padding: 18px 0;
		border-top: 1px solid #eee;
		position: relative;
	}
	.site-container.experiencia .experiencia-header .empresa-header {
		display: flex;
		justify-content: space-between;
		width: var(--w-size);
	}
	.site-container.experiencia .experiencia-header .empresa-header h2 {
		font-size: 12pt;
		font-weight: 600;
	}
	.site-container.experiencia .experiencia-header .empresa-header h3 {
		font-size: 12pt;
		font-weight: 900;
	}
	.site-container.experiencia .experiencia-header h4 {
		font-size: 16pt;
		font-weight: 900;
	}
	.site-container.experiencia .experiencia-header h5 {
		font-size: 11pt;
		font-weight: 700;
		margin: 12px 0;
	}
	.site-container.experiencia .experiencia-header li {
		font-size: 11pt;
		font-weight: 400;
		margin: 4px 0;
	}
	.site-container.experiencia .experiencia-header a {
		cursor: pointer;
		color: var(--bs-blue);
	}
	.site-container.experiencia .modal-atuacao {
		position: absolute;
		width: var(--w-size);
		height: auto;
		top: 24px;
		left: 24px;
		background: #fff;
		border-radius: 8px;
		box-shadow: 0 0 10px -5px #000;
		padding: 24px;
		z-index: 100;
	}
	.site-container.experiencia .modal-atuacao * {
		font-size: 0.8%;
	}
	.site-container.experiencia .modal-atuacao .empresa-header {
		width: 100%;
	}
</style>

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
							<a href="#experiencia" @click="showModal(item)">Saiba mais</a>
						</div>
						<h6>{{ item.resumo }}</h6>
						<div @click="closeModal(item)" class="modal-atuacao" v-if="item.show">
							<div @mouseover="cancelScroll()" class="modal">
								<div @mouseover="cancelScroll()" class="modal-body">
									<div class="empresa-header">
										<h2>{{ item.empresa }}</h2>
										<h3>{{ item.data }}</h3>
									</div>
									<div class="empresa-header">
										<h4>{{ item.cargo }}</h4>
									</div>
									<div class="item" v-for="(exp, j) in item.atuacao" :key="j">
										<p>✔ {{ exp.texto }}</p>
										<div class="tech">
											<div v-if="exp.itens">
												<span> {{ exp.itens }} </span>
											</div>
										</div>
									</div>
								</div>
							</div>
							<div @mouseout="cancelScroll()" @mouseover="scrollText(-1)" v-if="positionScroll != null && positionScroll > 0" class="button-scroll-up"><i class="bi bi-arrow-up"></i></div>
							<div @mouseout="cancelScroll()" @mouseover="scrollText(1)" v-if="positionScroll != null && positionScroll < textScroll.scrollHeight - textScroll.clientHeight" class="button-scroll-down"><i class="bi bi-arrow-down"></i></div>
							<span class="info-close">* Clique na tela para fechar</span>
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
	const timerScroll = ref(null);
	const textScroll = ref(null);
	const positionScroll = ref(null);

	onMounted(() => {
		experiencias.value = experienciasDB;
		// experiencias.value.map((item) => {
		// 	item.show = false;
		// });
		clearInterval(timerScroll.value);
	});

	function showModal(item) {
		item.show = true;
		positionScroll.value = null;
		setTimeout(() => {
			textScroll.value = document.querySelector('.modal-body');
			if (textScroll.value) {
				textScroll.value.addEventListener('scroll', function () {
					positionScroll.value = textScroll.value.scrollTop;
				});
				textScroll.value.scrollTop = 0;
				positionScroll.value = 0;
			}
		}, 100);
		clearInterval(timerScroll.value);
	}

	function closeModal(item) {
		item.show = false;
		clearInterval(timerScroll.value);
	}

	function scrollText(value) {
		clearInterval(timerScroll.value);
		if (textScroll.value) {
			timerScroll.value = setInterval(() => {
				textScroll.value.scrollTop += value;
				positionScroll.value = textScroll.value.scrollTop;
			}, 1);
		}
	}

	function cancelScroll() {
		clearInterval(timerScroll.value);
	}
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
		position: fixed;
		height: 100vh;
		width: 100vw;
		top: 0px;
		left: 0px;
		background: #000000dd;
		z-index: 2000;
	}
	.site-container.experiencia .modal-atuacao .button-scroll-up,
	.site-container.experiencia .modal-atuacao .button-scroll-down {
		background: #ff8626;
		color: #000000;
		border-radius: 50%;
		position: absolute;
		width: 30px;
		height: 30px;
		left: calc(100vw - 250px);
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
		z-index: 200;
	}
	.site-container.experiencia .modal-atuacao .button-scroll-up {
		top: 80px;
	}
	.site-container.experiencia .modal-atuacao .button-scroll-down {
		bottom: 110px;
	}
	.site-container.experiencia .modal-atuacao span.info-close {
		position: absolute;
		bottom: 50px;
		color: #ffffff;
		font-size: 8pt;
		display: flex;
		justify-content: center;
		width: 100vw;
		cursor: pointer;
		font-style: italic;
	}
	.site-container.experiencia .modal {
		position: absolute;
		top: 60px;
		left: 200px;
		background: #fff;
		border-radius: 8px;
		box-shadow: 0 0 10px -5px #000;
		padding: 24px;
		width: calc(100vw - 400px);
		height: calc(100vh - 150px);
		z-index: 100;
		display: block;
		cursor: pointer;
	}
	.site-container.experiencia .modal-body {
		width: 100%;
		height: calc(100vh - 198px);
		overflow-y: scroll;
	}
	.site-container.experiencia .modal-body .empresa-header {
		width: 100%;
	}
	.site-container.experiencia .modal-body .empresa-header h4 {
		margin-bottom: 16px;
		padding-bottom: 24px;
		border-bottom: 1px solid #333333;
		width: 100%;
	}
	.site-container.experiencia .modal-body .item {
		margin-bottom: 16px;
	}
	.site-container.experiencia .modal-body p {
		margin: 4px 0;
		padding-right: 24px;
	}
	.site-container.experiencia .modal-body .tech {
		font-size: 9pt;
		font-weight: 700;
		margin-bottom: 16px;
	}
</style>

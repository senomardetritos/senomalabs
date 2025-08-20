<template>
	<div class="site-container projeto" id="projetos">
		<div class="projeto-bg-image">
			<img :src="actualItem.images[index]" />
		</div>
		<div class="projeto-names">
			<div class="projeto-names-item" v-for="(item, i) in data" :key="i">
				<a :class="actualItem.name == item.name ? 'orange' : ''" href="#projetos" @click="changeItem(item)">{{ item.name }}</a>
			</div>
		</div>
		<div class="divider"></div>
		<div class="projeto-description">
			<div class="projeto-description-header" @mouseover="cancelScroll()">
				<h4>Sobre o projeto</h4>
				<h6>{{ actualItem.date }}</h6>
			</div>
			<div class="projeto-description-text" id="description-text" @mouseover="cancelScroll()">
				<p v-for="(item, i) in actualItem.description" :key="i">
					{{ item === '' ? '&nbsp;' : item }}
				</p>
			</div>
			<div class="projeto-description-button" @mouseover="cancelScroll()">
				<a :href="item" target="_blank" v-for="(item, i) in actualItem.links" :key="i">
					{{ i }}
				</a>
			</div>
			<div @mouseout="cancelScroll()" @mouseover="scrollText(-1)" v-if="positionScroll != null && positionScroll > 0" class="button-scroll-up"><i class="bi bi-arrow-up"></i></div>
			<div @mouseout="cancelScroll()" @mouseover="scrollText(1)" v-if="positionScroll != null && positionScroll < textScroll.scrollHeight - textScroll.clientHeight" class="button-scroll-down"><i class="bi bi-arrow-down"></i></div>
		</div>
		<div class="projeto-information">
			<h3>{{ actualItem.name }}</h3>
			<div class="projeto-information-languages">
				<span v-for="(item, i) in actualItem.languages" :key="i">
					{{ item }}
				</span>
			</div>
			<img :src="actualItem.images[index]" @click="showModalImage()" />
			<div class="projeto-information-counter">
				<span :class="index == i ? 'orange' : ''" @click="changeCounter(i)" v-for="(item, i) in actualItem.images" :key="i"></span>
			</div>
			<i>* Clique na imagem para ver maior</i>
		</div>
		<div class="modal-image" v-if="actualItem.show">
			<img :src="actualItem.images[index]" @click="actualItem.show = false" />
			<div class="projeto-information-counter">
				<span :class="index == i ? 'orange' : ''" @click="changeCounter(i)" v-for="(item, i) in actualItem.images" :key="i"></span>
			</div>
			<i>* Clique na imagem para fechar</i>
		</div>
	</div>
</template>

<script setup>
	import { ref, onMounted, onUnmounted } from 'vue';
	import data from '../db/data';

	const index = ref(0);
	const actualItem = ref(data[0]);
	const timer = ref(null);
	const timerScroll = ref(null);
	const textScroll = ref(null);
	const positionScroll = ref(null);

	onMounted(() => {
		changeItem(data[0]);
	});

	onUnmounted(() => {
		clearInterval(timer.value);
	});

	function changeItem(item) {
		actualItem.value = item;
		index.value = 0;
		positionScroll.value = null;
		setTimeout(() => {
			textScroll.value = document.querySelector('#description-text');
			textScroll.value.addEventListener('scroll', function () {
				positionScroll.value = textScroll.value.scrollTop;
			});
			textScroll.value.scrollTop = 0;
			positionScroll.value = 0;
		}, 100);
		startCounterInterval();
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

	function startCounterInterval() {
		clearInterval(timer.value);
		timer.value = setInterval(() => {
			index.value++;
			if (index.value > actualItem.value.images.length - 1) index.value = 0;
		}, 7000);
	}

	function showModalImage() {
		actualItem.value.show = true;
		startCounterInterval();
	}

	function changeCounter(value) {
		index.value = value;
		startCounterInterval();
	}
</script>

<style scoped>
	.projeto {
		background-color: #000000;
		color: #000;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: start;
		min-height: 100vh;
		position: relative;
	}
	.projeto .line {
		border-top: 1px solid #ffffff;
		width: 100%;
	}
	.projeto .divider {
		border-top: 1px solid #ffffff;
		width: 95%;
		margin-top: 30px;
	}
	.projeto-bg-image {
		position: absolute;
		top: 0px;
		left: 0px;
		width: 100%;
		height: 100%;
		z-index: 0;
		overflow: hidden;
	}
	.projeto-bg-image img {
		height: 150%;
		opacity: 0.075;
	}
	.projeto-names {
		display: flex;
		gap: 36px;
		margin-top: 96px;
		position: relative;
		z-index: 1;
	}
	.projeto-names a {
		color: #ffffff;
	}
	.projeto-names a.orange {
		color: #ff8626;
	}
	.projeto-description {
		display: flex;
		flex-direction: column;
		gap: 2px;
		margin-top: 48px;
		position: absolute;
		z-index: 1;
		top: 140px;
		left: 60px;
		width: 40%;
	}
	.projeto-description-header {
		display: flex;
		justify-content: space-between;
	}
	.projeto-description-text {
		height: 350px;
		overflow-y: scroll;
	}
	.projeto-description .button-scroll-up,
	.projeto-description .button-scroll-down {
		background: #ff8626;
		color: #000000;
		border-radius: 50%;
		position: absolute;
		width: 30px;
		height: 30px;
		right: 0px;
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
	}
	.projeto-description .button-scroll-up {
		top: 50px;
	}
	.projeto-description .button-scroll-down {
		bottom: 60px;
	}
	.projeto-description h4 {
		color: #ffffff;
		margin-bottom: 16px;
	}
	.projeto-description h6 {
		color: #ffffff;
		margin-top: 8px;
	}
	.projeto-description p {
		color: #ffffff;
		font-size: 10pt;
		margin: 0;
		padding: 0;
	}
	.projeto-description-button {
		display: flex;
		gap: 16px;
		margin-top: 24px;
	}
	.projeto-description-button a {
		background: #ffffff;
		color: #333333;
		display: inline-block;
		padding: 8px 16px;
		border-radius: 50px;
		font-weight: 700;
	}
	.projeto-information {
		position: absolute;
		top: 140px;
		right: 60px;
		width: 40%;
		z-index: 1;
		margin-top: 48px;
	}
	.projeto-information h3 {
		color: #ffffff;
	}
	.projeto-information-languages {
		display: flex;
		gap: 8px;
	}
	.projeto-information-languages span {
		display: inline-block;
		background: #333333;
		color: #ffffff;
		display: inline-block;
		padding: 4px 8px;
		border-radius: 50px;
		font-size: 9pt;
	}
	.projeto-information img {
		display: inline-block;
		margin: 24px 0;
		width: 75%;
		border-radius: 8px;
		cursor: pointer;
	}
	.projeto-information .projeto-information-counter {
		display: flex;
		gap: 8px;
		justify-content: center;
		width: 75%;
	}
	.projeto-information .projeto-information-counter span {
		display: block;
		background: #ffffff;
		height: 6px;
		width: 40px;
		cursor: pointer;
	}
	.projeto-information .projeto-information-counter span.orange {
		background: #ff8626;
	}
	.projeto-information i {
		color: #ffffff;
		display: block;
		padding: 24px 0;
		font-size: 8pt;
		text-align: center;
		width: 75%;
	}
	.modal-image {
		position: fixed;
		top: 0px;
		left: 0px;
		width: 100vw;
		height: 100vh;
		background-color: #000000dd;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		z-index: 2000;
	}
	.modal-image img {
		height: 80%;
		width: auto;
		cursor: pointer;
	}
	.modal-image .projeto-information-counter {
		display: flex;
		gap: 8px;
		justify-content: center;
		width: 90%;
		margin-top: 16px;
	}
	.modal-image .projeto-information-counter span {
		display: block;
		background: #ffffff;
		height: 6px;
		width: 40px;
		cursor: pointer;
	}
	.modal-image .projeto-information-counter span.orange {
		background: #ff8626;
	}
	.modal-image i {
		color: #ffffff;
		display: block;
		margin-top: 16px;
		font-size: 8pt;
		text-align: center;
		width: 90%;
	}
</style>

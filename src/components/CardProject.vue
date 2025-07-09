<template>
	<div class="site-container projeto" :id="item.name">
		<div class="projeto-header">
			<h1>{{ item.name }}</h1>
		</div>
		<div class="projeto-body">
			<div class="left-body">
				<div class="projeto-languages">
					<span class="badge rounded-pill" v-for="(l, i) in item.languages" :key="i">
						{{ l }}
					</span>
				</div>
				<p v-for="(desc, i) in item.description" :key="i">{{ desc }}</p>
				<div class="body-buttons">
					<a :href="btn" target="_blank" v-for="(btn, i) in item.links" :key="i">
						{{ i }}
					</a>
				</div>
			</div>
			<div class="computer" v-if="item.type == 'computer'">
				<div class="print">
					<img :src="item.images[index]" />
				</div>
				<img class="note" :src="Note" />
			</div>
			<div class="mobile" v-if="item.type == 'mobile'">
				<div class="print">
					<img :src="item.images[index]" />
				</div>
				<img class="phone" :src="Phone" />
			</div>
		</div>
	</div>
</template>

<script setup>
	import { ref, defineProps, onMounted, onUnmounted } from 'vue';
	import Note from '../assets/note.png';
	import Phone from '../assets/phone.png';
	const props = defineProps({
		item: Object,
		id: Number,
	});

	const index = ref(0);
	const timer = ref(null);
	onMounted(() => {
		timer.value = setInterval(() => {
			index.value++;
			if (index.value > props.item.images.length - 1) index.value = 0;
		}, 5000);
	});
	onUnmounted(() => {
		clearInterval(timer.value);
	});
</script>

<style scoped>
	.site-container.projeto {
		background-color: #fff;
		color: #000;
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
	.site-container.projeto .projeto-body .projeto-languages {
		margin-bottom: 24px;
		width: 100%;
	}
	.site-container.projeto .projeto-body .projeto-languages .badge{
		background: #040631;
		margin-right: 14px;;
	}
	.site-container.projeto .projeto-body {
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 24px;
	}
	.site-container.projeto .projeto-body .left-body {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: 1px;
		margin-top: 12px;
	}
	.site-container.projeto .projeto-body .left-body .body-buttons {
		display: flex;
		gap: 8px;
		margin-top: 24px;
	}
	.site-container.projeto .projeto-body .left-body a {
		background: #333;
		color: #fff;
		border: none;
		padding: 8px 16px;
		border-radius: 8px;
		cursor: pointer;
	}
	.site-container.projeto .projeto-body .computer {
		position: relative;
	}
	.site-container.projeto .projeto-body .computer .print {
		position: absolute;
		z-index: 0;
		top: 20px;
		left: 39px;
		width: 420px;
	}
	.site-container.projeto .projeto-body .computer .print img {
		width: 100%;
	}
	.site-container.projeto .projeto-body .computer .note {
		position: relative;
		width: 500px;
		z-index: 1;
	}
	.site-container.projeto .projeto-body .mobile {
		position: relative;
	}
	.site-container.projeto .projeto-body .mobile .print {
		position: absolute;
		z-index: 0;
		top: 12px;
		left: 12px;
		width: 280px;
		height: 550px;
		border-radius: 32px;
		overflow: hidden;
	}
	.site-container.projeto .projeto-body .mobile .print img {
		width: 100%;
	}
	.site-container.projeto .projeto-body .mobile .phone {
		position: relative;
		width: 300px;
		z-index: 1;
	}
</style>

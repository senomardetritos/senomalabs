<template>
	<div class="site-container home">
		<img :src="Logo" />
		<div class="home-footer">
			<div>LUCAS TORRES DOS ANJOS | DESENVOLVEDOR FULL STACK</div>
			<img :src="Logos" />
		</div>
	</div>
</template>

<script setup>
	import { onMounted } from 'vue';
	import Logo from '../assets/logo.png';
	import Logos from '../assets/logos.png';

	onMounted(() => {});
</script>

<style scoped>
	.site-container.home {
		background: url(../assets/background.png);
		background-position: center center;
		background-size: auto 100vh;
		background-blend-mode: multiply;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 100vh;
		gap: 24px;
	}

	.site-container.home img {
		max-width: 60%;
		margin: 8px 0;
	}

	.site-container.home .home-footer {
		color: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
</style>

<template>
	<div class="site-container home">
		<div class="menu-header">
			<a href="#sobre">SOBRE</a>
			<a href="#habilidades">HABILIDADES</a>
			<a href="#experiencia">EXPERIÊNCIA</a>
			<a href="#projetos">PROJETOS</a>
			<a href="#contato">CONTATO</a>
		</div>
		<img :src="Logo" />
		<div class="home-footer">
			<div>DESENVOLVEDOR FULL STACK</div>
			<img :src="Logos" />
		</div>
	</div>
</template>

<script setup>
	import Logo from '../assets/logo.png';
	import Logos from '../assets/logos.png';
</script>

<style scoped>
	.site-container.home {
		background: url(../assets/background.png);
		background-color: #888;
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

	.site-container.home .menu-header {
		display: flex;
		flex-direction: row;
		gap: 56px;
	}

	.site-container.home .menu-header a {
		color: #fff;
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

<template>
	<div class="menu">
		<div class="menu-header">
			<a href="#sobre">SOBRE</a>
			<a href="#habilidades">HABILIDADES</a>
			<a href="#experiencia">EXPERIÊNCIA</a>
			<a href="#projetos">PROJETOS</a>
			<a href="#contato">CONTATO</a>
		</div>
	</div>
</template>

<script setup></script>

<style scoped>
	.menu {
		position: sticky;
		top: 0;
		width: 100%;
		background: url(../assets/background.png);
		z-index: 1000;
		box-shadow: 0px 5px 10px -5px #000000;
	}
	.menu-header {
		display: flex;
		flex-direction: row;
		gap: 56px;
		width: 100%;
		align-items: center;
		justify-content: center;
		padding: 16px;
	}
	.menu-header a {
		color: #fff;
	}
</style>

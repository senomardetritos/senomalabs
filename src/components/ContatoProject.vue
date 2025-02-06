<template>
	<div class="site-container contato" id="contato">
		<div class="contato-header">
			<div class="dados">
				<h1>CONTATO</h1>
				<div><b>Telefone:</b> <a href="https://wa.me/+5534992230006" target="_blank">(34) 99223-0006</a></div>
				<div><b>Email:</b> <a href="mailto:senomar59@gmail.com">senomar59@gmail.com</a></div>
				<div><b>Linkedin:</b> <a href="https://www.linkedin.com/in/lucas-torres-dos-anjos/" target="_blank">https://www.linkedin.com/in/lucas-torres-dos-anjos/</a></div>
				<div><b>GitHub:</b> <a href="https://github.com/senomardetritos" target="_blank">https://github.com/senomardetritos</a></div>
			</div>
			<div class="logo">
				<img :src="Logo" />
			</div>
		</div>
	</div>
</template>

<script setup>
	import Logo from '../assets/logo.png';
</script>

<style scoped>
	.site-container.contato {
		background: url(../assets/background-contato.png);
		background-color: #eee;
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
	.site-container.contato .contato-header {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 24px;
	}
	.site-container.contato .contato-header h1 {
		font-weight: 700;
		font-size: 56pt;
		margin-bottom: 24px;
	}
	.site-container.contato .contato-header a {
		color: #fff;
	}
	.site-container.contato .contato-header .logo {
		margin-top: 150px;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		width: var(--w-size);
	}
	.site-container.contato .contato-header .logo img {
		width: 200px;
	}
</style>

<template>
	<div class="site-container habilidade" id="habilidades">
		<div class="habilidade-header">
			<div class="dados">
				<h1>HABILIDADES</h1>
				<div>✔ <b>Front-end:</b> Html5, Css3, Scss, Bootstrap, JQuery, JavaScript, TypeScript.</div>
				<div>✔ <b>WebApps:</b> Vue.js, Angular, React, Cordova.</div>
				<div>✔ <b>Back-end:</b> PHP, CakePHP, Laravel, Node.Js, Express, Python, Django.</div>
				<div>✔ <b>Mobile:</b> Objective-C (iOS), Java (Android).</div>
				<div>✔ <b>Desktop:</b> Visual Basic, VB.NET.</div>
				<div>✔ <b>Design:</b> Figma, Photoshop, Krita.</div>
			</div>
		</div>
	</div>
</template>

<script setup></script>

<style scoped>
	.site-container.habilidade {
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
	.site-container.habilidade .habilidade-header {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 24px;
	}
	.site-container.habilidade .habilidade-header h1 {
		font-weight: 700;
		font-size: 56pt;
		margin-bottom: 24px;
	}
</style>

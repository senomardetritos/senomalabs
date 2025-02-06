<template>
	<div class="site-container habilidade" id="habilidades">
		<div class="habilidade-header">
			<div class="dados">
				<h1>HABILIDADES</h1>
				<ul>
					<li><b>Front-end:</b> Html5, Css3, Scss, Bootstrap, JQuery, JavaScript, TypeScript.</li>
					<li><b>WebApps:</b> Vue.js, Angular, React, Cordova.</li>
					<li><b>Back-end:</b> PHP, CakePHP, Laravel, Node.Js, Express.</li>
					<li><b>Mobile:</b> Objective-C (iOS), Java (Android).</li>
					<li><b>Desktop:</b> Visual Basic, VB.NET.</li>
				</ul>
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
	.site-container.habilidade .habilidade-header ul li {
		margin: 8px 0;
	}
</style>

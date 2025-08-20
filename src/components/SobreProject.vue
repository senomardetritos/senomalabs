<template>
	<div class="site-container sobre" id="sobre">
		<div class="sobre-header">
			<div class="dados">
				<h1>SOBRE</h1>
				<h2>Lucas Torres dos Anjos</h2>
				<h4>Desenvolvedor Full Stack Sênior | Especialista em Soluções Tecnológicas</h4>
			</div>
		</div>
		<div class="sobre-body">
			<p>Com mais de 20 anos de experiência em TI, atuei em projetos desafiadores para diversos setores, combinando expertise técnica com visão estratégica para entregar soluções inovadoras e eficientes.</p>
			<div>
				<p><b>Experiência Técnica Multidisciplinar:</b></p>
				<div>✔ Back-end: Especialista em PHP (Laravel), Node.js (Express) e arquitetura de APIs RESTful</div>
				<div>✔ Mobile: Desenvolvimento nativo para iOS (Objective-C) e Android (Java)</div>
				<div>✔ Front-end: Projetos com Vue.js, Angular e React, priorizando UX e performance</div>
				<div>✔ Design: Figma, Photoshop e Krita</div>
			</div>
			<div>
				<p><b>Sistemas Especializados:</b></p>
				<div>✔ GIS para agricultura de precisão</div>
				<div>✔ WMS para gestão logística de café</div>
				<div>✔ Plataformas de contratos comerciais (barter, invoices)</div>
				<div>✔ Rastreabilidade e classificação de grãos</div>
				<div>✔ Redes sociais corporativas</div>
				<div>✔ Aplicativos de integração com softwares legados</div>
			</div>
			<div>
				<p><b>Diferenciais Profissionais</b></p>
				<div>✔ Liderança técnica: Capacidade de traduzir necessidades de negócio em soluções escaláveis</div>
				<div>✔ Inovação contínua: Atualização constante em novas tecnologias e melhores práticas</div>
				<div>✔ Habilidades interpessoais: Comunicação clara e trabalho em equipe multidisciplinar</div>
				<div>✔ Mentalidade ágil: Adaptabilidade para resolver problemas complexos com eficiência</div>
			</div>
			<div>
				<p><b>Por que meu trabalho faz diferença?</b></p>
				<p>Combinando profundidade técnica e visão de negócios, desenvolvo sistemas que não apenas funcionam, mas agregam valor real às operações. Meu foco está em criar soluções que sejam:</p>
				<div>✔ Robustas (arquitetura limpa e escalável)</div>
				<div>✔ Intuitivas (UX cuidadosamente planejado)</div>
				<div>✔ Alinhadas aos objetivos do negócio</div>
			</div>
			<p><b>Pronto para transformar desafios em resultados excepcionais.</b></p>
		</div>
	</div>
</template>

<script setup></script>

<style scoped>
	.site-container.sobre {
		background-color: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 100vh;
		padding: 72px 0;
	}
	.site-container.sobre .sobre-header {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 12px;
	}
	.site-container.sobre .sobre-header h1 {
		font-weight: 700;
		font-size: 56pt;
	}
	.site-container.sobre .sobre-header h2 {
		font-weight: 700;
		font-size: 24pt;
		margin-bottom: 8px;
	}
	.site-container.sobre .sobre-body {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: flex-start;
		width: var(--w-size);
		gap: 0px;
		margin-top: 8px;
	}
	.site-container.sobre .sobre-body p {
		margin: 16px 0;
	}
</style>

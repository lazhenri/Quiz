<svelte:head>
	<link rel="stylesheet" href="/styles/menu.css">
</svelte:head>

<script>
	import { estado } from './Estado.js'
	import { trocarEstadoDoJogo } from './Estado.js'
</script>

<h1>
	QUIZ
</h1>

<div class='menu' on:click={() => trocarEstadoDoJogo('jogar')}>
	JOGAR
</div>

<div class='menu' on:click={() => trocarEstadoDoJogo('sobre')}>
	SOBRE
</div>
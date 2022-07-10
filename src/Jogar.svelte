<svelte:head>
	<link rel="stylesheet" href="/styles/jogar.css">
</svelte:head>

<script>
	import VoltarMenu from './VoltarMenu.svelte'
	import Question from './Question.svelte';
    import Answer from './Answer.svelte';
    import Points from './Points.svelte';
	import { estado } from "./Estado.js"
	import { trocarEstadoDoJogo } from './Estado.js'

	// Esta classe representa o estado da tela jogar,
	// ela guarda o estado da tabela com trues e false,
	// a quantidade de atual de elementos verdadeiros,
	// e quantidade verdadeiros necessária para ganhar.

	let points = 0;
	let quizIndex = 0;
	const quiz = [
		{
			question:' o céu é azul?',
			correctAnswer: 0,
			answers: [
				'yes',
				'no'
			]
		},
			{
			question:' a grama é roxa?',
			currectAnswer: 1,
			answers: [
				'yes',
				'no'
			]
		},
		
	]
	
	function checkAnswer(answerText){
		const isCorrect = quiz[quizIndex].answers.indexOf(answerText) === quiz[quizIndex].currectAnswer;
		if (isCorrect)	{
			Points += 10
			quiz[quizIndex].question = 'Correct';
		}else {
			quiz[quizIndex].question = 'Wrong';
		}
		setTimeout(function() {
			quizIndex += 1
		}, 2000);
	}
</script>

<style>
	.jogar{
		
	}
</style>

<div class="Jogar">
	<Points />
	<Question questionText={quiz[quizIndex].question}/>
	<div class="answers">
	<Answer answerText={quiz[quizIndex].answers[0]}/>
	<Answer answerText={quiz[quizIndex].answers[1]}/>
</div>
</div>
	
<!-- reaproveita o botão de voltar para o menu -->
<VoltarMenu/>
<svelte:head>
	<link rel="stylesheet" href="/styles/jogar.css">
</svelte:head>

<script>
	import VoltarMenu from './VoltarMenu.svelte'
	import { estado } from "./Estado.js"
	import { trocarEstadoDoJogo } from './Estado.js'

	// Esta classe representa o estado da tela jogar,
	// ela guarda o estado da tabela com trues e false,
	// a quantidade de atual de elementos verdadeiros,
	// e quantidade verdadeiros necessária para ganhar.
	<svelte:head>
	<link rel="stylesheet" href="/styles/jogar.css">
</svelte:head>

	import VoltarMenu from './VoltarMenu.svelte'
	import { estado } from "./Estado.js"
	import { trocarEstadoDoJogo } from './Estado.js'

	// Esta classe representa o estado da tela jogar,
	// ela guarda o estado da tabela com trues e false,
	// a quantidade de atual de elementos verdadeiros,
	// e quantidade verdadeiros necessária para ganhar.

  let questions = [
    {
      "question": "amarelo",
      "options": [
        "*(fruta)",
        "|(bicho)",
        "-(cor)",
        "_(gosto)",
      ],
      "correctIndex":3
    },
    {
      "question": "peixe",
      "options": [
        "*(fruta)",
        "|(cor)",
        "-(animal)",
        "_(gosto)",
      ],
      "correctIndex":3
    },
    {
      "question": "fruta",
      "options": [
        "*(rosa)",
        "|(laranja)",
        "-(verde)",
        "_(salmao)",
      ],
      "correctIndex":2
    },
    {
      "question": "peixe",
      "options": [
        "*(bacalhau)",
        "|(laranja)",
        "-(verde)",
        "_(salmao)",
      ],
      "correctIndex":1
    },
  ];
  let answers = new Array(questions.length).fill(null);
  let questionPointer = -1;
  function getScore(){
    let score = answers.reduce((acc,val,index)=>{
      if(questions[index].correctIndex == val){
        return acc+1;
      }
      return acc;
    },0);
    return (score/questionPointer.length *100)+"%";
  }
  function restartQuiz(){

  }
</script>
<style>
  .app {
    position: absolute;
    top: 0px;
    left: 0px;
    width: 100vw;
    height: 100vh;
  }
  .app > div {
    width: 100%;
    height: 100%;
  }
  .app .start-screen,
  .app .score-screen {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .app .start-screen button,
  .app .score-screen button {
    padding: 10px 20px;
    background: blue;
    color: red;
    border: none;
    outline: none;
    border-radius: 20px;
    cursor: pointer;
  }
  .app .quiz-screen .main {
    padding: 50px;
  }
  .app .quiz-screen .main .options {
    display: flex;
    justify-content:space-between;
    flex-wrap: wrap;
  }
  .app .quiz-screen .main .options button {
    width: 45%;
    border-radius: 20px;
    margin: 10px 0px;
  }
  .app .quiz-screen .main .options button selected {
    background: #111;
    color: #eee;
  }
  .app .quiz-screen .footer {
    position: fixed;
    bottom: 0px;
    left: 0px;
    width: 100px;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #eee;
  }  
  .app .quiz-screen .footer > div {
    margin: 0px 10px;
  }
  .app .quiz-screen .progress-bar {
    width: 150px;
    height: 10px;
    background: #aaa;
    border-radius: 10px;
    overflow: hidden;
  }
  .app .quiz-screen .progress-bar div {
    height: 100%;
    background: purple;
  }
  .app .score-screen {
    flex-direction: column;
  }
</style>

<div class="app">
  {#if questionPointer==-1}
    <div class="start-screen">
      <button on:click={()=>{questionPointer=0}}>
        start Quiz
      </button>
  </div>    
  {:else if !(questionPointer > answers.length-1)}
  <div class="quiz-sreen">
    <div class="main">
      <h2>
        {questions[questionPointer].question}
       </h2>
     <div class="options">
        {#each questions[questionPointer].options as opt,i}
          <button class="{answers[questionPointer]==i?'selected':''}" on:click={()=>{answers[questionPointer]=i}}>
            {opt}
          </button>
        {/each}
      </div>   
    </div>
    <div class="footer">
      <div class="progress-bar">
        <div style='width:{questionPointer/questions.length*100}%'>
        </div>
      </div>  
      <div class="buttons">
          <button disabled={questionPointer==0} on:click={()=>{questionpointer--}}>
            &lt;
          </button>
          <button on:click={()=>{questionpointer++}}>
             &gt;
          </button>
        </div>
      </div>
    </div> 
  {:else}
    <div class="score-screen">
      <h1>
        your score: {get-screen()}
      </h1>
      <button on:click={restartQuiz}>
        restart

      </button>
    </div> 
  {/if}
 </div>


  <br>
<br>
<br>
<br>

<!-- reaproveita o botão de voltar para o menu -->
<VoltarMenu/> 
<br>

<!-- reaproveita o botão de voltar para o menu -->
<VoltarMenu/>
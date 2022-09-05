<script>
let TheAnswer = [];
let TrueAnswer = [8, 1, 4, 4, 4, 2, 5, 3];
function ChangeAnswer(CurrQuestion, CurrAnswer){
    TheAnswer[CurrQuestion - 1] = CurrAnswer;
    console.log(TheAnswer);
  }
  function CheckAnswer(){
    let correct = 0;
      for (let i = 0; i < 8; i++){
          if (TheAnswer[i] == TrueAnswer[i]){
              correct++;
            }
        }
    alert("คุณตอบถูก " + correct + " ข้อ");
    }
    function FindCurrent(currq,thea){
        if (TheAnswer[currq] == thea){
          console.log("shadow-lg");
            return "shadow-lg";
          }
          else {return;}
      }

</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1 class="font-bold">
  แบบทดสอบ IQ
	</h1>

	<h2>
  <div class="flex flex-col space-y-10">
  {#each [1, 2, 3, 4, 5, 6, 7, 8] as question}
    <img src={`./ques/q` + question + `.png`} />
    <div class={`grid gap-3 grid-cols-4`}>{#each [1, 2, 3, 4, 5, 6, 7, 8] as answer}
    {#if TheAnswer[question - 1] == answer}
      <button on:click|once={() => ChangeAnswer(question, answer)} ><img class="brightness-75 rounded-lg" src={`./ans/q` + question + `/` + answer + `.png`} /></button>
    {:else}
     <button on:click|once={() => ChangeAnswer(question, answer)} ><img class="md:hover:shadow-lg rounded-lg" src={`./ans/q` + question + `/` + answer + `.png`} /></button>
    {/if}{/each}</div>
  {/each}
  </div>
  <div class="flex h-screen"><div class="mt-5"><button on:click|once={CheckAnswer} class="px-8 py-4 font-bold tracking-wide text-white bg-gradient-to-b from-blue-400 to-blue-500 rounded-full transition duration-300 ease-in-out outline-none lg:scale-90 lg:hover:scale-100 dark:text-white focus:outline-none md:hover:shadow-lg md:hover:shadow-blue-500/50 md:hover:from-blue-500 md:hover:to-blue-500 md:hover:-translate-y-1 md:hover:scale-110">ตรวจคําตอบ</button></div></div>
	</h2>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
    @apply mb-10;
	}
</style>

<script context="module">
  export async function preload(page, session) {
    console.log("hello");
    const { slug } = page.params;
    const res = await this.fetch(
      `http://lit-cliffs-44994.herokuapp.com/question/${slug}`
    );
    const question = await res.json();
    console.log(question);
    return { question };
  }
</script>

<script>
  export let question;
</script>

<style>
  h1 {
    font-weight: bold;
  }
  main {
    background-color: white;
    margin-top: 20px;
    box-sizing: border-box;
    border: 1px solid;
    border-color: var(--border-color);
  }
  h1 {
    margin-bottom: 0;
  }
  .question {
    border-bottom: 2px solid var(--border-color);
    padding: 10px;
  }
  .answers {
    margin: 0;
    padding-left: 0.5em;
    background-color: gray;
    list-style: none;
  }
  li {
    background-color: white;
    padding-left: 1em;
    padding-top: 0.5em;
    min-height: 60px;
    border-bottom: 1px solid var(--border-color);
  }
  ul {
    padding: none;
  }

  .question-info {
    font-size: 0.7em;
    color: #808080;
  }
</style>

<svelte:head>
  <title>Q: {question.text}</title>
</svelte:head>

<main>
  <div class="question">
    <h1>{question.text}</h1>
    <div class="question-info">
      <span>Asked By:{question.discordUser}</span> on <span>{question.createdOn}</span>
    </div>
  </div>
  {#if question.answers.length > 0}
    <ul class="answers">
      {#each question.answers as answer}
        <li>{answer.text}</li>
      {/each}
    </ul>
  {:else}
    <p>There are no answers for this question</p>
  {/if}
</main>

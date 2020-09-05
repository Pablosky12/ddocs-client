<script context="module">
  export async function preload(page, session) {
    const { slug } = page.params;
    const res = await this.fetch(
      `http://lit-cliffs-44994.herokuapp.com/question`
    );
    const latestQuestions = await res.json();
    console.log(latestQuestions);
    return { latestQuestions };
  }
</script>

<script>
  export let latestQuestions;
</script>

<svelte:head>
  <title>Questions</title>
</svelte:head>

<h1>{latestQuestions.total}</h1>
{#each latestQuestions.questions as question}
  <li>{question.text}</li>
{/each}

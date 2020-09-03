<script context="module">
  export async function preload(page, session) {
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

<svelte:head>
  <title>{question.question_text}</title>
</svelte:head>

<h1>{question.text}</h1>
{#each question.answers as answer}
  <li>{answer.text}</li>
{/each}

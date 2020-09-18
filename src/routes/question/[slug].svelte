<script context="module">
  export async function preload(page, session) {
    console.log("hello");
    const { slug } = page.params;
    const res = await this.fetch(
      `http://localhost:3002/question/${slug}`
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
{#if question.answers.length > 0}
<ul>
  {#each question.answers as answer}
      <li>{answer.text}</li>
    {/each}
  </ul>
{:else}
  <p>There are no answers for this question</p>
{/if}

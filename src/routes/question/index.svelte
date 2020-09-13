<script context="module">
  export async function preload(page, session) {
    const { slug } = page.params;
    const res = await this.fetch(
      `http://lit-cliffs-44994.herokuapp.com/question`
    );
    const latestQuestions = await res.json();
    return { latestQuestions };
  }
</script>

<script>
  import QuestionItem from "../../components/QuestionItem.svelte";

  export let latestQuestions;
</script>

<style>
</style>

<svelte:head>
  <title>Questions</title>
</svelte:head>

<h1>Recent questions</h1>
<div class="list-container">
  {#each latestQuestions.questions as question}
    <QuestionItem class="question" {question} />
  {/each}
</div>

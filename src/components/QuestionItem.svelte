<script>
  export let question;
</script>

<style>
    h3 {
        font-weight: bold;
    }
  li {
    padding: 0;
    border: 1px solid #00000016;
    border-radius: 5px;
    list-style: none;
    box-shadow: 5px 5px 5px -5px rgba(0, 0, 0, 0.2);
    margin: 10px 0;
  }

  li a {
    padding: 1em;
    display: block;
    text-decoration: none;
  }

  li a div {
    display: flex;
    justify-content: space-between;
  }

  .answer-count {
    min-width: 2em;
    background-image: url("/icons/message.svg");
    background-size: 2em;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .answer-count span {
    background: white;
    height: 1em;
    min-width: 1em;
    font-size: 0.8em;
    line-height: 1em;
    font-weight: bold;
    display: flex;
    justify-content: center;
    margin-top: -5px;
    border-radius: 100%;
  }

  .extra-info {
    font-size: 0.6em;
    justify-content: flex-start;
  }
  .extra-info span {
      padding-right: 1em;
  }
</style>

<li>
  <a href="question/{question.id}" rel="prefetcg">
    <div>
      <h3>{question.text.charAt(0).toUpperCase()}{question.text.slice(1)}</h3>

      <div class="answer-count">
        {#if question.answerCount > 9}
          <span>+10</span>
        {:else}<span>{question.answerCount}</span>{/if}
      </div>
    </div>
    <div class="extra-info">
      <span> On: {question.createdOn} </span>
      <span> By: {question.discordUser}</span>
    </div>
  </a>
</li>

<script>
    export let question;
</script>

<style>
    li {
        padding: 1em;
        border: 1px solid #00000016;
        border-radius: 5px;
        list-style: none;
        box-shadow: 5px 5px 5px -5px rgba(0,0,0,0.2);
        margin: 10px 0;
    }

</style>

<li>
    <h3>{question.text.charAt(0).toUpperCase()}{question.text.slice(1)}</h3>
</li>
<script context="module">
  export async function preload(page, session) {
    const { slug } = page.params;
    const res = await this.fetch(
      `https://jsonplaceholder.typicode.com/todos/${slug}`
    );
    const user = await res.json();
    return { user };
  }
</script>

<script>
    export let user;
</script>

<svelte:head>
    <title>{user.title}</title>
</svelte:head>

<h1>
    {user.title}
</h1>



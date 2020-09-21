<script>
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<style>
  div {
      position: relative;
	  max-width: 56em;
	  margin: 0 auto;
  }
</style>

<Nav {segment} />

<div>
  <slot />
</div>

<script>
	import Counter from "./Counter.svelte";
	import Input from "./Input.svelte";
    import Monster from "./Monster.svelte";
	import Login from "./Login.svelte";
	let band = true;
</script>
{#if band}
	<Login />
{:else}
	<div class="background">
		<Monster />
	</div>
{/if}


<style>
	.background{
        background-color: rgb(27, 79, 85);
    }
</style>
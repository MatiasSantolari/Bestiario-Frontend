<script>
	import Counter from "./Counter.svelte";
	import Input from "./Input.svelte";
    import Monster from "./Monster.svelte";
	const commonProps = {maxCounter: 5} //asi no hace falta ponerlo debajo 3 veces, siendo que siempre será 5
</script>
<!--
<Counter initialCounter={7} {...commonProps}/>
<Counter initialCounter={2} {...commonProps}/>
<Counter {...commonProps}/>

<Input/>
-->

<Monster/>
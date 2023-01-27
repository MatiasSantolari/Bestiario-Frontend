<script>
let value = '';
let loading = false
let response=[];
const handleInput = (event) => value = event.target.value

$:if(value.length > 2){
    loading = true
    fetch(`http://www.omdbapi.com/?s=${value}&apikey=422350ff`)
    .then(res => res.json())
    .then(apiResponse => {
        response = apiResponse.Search || []
        loading = false
    })
}
</script>

<input placeholder="Search Movies..." value={value} on:input={handleInput}>

<!--renderizado condicional-->
{#if loading}
  <strong>Loading...</strong>
{:else}
  {#if response.length > 0}
    <strong>Tenemos {response.length} películas</strong>
  {:else}
    <strong>No hay resultados</strong>
  {/if}
{/if}
<!--fin renderizado condicional-->
<style>
    input{
        color: rgb(6, 0, 43);
        background-color: hotpink;
    }
</style>
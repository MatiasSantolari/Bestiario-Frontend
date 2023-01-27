<script>
    export let especie = '';
    export let monstruos = [];

    const handleInput = (event) => especie = event.target.value

    function handleClick(){
        fetch(`http://localhost:3000/api/monstruos`)
        .then(res => res.json())
        .then(apiResponse => {
        monstruos = apiResponse.body || []
        //console.log(`Monstruos: ${JSON.stringify(monstruos)}`)
        console.log(especie)
        })
    }

    function getAllMonstruos(){
        fetch(`http://localhost:3000/api/monstruos`)
        .then(res => res.json())
        .then(apiResponse => {
        monstruos = apiResponse.body || []
        })
    }
    function getMonstruosByEspecie(){
        fetch(`http://localhost:3000/api/monstruos/monstruoByEspecie/637bd550cdf8ea0527a5548f`)
        .then(res => res.json())
        .then(apiResponse => {
        monstruos = apiResponse.body || []
        })
    }

    //Renderizado condicional para filtrar monstruos por especie
    $:if(especie === 'Primigenios'){
        getMonstruosByEspecie()
    }
    else{fetch(`http://localhost:3000/api/monstruos`)
        getAllMonstruos()
    }
    //fin renderizado condicional para filtrar monstruos por especie

</script>

<input placeholder="Buscar por especie" value={especie} on:input={handleInput}>
<button on:click={handleClick}>Mostrar Monstruos</button>
<button on:click={getMonstruosByEspecie}>Mostrar Monstruos Primigenios</button>


{#each monstruos as monster}
    <p>{monster.nombre}</p>
    <p>{monster.estado}</p>
    <br>
{/each}

<!--
<p>
    {#each monstruos as monstruo}
        {monstruo.nombre}
    {/each}
</p>
-->
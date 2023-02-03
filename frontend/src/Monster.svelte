<script>
    let especie = 'Todos';
    let monstruos = [];
    let especies = ['Todos','Primigenios','Dioses Exteriores', 'Dioses Arquetípicos']

    //const handleInputEspecie = (event) => especie = event.target.value
    //const handleInputNombreMonstruo = (event) => nombreMonstruo = event.target.value

    function getOneMonstruo(){
        fetch(`http://localhost:3000/api/monstruos/monstruoNombre/${nombreMonstruo}`)
        .then(res => res.json())
        .then(apiResponse => {
            monstruos = apiResponse.body || []
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
        fetch(`http://localhost:3000/api/monstruos/monstruoByEspecie/${especie}`)
        .then(res => res.json())
        .then(apiResponse => {
            monstruos = apiResponse.body || []
        })
    }

    //Renderizado condicional para filtrar monstruos por especie
    $:if(especie != 'Todos'){
        getMonstruosByEspecie()
    }
    else{
        getAllMonstruos()
    }
    //fin renderizado condicional para filtrar monstruos por especie
</script>

<!--
<input placeholder="Buscar monstruo" value={nombreMonstruo} on:input={handleInputNombreMonstruo}>
-->

<div class="container">
    <div class="select-especie">
        <select bind:value={especie}>
            {#each especies as value}<option {value}>{value}</option>{/each}
        </select>
    </div>
    <br>

    <div class="row justify-content-center align-items-center g-2">
        <div class="col"> 
            <h1>
                Monstruos
            </h1>
        </div>
    </div>

    {#each monstruos as monster}
        <div class="column col-sm-12 col-md-6 col-lg-4 listado_horizontal">
            <div class="card text-bg-dark" style="width: 300px">
            <img class="card-img-top imagenes_monstruos img-thumbnail" src={monster.urlImagen} alt="Card image">
            <div class="card-body">
                <h4 class="card-title"> {monster.nombre} </h4>
                <p class="card-text">Detalle: {monster.detalle}</p>
                <p class="card-text">Nivel de Amenaza: {monster.nivelAmenaza}</p>
                <p class="card-text">Estado: {monster.estado}</p>
                <p class="card-text">Nombres Alternativos: {monster.nombresAlternativos}</p>
                <a href="#" class="btn btn-success">See Profile</a>
            </div>
            <br>
            </div>
        </div>
    {/each}
</div>
<style>
    .listado_horizontal{
        display: inline-block;
        margin-top: 20px;
    }
    .imagenes_monstruos{
        height: 399px;
        width: 399px;
    }
    h1{
        margin-top: 10px;
    }
    
    .select-especie{
        display: flex;
        justify-content: flex-end;
        padding-top: 30px;
        padding-right: 80px;
    }
</style>
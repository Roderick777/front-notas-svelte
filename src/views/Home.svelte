<script>
	import { onMount } from 'svelte'
	import axios from 'axios'
	import Item from '../components/item.svelte'	
	let texto = 'ejemplo'
	let listado = null 
	
	onMount(() => { obtener(); obtenerUser(); })
	async function obtener() {
		let respuesta = await axios.get('http://beta.redcollege.net/api/LibroClases/escuelas')
		listado = respuesta.data
	}
	async function obtenerUser() {
		let respuesta = await axios.get('http://roocodex.com/api/users')
		console.log('usuarios roocodex', respuesta.data)
	}
	async function crear() {
		let axiosConfig = {
			headers: {
				'Content-Type': 'application/json;charset=UTF-8',
				"Access-Control-Allow-Origin": "*",
			}
		}
		let datos = {
			nombre: 'Nombre',
			correo: 'Correo',
			password: '12345'
		} 

		let res = await axios.post('http://roocodex.com/api/user', datos, axiosConfig)
		console.log(res)
	}
</script>

<main class="container-fluid">
	<button class="btn btn-primary" on:click={ () => crear() }>Crear</button>
	<div>
		<h1>Hello!</h1>
		<input type="text" bind:value={texto}> 
	</div>
	<div class="row">
		{#if listado != null}
			{#each listado as elemento}
				<div class="col-xl-3 col-lg-4 col-md-6 col-sm-12 mb-4">
					<Item bind:dato={elemento} />
				</div>
			{/each}
		{/if}
	</div>
</main>

<style lang="scss">
	$primario : #ff3e00;
	h1 {
		color: $primario;
		text-transform: uppercase;
		font-weight: 100;
	}
</style>

<script>
  import Card from './Card.svelte'
  export let dato
</script>

<Card bind:titulo={dato.nombre}>
  <label>Correo: </label>{dato.correo_contacto}
</Card>
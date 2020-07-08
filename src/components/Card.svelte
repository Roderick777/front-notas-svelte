<script>
    export let titulo
</script>

<div class="card">
  <div class="card-body">
    <h5 class="card-title">{titulo}</h5>
    <div class="card-text">
        <slot />
    </div>
    <div class="text-center">
        <button class="btn btn-primary" on:click={() => console.log('nombre', titulo) }>boton</button>
    </div>
  </div>
</div>
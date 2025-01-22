<script>
  import { onMount } from 'svelte';

  let photos = []; // Lista de fotos
  let loading = true; // Indicador de carga
  let error = null; // Error al cargar las fotos

  onMount(async () => {
    try {
      // Consumir la API para obtener una lista de fotos
      const response = await fetch('https://picsum.photos/v2/list?page=1&limit=10');

      if (!response.ok) throw new Error('Error al cargar las fotos');

      photos = await response.json();
      console.log(photos);
    } catch (err) {
      error = err.message;
    } finally {
      loading = false;
    }
  });
</script>

<main>
  <h1>Galería de Fotos</h1>
  {#if loading}
    <p>Cargando fotos...</p>
  {:else if error}
    <p>Error: {error}</p>
  {:else}
    <div class="gallery">
      {#each photos as photo}
        <div class="photo">
          <img src={photo.download_url} alt={photo.author} />
          <p>Autor: {photo.author}</p>
        </div>
      {/each}
    </div>
  {/if}
</main>

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
  }

  .photo {
    text-align: center;
  }

  img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  p {
    margin: 0.5rem 0 0;
  }
</style>

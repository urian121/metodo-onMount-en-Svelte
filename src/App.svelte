<script>
  import "bootstrap/dist/css/bootstrap.min.css";
  import Api from "./components/Api.svelte";
  import { onMount } from "svelte";

  let message = "Cargando...";

  onMount(() => {
    // Simular una llamada a una API o una acción al montar el componente
    const timeout = setTimeout(() => {
      message = "¡Componente montado exitosamente!";
    }, 1000);

    // Cleanup si el componente se desmonta antes
    return () => {
      clearTimeout(timeout);
    };
  });
</script>

<div class="container mt-4">
  <div class="row">
    <div class="col-md-12">
      <h1 class="text-center fw-bold mb-5">
        El Método <code>onMount()</code> en Svelte <hr>
      </h1>
    </div>
  </div>
  <div class="row">
    <div class="col-md-5">
      <h1>{message}</h1>
    </div>
    <div class="col-md-7">
      <Api />
    </div>
  </div>
</div>

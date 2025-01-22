# Función `onMount()` con Svelte

#### Resultado final 😍

![](https://raw.githubusercontent.com/urian121/imagenes-proyectos-github/refs/heads/master/el-metodo-onMount-en-Svelte.gif)

A menudo, es necesario realizar ciertas acciones cuando un componente se renderiza en el DOM. 
Por ejemplo, llamar a una función para inicializar datos o configurar eventos antes de actualizar o eliminar un componente.
Para manejar estas situaciones, Svelte proporciona métodos de ciclo de vida como **`onMount()`**, **`beforeUpdate`**, **`afterUpdate`** y **`onDestroy()`**.

## ¿Qué es `onMount()`?

El método `onMount()` se ejecuta automáticamente después de que el componente se haya montado en el DOM. Este ciclo de vida es útil para realizar tareas como:

- Llamadas a APIs.
- Inicialización de bibliotecas externas.
- Configuración de suscripciones o eventos.

La función `onMount` programa una devolución de llamada para que se ejecute inmediatamente después de que el componente esté disponible en el DOM. Es importante destacar que debe llamarse durante la inicialización del componente (aunque puede provenir de un módulo externo).

## Ejemplo del Proyecto

Este proyecto demuestra cómo usar `onMount` en Svelte para ejecutar lógica al montar un componente. En este caso, se simula una llamada a una API que actualiza un mensaje en pantalla después de 2 segundos.

### Código Principal

```svelte
<script>
  import { onMount } from 'svelte';

  let message = 'Cargando...';

  onMount(() => {
    // Simular una llamada a una API o una acción al montar el componente
    const timeout = setTimeout(() => {
      message = '¡Componente montado exitosamente!';
    }, 2000);

    // Cleanup si el componente se desmonta antes
    return () => {
      clearTimeout(timeout);
    };
  });
</script>

<main>
  <h1>{message}</h1>
</main>
```

### Cómo Funciona

1. **Inicialización del Estado:**
   - Se define una variable `message` con un mensaje inicial.

2. **Uso de `onMount`:**
   - Se ejecuta una función que simula una tarea asíncrona (un `setTimeout` en este caso).
   - El mensaje cambia después de 2 segundos para reflejar que el componente se ha montado.

3. **Limpieza:**
   - Se retorna una función que limpia el temporizador si el componente se desmonta antes de completar el tiempo.

## Instalación y Ejecución

1. Clona este repositorio:
   ```bash
   git clone https://github.com/urian121/metodo-onMount-en-Svelte
   cd metodo-onMount-en-Svelte
   ```

2. Instala las dependencias:
   ```bash
   npm install
   ```

3. Inicia el servidor de desarrollo:
   ```bash
   npm run dev
   ```

4. Abre el navegador en `http://localhost:5173`.


# Apóyanos 🙌

✨ **Comparte este proyecto** con otros desarrolladores para que puedan beneficiarse 📢.

☕ **Invítame un café o una cerveza 🍺**:
   - [Paypal](https://www.paypal.me/iamdeveloper86) (`iamdeveloper86@gmail.com`).

👍 **Suscríbete a mi canal de [YouTube](https://www.youtube.com/WebDeveloperUrianViera?sub_confirmation=1)** para más contenido increíble y tutoriales.

⭐ **Déjanos una estrella en GitHub**:
   - Dicen que trae buena suerte 🍀.

Gracias por tu apoyo 🤓.

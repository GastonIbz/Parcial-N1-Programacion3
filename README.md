## Introducción

Página web interactiva que muestra un horario de cursada organizado y permite al usuario escuchar música simultáneamente. La idea futura es integrar una API de audio para ofrecer una experiencia más rica (como radio o música). Además, la página incluye una función de "Modo Luces" que aplica efectos visuales dinámicos a la tabla del horario.

## Funcionalidades Principales

1.  **Horario de Cursada:**
    * Presenta una tabla HTML claramente organizada con la información de las clases distribuidas por hora y día de la semana.
    * La estructura HTML de la tabla se basa en los siguientes elementos:
        * `<table>`: Contenedor principal del horario.
        * `<thead>`: Encabezado con los días de la semana y la hora.
        * `<tbody>`: Contenido principal con las filas de cada hora de clase.
        * `<tr>`: Representa cada fila del horario.
        * `<th>`: Celda para los encabezados (hora y días).
        * `<td>`: Celda de datos que contiene la materia y el profesor. Se utilizan los atributos `data-materia` y `data-profesor` para almacenar esta información de manera semántica.
        * Clases CSS (`.hora`, `.recreo`, `.profesor`): Se aplican para dar estilos específicos a diferentes elementos del horario.

2.  **Reproductor de Audio:**
    * Ubicado en la parte inferior de la página, permite reproducir una lista de canciones, navegar entre ellas y controlar la reproducción.
    * **Objetivos:**
        * Permitir la reproducción de una lista de archivos de audio.
        * Ofrecer controles básicos: Reproducción (Play), Pausa, Anterior y Siguiente.
        * Proporcionar una barra de progreso para visualizar y controlar el tiempo de reproducción.
    * **Variables y Estructuras (HTML):**
        * `<div class=”audio-player-container”>`, `<div class=”audio-player”>`: Contenedores principales para los elementos del reproductor.
        * `<button id="botonPlay">`, `<button id="botonPausa">`, `<button id="botonAnterior">`, `<button id="botonSiguiente">`: Botones para controlar la reproducción.
        * `<input type="range" id="barraProgreso">`: Barra de progreso para controlar la posición de reproducción.
        * `<span id="tiempoActualDisplay">`, `<span id="duracionDisplay">`: Elementos para mostrar el tiempo actual y la duración total.
        * `<audio id="reproductorAudio" src="" data-playlist='["ruta/cancion1.mp3", "ruta/cancion2.mp3", "ruta/cancion3.mp3"]'>`: Elemento de audio HTML que carga y reproduce los archivos de sonido. El atributo `data-playlist` contiene la lista de las canciones en formato JSON.
    * **Variables y Estructuras (JavaScript):**
        * `reproductorAudio` (`const`): Referencia al elemento `<audio>`.
        * `botonPlay`, `botonPausa`, `botonAnterior`, `botonSiguiente`, `barraProgreso`, `tiempoActualDisplay`, `duracionDisplay` (`const`): Referencias a los elementos interactivos del reproductor.
        * `listaDeReproduccion`: Array JavaScript que contiene las rutas de los archivos de audio, obtenida del atributo `data-playlist`.
        * `indiceCancionActual`: Índice numérico que representa la posición de la canción que se está reproduciendo actualmente dentro de `listaDeReproduccion` (comenzando desde 0).
    * **Funciones (JavaScript):**
        * `cargarCancion(indiceCancion)`: Carga la canción especificada en el reproductor según su índice.
        * `formatearTiempo(segundos)`: Formatea el tiempo en minutos y segundos para su visualización.
    * **Eventos (JavaScript):**
        * Eventos de clic en los botones de Play, Pausa, Anterior y Siguiente para controlar la reproducción.
        * Evento `timeupdate` del elemento `<audio>` para actualizar la barra de progreso y los tiempos durante la reproducción.
        * Evento `input` de la barra de progreso para permitir la navegación manual en la canción.
        * Evento `ended` del elemento `<audio>` para pasar automáticamente a la siguiente canción al finalizar la actual.

3.  **Modo Luces:**
    * Se activa y desactiva mediante un botón en la parte inferior de la página.
    * Al activarse, aplica un efecto visual dinámico de gradientes de color aleatorios a las celdas del horario.
    * **Variables y Estructuras (JavaScript):**
        * `botonLuces` (`const`): Referencia al botón "Activar Luces".
        * `celdasMaterias`, `celdasRecreo`, `celdasDias` (`const`): Colecciones de elementos del DOM correspondientes a las celdas del horario.
        * `modoLucesActivo` (`let`): Variable booleana para rastrear el estado del modo luces.
        * `intervalosLuces` (`let`): Array para almacenar los IDs de los intervalos de color.
    * **Funciones (JavaScript):**
        * `ColorAleatorio()`: Genera un color RGB aleatorio.
        * `GradienteAleatorio()`: Genera un gradiente lineal aleatorio utilizando dos colores aleatorios.
        * `activarModoLuces()`: Aplica gradientes dinámicos a las celdas del horario utilizando `setInterval()`.
        * `desactivarModoLuces()`: Detiene los intervalos y remueve los estilos de fondo de las celdas.
    * **Eventos (JavaScript):**
        * Evento de clic en el `botonLuces` para alternar entre activar y desactivar el modo luces.

## Instrucciones de Uso

* **Horario de Cursada:** La tabla muestra el horario de tus clases. Cada celda contiene el nombre de la materia y el profesor. Las filas sombreadas indican los recreos.
* **Reproductor de Audio:**
    * Para reproducir o pausar la música, utiliza los botones con los símbolos ▶ (Play) y ❚❚ (Pausa).
    * Para pasar a la canción anterior o siguiente, haz clic en los botones con los símbolos ⏮ (Anterior) y ⏭ (Siguiente).
    * Puedes controlar el avance de la canción haciendo clic en cualquier punto de la barra de reproducción.
* **Modo Luces:** Haz clic en el botón "Activar Luces" para iniciar el efecto de cambio de color en el horario. Haz clic de nuevo en "Desactivar Luces" para detenerlo.

## Próximos Pasos

La idea a futuro es seguir aprendiendo y expandiendo las funcionalidades de esta página web. Algunas posibles implementaciones incluyen:

* Integración de una API de audio (como Spotify, SoundCloud o una API de radio online) para ofrecer una mayor variedad de contenido.
* Mejoras en la interfaz de usuario y el diseño visual.
* Implementación de persistencia de datos para guardar las preferencias del usuario (por ejemplo, la última canción reproducida o el estado del Modo Luces).
* Adición de más funcionalidades interactivas al horario (por ejemplo, resaltar la clase actual).

## Tecnologías Utilizadas

* HTML
* CSS
* JavaScript

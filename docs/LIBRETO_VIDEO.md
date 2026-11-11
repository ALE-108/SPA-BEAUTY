# Libreto del desarrollo — GlowQueen Spa & Beauty

Guion para una futura explicación de un programador. Duración orientativa: 15–20 minutos, según las pausas y demostraciones. La grabación todavía no se ha realizado. Las expresiones «voy a crear» y «voy a cambiar» son indicaciones para una demostración futura: el código entregado ya contiene el resultado.

## Preparar antes de grabar

Abrir el proyecto en el editor, el PDF en su página 2, una terminal y el navegador. Ejecutar `npm ci`, `npm run build` y `npm start`. En una segunda terminal se puede dejar `npm run watch`. Usar primero un viewport de 1920 × 1080 al 100 % de zoom y luego mostrar el modo móvil. Aumentar el tamaño de la fuente del editor para que el código se lea en video. Preparar una copia de demostración para cambios temporales y restaurarla después.

No mostrar configuración de cuentas ni credenciales. El repositorio es privado: para enseñar el resultado basta el navegador local y los archivos del ejercicio.

## Escena 1. Entender qué vamos a construir — 0:00–1:20

**En pantalla:** alternar entre el PDF y la página terminada.

**Narración:**

«Vamos a reproducir esta cabecera de un spa llamado GlowQueen. Primero identifico sus piezas: arriba están la marca, la navegación y los accesos de cuenta. A la izquierda hay un título, una descripción y dos acciones. Debajo aparecen tres cifras. A la derecha tenemos una fotografía con transparencia y dos tarjetas de testimonios.

»La referencia mide 1920 por 1080. Mi primer objetivo es reproducir esa composición con precisión. La consigna no exige responsive, pero después mostraré una adaptación sencilla para que el contenido también se pueda leer en un teléfono.

»Es una práctica de HTML y CSS. No necesitamos un servidor de reservas, una base de datos ni una aplicación de cuentas. Los botones de esas funciones mostrarán un aviso para que la maqueta no prometa servicios que todavía no tiene.»

**Idea a destacar:** leer los requisitos antes de elegir tecnologías. La privacidad actual del repositorio es una decisión del propietario y prevalece sobre la publicación pública que pide la consigna.

## Escena 2. Preparar recursos y carpetas — 1:20–2:40

**En pantalla:** árbol del proyecto y `docs/RECURSOS.md`. Abrir la fotografía y uno de los SVG.

**Narración:**

«Antes de escribir estilos, preparo los recursos originales. La modelo viene del Figma y conserva el fondo transparente. Ese canal alfa permite verla encima de los dos colores del fondo sin un rectángulo blanco alrededor.

»Los iconos de las estadísticas y la flor se recuperaron como vectores del PDF. SVG mantiene los bordes definidos al cambiar de tamaño. La fotografía sí es una imagen rasterizada, guardada como WebP.

»También guardo Poppins dentro del proyecto. Así, al abrir la página, el navegador no necesita pedir la fuente a otro sitio. Su licencia está junto a los archivos.

»Separo contenido, recursos y estilos. El navegador lee index.html y el CSS. Sass es nuestra herramienta de desarrollo: tenemos que compilarlo para producir ese CSS.»

**Demostración:** señalar `assets/`, `scss/`, `css/` y `package-lock.json`. Explicar que las dependencias se reconstruyen con `npm ci` y no se suben desde `node_modules`.

## Escena 3. Dar significado al HTML — 2:40–4:10

**En pantalla:** `index.html`, desde `<html lang="en">` hasta el comienzo de `<main>`.

**Narración:**

«La página conserva textos en inglés; por eso declaro lang igual a en. El título de la pestaña y la descripción ayudan a identificar el documento.

»Uso header para la cabecera y nav para el bloque de navegación. Los enlaces van dentro de una lista porque forman un conjunto de destinos relacionados.

»Un enlace sirve para ir a un lugar. Un botón sirve para ejecutar una acción. Home y Services tienen destinos reales dentro de esta misma página. Book Now es un botón porque abrirá un aviso.

»La lupa no lleva texto visible, así que añado un nombre accesible con aria-label. El SVG interior es decorativo y lleva aria-hidden para que el lector de pantalla no lo anuncie por separado.

»Los comentarios explican pequeños grupos. La idea es que otra persona entienda para qué existe cada bloque sin tener que reconstruir toda la página.»

**Demostración:** seguir con el cursor la relación entre `href="#services"` e `id="services"`. Mostrar que hay un único `h1`.

## Escena 4. Organizar Sass y fijar la escala — 4:10–5:50

**En pantalla:** `scss/styles.scss` y `scss/_tokens.scss`.

**Narración:**

«El archivo principal importa módulos con responsabilidades concretas: base, cabecera, composición y móvil. Los archivos que empiezan por guion bajo son parciales de Sass; no son hojas CSS independientes que tengamos que enlazar en HTML.

»En tokens centralizo los colores. Si más adelante se corrige el azul, tengo un lugar claro donde cambiarlo.

»La función design recibe una medida del lienzo original. Una unidad cqw representa el uno por ciento del ancho del contenedor. En un lienzo de 1920, equivale a 19,2 píxeles. Por eso divido cada medida entre 19,2. Por ejemplo, design de 160 produce aproximadamente 8,33 cqw; cuando el contenedor mide 1920, vuelve a ser 160 píxeles.

»Esto mantiene las proporciones en escritorio. Para que funcione, el contenedor stage declara container-type: inline-size. No es una solución universal para cualquier web: aquí resulta útil porque estamos reproduciendo una composición fija.»

**Demostración:** señalar un `design(160)` y reducir ligeramente el viewport. No cambiar la función en el código final.

## Escena 5. Construir la base y la cabecera — 5:50–7:20

**En pantalla:** `scss/_base.scss` y `scss/_header.scss`.

**Narración:**

«Primero reduzco las diferencias por defecto del navegador: quito el margen del body y uso border-box para que el ancho incluya rellenos y bordes.

»Declaro las variantes de Poppins con font-face y su peso correspondiente. La ruta parte del CSS compilado, por eso sube un nivel antes de entrar en assets.

»En la cabecera, Grid distribuye marca, navegación y acciones. Dentro de cada grupo, Flexbox alinea los elementos. Combino las herramientas según la distribución que necesito.

»No fijo una coordenada para cada enlace. Mantengo relacionados los elementos que pertenecen al mismo bloque; eso hace que los ajustes sean más fáciles.

»Los botones comparten una clase base. Hover cambia su aspecto al pasar el ratón. Focus-visible dibuja una señal al usar el teclado, que es una interacción distinta y también debe verse.»

**Demostración:** pasar el ratón por Sign Up y luego usar Tab. Abrir More y explicar que `details` y `summary` ofrecen un desplegable nativo.

## Escena 6. Crear el fondo y colocar la fotografía — 7:20–9:10

**En pantalla:** `scss/_hero.scss`, reglas de `.stage`, `.stage::before`, `.lotus` y `.portrait`.

**Narración:**

«Stage es nuestro lienzo. Tiene posición relativa y proporción de dieciséis novenos. Las capas con posición absoluta toman este contenedor como referencia.

»El fondo se dibuja con un pseudoelemento: su altura reproduce la franja coloreada del PDF y un gradiente separa el crema del verde agua. No necesitamos una imagen grande para pintar dos colores.

»La flor es decorativa, tiene alt vacío y una opacidad baja. La fotografía conserva su proporción y ocupa una capa por delante del fondo. Su posición se calculó teniendo en cuenta el recorte transparente del recurso original.

»El z-index establece qué elemento queda delante. Isolation mantiene esa organización dentro de nuestro lienzo. Overflow clip recorta lo que sale del borde, como la parte inferior de la fotografía en la referencia.

»El posicionamiento absoluto está reservado a la composición que necesita superposiciones. El contenido dentro de cada tarjeta sigue usando el flujo normal.»

**Demostración:** desactivar temporalmente la regla de la fotografía en DevTools y volver a activarla para mostrar qué aporta cada capa.

## Escena 7. Afinar el texto y las acciones — 9:10–10:30

**En pantalla:** `.hero-copy`, `.hero-description` y `.hero-actions`.

**Narración:**

«La tipografía ocupa mucho espacio visual. Aunque la imagen esté bien, una fuente incorrecta o un interlineado distinto cambia toda la composición.

»Ajusto el tamaño del título, sus dos líneas y la separación con la descripción. Los saltos que necesitamos para esta referencia están explícitos. El salto de la descripción se oculta en móvil para dejar que el texto se distribuya con el ancho disponible.

»Las acciones se alinean con Flexbox. El icono de reproducción vive dentro del botón completo, de modo que se puede hacer clic tanto en el círculo como en el texto.

»Cuando comparo con el PDF, corrijo primero tamaños y posiciones grandes. Después ajusto márgenes, radios, transparencias y sombras. No intento arreglar todo a la vez.»

**Demostración:** mostrar ambas vistas a la misma resolución y explicar que el navegador y el PDF pueden rasterizar los bordes del texto de forma ligeramente distinta.

## Escena 8. Maquetar cifras y testimonios — 10:30–12:00

**En pantalla:** HTML de `.statistics` y `.testimonials`, seguido de sus estilos.

**Narración:**

«Las tres estadísticas forman una lista. Cada elemento contiene un icono decorativo, una cifra destacada y una descripción. Las cifras y sus etiquetas son texto seleccionable.

»Grid distribuye las columnas. Sus proporciones mantienen los centros del diseño original. Dentro de cada columna, Flexbox apila los elementos y los centra.

»Para los testimonios uso blockquote y figcaption dentro de figure. Así distingo el contenido de la cita y su autor. La posición de cada tarjeta cambia, pero el orden del HTML sigue siendo lógico.

»El fondo blanco tiene transparencia. Backdrop-filter difumina lo que hay detrás de la tarjeta, no el texto que contiene. Si un navegador no aplica ese efecto, conserva el fondo semitransparente.

»Las comillas se dibujan con pseudoelementos. Se marcan como decorativas para que no se lean como contenido adicional.»

**Demostración:** seleccionar una frase del testimonio en el navegador. Mostrar que no es una captura colocada como fondo.

## Escena 9. Interacción y accesibilidad — 12:00–13:30

**En pantalla:** avisos al final de `index.html` y estilos de foco en `_base.scss`.

**Narración:**

«Los materiales no incluyen un sistema de reservas ni un video. En lugar de dejar botones sin respuesta, muestro un aviso que explica el alcance de esta vista.

»Uso popover, una función nativa de HTML. El atributo popovertarget apunta al identificador del aviso. El navegador lo abre y permite cerrarlo con Escape. También hay un botón de cierre explícito.

»El enlace Skip to content aparece al recibir foco y permite saltar la navegación. Main tiene tabindex menos uno para poder recibir ese foco sin añadirse a la secuencia habitual de Tab.

»Las imágenes informativas tienen texto alternativo y las decorativas llevan alt vacío. Además, si la persona ha solicitado reducir movimiento, desactivo las transiciones.

»Estas comprobaciones mejoran el acceso, aunque no equivalen a una auditoría completa de accesibilidad. Por ejemplo, conservamos el gris de la referencia y no afirmamos una certificación de contraste.»

**Demostración:** abrir Book Now, pulsar Escape, usar el enlace de salto y abrir Watch Video. No simular una reserva ni introducir datos personales.

## Escena 10. Mantener legibilidad en móvil — 13:30–14:40

**En pantalla:** `_mobile.scss` y viewport de 390 px.

**Narración:**

«Bajo 900 píxeles cambio el enfoque. El lienzo deja de tener una altura proporcional fija y los bloques vuelven al flujo.

»La cabecera permite varias filas, el título usa un tamaño legible y las tarjetas dejan de superponerse. La fotografía se coloca entre las estadísticas y los testimonios.

»No reduzco toda la composición hasta convertir el texto en algo minúsculo. En móvil reorganizo los bloques. Esta parte es una mejora adicional sobre el escritorio que exige el ejercicio.»

**Demostración:** recorrer la página completa y comprobar que no aparece desplazamiento horizontal.

## Escena 11. Compilar y verificar — 14:40–16:00

**En pantalla:** terminal y `package.json`.

**Narración:**

«Para repetir el entorno uso npm ci: instala las versiones e integridades del lockfile. Npm run build transforma Sass en CSS. El archivo compilado también se guarda en Git para poder abrir la página sin instalar herramientas.

»Check:css recompila y falla si el CSS guardado estaba desactualizado. Format:check comprueba el formato de los archivos fuente. GitHub Actions repite esas comprobaciones al subir cambios.

»Además de compilar, hay que abrir la página. Se comprobó en Chromium que las imágenes y fuentes cargan, los enlaces internos llegan a sus destinos, el menú abre, los avisos cierran y el teclado permite saltar al contenido. También se revisaron capturas de escritorio y móvil.

»Un build correcto no demuestra por sí solo que el diseño coincida con el PDF. Por eso se hizo también una comparación visual a la resolución de referencia.»

**Demostración:** ejecutar `npm run check:css` y `npm run format:check`. Abrir DevTools y mostrar que no hay recursos fallidos.

## Escena 12. Entregar y continuar — 16:00–17:00

**En pantalla:** README y árbol de archivos, sin mostrar configuración privada.

**Narración:**

«El proyecto se entrega en un repositorio específico y privado. El README explica cómo ejecutarlo, dónde editar los estilos y qué funciones son sólo parte de la maqueta.

»La consigna pide un enlace público, pero el propietario ha indicado mantener la privacidad en esta primera etapa. Por eso no se habilitó GitHub Pages. Si más adelante se autoriza la publicación, primero revisaremos los permisos de los recursos y después prepararemos ese despliegue.

»Para mantener el proyecto, cambio los módulos Sass, compilo y guardo el CSS junto con el código. Si una modificación publicada falla, git revert permite deshacerla conservando el historial.

»Ya tenemos una base que se puede estudiar y explicar: estructura semántica, composición con capas, estilos organizados e interacciones visibles. La grabación de esta explicación será el siguiente trabajo.»

## Preguntas para preparar la explicación

| Pregunta                                  | Respuesta que conviene demostrar                                                                  |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------- |
| ¿Por qué Sass?                            | Centraliza colores, permite módulos y convierte medidas con una función. El navegador recibe CSS. |
| ¿Por qué no un framework?                 | La maqueta no necesita estado complejo ni componentes dinámicos.                                  |
| ¿Por qué absolute?                        | Reproduce superposiciones dentro de un contenedor controlado. En móvil se recupera el flujo.      |
| ¿Qué diferencia hay entre Grid y Flexbox? | Grid organiza columnas; Flexbox alinea elementos dentro de grupos.                                |
| ¿Para qué sirve cqw?                      | Expresa medidas según el ancho del contenedor, no según cualquier elemento de la pantalla.        |
| ¿Qué hace WebP?                           | Guarda la fotografía con transparencia y menor peso; los iconos siguen siendo SVG.                |
| ¿Por qué no funciona una reserva real?    | El alcance es maquetación y no existe un backend de reservas. El aviso lo explica.                |
| ¿Qué falta para la entrega pública?       | Autorización del propietario, revisión de recursos y despliegue.                                  |

## Lista de comprobación para la futura grabación

- Ensayar el recorrido completo con los mismos nombres de archivo del proyecto.
- Grabar código legible y mantener las pausas necesarias para seguirlo.
- Mostrar el resultado antes de entrar en el código.
- No atribuir al video acciones que no se muestren ni servicios que no existen.
- Restaurar los cambios temporales de demostración y recompilar al terminar.

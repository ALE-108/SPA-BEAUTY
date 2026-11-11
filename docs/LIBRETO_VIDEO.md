# Libreto — maquetación estática GlowQueen

Guion para un programador que explica el desarrollo del ejercicio. Duración orientativa12–15minutos con demostraciones. El video todavía no está grabado. Los cambios de demostración se hacen en una copia y se restauran.

## Preparación

Abrir el PDF en página2, el editor y el navegador a1920×1080, zoom100%. Ejecutar `npm ci`, `npm run build` y `npm start`. Aumentar la fuente del editor. No mostrar cuentas ni credenciales.

## Escena 1. Leer la consigna

**Pantalla:** Captura de requisitos y PDF.

**Narración:** «Este ejercicio pide reproducir la cabecera del spa con fidelidad al PDF, HTML semántico e iconos SVG cuando sea posible. Los elementos interactivos deben tener hover. Sass está recomendado, pero no es obligatorio. También se exige repositorio específico y enlace público. Usaremos la composición estática de1920por1080. No añadiremos una versión móvil, desplegables ni servicios de reservas.»

**Demostración:** Identificar marca, navegación, texto, foto, estadísticas y testimonios.

## Escena 2. Preparar recursos

**Pantalla:** assets/ y docs/RECURSOS.md.

**Narración:** «La foto original se recuperó del archivo FIG adjunto y conserva transparencia. No se abrió Figma ni se inspeccionaron sus capas desde la aplicación. Los vectores vienen del PDF. WebP guarda la foto; SVG mantiene definidos los iconos. Poppins se incluye localmente con OFL; se identificó por comparación, no por un nombre legible de las fuentes del PDF.»

**Demostración:** Mostrar la transparencia de la foto y abrir un SVG.

## Escena 3. Construir HTML semántico

**Pantalla:** index.html.

**Narración:** «Header contiene la cabecera y nav identifica la navegación. Main contiene el contenido principal, con un único h1. Las estadísticas son una lista; las citas usan blockquote con autor. Los textos siguen siendo seleccionables. Las imágenes decorativas tienen alt vacío y los botones de icono llevan nombre accesible. Los botones reproducen el diseño, sin reservas, compras, cuentas o video reales.»

**Demostración:** Relacionar cada etiqueta semántica con su bloque visual y señalar comentarios por grupos.

## Escena 4. Explicar Sass y SCSS

**Pantalla:** scss/styles.scss, _tokens.scss y package.json.

**Narración:** «Sí usamos Sass. SCSS es una de sus sintaxis: permite CSS con variables, funciones y módulos. Los parciales empiezan con guion bajo y se cargan con use. Tokens centraliza colores. La función design añade píxeles a las medidas de referencia, sin escalarlas con la pantalla. El navegador no interpreta SCSS; npm run build ejecuta Sass y genera css/styles.css, que enlazamos desde HTML.»

**Demostración:** Compilar y localizar en el CSS una regla que utiliza una variable Sass. Mostrar watch como ayuda de desarrollo.

## Escena 5. Maquetar la cabecera

**Pantalla:** _header.scss.

**Narración:** «Grid distribuye marca, navegación y acciones. Flexbox alinea elementos dentro de esos grupos. La navegación y la flecha de More se reproducen visualmente como en el PDF. More no abre una lista adicional. Los nombres y comentarios indican qué bloque controla cada regla.»

**Demostración:** Mostrar una regla Grid y una Flexbox, y su efecto en pantalla.

## Escena 6. Construir lienzo y capas

**Pantalla:** _hero.scss y PDF a igual resolución.

**Narración:** «Stage mide1920por1080píxeles y no usa breakpoints ni reordena bloques al reducir la ventana. En una pantalla menor se recorre mediante desplazamiento. Relative ancla las capas absolute. Z-index ordena fondo, fotografía, texto y tarjetas. La foto conserva transparencia y la flor aparece detrás con poca opacidad. Sombras, degradado y transparencias reproducen el aspecto estático del PDF; no son animaciones.»

**Demostración:** Desactivar temporalmente la foto en DevTools y restaurarla para mostrar las capas.

## Escena 7. Afinar texto, cifras y citas

**Pantalla:** hero-copy, statistics y testimonial.

**Narración:** «La fuente y el interlineado afectan a la fidelidad. Primero ajusto posiciones y tamaños; después márgenes, radios y transparencias. Las cifras se distribuyen en tres columnas. Las citas tienen fondo semitransparente y difuminado del fondo mediante backdrop-filter, que no mueve el contenido. Comparamos siempre a1920por1080. Puede haber diferencias menores de rasterizado entre PDF y navegador.»

**Demostración:** Seleccionar texto para mostrar que no está convertido en imagen y comparar la composición.

## Escena 8. Implementar el hover exigido

**Pantalla:** Selectores hover de _base.scss, _header.scss y _hero.scss.

**Narración:** «La consigna sí pide hover: al colocar el puntero sobre un control, cambia su aspecto. No exige animación ni prescribe colores concretos. El menú superior cambia a verde oscuro sin subrayado. Los botones cambian de fondo; los demás enlaces conservan su subrayado; la marca cambia de opacidad y los iconos cambian de color. Video cambia el fondo del círculo y subraya su texto. Son cambios inmediatos. No hay transition, animation ni keyframes, tampoco popovers ni un desplegable. El foco de teclado conserva el comportamiento nativo del navegador.»

**Demostración:** Pasar por los doce controles y pulsarlos para comprobar que no aparecen funciones adicionales.

## Escena 9. Verificar la entrega

**Pantalla:** Tabla de requisitos del README y terminal.

**Narración:** «Reviso semántica, SVG, recursos originales, composición, hover y enlaces de entrega. Npm run check:css verifica que el CSS guardado coincida con la compilación Sass. Format:check revisa el formato. En el navegador comprobamos recursos, medidas fijas, hover y ausencia de funciones extra. Compilar no demuestra por sí solo fidelidad: también se revisa una captura frente al PDF.»

**Demostración:** Ejecutar comandos y mostrar el lienzo a1920por1080 y el hover.

## Escena 10. Entregar en GitHub y Pages

**Pantalla:** Repositorio y https://ale-108.github.io/SPA-BEAUTY/.

**Narración:** «El ejercicio tiene repositorio específico y enlace público. Pages sirve la raíz de main y nojekyll evita procesarla como un sitio Jekyll. El README explica ejecución y compilación. Este libreto describe la versión estática entregada; la grabación corresponde a la etapa posterior.»

**Demostración:** Abrir la URL pública y comparar con la versión local.

## Preguntas para ensayar

| Pregunta                                              | Respuesta                                                           |
| ----------------------------------------------------- | ------------------------------------------------------------------- |
| ¿Se usó Sass?                                         | Sí: SCSS, módulos, variables y función de medidas; compila a CSS.   |
| ¿Era obligatorio?                                     | No, recomendado por la consigna.                                    |
| ¿Qué interacción se exige?                            | Hover visible en elementos interactuables.                          |
| ¿Hover es una animación?                              | No; aquí el cambio es inmediato.                                    |
| ¿More debe desplegarse?                               | No lo exige la consigna; se reproduce su aspecto.                   |
| ¿Se exige responsive?                                 | No; esta versión conserva el lienzo estático de escritorio.         |
| ¿Por qué los botones no reservan ni reproducen video? | Son parte de un ejercicio de maquetación, sin servicios de negocio. |

# Recursos y procedencia

## Material de la consigna

El propietario proporcionó un PDF de referencia y dos ZIP con archivos Figma. La composición reproducida corresponde a la página 2 de `spa-beauty-entregable_9a594217.pdf`, titulada GlowQueen. El PDF tiene tamaño de página 1920 × 1080.

- `assets/images/model.webp`: fotografía original con canal alfa extraída de la imagen `30f53723d6cf4245c6d4f518fd6fa57f431e1561` del Figma `spa & beauty entregable.fig`, contenido en el primer ZIP. Se recortó el espacio transparente, se redimensionó a 1100 × 1330 y se convirtió a WebP. No se generó ni sustituyó la modelo.
- `treatment.svg`, `therapist.svg`, `herbal.svg` y `lotus.svg`: trayectorias vectoriales recuperadas de la página 2 del PDF. Se descartaron duplicados negros asociados a sombras. La flor se aplica como decoración de baja opacidad.
- Iconos de lupa, bolsa, flecha y reproducción: trazos SVG simples escritos en el HTML siguiendo la referencia.
- Los textos, las cifras y los nombres de los testimonios se conservan del diseño proporcionado.

La consigna no aporta una licencia de redistribución de la fotografía, marca o diseño. Su uso aquí corresponde al ejercicio solicitado. No se atribuye una licencia abierta a estos materiales. El propietario autorizó publicar este ejercicio y su repositorio el 11 de noviembre de 2026. Esta autorización de publicación no convierte los materiales originales en recursos con licencia abierta.

## Tipografía

Poppins, de Indian Type Foundry. Archivos Regular, Medium, SemiBold y Bold descargados del [repositorio oficial Google Fonts](https://github.com/google/fonts/tree/main/ofl/poppins). Se incluye su licencia SIL Open Font License 1.1 en `assets/fonts/OFL.txt`.

La identificación Poppins se contrastó visualmente y mediante medidas de texto con el PDF. El PDF contiene fuentes Type 3 sin nombre de familia legible; por eso no se presenta ese nombre como metadato extraído del documento. Puede haber pequeñas diferencias de rasterización entre PDF y navegador.

## Dependencias

Sass compila los estilos y Prettier mantiene el formato de las fuentes de código. Sus versiones exactas e integridades están en `package-lock.json`. La página final no descarga bibliotecas, tipografías ni imágenes de terceros durante su uso.

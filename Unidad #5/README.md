# Reto 5: Forum

## 1. Punto de partida

El reto de esta unidad era entender los sistemas de partículas como elementos que se relacionan entre sí, no como un montón de efectos bonitos. Así que la pregunta con la que arranqué fue: ¿cómo hago para que el movimiento diga algo del discurso y no solo lo decore?
La charla habla de comunidad, de confianza y de que las generaciones nuevas y las que ya tienen camino recorrido crecen más cuando trabajan juntas. Quería que eso se sintiera en la pantalla sin dibujarlo literal (nada de abuelitos y jóvenes de caricatura). La idea que me ordenó todo fue esta: el arte de fondo cambia de comportamiento igual que cambia la historia. Empieza con algo que respira, pasa por estructuras rígidas, se abre a redes y flujos, y termina construyendo un terreno nuevo.
Además, tenía una condición práctica: la presentación se iba a proyectar en pantalla grande en un evento internacional, y también tenía que correr bien online. Por eso la hice como página web, con una regla clara: el canvas siempre va detrás y nunca puede tapar un texto ni una foto.


## 2. Concepto y decisiones de diseño
En vez de una sola escena que se transforma, armé siete escenografías generativas y las repartí a lo largo de los 13 momentos del guion. Cada una tiene su propia lógica de movimiento y encaja con lo que se está diciendo en ese momento.
Algunas decisiones que tomé:
- Orgánico, no geométrico. Quería evitar ese look de "hecho por IA": círculos perfectos y figuras duras. Usé ruido de Perlin y campos de flujo para que todo se sienta más vivo, como una célula respirando o una corriente de agua.
- Dos colores, dos maneras de estar. Un dorado para la experiencia y un azul ultravioleta para las nuevas generaciones. No quise etiquetar "esto es joven, esto es mayor"; los dos colores conviven y se mezclan, y en la hélice y la topografía se funden.
- p5.js en vez de algo más pesado. La entrega era corta y necesitaba abrirse directo en el navegador. p5.js me daba control total del dibujo sin complicarme con instalaciones.
- Texto primero. La interfaz va en una capa aparte, por encima del canvas, con un velo oscuro suave detrás del texto para que se lea bien incluso en un proyector.




























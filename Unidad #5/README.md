# Reto 5: Forum

[Evento Forum](https://armandomr99.github.io/ForumBoceto/)

<img width="2439" height="1307" alt="image" src="https://github.com/user-attachments/assets/e9991a90-b788-4762-aa98-b9711cfb2356" />

[Github del Programa](https://github.com/ArmandoMR99/ForumBoceto)

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


## 3. Gramática Visual

| Elemento o comportamiento | Qué significa dentro del discurso |
| :--- | :--- |
| Anillos con ruido de Perlin | Algo vivo que respira: la idea de que un espacio puede abrirse y cambiar |
| Retícula intermitente | Estructuras rígidas, el auditorio pensado solo para una cosa |
| Tres atractores con enjambre | Academia, industria y ciudad compartiendo un mismo centro de gravedad |
| Red de hilos que palpitan | Comunidad y confianza: nada se sostiene solo, todo está conectado |
| Campo de flujo | Rutas que se abren, corrientes que cambian de dirección |
| Hélice de dos colores | Dos generaciones enlazadas que giran juntas, ninguna reemplaza a la otra |
| Topografía en relieve | El futuro como terreno que se va construyendo |
| Dorado y azul ultravioleta | Experiencia y nuevas generaciones, en el mismo universo visual |
| Borrado total entre slides | Cada momento empieza limpio, sin restos del anterior |


## 4. Storyboard: 13 elementos

| Momento | Qué se dice | Qué pasa en pantalla |
| :--- | :--- | :--- |
| 1. Introducción | Relevo generacional: la ventaja que nadie está aprovechando | Anillos líquidos que respiran. Algo vivo está por empezar |
| 02. El paradigma | ¿Un gran auditorio solo para hacer grados? | Retícula rígida con partículas que saltan a la cuadrícula. Todo ordenado, todo igual |
| 03. Transición | La Universidad decidió encontrarse con el mundo | Vuelven los anillos orgánicos: la estructura se ablanda |
| 04. Convergencia | Academia + Industria + Ciudad | Enjambre atraído por tres centros que se mueven despacio |
| 05. Propósito | Los eventos nunca fueron el objetivo, el impacto sí | Mismo enjambre, pero con la foto del evento al lado: lo que importa es lo que queda |
| 06. Comunidad | Un evento trae personas, una comunidad trae transformación | Red de nodos con hilos que palpitan |
| 07. Confianza | El talento crece a la velocidad de la confianza | La red sigue, sin foto: solo texto y conexiones |
| 08. Rutas | La experiencia construye el camino, las nuevas generaciones descubren rutas | Corrientes de partículas que siguen un campo de flujo |
| 09. Integración | Una visión. Dos generaciones. | Hélice de dos colores girando en pantalla |
| 10. Trabajo conjunto | Ocurre cuando trabajan juntas | La hélice sigue; la foto muestra el espacio real |
| 11. Presente | Los jóvenes son el presente | Hélice y foto del ecosistema de la industria |
| 12. Futuro | El futuro no se hereda, se construye | Topografía en relieve que se mueve como terreno vivo |
| 13. Continuidad | @centrodeeventosupb | La topografía sigue, con los QR para quedarse conectados |


## 5. ¿Cómo construye significado el sistema?

Una partícula sola solo se mueve. Cuando varias comparten un centro, dejan hilos entre ellas o giran enlazadas, empiezan a decir cosas: comunidad, confianza, colaboración, construcción.
La progresión que armé va así: algo vivo → estructuras rígidas → apertura → convergencia → comunidad → rutas nuevas → dos generaciones enlazadas → futuro en construcción. Es la misma historia de la charla, contada con movimiento.
Lo que más me importaba: en ningún momento una escena "reemplaza" a la anterior de forma agresiva. Cada una nace limpia, pero la paleta, la tipografía y la manera de moverse se mantienen, para que se sienta como un mismo universo que va cambiando.

## 6. AutoEvaluación

| Criterio | Puntaje | Justificación |
| :--- | :--- | :--- |
| Cumplimiento del encargo | 24/25 | El sistema cumple de sobra con los 13 momentos del guion, la integración de las fotos institucionales y la navegación web fluida en pantalla completa. |
| Relaciones estructurales | 23/25 | Logré conectar bien las matemáticas de los elementos con conceptos como redes y campos de flujo, aunque me hubiera gustado profundizar aún más en las dependencias físicas entre nodos. |
| Comportamiento y significado | 22/25 | Las transiciones logran acompañar la narrativa de Alma, pero reconozco que en algunas escenas la paleta de colores o el ritmo visual podrían comunicar el mensaje de forma todavía más directa. |
| Explicación y demostración | 23/25 | El repositorio en GitHub Pages funciona perfecto y puedo justificar cada línea de código, aunque me costó un poco más estructurar la documentación técnica inicial. |
| **Total** | **92/100** | **Equivale a 4.6/5.0** |




















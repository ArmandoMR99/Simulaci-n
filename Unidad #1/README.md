# Aleatoridad

## Actividad 2
```js
function draw() {                       Then draw() loops forever and ever (until you quit).

  walker.step();
  walker.show();                         Call functions on the walker.
}
```

- Como el background esta definido en setup(), lo que entiendo es que en draw() dibujamos los pasos de walker y tambien los mostramos para que se pueda ser visible desde el background, esto lo hace de manera infinita en todas las direcciones, en la variable step esta definido el factor aleatorio.

________________________________________________________________________________________________________________________________________________

## Actividad 7

### Navegar la incertidumbre

### 1 Intención Conceptual
- Desde el comienzo quise trabajar con pétalos de cerezo cayendo. Sentía que la forma en que caen y se mueven con el viento mostraba la incertidumbre de una manera súper elegante, fluida y un poco diferente a los ejemplos de la clase.
Al principio la idea era hacer un diseño generativo que mostrara los comportamientos que pedían. Pensé en meter Handpose para interactuar con las manos, pero me di cuenta de que la persona terminaba interviniendo demasiado y no dejaba que el sistema fluyera por sí solo. Por eso busqué otra forma de interactuar más sutil.

***Los Momentos del Sistema***
- *Posibilidad:* Al inicio no quería que los pétalos cayeran de una hacia abajo. Les puse un movimiento flotante en círculos suaves para que se sienta que pueden coger para cualquier lado, como si todas las direcciones fueran igual de posibles.

- *Tendencia:* Usé Ruido Perlin para simular una brisa invisible. Aunque cada pétalo flota a su aire, el viento los va empujando suavemente hacia un mismo lado, haciendo que una pequeña preferencia repetida termine creando una dirección colectiva.

- *Normalidad:* Para la velocidad de caída usé una distribución Gaussiana. Eso hace que casi todos los pétalos caigan a un ritmo súper parecido y constante, manteniendo una masa flotante predecible sin que se vea robótica.

- *Excepción:* Le metí un evento de muy baja probabilidad (un impulso raro) para que, de vez en cuando, un pétalo reciba un "empujón" fuerte e inesperado que lo mande a explorar zonas del lienzo por las que casi ninguno pasa.

- *Influencia:* Al acercar el cursor o tocar la pantalla, la física de la zona se altera: el viento se acelera y los pétalos giran con más turbulencia. El visitante no "dibuja" ni controla la pantalla, solo deforma el entorno a su paso.































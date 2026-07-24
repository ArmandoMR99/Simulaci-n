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

## Actividad 7 - Navegar la incertidumbre

### 1. Intención Conceptual
- Desde el comienzo quise trabajar con pétalos de cerezo cayendo. Sentía que la forma en que caen y se mueven con el viento mostraba la incertidumbre de una manera súper elegante, fluida y un poco diferente a los ejemplos de la clase.
Al principio la idea era hacer un diseño generativo que mostrara los comportamientos que pedían. Pensé en meter Handpose para interactuar con las manos, pero me di cuenta de que la persona terminaba interviniendo demasiado y no dejaba que el sistema fluyera por sí solo. Por eso busqué otra forma de interactuar más sutil.

***Los Momentos del Sistema***
- *Posibilidad:* Al inicio no quería que los pétalos cayeran de una hacia abajo. Les puse un movimiento flotante en círculos suaves para que se sienta que pueden coger para cualquier lado, como si todas las direcciones fueran igual de posibles.

- *Tendencia:* Usé Ruido Perlin para simular una brisa invisible. Aunque cada pétalo flota a su aire, el viento los va empujando suavemente hacia un mismo lado, haciendo que una pequeña preferencia repetida termine creando una dirección colectiva.

- *Normalidad:* Para la velocidad de caída usé una distribución Gaussiana. Eso hace que casi todos los pétalos caigan a un ritmo súper parecido y constante, manteniendo una masa flotante predecible sin que se vea robótica.

- *Excepción:* Le metí un evento de muy baja probabilidad (un impulso raro) para que, de vez en cuando, un pétalo reciba un "empujón" fuerte e inesperado que lo mande a explorar zonas del lienzo por las que casi ninguno pasa.

- *Influencia:* Al acercar el cursor, la física de la zona se altera: el viento se acelera y los pétalos giran con más turbulencia. El visitante no "dibuja" ni controla la pantalla, solo deforma el entorno a su paso.


### 2. Experimentos

Para llegar al resultado final fui probando y metiendo las reglas matemáticas poco a poco.

- ***Versión 1:*** Al principio solo quería ver si lograba que los pétalos cayeran. Usé random() para todo: velocidad de caída, posición y dirección. El problema es que se veía súper tieso y falso, como si fuera lluvia de papel o un glitch, sin nada de gracia física, con la ayuda de la IA pude hacer el efecto que sigue las particulas y analizar porque se veia tan tosco.

```js
let petals = [];

function setup() {
  createCanvas(400, 700);
  for (let i = 0; i < 100; i++) {
    petals.push({ x: random(width), y: random(height), size: random(5, 8) });
  }
}

function draw() {
  background(0, 50);
  for (let p of petals) {
    p.y += random(1, 3); 
    p.x += random(-1, 1); 

    ellipse(p.x, p.y, p.size, p.size * 2);

    if (p.y > height) p.y = 0;
  }
}
```
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/4885280a-e963-4b61-a9be-02f12772fec7" />


- ***Versión 2:*** Aquí ya le metí Ruido Perlin (noise) para que el viento no fuera un temblor feo sino una brisa suave, y Distribución Gaussiana (randomGaussian) para que la velocidad de caída fuera más natural (unos más rápidos, otros más lentos, pero la mayoría al mismo ritmo). También metí el rastro en el fondo.

```js
let petals = [];

function setup() {
  createCanvas(400, 700);
  for (let i = 0; i < 120; i++) {
    petals.push({
      x: random(width),
      y: random(height),
      noiseX: random(1000),
      size: random(5, 8)
    });
  }
}

function draw() {
  background(0, 25); 
  for (let p of petals) {
    let wind = map(noise(p.noiseX), 0, 1, -1.5, 1.5);
    p.noiseX += 0.003;

    let step = randomGaussian(1.4, 0.2);

    p.x += wind;
    p.y += step;

    ellipse(p.x, p.y, p.size, p.size * 2);

    if (p.y > height) p.y = 0;
  }
}
```
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/8ae6e828-cf04-494b-9834-10121148a450" />

- ***Versión 3 - Final:*** Acá integré todo lo que faltaba: la interacción con el mouse (Influencia), los impulsos raros (Excepción), la flotabilidad circular inicial (Posibilidad) y el ajuste automático para que el lienzo siempre quede en formato 9:16 vertical súper bien centrado, con ayuda de la IA le pude dar el estilo de petalo y su efecto y giro.

```js
let petals = [];
let total = 180;

function setup() {
  calculateCanvasSize();
  angleMode(DEGREES);
  for (let i = 0; i < total; i++) {
    petals.push({
      x: random(width),
      y: random(height),
      angle: random(360),
      noiseX: random(1000),
      size: random(5, 8),
      seedOffset: random(100)
    });
  }
  background(0);
}

function draw() {
  background(0, 25);
  for (let p of petals) {
    // P(giro flotante)
    let freedomAngle = noise(p.seedOffset + frameCount * 0.01) * 360;
    let dirX = cos(freedomAngle) * 0.4;
    let dirY = sin(freedomAngle) * 0.4;

    // T(Perlin)
    let wind = map(noise(p.noiseX), 0, 1, -2, 2);
    p.noiseX += 0.003;

    // N(Gauss)
    let step = randomGaussian(1.4, 0.2);
    step = constrain(step, 0.8, 2.2);

    // I(Mouse)
    if (dist(mouseX, mouseY, p.x, p.y) < 120) {
      wind *= 2.2;
      step += 0.5;
      p.angle += 3;
    }

    p.x += wind + dirX;
    p.y += step + dirY;
    p.angle += random(-1, 1);

    // E(Impulso raro)
    if (random(1000) < 2) {
      p.x += randomGaussian(0, 45);
      p.y += random(-20, 20);
    }

 
    push();
    translate(p.x, p.y);
    rotate(p.angle);
    noStroke();
    fill(255, 235, 245, 220);
    ellipse(0, 0, p.size, p.size * 2);
    fill(255, 255, 255, 90);
    ellipse(-1, -2, 2, 3);
    pop();

    if (p.y > height + 20) { p.y = -20; p.x = random(width); }
    if (p.x < -20) p.x = width + 20;
    if (p.x > width + 20) p.x = -20;
  }
}

function calculateCanvasSize() {
  let h = windowHeight;
  let w = h * (9 / 16);
  if (w > windowWidth) { w = windowWidth; h = w * (16 / 9); }
  let canvas = createCanvas(w, h);
  canvas.position((windowWidth - w) / 2, (windowHeight - h) / 2);
}

function windowResized() {
  calculateCanvasSize();
  background(0);
}
```
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/f180530f-9046-4ba4-92be-28a172f710e1" />


### 3. Decisiones tomadas y cosas que descarté

- ***Descarté el Handpose (detección de manos):*** Al principio me llamaba mucho la atención usar la cámara para que la gente moviera los pétalos con las manos. Pero leyendo bien las instrucciones del reto, entendí que el usuario no debe tener el control directo del sistema. Si ponía la cámara, la gente se iba a poner a "dibujar" o a empujar las cosas como si fuera un videojuego, perdiendo la idea de que la incertidumbre funciona sola.

- ***Elegí la interacción por cercanía:*** En lugar de hacer que el mouse fuera un "pincel" o un borrador, decidí que funcionara más como una presencia física (como cuando uno camina cerca de un montón de hojas secas). Solo con acercar el cursor, el entorno se altera, pero los pétalos siguen su propio camino sin que puedas manipularlos del todo, ya que si implementaba la idea del pincel ocurria el mismo problema que con el handpose, se iba a entender distinto el diseño.


### 4. Dificultades y Soluciones

Me guié muchísimo del texto guía de la materia para entender la lógica de la caminata aleatoria y las distribuciones, pero me costaba traducir esas fórmulas al código sin que se me dañara la animación.

- ***El momento de Excepción:*** Fue casi todo con ayuda de la IA. Siguiendo la idea del texto sobre los eventos raros, no sabía cómo programarlo de forma fluida, así que la IA me ayudó a armar la lógica del impulso atípico para que no se viera como un error.

- ***Estructura del código:*** Me ayudó a ordenar el desorden de variables que tenía al inicio, organizando todo de forma limpia y cuadrando la función para centrar el formato 9:16.

### 5. Enlace al prototipo

- https://editor.p5js.org/ArmandoMR99/sketches/myB1YRf9k






















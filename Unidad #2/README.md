# Reto #2: Spider-Man: Symbiote Crisis

Aplicación Base: https: https://editor.p5js.org/ArmandoMR99/full/glVz27YdX
<img width="1214" height="1009" alt="image" src="https://github.com/user-attachments/assets/938cf631-0a30-4e90-b917-1a818482cb70" />


 ## Intención 
Quiero explorar la tensión entre el deseo de poder para proteger y la destrucción inevitable del entorno tras la corrupción.

- Espero que esta tensión se manifieste mediante una mecánica de Particle Life donde Spider-Man, impulsado por su sentido de responsabilidad, persigue incesantemente a los Villanos para neutralizarlos y acude a proteger a los Civiles. Sin embargo, los Villanos atacan a la población indefensa y huyen de Spider-Man. La contradicción radica en que la presencia del héroe acelera la dinámica de persecución y desplazamiento de la multitud, requiriendo la intervención constante del usuario a través de los parámetros de la matriz para ajustar el frágil equilibrio de la ciudad.

## Diseño del Sistema
### Tipo de Partículas
1. Spider-Man
2. Villanos
3. Civiles

- Elegí estos tres tipos de partículas para sintetizar el conflicto social de un ecosistema de superhéroes sin saturar el espacio: el protector ágil, la amenaza depredadora y la masa vulnerable de ciudadanos. La idea es que la narrativa visual sea tan clara que cualquiera pueda identificar de inmediato los roles a través de sus colores (neón rojo/azul, púrpura/verde y amarillo) y sus trayectorias en pantalla.


## Cantidad de Partículas
1. 12 Spider-Man
2. 28 Simbionte Único
3. 50 Civiles (iniciales)

- Elegí una cantidad reducida de Spider-Man (12) para reflejar su naturaleza de elite rápida e hiperactiva que destaca en el espacio. Mantuve una población moderada de Villanos (28) para representar un peligro constante pero controlable, y una multitud superior de Civiles (50) para evidenciar la fragilidad del entorno social y cómo sus patrones de dispersión reaccionan ante la presencia de ambos bandos.


## Matriz de Relación 

| Fila (reacciona a) → Columna | 🔴 Spidey | 🟣 Villanos | 🟡 Civiles | 
| :--- | :---: | :---: | :---: |
| **🔴 Spidey** | +0.20 | +0.85 | +0.60 |
| **🟣 Villanos** | -0.50 | +0.10 | +0.90 |
| **🟡 Civiles** | +0.70 | -0.85 | +0.05 | 


- Seleccioné una atracción muy alta de Spider-Man hacia Villanos ($+0.85$) para simular el deber incondicional de caza y captura.

- Seleccioné una asimetría marcada en la relación Villanos/Civiles (Villanos buscan Civiles con $+0.90$, mientras Civiles huyen con $-0.85$) para generar patrones emergentes de emboscada y estampida humana, mientras que la alta atracción de los Civiles hacia Spider-Man ($+0.70$) provoca que la masa orbite al héroe en busca de refugio.


## Intensidad y Alcance
- Todas las poblaciones utilizan un alcance máximo de interacción (rmax) de 170 píxeles. Adicionalmente, el radio de repulsión física universal (beta) está fijado en 0.22 (equivalente a una distancia mínima de ~37px antes de generar rechazo).

- Seleccioné un alcance de 170px para garantizar que los campos de fuerza se perciban amplios y continuos. Seleccioné una repulsión de corta distancia (beta = 0.22) para evitar que las partículas colapsen en un solo punto geométrico, dotándolas de "volumen" físico e imponiendo una distancia mínima de seguridad que hace visible la red de hilos de telaraña (drawWebConnections) en un rango del 80% de rmax.

## Distancia de Interacción
- Seleccioné la función de fuerza canónica de Particle Life (Tom Mohr / Ventrella) porque quiero que la transición entre la repulsión física cercana ($r < \beta$) y la fuerza atrayente/repulsiva a media distancia ($\beta \le r < 1$) sea suave y matemáticamente continua. Espero que las agrupaciones y huidas no generen saltos bruscos en el movimiento, sino órbitas y persecuciones fluidas.


## Fricción y Velocidad Máxima
- Spider-Man: Vel Max 3.2, Fricción 0.86
- Villanos: Vel Max 2.7, Fricción 0.86
- Civiles: Vel Max 2.3, Fricción 0.86

- Seleccioné la mayor velocidad para Spider-Man (3.2) porque quiero hacer perceptible su agilidad superior para dar alcance a los Villanos. Los Villanos tienen una velocidad intermedia (2.7) que les permite acosar a los Civiles (2.3), garantizando que los ciudadanos sean los más vulnerables pero que Spider-Man siempre pueda eventualmente intervenir.


## Distribución Inicial
- Al iniciar o reiniciar la simulación con la tecla R o el botón "Nueva semilla", todas las partículas se posicionan con coordenadas y vectores de velocidad aleatorios en un espacio toroidal infinito sin paredes.


## Parámetros Constantes y Variables
- Constantes: El radio máximo de interacción (rmax = 170), la escala de fuerza (forceScale = 0.055), la fricción global (0.86), los tamaños visuales de los núcleos/halos y la fórmula de repulsión física beta.

- Variables: Las posiciones y velocidades instantáneas, los coeficientes de la matriz modificables en tiempo real mediante el panel lateral, la semilla aleatoria (seed) y las fuerzas de repulsión radial aplicadas manualmente mediante el clic del ratón (applyMouseInfluence).


## Apariencia y Interacción
- Estilo Neón / Dark Mode: Fondo oscuro con acumulación de trazo (rgba(10, 12, 18, 190)) que deja estelas de persecución.
- Sentido Arácnido y Telarañas: Líneas dinámicas renderizadas entre Spider-Man y su entorno; líneas celestes/blancas de protección hacia Civiles y líneas rojas/púrpuras hacia Villanos.
- Halos Neón: Círculos translúcidos alrededor del núcleo de cada partícula para dar densidad visual.
- Panel UI Flotante: Control lateral interactivo en HTML/DOM para ajustar los 9 valores de la matriz en tiempo real, cambiar semillas o reiniciar el preset.
- Interacción: Presionar el ratón genera una onda expansiva de repulsión que dispersa las partículas a 200px de distancia.


## Condiciones del Sistema
- Cada simulación parte de un estado único gracias al generador de semillas aleatorias (randomSeed/noiseSeed). A pesar de la aleatoriedad inicial, el sistema siempre evoluciona hacia patrones reconocibles de enjambres: persecuciones en bucle, vórtices de villanos e islas de civiles resguardados bajo Spider-Man.

| Versión / Fase | Cambios / Implementación | Hallazgo / Problema | Decisión / Solución |
| :--- | :--- | :--- | :--- |
| **v1.0 - Matriz Simétrica** *(Descartada)* | Matriz con valores idénticos de atracción y repulsión entre todas las especies. | El sistema colapsaba en grumos estáticos o dispersión homogénea sin narrativa ni conflicto. | Introduje asimetría pura en la matriz (M_ij ≠ M_ji) para forzar relaciones dinámicas de caza y huida. |
| **v2.0 - Sin Repulsión Física** *(Descartada)* | Ajuste de beta cercano a 0 sin fuerza repulsiva universal a corta distancia. | Las partículas de diferente tipo terminaban encimadas en un solo punto, destruyendo la legibilidad visual. | Implementé la función canónica de Particle Life con beta = 0.22 para garantizar distancia de choque. |
| **v3.0 - Movimiento Rígido** *(Descartada)* | Sin límite de velocidad ni mapa toroidal de distancias. | Las partículas rebotaban en bordes invisibles y alcanzaban velocidades desproporcionadas que rompían la pantalla. | Implementé límites de velocidad por rol (maxSpeed) y un espacio toroidal en getToroidalDifference(). |
| **Versión Final - Dilema del Héroe** | Integración del panel UI responsivo, trazado de telarañas dinámicas y valores optimizados para Spidey (+0.85 a Villanos). | Se logró el equilibrio entre estética de cómic neón, fluidez física y control en tiempo real por el usuario. | Consolidación de la versión definitiva con simulación de telarañas, halos neón e interfaz gráfica. |


## Autoevaluación
| Criterio | Peso | Valoración | Aporte |
| :--- | :---: | :---: | :---: |
| La intención es clara y perceptible en el comportamiento. | 20% | 100% | Se comprende la dinámica de protección, persecución y huida entre las tres poblaciones. |
| Los tipos, cantidades, matriz y parámetros están justificados desde la intención. | 25% | 100% | Las velocidades, cantidades y valores de matriz justifican el rol de cada personaje. |
| Comprendo y puedo modificar el funcionamiento técnico del sistema. | 20% | 100% | La matriz y los parámetros globales son totalmente editables desde el código y la interfaz UI. |
| El sistema produce variaciones con una identidad reconocible. | 15% | 100% | Las semillas aleatorias varían las posiciones, pero los patrones de persecución se mantienen. |
| Experimenté, comparé, seleccioné y descarté con criterios claros. | 10% | 100% | Se iteró desde modelos simétricos hasta ajustar las fuerzas asimétricas y la función de Particle Life. |
| Puedo distinguir y sustentar lo diseñado y lo emergente. | 10% | 100% | Lo diseñado son las reglas y velocidades; lo emergente son las espirales y enjambres de persecución. |
| **Total** | **100%** | **—** | **100** |

**Nota propuesta:** 5.0 (100 ÷ 20)































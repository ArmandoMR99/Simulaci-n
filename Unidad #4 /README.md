# Reto 4: Harmonic Synapse

<img width="1093" height="1013" alt="image" src="https://github.com/user-attachments/assets/dce9b835-7247-4191-a424-87fd250262b3" />

P5.js: https://editor.p5js.org/ArmandoMR99/full/Px-AwVrI8

## Intención

Quiero explorar la transición entre el caos polirrítmico individual y la cristalización armónica colectiva mediante un sistema audiovisual basado en el modelo de Kuramoto.

- Espero que esta tensión se manifieste cuando manipuló el acoplamiento (K) y perturbo manualmente los agentes. En estados de desorden (K=0), las 8 entidades emiten muestras sonoras de forma arrítmica mientras orbitan de manera independiente. A medida que $K$ aumenta, las fases ($\theta_i$) se alinean suavemente y las frecuencias naturales ($\omega_i$) ceden ante la presión del grupo. La estructura se autoorganiza en un polígono regular de haces de luz resplandecientes que emiten un acorde rítmico unificado. La intervención performativa permite romper esta estabilidad mediante impulsos de fase y observar el proceso de reorganización elástica del sistema en tiempo real.


## Diseño del Sistema
### Tipo de Agentes
1. Agente 1 (Tensores A - Percusión / Kick): Marcador del pulso percusivo fundamental en tonos carmesí.

2. Agente 2 (Membranas A - Pad / Textura): Capa de relleno resonante con envolvente suave en tonos cian.

3. Agente 3 (Arpegiadores A - Glitch Agudo): Acentos de alta frecuencia y destellos vectoriales amarillos.

4. Agente 4 (Contrapesos A - Sub-Bass): Masa e inercia sónica en frecuencias graves y tonos púrpura.

5. Agente 5 (Tensores B - Pluck Cristal): Respuesta de ataque percusivo brillante en naranja fuego.

6. Agente 6 (Arpegiadores B - Vocal Chop): Acento melódico agudo en tonos magenta eléctrico.

7. Agente 7 (Contrapesos B - Impacto Industrial): Base de vibración profunda y cuerpo en azul cobalto.

- Elegí 7 agentes con muestras de audio individuales (agente1.mp3 a agente7.mp3) e identidades de color distintas para garantizar que cada oscilador aporte un timbre único al ensamble. Las formas geométricas (cuadrados articulados, anillos concéntricos, estrellas de 5 puntas y esferas de masa) permiten reconocer al instante qué tipo de voz está aportando al ritmo colectivo.


## Cantidad de Agentes
1. 1 Agente Tensor A

2. 1 Agente Membrana A

3. 1 Agente Arpegiador A

4. 1 Agente Contrapeso A

5. 1 Agente Tensor B

6. 1 Agente Arpegiador B

7. 1 Agente Contrapeso B

- Elegí exactamente 8 agentes individuales para mantener el sistema dentro de los requisitos mínimos y asegurar un espacio sonoro legible. Esto evita el solapamiento estruendoso de audio y permite que la transición de fase se perciba claramente como una construcción polifónica limpia.


## Matriz y Topología de Interacción

| Agente (i) \ Influye en (j) | Agentes Agudos | Agentes Graves |
| :--- | :---: | :---: |
| **Agentes Agudos** | K_base * 0.8 | K_base * 1.1 |
| **Agentes Graves** | K_base * 1.4 | K_base * 1.0 |

- Seleccioné una topología de interacción espacial atenuada por la distancia física en pantalla: $K_{efectivo} = K \cdot e^{-d / D_{max}}$. Adicionalmente, ajusté las velocidades angulares base ($\omega_i$) como múltiplos armónicos escalonados ($0.6, 1.2, 1.8, \dots$) para simular la física de los péndulos de resonancia de Memo Akten (Simple Harmonic Motion). Esto evita ráfagas de audio fuera de tiempo y logra que el colectivo ensamble de forma natural.


## Intensidad y Alcance Performativo

- Alcance de Red Visual: Las líneas de conexión de la red neón solo se dibujan de manera intensa cuando la diferencia de fase $\cos(\theta_i - \theta_j)$ supera el umbral de $0.85$, reflejando gráficamente el nivel de alineación.
- Intervención Global ($K$): Control deslizante HTML para variar $K$ entre $0.0$ (desorden arrítmico) y $15.0$ (resonancia unificada).
- Intervención Individual (Drag & Pin): Al hacer clic y arrastrar un agente, se fija su posición física (isPinned) y su frecuencia natural ($\omega_i$) se reasigna según la altura vertical ($Y$), permitiendo usarlo como un metrónomo fuera de fase que desestabiliza la red.
- Mecanismo de Perturbación (Onda de Fase): Un clic sobre el lienzo en blanco genera un choque expansivo que altera aleatoriamente el valor del ángulo de fase $\theta_i$ de los agentes cercanos, disparando halos de resplandor y ondas visuales de dispersión.


## Distancia de Interacción
- Seleccioné la atenuación exponencial por distancia espacial ($e^{-d / D_{max}}$) porque permite que la proximidad física influya en la capacidad de sincronización entre los agentes. Si alejas un agente del centro, tarda más tiempo en responder a la presión de fase del grupo.


## Fricción y Velocidad de Fase
- Velocidades angulares base ($\omega_i$): Ajustadas en el rango de $0.6 \text{ rad/s}$ a $2.7 \text{ rad/s}$.
- Interpolación Espacial: Uso de lerp() a $0.07$ para suavizar el movimiento de las órbitas concéntricas, evitando saltos bruscos y garantizando una trayectoria fluida.


## Distribución Inicial
- Los 8 agentes parten organizados en una geometría circular alrededor del centro del lienzo, con ángulos de fase $\theta_i$ inicializados de forma aleatoria ($0 \text{ a } 2\pi$).


## Parámetros Constantes y Variables
- Constantes: Cantidad de agentes ($N = 8$), muestras de audio locales (agente1.mp3 a agente8.mp3), frecuencias angulares armónicas base y la paleta de colores de firma.
- Variables: Las fases instantáneas ($\theta_i$), la constante de acoplamiento ($K$), el indicador de masa armónica ($R$), las posiciones de arrastre individual y los impulsos por perturbación táctil.


## Apariencia e Interacción
- Estilo Neón / Bioluminiscente: Fondo oscuro azul noche (rgba(4, 5, 8, 30)) con rastro fantasma elástico inspirado en las obras de luz de Memo Akten.
- Partículas e Impulsos: Cada disparo de fase genera un destello de partículas bioluminiscentes que se disipan con atenuación alpha.
- Grafo Neón: Haces de luz cian que entrelazan los nodos en sincronía.
- Panel HUD: Interfaz con tipografías Orbitron y Share Tech Mono, barra de progreso dinámica e indicador del Parámetro de Orden $R(t)$.


## Condiciones del Sistema
| Versión / Fase | Cambios / Implementación | Hallazgo / Problema | Decisión / Solución |
| :--- | :--- | :--- | :--- |
| **v1.0 - Kuramoto Sintético** *(Descartada)* | Síntesis de audio con osciladores puros mediante Tone.Synth. | El sonido se sentía demasiado simple y de laboratorio, sin riqueza tímbrica ni identidad musical. | Reemplacé la síntesis por carga de muestras locales de audio (.mp3) individuales para cada agente. |
| **v2.0 - Desorden Rítmico** *(Descartada)* | Frecuencias angulares base asignadas con valores totalmente aleatorios. | La reproducción producía ráfagas desordenadas y el ensamble musical no lograba asentarse correctamente. | Calibré las velocidades angulares a múltiplos armónicos escalonados, imitando el modelo de péndulos de Memo Akten. |
| **v3.0 - Colisión de Nombres** *(Descartada)* | Uso de la variable 'dist' dentro del bucle de interacción de Kuramoto. | Se generaba un error ReferenceError que bloqueaba la ejecución de p5.js por opacar la función nativa dist(). | Renombré la variable local a 'd' en todas las funciones para proteger las funciones del lienzo. |
| **Versión Final - Resonancia Biomecánica** | Integración de 8 muestras MP3, topología espacial elástica, partículas de pulso e interfaz HUD Neón. | Se logró el equilibrio perfecto entre rigor matemático del modelo, estética de vanguardia y control performativo. | Consolidación de la versión definitiva: instrumento de osciladores acoplados listo para ejecutarse en tiempo real. |


## Autoevaluación
| Criterio | Peso | Valoración | Aporte |
| :--- | :---: | :---: | :---: |
| Leí y verifiqué que mi proyecto cumple con los requisitos mínimos de la unidad. | 25% | 100% | Cumple con 8 agentes, 8 muestras MP3, K modificable, 2 modos performativos, perturbación y 3 estados de R. |
| Puedo explicar claramente qué representa cada variable del modelo de Kuramoto en mi proyecto. | 25% | 100% | theta = ciclo/fase visual-sonora, omega = ritmo base armónico, K = acoplamiento de la red, R = masaarmónica. |
| Puedo explicar claramente cómo las variables del modelo producen el comportamiento observado en mi proyecto. | 25% | 100% | Demostrable en la transición de la polirritmia desordenada al acorde unificado cuando K supera el umbral crítico. |
| Puedo demostrar que mi proyecto cumple con los objetivos establecidos en la unidad. | 25% | 100% | Kuramoto no es reemplazable por un reloj estático; la música y la geometría emergen dinámicamente del acoplamiento. |
| **Total** | **100%** | **—** | **100** |

Nota propuesta: 5.0 (100 ÷ 20)



























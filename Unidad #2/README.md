# Reto #2: Spider-Man: Symbiote Crisis

Aplicación Base: https://editor.p5js.org/ArmandoMR99/full/1JS5K7vjU
<img width="1214" height="1013" alt="image" src="https://github.com/user-attachments/assets/24e465b9-14b1-4b8f-a60a-df68e3b8a398" />

Aplicación con detalles de Comic: https://editor.p5js.org/ArmandoMR99/full/glVz27YdX
<img width="1214" height="1097" alt="image" src="https://github.com/user-attachments/assets/212b4ffc-9667-4b36-afb2-e08e382e00f6" />

 ## Intención 
Quiero explorar la tensión entre el deseo de poder para proteger y la destrucción inevitable del entorno tras la corrupción.

- Espero que esta tensión se manifieste cuando Spider-Man y el Simbionte, impulsados por una atracción mutua extrema, se fusionen para obtener poder. Esta unión creará una entidad veloz y dominante que, en su intento por interactuar con los civiles, los infectará y corromperá inevitablemente. La contradicción radica en que el camino hacia el "poder" o la "protección" individual de Spidey resulta en la ruina de la población que juró proteger, requiriendo la intervención de Miles Morales y la Campana Sónica para reiniciar el ciclo.


## Diseño del Sistema
### Tipo de Partículas
1. Spider-Man
2. Simbionte Único (Venom)
3. Miles Morales
4. Civiles
5. Civiles Corruptos

- Elegí estos cinco tipos de partículas para que el conflicto no se quede solo en una idea abstracta, sino que realmente cobre vida a través de personajes bien definidos: el héroe tentado, el elemento corruptor, el héroe incorruptible, las víctimas inocentes y la manifestación del caos; la idea es que la narrativa visual sea tan clara que cualquiera pueda identificar de inmediato quién es quién y qué está pasando en la escena.


## Cantidad de Partículas
1. 1 Spider-Man
2. 1 Simbionte Único
3. 1 Miles Morales
4. 140 Civiles (iniciales)
5. Variable (Civiles Corruptos)

- Elegí solo un individuo para Spider-Man, el Simbionte y Miles para dejar clara su relevancia y mostrar que el conflicto principal es totalmente personal, haciendo que sus interacciones destaquen frente al resto. En contraste, incluí a 140 civiles para reflejar la fragilidad del entorno y el enorme daño colateral, creando una masa social orgánica que reaccione con pánico y haga evidente la verdadera escala de la tragedia cuando la infección se propaga.


## Matriz de Relación 

| Fila (reacciona a) → Columna | 🔴 Spidey | 🟣 Venom | 🟡 Miles | ⚪ Civiles | 🟪 Corruptos |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **🔴 Spidey** | 0.0 | **+7.0** | -0.3 | +0.8 | 0.0 |
| **🟣 Venom** | **+7.0** | 0.0 | -0.5 | +1.0 | 0.0 |
| **🟡 Miles** | -1.0 | 0.0 | 0.0 | +0.1 | **+3.5** |
| **⚪ Civiles** | 0.0 | -2.5 | 0.0 | 0.0 | -1.8 |
| **🟪 Corruptos** | 0.0 | 0.0 | -1.0 | **+1.8** | 0.0 |

- Seleccioné una atracción mutua extrema ($+7.0$) entre Spider-Man y el Simbionte porque quiero hacer perceptible la naturaleza adictiva e inevitable de su unión.

- Seleccioné una relación asimétrica entre Miles Morales ($+3.5$ hacia Corruptos) y los Civiles Corruptos (indiferentes o repulsión leve a Miles) porque quiero hacer perceptible el rol de Miles como pastor o redentor. Espero que produzca que Miles "arree" activamente a los corruptos hacia la Campana Sónica Central.


## Intensidad y Alcance
- Todas las especies utilizan un alcance máximo de interacción de 150 píxeles. Sin embargo, cuando Spider-Man está fusionado con el Simbionte (isBonded), se activa una regla de infección por contacto a una distancia de 32 píxeles.

- Seleccioné un alcance estándar para las fuerzas físicas porque quiero que el movimiento general sea fluido y predecible como en Particle Life. Seleccioné un radio de contacto corto y específico para la infección porque quiero hacer perceptible que la corrupción requiere una proximidad peligrosa o un roce físico con el poder descontrolado. Espero que produzca patrones de caos difuso en la masa social solo cuando Spidey "toca" a la multitud en su carrera veloz.


## Distancia de Interacción
- Seleccioné estas distancias porque quiero que la atracción extrema mutua (Spidey-Venom) se sienta intensa pero no instantánea. Espero que las agrupaciones y las persecuciones se formen y se deshagan de manera natural en lugar de producir saltos bruscos en el movimiento.


## Fricción y Velocidad Máxima
- Spider-Man (Normal): Vel Max 3.8, Fricción 0.92
- Spider-Man (Fusionado): Vel Max $11.4(X3), Fricción 0.92
- Simbionte: Vel Max 3.5, Fricción 0.93
- Miles Morales: Vel Max 4.2, Fricción 0.91
- Civiles: Vel Max 1.3, Fricción 0.88
- Corruptos: Vel Max 2.0, Fricción 0.90

- Seleccioné un incremento dramático de velocidad ($\times 3$) para Spider-Man cuando está fusionado porque quiero hacer perceptible la "ventaja" tentadora y el poder abrumador que otorga el traje negro.


## Distribución Inicial
- Todas las partículas aparecen en posiciones aleatorias al iniciar o reiniciar la simulación. La Campana Sónica Central siempre permanece fija en el centro del lienzo.


## Parámetros Constantes y Variables
- Constantes: Cantidad de héroes y simbiontes (1 de cada uno), matriz de relaciones, velocidades base, fricciones, distancias de interacción y la ubicación de la Campana Central.

- Variables: Posiciones iniciales de todas las partículas, la tasa de infección por frame, y la aparición de Onomatopeyas visuales.


## Apariencia y Interacción
- Estilo Cómic: Fondo con Ben-Day dots, trazos de tinta negra marcados, HUD estilo novela gráfica.
- Spidey Simbionte: Aura púrpura Bezier y tentáculos orgánicos que brotan de la fusión.
- Miles Morales: Rayos bioeléctricos zigzagueantes (renderizados con líneas quebradas aleatorias) cuando guía a los corruptos.
- Onomatopeyas visuales: Textos pop-art (THWIP!, ZAP!, BONG!, PURIFIED!) que aparecen brevemente.
- Interacción: Solo a través de fuerzas físicas y la lógica de contacto de la Campana Central (cura a los Corruptos cercanos).


## Condiciones del Sistema
- Cada ejecución es única debido a la distribución inicial aleatoria. El comportamiento general sigue siendo reconocible porque el sistema siempre tiende a la fusión Spidey-Venom, genera caos infeccioso y requiere la purga sónica central para reiniciar el ciclo de tensión.

| Versión / Fase | Cambios / Implementación | Hallazgo / Problema | Decisión / Solución |
| :--- | :--- | :--- | :--- |
| **v1.0 - Intención Inicial** *(Descartada)* | El Simbionte huía de Spider-Man. | El sistema carecía de tensión real; era solo una persecución unilateral sin conflicto interno. | Replanteé la matriz para que Spidey sintiera atracción hacia el simbionte, creando la contradicción de buscar algo que daña su entorno. |
| **v2.0 - Saturación Visual** *(Descartada)* | Onomatopeyas y ondas sónicas grandes de alta opacidad. Fricción global alta (0.85). | Los textos y ondas tapaban la pantalla. El movimiento se sentía tosco y las agrupaciones se dispersaban muy lento. | Reduje tamaño de letra (Impact, 11-14px) y opacidad. Adelgacé ondas a 1.5px y diferencié fricciones (civiles: 0.88, héroes: 0.92-0.93). |
| **v3.0 - Población Baja** *(Descartada)* | Sistema configurado con 70 civiles iniciales. | La ciudad se sentía vacía y las persecuciones dominaban el espacio. La infección no reflejaba una crisis masiva. | Aumenté la cantidad inicial de ciudadanos a 140 para hacer perceptible el daño colateral y la fragilidad del entorno. |
| **Versión Final - Equilibrio Sónico** | Matriz final con atracción mutua Spidey-Venom (+7.0) y Miles enfocado en Corruptos (+3.5). | Los civiles sanos desarrollaron repulsión social a Venom/Corruptos. Se logró el equilibrio entre estética y dinámica. | Se consolidó la versión definitiva: alta densidad de civiles, estética de cómic limpia y un ciclo claro de unión, caos y redención. |


## Autoevaluación
| Criterio | Peso | Valoración | Aporte |
| :--- | :---: | :---: | :---: |
| La intención es clara y perceptible en el comportamiento. | 20% | 100% | Se entiende la intención de la atracción de spidey hacia el simbionte |
| Los tipos, cantidades, matriz y parámetros están justificados desde la intención. | 25% | 100% | Si todo esta justificado para que el sistema no se vea caotico |
| Comprendo y puedo modificar el funcionamiento técnico del sistema. | 20% | 100% | la mayoría de valores y velocidades las puedo modificar de manera manual |
| El sistema produce variaciones con una identidad reconocible. | 15% | 100% | siempre varia la cantidad de civiles limpios y la cantidad de corruptos |
| Experimenté, comparé, seleccioné y descarté con criterios claros. | 10% | 100% | si, puesto que tenia la idea clara solo faltaba encontrar un equilibrio en el sistema |
| Puedo distinguir y sustentar lo diseñado y lo emergente. | 10% | 100% | Si, la idea fue totalmente mía, la IA me ayudo a llevarla a cabo |
| **Total** | **100%** | **—** | **100** |

**Nota propuesta:** 5.0 (100 ÷ 20)
































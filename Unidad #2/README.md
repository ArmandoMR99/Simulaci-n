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

Elegí estos cinco tipos de partículas para que el conflicto no se quede solo en una idea abstracta, sino que realmente cobre vida a través de personajes bien definidos: el héroe tentado, el elemento corruptor, el héroe incorruptible, las víctimas inocentes y la manifestación del caos; la idea es que la narrativa visual sea tan clara que cualquiera pueda identificar de inmediato quién es quién y qué está pasando en la escena.


## Cantidad de Partículas
1. 1 Spider-Man
2. 1 Simbionte Único
3. 1 Miles Morales
4. 140 Civiles (iniciales)
5. Variable (Civiles Corruptos)

Elegí solo un individuo para Spider-Man, el Simbionte y Miles para dejar clara su relevancia y mostrar que el conflicto principal es totalmente personal, haciendo que sus interacciones destaquen frente al resto. En contraste, incluí a 140 civiles para reflejar la fragilidad del entorno y el enorme daño colateral, creando una masa social orgánica que reaccione con pánico y haga evidente la verdadera escala de la tragedia cuando la infección se propaga.


## Matriz de Relación 

| Fila (reacciona a) → Columna | 🔴 Spidey | 🟣 Venom | 🟡 Miles | ⚪ Civiles | 🟪 Corruptos |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **🔴 Spidey** | 0.0 | **+7.0** | -0.3 | +0.8 | 0.0 |
| **🟣 Venom** | **+7.0** | 0.0 | -0.5 | +1.0 | 0.0 |
| **🟡 Miles** | -1.0 | 0.0 | 0.0 | +0.1 | **+3.5** |
| **⚪ Civiles** | 0.0 | -2.5 | 0.0 | 0.0 | -1.8 |
| **🟪 Corruptos** | 0.0 | 0.0 | -1.0 | **+1.8** | 0.0 |

Seleccioné una atracción mutua extrema ($+7.0$) entre Spider-Man y el Simbionte porque quiero hacer perceptible la naturaleza adictiva e inevitable de su unión.

Seleccioné una relación asimétrica entre Miles Morales ($+3.5$ hacia Corruptos) y los Civiles Corruptos (indiferentes o repulsión leve a Miles) porque quiero hacer perceptible el rol de Miles como pastor o redentor. Espero que produzca que Miles "arree" activamente a los corruptos hacia la Campana Sónica Central.














 

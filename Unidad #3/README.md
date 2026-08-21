# Reto #3: Instrumento Visual para "LesAlpx"
[App desplegada](https://armandomr99.github.io/Unidad-3/)

## Flujo del Proyecto
1. El cerebro (main.js): Es donde escucho el teclado. Aquí programé los "Actos" de la canción y puse el Lerp (la transición suave) para que, al cambiar de fuerza, el sistema no se trabe y todo se sienta fluido.
2. Las reglas (parameters.js): Aquí viven todas las variables. Si quiero cambiar el color o qué tan rápido se mueve algo, todo se ajusta desde acá.
3. La física (createSimulation.js): Esta es la parte pesada. Es donde el shader calcula la posición de las 131,000 partículas en tiempo real.
4. Lo que vemos: Básicamente renderizo las partículas sobre un canvas que no se borra, con un plano negro de fondo que tiene transparencia. Eso me dio el rastro (el Motion Blur) que buscaba para que se vean como pinceladas de tinta.

## Diseño de Fuerzas
Me fui por una estética bien limpia: tinta negra moviéndose sobre fondo blanco. Para que no se viera como un montón de puntitos, desactivé el borrado del canvas y le puse un plano negro encima con transparencia. Eso generó un efecto de rastro (Motion Blur) que hace que se vea como si estuvieras dibujando con pincel en tiempo real.

La clave aquí fue el Curl Noise (turbulencia). Si usaba ruido normal, las partículas se amontonaban y se veía súper sucio. El Curl Noise simula cómo se mueven los fluidos y me dio remolinos súper naturales. La matemática en el shader es algo así:
- Fx = sin(y * f + t)
- Fy = cos(x * f + t)

Antes de armar la coreografía, pasé un buen rato en el modo LAB probando todo por separado. El hallazgo clave fue combinar una repulsión súper fuerte con mucha dispersión (Jitter): la pantalla explota de una forma caótica pero controlada, que es justo lo que necesitaba para el clímax de la canción.

## Coreografía 
Mapeé todo al teclado para tocar en vivo sin depender de sliders:

- [Q] 0:00 (Acto 1): Atracción suave. Dejo el mouse quieto. Trazos limpios y estables.
- [W] 0:40 (Acto 2): Entra el beat. Subo el Curl Noise y meto un pulso. La tinta empieza a vibrar.
- [E] 1:15 (Acto 3): Sintes agudos. Subo la turbulencia a tope y bajo la fricción. Todo se vuelve inestable.
- [R] + [Espacio] 2:17 (Acto 4): Cae el drop. Toco R y mantengo Espacio en los golpes pesados. Explosión de dispersión.
- [T] 3:30 (Acto 5): Cierre. Las partículas mutan del blanco/negro a los tonos azules y dorados de la portada del álbum.
- [Y] Modulador: Lo uso en los tramos largos para que el sistema gire como un vórtice y respire solo.























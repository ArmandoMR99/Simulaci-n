# Reto #3: Instrumento Visual para "LesAlpx"
Para la parte visual, me fui por algo minimalista, estilo caligrafía japonesa (Shodo). Básicamente, tinta negra moviéndose en un fondo blanco limpio, jugando a full con el contraste.

## Flujo del Proyecto
1. El cerebro (main.js): Es donde escucho el teclado. Aquí programé los "Actos" de la canción y puse el Lerp (la transición suave) para que, al cambiar de fuerza, el sistema no se trabe y todo se sienta fluido.
2. Las reglas (parameters.js): Aquí viven todas las variables. Si quiero cambiar el color o qué tan rápido se mueve algo, todo se ajusta desde acá.
3. La física (createSimulation.js): Esta es la parte pesada. Es donde el shader calcula la posición de las 131,000 partículas en tiempo real.
4. Lo que vemos: Básicamente renderizo las partículas sobre un canvas que no se borra, con un plano negro de fondo que tiene transparencia. Eso me dio el rastro (el Motion Blur) que buscaba para que se vean como pinceladas de tinta.

























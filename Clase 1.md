# Clase 1
## Control de movimiento
El objetivo de un proceso de control de movimiento es controlar la posición, velocidad y torque de un axis (actuador de movimiento), el cual puede ser:

 - Servomotores
 - Pistones

Esto con el fin de realizar con absoluta precisión procesos automatizados como pueden ser:

 - Empaque
 - Ensamblaje
 - Impresión
 - Electrónica y semiconductores

El control de movimiento se aplica cuando el proceso requiere de varios movimientos al mismo tiempo y están sincronizados, con el objetivo de mejorar la eficiencia del proceso.

<div align="center">
<img src="Imagenes/Impresora_3d.png" alt="Tabla Austin"/>
<br>
<figcaption> Fuente: https://www.mercadolibre.com.co/impresora-creality-3d-ender-3-v2-neo-color-blanco-110v-con-tecnologia-de-impresion-fdm/p/MCO44116355</figcaption>
</div>

Un ejemplo muy visto actualmente son las impresoras 3d, las cuales utilizan varios servomotores para la inyección del plástico.

### Control cascada

Es un método de control el cual involucra varios lazos dentron de otros lazos y la salida de los controladores de los lazos externos son la entrada del siguiente lazo, como se puede ver en la siguiente imagen:

<div align="center">
<img src="Imagenes/Control_Cascada.png" alt="Tabla Austin"/>
<br>
<figcaption> Fuente: Presentación clase</figcaption>
</div>

Este método se implementa cuando un proceso principal se ve alterado por perturbaciones, generalmente más rápidas que el proceso principal. Por este motivo el control cascada
es utilizado para el control de movimiento ya que todo movimmiento ejercido a una carga por tercera ley de Newton genera una fuerza opuesta al movimiento que altera la velocidad y finalmente la posición de la carga (al efecto se le llama offset). Al tomar esta fuerza como una perturbación es posible disminuir drásticamente e incluso eliminar su efecto en el proceso.
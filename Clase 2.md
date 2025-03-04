# Clase 2

## Control cascada

### Implementación

<div align="center">
<img src="Imagenes/Diagrama_Control_Cascada.png" alt="Diagrama de un controlador en cascada"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

El control de cascada es posible implementarlo si el comportamiento de las perturbaciones (G2) es más rápido que el comportamiento de la variable principal (G1). Por ese motivo el lazo secundario (C2) es controlado con un controlador P o PI, y el lazo primario (C1) es controlado por un PI o un PID.

### Sintonización de controlador cascada

#### Metodología empírica de lazo abierto

Como otros controladores los controladores
cascada pueden ser sintonizados con métodos 
empíricos, siguiendo el siguiente procedimiento:

 - Se abre el lazo en todo el sistema.
 - Se realizan las pruebas midiendo la variable del lazo secundario (y2).
 - Se sintoniza el controlador del lazo secundario y se cierra el lazo.
 - Con el lazo secundario cerrado se realizan las pruebas midiendo la variable del lazo primario (y1).
 - Finalmente se sintoniza el controlador del lazo primario.

#### Metodología empírica de lazo abierto Austin

Austin desarrollo un método por el cual se pueden sintonizar el lazo primario mediante ecuaciones después de hacer sintonizado el lazo secundario.

 - Se realizan las pruebas en lazo abierto y se miden ambas salidas de los lazos.
 - Con la respuesta del lazo secundario se utiliza para ganancia (k2), la constante de tiempo (t2) y el tiempo muerto (to2). Y la respuesta del lazo primario también se utiliza para calcular la ganancia la ganancia (k1), la constante de tiempo (t1) y el tiempo de largo (to1).
 - Y mediante las ecuaciones de la tabla se sintoniza ambos lazos.

<div align="center">
<img src="Imagenes/Tabla_Calculo_Austin.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

<div align="center">
<img src="Imagenes/Tabla_Calculo_Austin_2.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

#### Metodología empírica de lazo cerrado Hang

Este método propone sintonizar ambos lazos por medio de pruebas de rele sobre estos, como se ve en la siguiente imagen.

<div align="center">
<img src="Imagenes/Prueba_Rele_Cascada.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

 - Primero se realiza una prueba al lazo secundario, donde un rele activara y desactivara una señal de entrada.
 - Se mide el ciclo último (Wu) y la ganancia última (Ku), donde el ciclo último es el periodo entre picos de la variable de lazo y la ganancia ultima se calcula.

$$K_{u}= \frac{4*d}{\pi*a}$$

Donde a es la amplitud de la variable de lazo y d es el valor de la histéresis del rele.
- Se procede a calcular por medio de la tabla los valores para los controladores.

<div align="center">
<img src="Imagenes/Tabla_Rele.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

 - Se cierra el lazo secundario y se procede a repetir los anteriores pasos para el lazo primario.
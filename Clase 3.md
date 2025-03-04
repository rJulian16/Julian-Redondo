# Clase 3

## Actuadores

### Servomotor

Servo proviene de la palabra latina "servos" que significa esclavo, esto hace mención de la capacidad de cambiar una variable a un valor objetivo como lo hace un motor con las variables de posición, velocidad o torque.

### Motor DC

<div align="center">
<img src="Imagenes/Motor_DC.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

Motor que funciona con corriente directa que induce a la bobina del rotor un campo magnético que al interactuar con los imanes del estator produce el giro del rotor.

#### Ventajas:

 - Control más simple.
 - Driver de potencia más simple.
 - Bajo precio en bajas capacidades.
 - Alta eficiencia en aplicaciones pequeñas.

#### Desventajas:

 - Requiere mantenimiento e inspecciones periódicas.
 - Las escobillas están en constante abración
 - No aplicable para altos torques
 - Sus imanes pueden sufrir desmagnetización con el tiempo.
  
### Motor AC síncrono

<div align="center">
<img src="Imagenes/Motor_sincrono.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

Son maquinas eléctricas cuya velocidad de rotación está vinculada con la frecuencia de la red AC,lo que requiere de la sincronización de as señales de control, por esto se llaman síncronos.

#### Ventajas

 - Muy poco mantenimiento
 - Excelente resistencia al entorno
 - Compactos y ligeros
 - Alta eficiencia en todo tipo de aplicaciones

#### Desventajas
 - Control de dificultad intermedia
 - Se requiere respuesta 1:1 entre driver y motor
 - Sus imanes pueden sufrir desmagnetización con el tiempo

### Motor AC asíncrono

Se basa en la creación de un campo magnético giratorio en un devanado inductor situado en el estator. Existen diferentes formas de construir un motor.

 - Jaula de ardilla
<div align="center">
<img src="Imagenes/Motor_jaula_ardilla.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

 - Rotor bobinado

<div align="center">
<img src="Imagenes/Motor_rotor_bobinado.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

#### Ventajas

 - Poco mantenimiento
 - Excelente resistencia al entorno
 - Alta velocidad y alto torque
 - Alta eficiencia en aplicaciones grandes
 - Estructura robusta

#### desventajas

 - Baja eficiencia en aplicaciones pequeñas
 - Control más complicado que el DC por las señales de potencia.
 - Pude sufrir cambios en sus características debido a temperaturas.

### Zonas de operación de servomotores

Son graficas de torque contra velocidad angular que muestra el torque máximo que puede ejercer un motor al tener cierta velocidad angular. Cada fabricante provee estos datos de operatividad.

<div align="center">
<img src="Imagenes/Grafica_Torque_velocidad.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: https://instrumentacionycontrol.net/metodos-de-control-de-velocidad-en-motores-ac/</figcaption>
</div>

En estas hay dos zonas principales en las gráficas, la primera llamada continua es la zona de operación constante del motor, donde va a estar operativo la mayor parte del tiempo. La segunda llamada intermitente muestra los puntos de operación que puede alcanzar el motor en breves instantes.

### Simulaciones

Es posible simular el comportamiento de un motor, teniendo las características electromagnéticas y mecánicas del motor. Validando la simulación por medio de las gráficas de torque y velocidad.

## Sensores en servomotores

### Encoders

Son sensores capaces de medir la posición y velocidad de, existen de dos tipos

 - Encoder absoluto

<div align="center">
<img src="Imagenes/Encoder_Absoluto.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

 - Encoder incremental

<div align="center">
<img src="Imagenes/Encoder_Incremental.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

### Resolver

Es un sensor analógico de posición angular, que consta de dos embobinados (rotor y estator), para posiciones relativas de uno con respecto al otro varia la amplitud que se induce en el rotor.

<div align="center">
<img src="Imagenes/Resolver.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

### Sensor de torque

Directamente es muy complicado medir el torque de un motor, pero teniendo en cuenta que la corriente requerida por un motor para mover una carga es directamente proporcional al toque de este. Por lo tato podemos saber el torque del motor al medir la corriente y multiplicar por una constante de proporción.

Existe dos tipos de sensores de corriente:

 - Shunt: Una resistencia muy pequeña para tomar la tensión en esta y aplicar ley de ohm.

<div align="center">
<img src="Imagenes/Shunt.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

 - Efecto Hall: Es un sensor que detecta cambios de campo magnético y por ley de inducción de Faraday se puede obtener la corriente.

<div align="center">
<img src="Imagenes/Hall.png" alt="Tabla Austin"/>
<br>
<figcaption>Fuente: Presentación clase</figcaption>
</div>

## Drivers de potencia

Es el elemento que recibe las señales de baja potencia (señales de control) y las amplifica a señales de alta potencia. Cada axis tiene un accionador y cada accionador posee su driver ya que los accionadores son los encargado de transformar energía eléctrica a mecánica lo que involucra un alto costo energético.

Por estándar de la industria el control de los accionadores se hace por medio de señales PWM.
# Control de Movimiento
Julian Stiven Redondo Chacon & Sebastian Cifuentes Alfonso & David Esteban Vasquez Alarcon
## 1. Que es?
El control de movimiento es una tecnología utilizada para gestionar y dirigir el movimiento de máquinas y dispositivos. Este sistema es esencial en procesos industriales, permitiendo precisión y eficiencia en la operación de equipos. 

## 2. Aplicaciones del Control de Movimiento

El control de movimiento tiene numerosas aplicaciones en diferentes sectores industriales, incluyendo:

- **Impresión**: Utilizado en impresoras de alta precisión para controlar el movimiento del cabezal de impresión y asegurar la calidad de las impresiones.
- **Empaque**: En sistemas de empaque, facilita la alineación precisa y el movimiento sincronizado de productos en la línea de producción.
- **Productos de Madera**: En la fabricación de muebles y otros productos de madera, controla las herramientas de corte y moldeado para obtener resultados precisos.
- **Maquinaria**: Imprescindible en maquinarias industriales para la automatización de procesos complejos y repetitivos.
- **Electrónica**: En la producción de dispositivos electrónicos, controla el posicionamiento de componentes en las placas de circuito.
- **Semiconductores**: Utilizado en la fabricación de semiconductores para manejar la precisión extrema requerida en los procesos de litografía y ensamblaje.

El control de movimiento se aplica cuando el proceso requiere de varios movimientos al mismo tiempo y están sincronizados, con el objetivo de mejorar la eficiencia del proceso.

![image](https://github.com/user-attachments/assets/7fac3cf4-1559-4c6b-9e63-316432b3bb74)

Figura 1. Maquina de impresion 3d actual.

Un ejemplo muy visto actualmente son las impresoras 3d, las cuales utilizan varios servomotores para la inyección del plástico.

## 3. Control 
Los sistemas contienen multiples ejes a controlar, donde a cada eje le podemos llegar a controlar la posicion, velocidad, torque, aceleracion con ayuda de algun piston o servomotor. hoy en dia a estos sistemas que ya disponen de componentes electricos para este control se les conoce como Electronic Gearing for Coordination. 
>🔑Ejes: Cada movimiento que genere un actuador

### 3.1 Mechanical Coordination?
Antes del control como lo conocemos hoy en dia, estas maquinas o estos procesos funcionaban con un enfoque netamente mecanico, en ejemplo claro puede ser el de una maquina de impresion.


![image](https://github.com/user-attachments/assets/893c3501-8367-41f8-ade2-7408f0ff9eec)




Figura 2. Maquina de impresion.

Donde solo habia tanto un motor como un eje grande y funcionaba con diferentes sistemas de transmision, el problema de esto era que requieren de un mantenimiento muy complejo y era muy costoso

### 3.2 El Ahora
Hoy en día, el control de movimiento se realiza con sistemas eléctricos que emplean múltiples motores y ejes para optimizar los procesos en diversas aplicaciones. Estos sistemas son generalmente más económicos y requieren un mantenimiento más sencillo. A continuación, se mencionan los diferentes componentes  que los conforman.
- **HMI**
- **Control de movimiento**
- **Drivers**
- **Actuadores**
- **Mecanismos de transmision**
- **Retroalientacion**


### 3.3 Caracteristicas de control: 
Un movimiento sobre una carga genera una fuerza negativa ejercida por el motor, esta fuerza negativa provoca cambios en la velocidad, a esto se le llama offset para ello es necesario controlar el offset para reducirlo lo mas que se pueda ya que esto es una perturbación.

Los componentes de nuestro sistema deben ser bien diseñados ya que la dinamica de estos sistemas son muy rapidos y necesitamos componentes que tengan propositos de eficiencia y productividad para la electronica y el motor
La siguiente imagen muestra el esquema de control cascada para un sistema. 

### 3.4 Control cascada
Es un método de control el cual involucra varios lazos dentron de otros lazos y la salida de los controladores de los lazos externos son la entrada del siguiente lazo.
Este método se implementa cuando un proceso principal se ve alterado por perturbaciones, generalmente más rápidas que el proceso principal. Por este motivo el control cascada es utilizado para el control de movimiento ya que todo movimmiento ejercido a una carga por tercera ley de Newton genera una fuerza opuesta al movimiento que altera la velocidad y finalmente la posición de la carga (al efecto se le llama offset). Al tomar esta fuerza como una perturbación es posible disminuir drásticamente e incluso eliminar su efecto en el proceso.


### 3.5 Tipos de controladores

![image](https://github.com/user-attachments/assets/0cfe162d-b10c-4444-bdb3-fbc8e259d337)


Figura 3. control cascada diagrama.

C1 o primario o  y C2 o secundario son los controladores, donde C2 es mas rapido que C1, para este controlador podemos usar un PI o proporcional para evitar que se ralentice, a este controlador tambien se le llama interno.
A C1 s ele debe de eliminar el error de estado estacionarios, este puede ser PI o PID, a este controlador tambien se le llama externo.

**Aplicaciones**
- Donde hay perturbaciones que afectan el funcionamiento
- Donde hay varibales mas rapidas que la variables controlada
- Donde se desea hacer la dinamica lo mas rapida posible

## 4. Metodos de sintonizacion
- **Metodos empiricos de lazo abierto y cerrado**
- **Metodos basados en modelos rigurosos**
- **Metodos basados en inteligencia computacional**

### 4.1 Metodologias empiricas de lazo abierto 
-**Sintonizacion Lazo Abierto**:
Como otros controladores los controladores cascada pueden ser sintonizados con métodos empíricos, siguiendo el siguiente procedimiento:

- Se abre el lazo en todo el sistema.
- Se realizan las pruebas midiendo la variable del lazo secundario (y2).
- Se sintoniza el controlador del lazo secundario y se cierra el lazo.
- Con el lazo secundario cerrado se realizan las pruebas midiendo la variable del lazo primario (y1).
- Finalmente se sintoniza el controlador del lazo primario.

#### 4.1.1 Metodología empírica de lazo abierto Austin
Austin desarrollo un método por el cual se pueden sintonizar el lazo primario mediante ecuaciones después de hacer sintonizado el lazo secundario.

- Se realizan las pruebas en lazo abierto y se miden ambas salidas de los lazos.
- Con la respuesta del lazo secundario se utiliza para ganancia (k2), la constante de tiempo (t2) y el tiempo muerto (to2). Y la respuesta del lazo primario también se utiliza para calcular la ganancia la ganancia (k1), la constante de tiempo (t1) y el tiempo de largo (to1).
- Y mediante las ecuaciones de la tabla se sintoniza ambos lazos.

### 4.2 Metodologias empiricas de lazo cerrado

#### 4.2.1 Metodología empírica de lazo cerrado Hang

Este método propone sintonizar ambos lazos por medio de pruebas de rele sobre estos, a comparacion de una prueba de rele normal, vamos a realirle la prueba a ambos lazos.

![image](https://github.com/user-attachments/assets/4bad72f3-c5eb-4728-a86b-d2c91f1e1584)

Figura 4. tabla prueba rele.

- Primero se realiza una prueba al lazo secundario, donde un rele activara y desactivara una señal de entrada.
- Se mide el ciclo último (Wu) y la ganancia última (Ku), donde el ciclo último es el periodo entre picos de la variable de lazo y la ganancia ultima se calcula.

$$K_{u}= \frac{4d}{pia}$$

Donde a es la amplitud de la variable de lazo y d es el valor de la histéresis del rele.

- Se procede a calcular por medio de la tabla los valores para los controladores.
- Se cierra el lazo secundario y se procede a repetir los anteriores pasos para el lazo primario.

## 5. Actuadores

### 5.1 Servomotor

Servo proviene de la palabra latina "servos" que significa esclavo, esto hace mención de la capacidad de cambiar una variable a un valor objetivo como lo hace un motor con las variables de posición, velocidad o torque.

##### 5.1.1 Motor DC

![image](https://github.com/user-attachments/assets/e322ecba-1531-43ad-b730-2ff4f1985e63)

Figura 5. Servomotor DC.

Motor que funciona con corriente directa que induce a la bobina del rotor un campo magnético que al interactuar con los imanes del estator produce el giro del rotor.

**Ventajas:**

- Control más simple.
- Driver de potencia más simple.
- Bajo precio en bajas capacidades.
- Alta eficiencia en aplicaciones pequeñas.
- 
**Desventajas:**

- Requiere mantenimiento e inspecciones periódicas.
- Las escobillas están en constante abración
- No aplicable para altos torques
- Sus imanes pueden sufrir desmagnetización con el tiempo.

##### 5.1.2 Motor AC Sincrono

![image](https://github.com/user-attachments/assets/218d4541-516b-4d11-9565-fa3dd28a8c09)

Figura 6. Servomotor AC sincrono.

Son maquinas eléctricas cuya velocidad de rotación está vinculada con la frecuencia de la red AC,lo que requiere de la sincronización de as señales de control, por esto se llaman síncronos.

**Ventajas:**

- Muy poco mantenimiento
- Excelente resistencia al entorno
- Compactos y ligeros
- Alta eficiencia en todo tipo de aplicaciones

**Desventajas:**

- Control de dificultad intermedia
- Se requiere respuesta 1:1 entre driver y motor
- Sus imanes pueden sufrir desmagnetización con el tiempo

##### 5.1.3 Motor AC Asincrono

![image](https://github.com/user-attachments/assets/723a637f-404a-4d4e-b4e9-d98471d4c289)

Figura 7. Servomotor AC Asincrono.

**Ventajas:**

- Poco mantenimiento
- Excelente resistencia al entorno
- Alta velocidad y alto torque
- Alta eficiencia en aplicaciones grandes
- Estructura robusta

**Desventajas:**

- Baja eficiencia en aplicaciones pequeñas
- Control más complicado que el DC por las señales de potencia.
- Puede sufrir cambios en sus características debido a temperaturas.

### 5.2 Zonas de operación de servomotores

Son graficas de torque contra velocidad angular que muestra el torque máximo que puede ejercer un motor al tener cierta velocidad angular. Cada fabricante provee estos datos de operatividad.

![image](https://github.com/user-attachments/assets/fdf56eb8-e9b2-468c-9829-138a2d398742)

Figura 8. Zona de operacion de servomotores.

En estas hay dos zonas principales en las gráficas, la primera llamada continua es la zona de operación constante del motor, donde va a estar operativo la mayor parte del tiempo. La segunda llamada intermitente muestra los puntos de operación que puede alcanzar el motor en breves instantes.

**Simulaciones**

Es posible simular el comportamiento de un motor, teniendo las características electromagnéticas y mecánicas del motor. Validando la simulación por medio de las gráficas de torque y velocidad.

### 5.3 Sensores en servomotores

#### 5.3.1 Encoders

Son sensores capaces de medir la posición y velocidad de, existen de dos tipos

- Encoder absoluto
  
  ![image](https://github.com/user-attachments/assets/1a0d794a-ecff-4b79-88ae-6d1f711a1cf2)
  
  Figura 9. Encoder absoluto.

- Encoder incremental

  ![image](https://github.com/user-attachments/assets/d9798887-2048-45d3-9993-ac769b5501ba)

   Figura 10. Encoder incremental.

  #### 5.3.2 Resolver

  Es un sensor analógico de posición angular, que consta de dos embobinados (rotor y estator), para posiciones relativas de uno con respecto al otro varia la amplitud que se induce en el rotor.

![image](https://github.com/user-attachments/assets/93acffd1-f8a9-4b83-89e8-5debec5ec837)

Figura 11. Resolver.

 #### 5.3.3 Sensor de torque

 Directamente es muy complicado medir el torque de un motor, pero teniendo en cuenta que la corriente requerida por un motor para mover una carga es directamente proporcional al toque de este. Por lo tato podemos saber el torque del motor al medir la corriente y multiplicar por una constante de proporción.

Existe dos tipos de sensores de corriente:

 - Shunt: Una resistencia muy pequeña para tomar la tensión en esta y aplicar ley de ohm.
   
![image](https://github.com/user-attachments/assets/7d969f6b-ef88-418f-b2db-044a28aa0b00)

   Figura 12. Shunt.

 - Efecto Hall: Es un sensor que detecta cambios de campo magnético y por ley de inducción de Faraday se puede obtener la corriente.

![image](https://github.com/user-attachments/assets/715dc556-eff9-404a-b0a3-b16d68c9f979)

   Figura 13. Hall.

### 5.4 Drivers de potencia

Es el elemento que recibe las señales de baja potencia (señales de control) y las amplifica a señales de alta potencia. Cada axis tiene un accionador y cada accionador posee su driver ya que los accionadores son los encargado de transformar energía eléctrica a mecánica lo que involucra un alto costo energético.

Por estándar de la industria el control de los accionadores se hace por medio de señales PWM.

## 6. Simscape
- Es un entorno de simulacion para podelar sistemas en 3d
- Formula y resuelve las ecuaciones de movimiento del sistema
- Funciona mediante piezas rigidas

### 6.1 Configuracion general
- Sistemas tipicos ode 23, 45, 23t
- Altas frecuencias 15s y 23s
- iniciar archivo: smnew, este entrega 7 objetos, en dado caso que no, va a generar un error
- Contiene 3 bloques principales que sirven para: configurar ecuaciones y su sintonizacion, configurar los ejes de coordenadas y configurar leyes fisicas.

## 7. Conclusiones

- Importancia del Control de Movimiento
El control de movimiento es un pilar fundamental en la automatización industrial, permitiendo una mayor precisión, eficiencia y optimización de los procesos. Su evolución ha llevado a la integración de sistemas electrónicos avanzados, eliminando muchas de las limitaciones de los mecanismos puramente mecánicos.

- Diferentes Tipos de Actuadores
Existen diversos tipos de motores utilizados en el control de movimiento, como los servomotores de corriente continua (DC), motores síncronos y motores asíncronos. Cada uno tiene ventajas y desventajas dependiendo de la aplicación, siendo clave seleccionar el adecuado para cada caso.

- Simulación y Modelado
Herramientas como Simscape permiten realizar simulaciones detalladas del comportamiento de los sistemas de control de movimiento, facilitando el análisis y optimización antes de la implementación en entornos reales.

## 8. Referencias

[1] J. Cote, Digital Control, GitHub repository, 2024. [Online]. Available: https://github.com/jorgecote/DigtalControl.

[2] K. Ogata, Ingeniería de control moderna, 5ª ed. Madrid, España: Pearson, 2010.

[3] S. J. Chapman, Máquinas eléctricas, 4ª ed. Madrid, España: McGraw-Hill Interamericana, 2005.

[4] J. Serrano Iribarnegaray, Fundamentos de máquinas eléctricas rotativas. Barcelona, España: Marcombo, 1989.

[5] C.-T. Chen, Diseño de sistemas de control analógicos y digitales. México: Pearson, 2004.

[6] K. J. Åström y T. Hägglund, Controladores PID: Teoría, diseño y sintonización. Madrid, España: Pearson, 1995.

[7] E. Papadopoulos y G. Chasparis, “Analysis and model-based control of servomechanisms with friction,” Proceedings of the 2002 IEEE International Conference on Control Applications, 2002, pp. 782-787.

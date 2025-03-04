# Control de Movimiento
Julian Redondo & Sebastian Cifuentes & David Vasquez
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

Figura 7. Zona de operacion de servomotores.

En estas hay dos zonas principales en las gráficas, la primera llamada continua es la zona de operación constante del motor, donde va a estar operativo la mayor parte del tiempo. La segunda llamada intermitente muestra los puntos de operación que puede alcanzar el motor en breves instantes.

**Simulaciones**

Es posible simular el comportamiento de un motor, teniendo las características electromagnéticas y mecánicas del motor. Validando la simulación por medio de las gráficas de torque y velocidad.



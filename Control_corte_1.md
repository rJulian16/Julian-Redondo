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
Es un método de control el cual involucra varios lazos dentron de otros lazos y la salida de los controladores de los lazos externos son la entrada del siguiente lazo, como se puede ver en la siguiente imagen:

![image](https://github.com/user-attachments/assets/aa3d4dba-4e69-4159-9b7b-8a3e85bf04fa)


Figura 3. control cascada, presentacion clase.

Este método se implementa cuando un proceso principal se ve alterado por perturbaciones, generalmente más rápidas que el proceso principal. Por este motivo el control cascada es utilizado para el control de movimiento ya que todo movimmiento ejercido a una carga por tercera ley de Newton genera una fuerza opuesta al movimiento que altera la velocidad y finalmente la posición de la carga (al efecto se le llama offset). Al tomar esta fuerza como una perturbación es posible disminuir drásticamente e incluso eliminar su efecto en el proceso.


### 3.5 Tipos de controladores

![image](https://github.com/user-attachments/assets/0cfe162d-b10c-4444-bdb3-fbc8e259d337)


Figura 4. control cascada diagrama.

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

### 4.2 Metodología empírica de lazo abierto Austin
Austin desarrollo un método por el cual se pueden sintonizar el lazo primario mediante ecuaciones después de hacer sintonizado el lazo secundario.

- Se realizan las pruebas en lazo abierto y se miden ambas salidas de los lazos.
- Con la respuesta del lazo secundario se utiliza para ganancia (k2), la constante de tiempo (t2) y el tiempo muerto (to2). Y la respuesta del lazo primario también se utiliza para calcular la ganancia la ganancia (k1), la constante de tiempo (t1) y el tiempo de largo (to1).
- Y mediante las ecuaciones de la tabla se sintoniza ambos lazos.

![image](https://github.com/user-attachments/assets/6f3b85fc-cc29-49a1-a704-3c34f9e7548b)

Figura 5. tabla sintonizacion Austin lazo abierto

![image](https://github.com/user-attachments/assets/3c876789-32b4-4df8-9000-908802820911)

Figura 6. tabla sintonizacion Austin lazo abierto 2

## 5 Metodologias empiricas de lazo cerrado

### 5.1 Metodología empírica de lazo cerrado Hang

Este método propone sintonizar ambos lazos por medio de pruebas de rele sobre estos, a comparacion de una prueba de rele normal, vamos a realirle la prueba a ambos lazos.

![image](https://github.com/user-attachments/assets/4bad72f3-c5eb-4728-a86b-d2c91f1e1584)

Figura 7. tabla prueba rele.



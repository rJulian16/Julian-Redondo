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

## 3. Control 
Los sistemas contienen multiples ejes a controlar, donde a cada eje le podemos llegar a controlar la posicion, velocidad, torque, aceleracion con ayuda de algun piston o . hoy en dia a estos sistemas que ya disponen de componentes electricos para este control se les conoce como Electronic Gearing for Coordination. 
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

![image](https://github.com/user-attachments/assets/663787f6-ecc7-41af-9c29-40eb915062c3)

Figura 3. esquema de bloques.

### 3.3 Caracteristicas de control: 
Un movimiento sobre una carga genera una fuerza negativa ejercida por el motor, esta fuerza negativa provoca cambios en la velocidad, a esto se le llama offset para ello es necesario controlar el offset para reducirlo lo mas que se pueda ya que esto es una perturbación.

Los componentes de nuestro sistema deben ser bien diseñados ya que la dinamica de estos sistemas son muy rapidos y necesitamos componentes que tengan propositos de eficiencia y productividad para la electronica y el motor
La siguiente imagen muestra el esquema de control cascada para un sistema. 

![image](https://github.com/user-attachments/assets/aa3d4dba-4e69-4159-9b7b-8a3e85bf04fa)


Figura 4. control cascada.

![image](https://github.com/user-attachments/assets/775149ce-9d29-4def-bc16-48ae113a6522)

Figura 5. control cascada diagrama.

### 3.4 Tipos de controladores
C1 y C2 son los controladores, donde C2 es nas rapido que C1, para este controlador podemos usar un PI o proporcional para evitar que se ralentice, a este controlador tambien se le llama interno o secundario.
A C1 s ele debe de eliminar el error de estado estacionarios, este puede ser PI o PID, a este controlador tambien se le llama externo o primario. 

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
- Aplicar pruebas de lazo abierto a cada una de las variables delcontrol cascada
- Con estas pruebas se puede sintonizar por alguno de los metodos conocidos los controladores
- Imporancia de tener en cuenta la sintonizacion en la interaccion entre los dos lazos.

![image](https://github.com/user-attachments/assets/d334f0c3-c245-4d2e-90ca-247be8cb5e05)

Figura 6. sintonizacion lazo abierto.


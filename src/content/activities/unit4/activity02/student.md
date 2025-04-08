### Manejo de angulos

#### 1. ¿Qué está pasando en esta simulación? ¿Cuál es la interacción?

La simulacion muestra elementos que rotan en torno a un punto de referencia. Se utiliza el sistema de coordenadas y funciones como ``` rotate() ``` para modificar la orientacion de los elementos.

#### 2.Nota que en cada frame se está trasladando el origen del sistema de coordenadas al centro de la pantalla. ¿Por qué crees que se hace esto?

Se hace esto para facilitar las transormaciones como rotacion y escalado, ya que normalmente el sistema de coordenadas tiene su origen en la esquina superior izquierda. Al trasladar el origen al centro, la rotacion se comporta de manera mas intuitiva.

#### 3. ¿Cuál es la relación entre el sistema de coordenadas y la función ``` rotate() ``` ?

La funcion ``` rotate() ``` gira el sistema de coordenadas en torno al punto de origen. Si el origen no se traslada al centro del objeto antes de rotarlo, el objeto girara alrededor del punto (0,0) en lugar de rotar sobre su propio eje.

### Direccion del movimiento

#### 1. Identifica el marco motion 101. ¿Qué es lo que se está haciendo en este marco?

En este caso, el codigo parece calcular la direccion de un objeto y alinear su orientacion en esa direccion.

#### 2. ¿Qué hace la función ``` heading() ```?

``` heading() ``` devuelve el angulo de orientacion del vector de velocidad en radianes. Se usa para determinar hacia donde esta apuntando un objeto en movimiento.

#### 3. ¿Qué hace la función ``` push() ``` y ``` pop() ```?

``` push() ``` guarda el estado actual del sistema de coordenadas (posicion, rotacion, escala, etc.) y ``` pop() ``` lo restaura. Esto permite hacer transformaciones locales sin afectar otros elementos de la escena.

#### 4. ¿Qué hace ``` rectMode(CENTER) ```?

Hace que los rectangulos se dibujen desde su centro en vez de la esquina superior izquierda, lo cual facilita la alineacion y rotacion de los objetos.

#### 5. ¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad?

El angulo de rotacion se pone en funcion del vector de velocidad con ``` heading() ```, lo que significa que el objeto se orienta en la misma direccion en la que se esta moviendo.

### ```mag()```

#### ¿Para qué sirve el método ``` mag() ```?
Se utiliza para calcular la magnitud y la longitud de un vector. Es literalmente lo mismo a aplicar el teorema de Pitagoras.

**magnitud = sqrt(x^2 + y^2)**

#### ¿Para qué sirve el método ```magSq()```?
Este devuelve la magnitud al cuadrado, sin aplicar la raiz cuadrada.

**magnitud^2 = x^2 + y^2**

#### Diferencia entre ``` mag() ``` y ``` magSq() ```
``` mag() ``` devuelve la longitud real del vector.

``` magSq() ``` devuelve el valor de la longitud al cuadrado.

#### Cual es mas eficiente?
``` magSq ``` es mas eficiente que ``` mag () ``` porque este evita el calculo de la raiz cuadrada, que es una operacion costosa por asi decirlo en terminos computacionales

### ```normalize()```
Este sirve para convertir un vector en un vector unitario, es decir, un vector con la misma direccion pero con magnitud igual a 1.

#### Como funciona?
Para normalizar un vector (x,y) se divide cada componente por su magnitud:

x′= x/magnitud , y′ = y/magnitud

la magnitud es: sqrt(x^2 + y^2).

#### Te encuentras con un periodista en la calle y te pregunta ¿Para que sirve el metodo ```dot()```?¿Que le responderias en una frase?
Le diria que el metodo ```dot()``` calcula el producto punto entre dos vectores, que indica cuanto se parecen en direccion;si es 0 estos son perpendiculares y si es maximo ambos apuntan en la misma direccion.

#### Diferencia entre la version estatica y la de instancia.

* **Version de instancia:**
Se llama desde un objecto ```p5.Vector``` y recibe otro vector como respuesta. Calcula el producto punto entre el vector que llama el metodo y el vector pasado como parametro.

* **Version estatica:**
Se llama directamente desde ```p5.Vector``` y recibe dos vectores como parametros. No modifica ningun objeto existente, solo realiza el calculo y devuelve el resultado.

### Producto Cruz
Este da como resultado un tercer vector perpendicular a ambos, lo que define un plano en el espacio. La direccion del nuevo vector sigue la regla de la mano derecha, y su magnitud representa el area del palalelogramo formado por los vectores iniciales. Si los vectores son paralelos, el producto cruz es cero porque no hay area.

### ```dist()```
Este sirve para calcular la distancia entre dos puntos en el espacio, representados como vectores.
Este usa la formula de la distancia euclidiana:

distancia = sqrt((x2-x1)^2 + (y2-y1)^2))

### ```normalize()```
Sirve para controlar la magnitud de un vector, pero este mantiene la direccion original y la ajusta a 1. Se usa cuando solo importa la direccion del vector, por ejemplo en movimiento o direcciones de fuerza.

### ```limit()```
Sirve para controlar la magnitud del vector pero si la magnitud del vector es mayor al valor limite, la reduce a ese maximo. Si la magnitud es menos, no la modifica. Util para controlar la velocidad maxima de objetos en juegos.


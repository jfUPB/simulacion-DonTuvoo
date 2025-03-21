### ¿Qué modificación hay que hacer al Motion 101 para agregar fuerzas acumulativas?

En vez de reemplazar la aceleracion en cada frame ``` acceleration = force ```, debemos acumular la fuerza con ``` acceleration.add(force) ```.

Tambien es necesario reiniciar la aceleracion en cada ciclo ``` acceleration.mult(0) ``` despues de aplicarla, para evitar acumulaciones indefinidas.

### Identifica dónde está el Attractor en la simulación. Cambia el color de este.

El Attractor esta definido por la clase de ``` Attractor ```, mas que todo en el metodo ``` display() ```

Podemos cambiar su color modificando los valores de ``` fill() ```, por ejemplo: 

``` fill(255, 0, 0): // Rojo ```

#### ¿Cómo podrías modificar el código para que esto funcione? considera las funciones que ofrece p5.js para interactuar con el mouse?

Para hacer que el Attractor pueda moverse con el mouse y cambiar de color al pasar sobre el se pueden utilizar las siguientes funciones.

``` mousePressed() ``` Para detectar cuando el usuario hace clic sobre el Attractor e iniciar el arrastre.

``` mouseDragged() ``` Para actualizar la posicion del Attractor mientras se mantiene presionado el mouse.

``` mouseReleased() ``` Para detener el arrastre cuando se suelta el boton del mouse.

``` dist(mouseX, mouseY, this.position.x, this.position.y) ``` Para verificar si el cursor esta sobre el Attractor y cambiar su color.

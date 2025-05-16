### Cuál es la relación entre r y theta con las posiciones x y y?

La relacion entre **y** y **theta** con las posiciones x y y se basa en la conversion de coordenadas polares a cartesianas.

**r** representa la distancia desde el origen hasta el punto.

**theta** es el angulo de rotacion en radianes.

**x = r * cos(theta)** y **y = r * sin(theta)** convierten las coordenadas polares en cartesianas.

### Modifica la función ``` draw() ```:

Ocurre un error ya que la variable **v** es un vector que se crea con ``` let v = p5.Vector.fromAngle(theta); ``` lo que dice que su magnitud es 1.

Para que el circulo se dibuje debemos multiplicar **v** por un radio **r**.

### Ahora realiza esta modificación:

#### ¿Que ocurre?

Ya no da error porque multiplicamos **v** por **r** y el punto se mueve en un circulo de radio **r**.

#### ¿Por que?

Antes sin r el el vector tenia una longitud de 1 haciendo asi que el circulo este muy cerca del punto de origen, ahora con r expande la distancia entre el circulo y el punto de origen.

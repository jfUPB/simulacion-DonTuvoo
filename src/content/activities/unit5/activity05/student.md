# Autoevaluacion

#### 1.
Si llegue a usar POO y la verdad creo que me quedo bastante claro el concepto desde un principio (o lo basico diria yo), ya que me explicaron de una forma bastate intuitiva y fue con espadas de minecraft fue algo como: Tenemos una espada que es una espada comun y esta seria la espada ''padre'' que la usariamos como base para las demas espadas, esta espada teniendo clases como, daño y durabilidad, teniendo asi la espada hija que tendria otra clase que podria ser ''largo'' y asi sucesivamente. El polimorfismo es algo parecido pero haciendo otras versiones de la misma espada, como por ejemplo una espada de fuego, de agua y asi.

#### 2. 
Yo creo que lo mas facil fue entender la POO porque ya habia visto ejemplos antes y la verdad me parecio bastante intuitivo. Lo que mas me ayudo fue pensar en objetos como si fueran cosas del mundo real, por ejemplo, las particulas son como bolitas que tienen posicion, velocidad y aceleracion, y el repeller es como un iman que las empuja. Tambien el concepto de herencia lo entendi rapido porque es como cuando en los juegos hay un objeto base y luego se crean versiones mejoradas o diferentes a partir de ese. Polimorfismo igual me parecio facil porque es como hacer varias versiones de un mismo objeto con comportamientos distintos segun la situacion.

### 3.
Yo diria que lo mas dificil fue hacer que las particulas desaparecieran cuando tocaban los bordes y al mismo tiempo cambiar el color global sin que hubiera errores. Al principio intentaba hacer que rebotaran, pero luego me pediste que desaparecieran y ahi tuve que cambiar la logica. Lo resolvi agregando una condicion en ```isDead()``` para detectar cuando una particula se sale de la pantalla y eliminandola en ```run()```. Tambien tuve que asegurarme de que el color global cambiara justo cuando una particula moria, porque si lo ponia en otro lado, el color cambiaba todo el tiempo y se veia raro.

### 4.
Si pudiera repetir la unidad, me enfocaria mas en entender bien como usar la herencia y el polimorfismo desde el principio. A veces escribia codigo repetido que luego me daba cuenta que podia simplificar con una clase padre, como hice con ```MovableObject```. Tambien trataria de hacer mas experimentos con polimorfismo, creando diferentes tipos de particulas con comportamientos distintos, para ver mejor como se pueden modificar metodos en clases hijas sin cambiar la estructura general del codigo.

### 5. 
Si, lo que aprendi en esta unidad me servira en futuros proyectos porque la POO permite organizar mejor los elementos en una animacion. Por ejemplo, el uso de clases y herencia hace que sea mas facil manejar objetos en movimiento, como personajes o efectos de particulas. En mi codigo, ```MovableObject``` es una clase base que otras clases como ```Particle``` y ```Repeller``` heredan, lo que evita repetir codigo y facilita modificaciones. Tambien el polimorfismo me ayuda a definir distintos comportamientos sin cambiar la estructura del programa, lo que hace que sea mas flexible y reutilizable para proyectos de animacion.

### 6.
Me gustaria profundizar mas en polimorfismo porque permite definir distintos comportamientos para las particulas sin cambiar la estructura base del sistema. En mi codigo, todas las particulas heredan de MovableObject, pero podria crear subclases como ```BouncingParticle``` o ```FadingParticle```, donde cada una tenga su propia logica de movimiento y desaparicion. Esto haria que el sistema sea mas flexible y facil de expandir, permitiendo agregar nuevos tipos de particulas sin modificar la clase base. Tambien podria explorar como optimizar el uso de memoria cuando hay muchas particulas activas.

### 7.
La POO se puede aplicar en animacion porque te deja organizar mejor los elementos en una escena. Por ejemplo, si estas haciendo un efecto de particulas, puedes tener una clase base ```MovableObject``` con metodos generales como ```applyForce``` y ```update```, y luego hacer clases hijas como ```Particle``` o ```Repeller``` que heredan de esta y agregan sus propias funciones. Esto hace que el codigo sea mas facil de mantener y modificar sin repetir tanto. Ademas, con polimorfismo puedes hacer que diferentes tipos de particulas se comporten distinto sin cambiar la estructura base del sistema.

# Consolidación de lo aprendido

### ¿Cómo se gestiona la creación y la desaparición de las partículas y cómo se gestiona la memoria?

Las particulas se crean en ``` Emitter.addParticle() ``` y se añaden al array ``` this.particles```

En ```Emitter.run()``` se recorren todas las particulas actualizandolas y dibujandolas.

Si una particula ''muere'' ```isdead()``` se elimina con ```splice(i, 1)``` optimizando la memoria

Cada que una particula muere, el color cambia con ```globalColor = color(random(255), random(255), random(255)) ```


### ¿Cómo se aplica el marco de movimiento motion 101 en los sistemas de partículas que analizaste en la actividad anterior?

Cada particula tiene ```position, velocity y acceleration```.

La aceleracion se modifica con ```applyForce()```, permitiendo que fuerzas externas la afecten.

En ```update()```, la velocidad se actualiza con la aceleracion y luego la posicion cambia con la velocidad.


### Cómo se aplican fuerzas externas a los sistemas de partículas que trabajaste en la unidad? ¿Qué fuerzas se aplicaron y cómo están modeladas?

Aplique una fuerza constante hacia abajo con ```applyForce(createVector(0, 0.1))```.

```Repeller``` genera una fuerza inversamente proporcional a la distancia ```(force.setMag(-this.power / (distance * distance)))```, haciendo que las particulas sean empujadas lejos del repeller.


### ¿Cómo se aplicaste los conceptos de herencia y polimorfismo en los sistemas de partículas que trabajaste en la unidad?

En herencia ```Particle``` y ```Repeller``` heredan de ```MovableObject```, reutilizando codigo base ```(position, velocity, applyForce(), update())```.

Y en polimorfismo ```Particle``` redefine ```display()``` para dibujar circulos con transparencia, ```Repeller``` redefine ```display()``` para dibujar un circulo rojo en una posicion controlada por el mouse, ```Repeller``` redefine ```move()``` para seguir el mouse.

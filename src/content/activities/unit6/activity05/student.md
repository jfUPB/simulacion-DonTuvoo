# Comparando algoritmos y consolidando conceptos

## 1. Diferencias fundamentales

### - Flow Fields:
En este la inteligencia esta en el entorno, cada punto en el espacio tiene una direccion predefinida y los agentes simplemente siguen esa direccion.

### - Flocking:
La inteligencia esta en los agentes, que se comportan segun sus reglas locales de interaccion. No hay un mapa externo que guie su movimiento el comprotamiento surge de las relaciones entre si.

## 2. Tipos de comportamiento emergente

### - Flow Fields:
Este es ideal para patrones suaves y fluidos como: Rios de particulas, efectos de humo, viento, simulacion de trayectorias tipo polen, polvo, etc.

### - Flocking:
Este es ideal para patrones colectivos como: fomramcion y disolucion de grupos, movimiento colectivo y reaccion colectiva.

## 3. Ventajas y desventajas 

### - Flow Fields:

Sus ventajas son que son muy facil de controlar globalmente, produce patrones fluidos y organicos este es ideal para texturas animadas. Pero es poco interactivo, no hay vida social entre ellos, todos son agentes pasivos.

### - Flocking: 

Tiene gran realismo en comportamiento grupal, una sensacion de vida y autoorganizacion y es muy responsivo a eventos locales. Pero es dificil de controlar globalmente, puede volverse caotico o desorganizado.

## 4. Agente autonomo

Ambos algoritmos muestran que un agente autonomo percibe su entorno, toma decisiones localmente y actua con base en reglas simples. Esto me ayudo a ver que un agente no necesita ser complejo ya que con pocas reglas y percepciones limitadas puede generar comportamientos sorprendentes y creibles.

## 5. Emergencia

Observe el comportamiento cuando:

En el flocking al cambiar los pesos de separacion/cohesion, los boids pasaron de estar dispersos a formar estructuras densas sin haber programado explicitamente que se agrupen

En Flow Fields pequeñas modificaciones al campo crearon patrones parecidos a torbellinos o corrientes invisibles.

Asi entendi que la complejidad surge de lo simple no hay que codificar cada resultado visual.

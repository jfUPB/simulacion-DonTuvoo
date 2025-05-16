## Logica Central
El sistema se basara en un enjambre de particulas que se mueven dentro de un flow field modulado por la amplitud del audio. Cada particula se comportara como un agente autonomo afectado por la direccion del campo y por su propia energia interna, la energia se ajusta en tiempo real segun los valores del FFT. 
El resultado sera un paisaje organico y cambiante donde las particulas forman estructuras fluidas o caoticas.

## Tecnicas seleccionadas
Flow Field, Agentes, FFT, Perlin Noise

## Inputs de audio y su efecto
### Amplitud general:
Escala el flow field y la cantidad de particulas emitidas, cambiando asi la direccion y turbulencia del campo visual y generando mas particulas.

### Graves:
Cohesion entre aprticulas, los graves altos generan formas compactas y los graves bajos dispersion.

### Agudos:
Velocidad y opacidad de las particulas agudos altos generan particulas mas rapdias y brillantes.

## Inputs del usuario
MouseX/MouseY cambia el nivel de distorsion del perlin noise
Click izquierdo alterna entre dos paletas de color

## Elementos generativos
Cada particula nace con una posicion y direccion distintas, el uso de ruido de perlin que cambian en tiempo real, numero de particulas conexiones y opacidad que se adaptan al audio y cambian constantemente

## Outputs visuales
Particulas en movimiento, lineas de conexion entre particuals cercanas, ondas o estructuras que emergen del campo de flujo, cambios suaves de color, brillo y opacidad

## Resumen documentado
Son particulas autonomas que se mueven dentro de un campo de flujo generado por el ruido de perlin. El cambio cambia segun la amplitud de la musica y las particulas reaccionan a la energia de distintas bandas de frecuencia. 
Por parte de las visuales espero que se generen formas organicas en constante cambio, con momentos de calma y momentos de caos, todo conectado a la narrativa emocional de la cancion.


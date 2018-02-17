# Crear una escena básica.

Para crear una escena básica que muestre un objeto 3D en Web, podemos utilizar la librería de javascript [Three.js](https://threejs.org/)

## Estos son los pasos a seguir:

1. Crear un archivo `.html`.
2. Importar nuestro archivo three.js.
3. Agregar styles al body y el canvas. En este caso, el canvas tomará el width del padre (body).

### Ahora, construimos nuestra escena:

1. Seteamos la escena.
2. Creamos la cámara. En three.js existen varios tipos de cámara, en este caso usaremos una cámara perspectiva.

### Esta recibe 4 atributos:

1. Field of View (FOV), que es la extensión de la escena. Este valor está en grados.
2. Aspect Ratio, usualmente se usa el ancho del elemento dividido por el alto. O si no la imagen se vería como aplastada.
3. Los otros 2 atributos son la distancia de cercanía (near) y lejanía (far) del plano. Lo que significa que los elementos más allá de esos 2 límites no se renderizan.

El siguiente paso es agregar el motor de render. Aquí es donde la magia sucede. Adicional al motor de WebGL Renderer, three.js trae integrados otras dos opciones de renderizado para browsers viejos o para las personas que no tienen webgl por alguna razón. Aquí mismo podemos definir en qué parte de nuestro HTML se dibujara nuestra escena. Se pueden agregar otros parámetros, como antialias que es un booleano que permite que el render se vea mas claro.

Después debemos definir el tamaño en que queremos renderizar nuestra app. En este caso tomará el ancho del browser. Para mejor performance podemos dar valores menores.

Por último agregamos el elemento renderizado a nuestro `HTML`. Este es un elemento <canvas> que el renderizador usará para mostrarnos la escena.

Todo va muy bien hasta ahora, pero ¿y el cubo?

### Para crear el cubo, debemos seguir los siguientes pasos:

1. Necesitamos agregar un nuevo objeto geométrico, en este caso, el objeto  BoxGeometry. Este contiene todas las caras y vértices del cubo. 
2. Además debemos agregarle un material a nuestro cubo para poder distinguirlo. Three.js trae diferentes materiales, en este caso, agregaremos un lambert material. Todos los materiales toman un objeto con propiedades, que se agregaran al cubo. Para mantenerlo simple solamente agregaremos un color. 
3. Lo tercero que necesitamos es un Mesh. El Mesh es un objeto que toma el material y se lo aplica a la geometría (cubo)
4. Después agregamos nuestro cubo a la escena. Por defecto se agrega en los puntos x= 0, y=0, z=0. Esto haría que la cámara y el cubo se crearan en el mismo punto. Para evitar esto, movemos el cubo un poco.

Teniendo nuestro objeto en la escena, es hora de renderizarla. Llamamos a la función render o animated, que es un loop que renderiza la escena cada que se actualiza -usualmente 60 veces por segundo o 60fps (frame per second)-. Lo bueno de usar el requestAnimationFrame es que trae muchas ventajas, la principal es que pausa el renderizado cuando el usuario cambia de tab. Lo que nos ahorra recursos :)

Ahora, para poder notar el cubo, le agregaremos una animación muy simple. 

Básicamente, todo lo que quieras cambiar mientras la aplicación esté corriendo debe pasar por el loop. Obviamente puedes llamar otras funciones desde esta, para evitar tener mil líneas de código.


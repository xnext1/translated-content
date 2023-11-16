html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Juego del perro</title>
    <style>
        /* Estilo del canvas */
        canvas {
            border: 1px solid black;
            margin: 10px auto;
            display: block;
        }
    </style>
</head>
<body>
    <!-- Canvas donde se dibuja el juego -->
    <canvas id="canvas" width="320" height="240"></canvas>
    <!-- Archivos JavaScript que contienen el código del juego -->
    <script src="perro.js"></script>
    <script src="obstaculo.js"></script>
    <script src="juego.js"></script>
</body>
</html>


A continuación, necesitas crear un archivo JavaScript que contenga el código del perro, que es el protagonista del juego. El perro tendrá una posición, una velocidad, una imagen y una función para moverse y dibujarse en el canvas. El archivo JavaScript podría tener este aspecto:

javascript
// Código del perro

// Variable que almacena el contexto del canvas
var ctx = document.getElementById("canvas").getContext("2d");

// Constructor del perro
function Perro(x, y) {
    this.x = x; // Posición horizontal del perro
    this.y = y; // Posición vertical del perro
    this.vx = 0; // Velocidad horizontal del perro
    this.vy = 0; // Velocidad vertical del perro
    this.img = new Image(); // Imagen del perro
    this.img.src = "perro.png"; // Ruta de la imagen del perro
}

// Método para mover al perro
Perro.prototype.mover = function() {
    // Actualizar la posición del perro según su velocidad
    this.x += this.vx;
    this.y += this.vy;

    // Limitar la posición del perro dentro del canvas
    if (this.x < 0) this.x = 0;
    if (this.x > 320 - this.img.width) this.x = 320 - this.img.width;
    if (this.y < 0) this.y = 0;
    if (this.y > 240 - this.img.height) this.y = 240 - this.img.height;
}

// Método para dibujar al perro
Perro.prototype.dibujar = function() {
    // Dibujar la imagen del perro en el canvas
    ctx.drawImage(this.img, this.x, this.y);
}

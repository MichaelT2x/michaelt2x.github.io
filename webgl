<!DOCTYPE html>
<html>
<head>
  <title>WebGL Initialization Example</title>
  <style>
    canvas {
      display: block;
      margin: 0 auto;
      width: 800px;
      height: 600px;
      border: 1px solid black;
    }
  </style>
</head>
<body>
  <canvas id="myCanvas"></canvas>

  <script>
    // Get the canvas element and its 2D rendering context
    const canvas = document.getElementById('myCanvas');
    const gl = canvas.getContext('webgl');

    // Set the viewport size
    gl.viewport(0, 0, canvas.width, canvas.height);

    // Define the red color (RGBA)
    const red = [1.0, 0.0, 0.0, 1.0];

    // Create a new program with a vertex shader and a fragment shader
    const program = gl.createProgram();
    const vs = gl.createShader(gl.VERTEX_SHADER);
    const fs = gl.createShader(gl.FRAGMENT_SHADER);

    // Set the shader source code
    gl.shaderSource(vs, `
      attribute vec4 aVertexPosition;
      void main() {
        gl_Position = aVertexPosition;
      }
    `);
    gl.shaderSource(fs, `
      precision mediump float;
      uniform vec4 uColor;
      void main() {
        gl_FragColor = uColor;
      }
    `);

    // Compile the shaders and attach them to the program
    gl.compileShader(vs);
    gl.compileShader(fs);
    gl.attachShader(program, vs);
    gl.attachShader(program, fs);

    // Bind the attribute and uniform variables
    gl.bindAttribLocation(program, 0, 'aVertexPosition');
    gl.uniform4fv(gl.getUniformLocation(program, 'uColor'), red);

    // Link and use the program
    gl.linkProgram(program);
    gl.useProgram(program);

    // Define the vertex data for a single point at the center of the canvas
    const vertexData = new Float32Array([0.0, 0.0, 1.0, 1.0]);

    // Create a buffer object and bind it to the ARRAY_BUFFER target
    const buffer = gl.createBuffer();
    gl.bindBuffer(gl.ARRAY_BUFFER, buffer);

    // Transfer the vertex data to the buffer object
    gl.bufferData(gl.ARRAY_BUFFER, vertexData, gl.STATIC_DRAW);

    // Enable the vertex attribute array and specify the attribute buffer
    const aVertexPosition = gl.getAttribLocation(program, 'aVertexPosition');
    gl.enableVertexAttribArray(aVertexPosition);
    gl.vertexAttribPointer(aVertexPosition, 2, gl.FLOAT, false, 0, 0);

    // Draw a single point
    gl.drawArrays(gl.POINTS, 0, 1);
  </script>
</body>
</html>

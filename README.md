# EffekseerForWebGL

- [Official website](http://effekseer.github.io)
- [Effekseer main repository](https://github.com/effekseer/Effekseer)

# Demo

- [Demo](https://effekseer.github.io/EffekseerForWebGL/Sample/index.html)

# Download

- [1.43](https://github.com/effekseer/EffekseerForWebGL/releases/download/143/EffekseerForWebGL143.zip)

# How to use

```html
<script src="three.min.js"></script>
<script src="effekseer.min.js"></script>
```

```js
// Setup WebGLRenderer
var renderer = new THREE.WebGLRenderer();

// Initialize by WebGLRenderingContext
effekseer.init(renderer.context);

// Load effect data
var effect = effekseer.loadEffect("Laser01.efk", function(){
  // Play the loaded effect
  effekseer.play(effect);
});

(function renderLoop() {
  requestAnimationFrame( renderLoop );

  // Effekseer Update
  effekseer.update();

  // Three.js Rendering
  renderer.render(scene, camera);

  // Rendering Settings
  effekseer.setProjectionMatrix(camera.projectionMatrix.elements);
  effekseer.setCameraMatrix(camera.matrixWorldInverse.elements);

  // Effekseer Rendering
  effekseer.draw();
})();

```

# How to develop

## Clone the repositories

```
git clone https://github.com/effekseer/Effekseer
git clone https://github.com/effekseer/EffekseerForWebGL
```

## Requirements

### Common

- python
- cmake
- mingw-make (Windows only)
- Emscripten 1.38.38 (Add directory to PATH)

### JavaScript

- npm
- babel-cli
- babel-preset-es2015

## Build

### Convert ES6 to ES5

```
npm install -g babel-cli
cd Dev/Source/
npm install babel-preset-es2015 --save-dev
babel effekseer.src.es6.js -o effekseer.src.js
```

### Compile Native

```
pip install jsmin
python build.py
```

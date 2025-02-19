# Obyek-3D-AR-RindangCavallera
Nama : Rindang Cavallera
NPM  : 2113025013
MK   : Augmented Reality
Tugas: Buatlah obyek 3D mengunakan kombinasi dari a-frame primitives. Obyek harus cukup kompleks, minimal terdiri dari 5 obyek.
Variasi bisa berdasarkan posisi, skala, warna, material, rotasi.

Source Code:
<html>
  <head>
    <meta charset="utf-8">
    <title>Objek 3D Rindang</title>
    <meta name="description" content="Rindang Cavallera">
    <script src="https://aframe.io/releases/0.5.0/aframe.min.js"></script>
    <script src="https://unpkg.com/aframe-teleport-controls@0.2.0/dist/aframe-teleport-controls.min.js"></script>
    <script src="https://unpkg.com/aframe-controller-cursor-component@0.2.2/dist/aframe-controller-cursor-component.min.js"></script>
    <script src="https://rawgit.com/dmarcos/aframe-motion-capture/master/dist/aframe-motion-capture.min.js"></script>
    <script src="components/random-color.js"></script>
    <script src="components/snap.js"></script>
  </head>
  <body>
    <a-scene avatar-recorder>
      <a-assets>
        <img id="groundTexture" src="https://cdn.aframe.io/a-painter/images/floor.jpg">
        <img id="skyTexture" src="https://cdn.aframe.io/360-image-gallery-boilerplate/img/sechelt.jpg">
        <a-mixin id="voxel"
           geometry="primitive: box; height: 0.5; width: 0.5; depth: 0.5"
           material="shader: standard"
           random-color
           snap="offset: 0.25 0.25 0.25; snap: 0.5 0.5 0.5"
        ></a-mixin>
        <a-mixin id="triangle"
           geometry="primitive: cone; height: 0.5; radiusBottom: 0.5; segmentsRadial: 3"
           material="shader: standard"
           random-color
           snap="offset: 0.25 0.25 0.25; snap: 0.5 0.5 0.5"
        ></a-mixin>
      </a-assets>

      <a-sky id="bg" radius="30" src="#skyTexture" theta-length="180"></a-sky>

      <a-cylinder id="ground" src="#groundTexture" radius="32" height="0.1"></a-cylinder>

      <!-- Persegi -->
      <a-entity position="-4 0.25 -2" geometry="primitive: box; width: 2; height: 0.5; depth: 2" material="color: gray"></a-entity>
      <a-entity position="4 0.25 -2" geometry="primitive: box; width: 2; height: 1; depth: 2" material="color: blue"></a-entity>
      <a-entity position="-4 0.25 2" geometry="primitive: box; width: 2; height: 0.75; depth: 2" material="color: red"></a-entity>
      <a-entity position="4 0.25 2" geometry="primitive: box; width: 2; height: 1.5; depth: 2" material="color: green"></a-entity>

      <!-- Segitiga -->
      <a-entity position="0 0.25 0" mixin="triangle" material="color: yellow"></a-entity>

      <!-- Hands -->
      <a-entity id="teleHand"
        hand-controls="left"
        teleport-controls="type: parabolic; collisionEntities: [mixin='voxel'], #ground"
      ></a-entity>

      <a-entity id="blockHand"
        hand-controls="right"
        controller-cursor
        intersection-spawn="event: click; mixin: voxel"
      ></a-entity>

      <!-- Kamera -->
      <a-camera>
        <a-cursor
          intersection-spawn="event: click; mixin: voxel"
        ></a-cursor>
      </a-camera>
    </a-scene>
  </body>
</html>



<!-- Copyright 2018 Google LLC.
     SPDX-License-Identifier: Apache-2.0 -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>model-viewer-example</title>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="stylesheet" href="/style.css" />
  </head>
  <body>
    <script
      type="module"
      src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"
    ></script>
    <script
      nomodule
      src="https://unpkg.com/@google/model-viewer/dist/model-viewer-legacy.js"
    ></script>
    <div class="demo">
      <model-viewer
        id="mv-shark"
        shadow-intensity="0"
        src="https://cdn.glitch.com/addcef2a-6839-4455-94d6-bcf986bfcf1c%2Fmodel.glb?v=1596225062063"
        camera-controls

      ></model-viewer>
    </div>
  </body>
</html>

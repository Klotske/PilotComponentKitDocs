---
title: "ClippingPlaneExtension"
draft: false
---

**ClippingPlaneExtension** -- расширение, которое позволяет задать секущие плоскости на сцене.

Расширение имеет имя `PilotWeb3D.ClippingPlane`.

Пример подключения в `html`:
```html
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/ClippingPlane3D/ClippingPlane.min.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ClippingPlane");
```

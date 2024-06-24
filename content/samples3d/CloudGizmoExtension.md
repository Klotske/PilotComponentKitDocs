---
title: "CloudGizmoExtension"
draft: false
---

**CloudGizmoExtension** -- пример расширения, которое использует API расширения [ModelPartGizmo](../../extensions3d/ModelPartGizmoExtension) для редактирования положения облаков точек на сцене.
Расширение имеет имя `CloudGizmoExtensionSample`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/samples/CloudGizmoExtension/CloudGizmoExtension.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
await viewer.extensionsLoader.loadExtension("CloudGizmoExtensionSample");
```